## 1. HTTP

port:80

The foundation of web communication. A request/response, stateless protocol.

Request structure:
```
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html
```

response structure:
```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>...</html>
```

#### Key methods

| Method | Purpose              |
| ------ | -------------------- |
| GET    | Retrieve resource    |
| POST   | Submit data (create) |
| PUT    | Replace resource     |
| PATCH  | Partial update       |
| DELETE | Remove resource      |
| HEAD   | GET without body     |
#### Status codes

| Code | Name                  | Class            | Meaning                                                                                    |
| ---- | --------------------- | ---------------- | ------------------------------------------------------------------------------------------ |
| 200  | OK                    | 2xx Success      | Request succeeded; response body contains the result                                       |
| 301  | Moved Permanently     | 3xx Redirection  | Resource has permanently moved to a new URL; clients should update bookmarks/links         |
| 302  | Found                 | 3xx Redirection  | Resource temporarily at a different URL original should be used in future requests         |
| 304  | Not Modified          | 3xx Redirection  | Cached copy is still valid; no body returned (used with conditional requests)              |
| 400  | Bad Request           | 4xx Client Error | Authentication is required and has failed or not been provided.                            |
| 403  | Forbidden             | 4xx Client Error | Server understood the request but refuses to authorize it. (authenticated but not allowed) |
| 404  | Not Found             | 4xx Client Error | The requested resource dosen't exist on the server.                                        |
| 500  | Internal Server Error | 5xx Server Error | Generic error; server encountered an unexpected condition                                  |
| 502  | Bad Gateway           | 5xx Server Error | Server acting as a gateway/proxy received an invalid response from an upstream server      |
| 503  | Service Unavailable   | 5xx Server Error | Server is temporarily overloaded or under maintenance; try again later                     |

---
## 2. HTTPS

port: 443

HTTP wrapped in TLS encryption. provides three guarantee:

1. Confidentiality - traffic encrypted (can't be read in transit)
2. Integrity - tamper detection
3. Authentication - server identity proven via X.509 certificate signed by a trusted CA

>Without HTTPS, credentials, cookies, and content visible to anyone on the path (MITM). Modern browsers flag plain HTTP as HTTP as "Not Secure". HSTS forces HTTPS; certificate pinning defends aganist rogue CAs.

---
## 3. DNS (Domain name system)

port: 53

The Internet's phone-book: translates human names (`google.com`)into IP addresses (`142.251.223.14`). A distributed, hierarchical database

#### Resolution flow

1. Client asks recursive resolver (eg: 8.8.8.8)
2. Resolver asks a root server -> referred to `.com` TLD server
3. Resolver asks TLD server -> referred to `example.com`'s authoriative NS.
4. Resolver asks authoritative NS -> gets the A record
5. Resolver caches the answer (per TTL) and returns it to the client.

#### Record types

| Type  | Meaning               |
| ----- | --------------------- |
| A     | IPv4 address          |
| AAAA  | IPv6 address          |
| CNAME | Alias to another name |
| MX    | Mail server           |
- Caching at every level (browser, OS, resolver)
- UDP by default; TCP when response > 512 bytes or for zone transfers (AXFR)

---
## 4. DHCP

port (server): 67, (client): 68 - UDP

- **UDP Port 67** is used by the **DHCP server** to listen for client requests.
- **UDP Port 68** is used by the **DHCP client** to receive server responses.

DHCP automatically assigns IP configuration to hosts, elimination manual setup. Uses broadcast because because the client has no IP yet.

#### DORA process (4 steps):

1. **Discover** - client broadcast "is there a DHCP server?" (source 0.0.0.0 -> 255.255.255.255)
2. **Offer** - server proposes an IP + config
3. **Request** - client formally requests the offered IP
4. **Acknowledge** - server confirms; client may also get gateway, DNS lease time

**What DHCP hands out:** IP address, subnet mask, default gateway, DNS servers, lease duration, NTP/WPAD options.

#### Concepts

- **DHCP relay** — forwards broadcasts across subnets to a central server (routers don't pass broadcasts).
- **Reservation** — bind a specific MAC to a fixed IP (static-like but centrally managed).
- **Rogue DHCP server** — a major attack vector (MITM); use **DHCP snooping** on switches.
- **APIPA** (169.254.x.x) — self-assigned when no DHCP answer; a telltale sign of DHCP failure.

---
## 5. FTP

Ports: 21 - TCP

Classic protocol for transferring files between client and server. Uses two separate connections: a control channel and a data channel (actual file bytes).

Active vs Passive:

- Active - server initiates the data connection back to the client (port -> 20 client). fails behind NAT/firewalls.
- Passive - client initiates both connection; server opens an ephemeral port and tells the client. preferred in modern networks.

commands:
`USER/PASS`,`LIST`,`RETR`,`STOR`,`CWD`,`QUIT`.

#### Weakness

- Plaintext: credentials and data sent unencrypted -> sniffable
- Complex firewall/NAT behavior (dual connections, dynamic ports).

#### Secure alternatives

- FTPS - FTP over TLS
- SFTP - file transfer over SSH (single encrypted channel, port 22). Not the same as FTPS despite the similar name. 
- SCP - simple copy over SSH

>FTP still appears in legacy systems, embedded devices, and some backup tooling, but SFTP/FTPS should be used for anything sensitive.

---
## 6. SMTP

Port: 25 

The protocol for sending email - pushing messages from client -> server and server -> server (Note: receiving is done by IMAP/POP3)

#### Basic flow:
```
EHLO client.example.com
MAIL FROM:<alice@example.com>
RCPT TO:<bob@example.org>
DATA
Subject: Hello
...
.
QUIT
```

#### How mail travels

1. User's mail client submits to their **outgoing server** (port 587, authenticated).
2. Sender's server does a **DNS MX lookup** for the recipient's domain.
3. Connects to the recipient's MX server (port 25) and relays the message.
4. Recipient retrieves it via IMAP/POP3.

#### Security - Email Authentication

| Mechanism | Purpose                                                              |
| --------- | -------------------------------------------------------------------- |
| SPF       | DNS TXT record listing authorized sending IPs                        |
| DKIM      | Cryptographic signature on the message (verifies integrity/origin)   |
| DMARC     | Policy tying SPF+DKIM together; tell receivers what to do on failure |
>Without these, spoofing/phishing is trivial. SMTP itself has **no built-in authentication or encryption** — those come from AUTH, STARTTLS, SPF/DKIM/DMARC.

**Common issues:** port 25 blocked by ISPs, blacklisting, misconfigured MX records, SPF failures landing mail in spam.

---
## 7. SSH (Secure Shell)

port: 22 TCP

Encrypted protocol for **remote login, command execution, file transfer and tunneling**. Replaced insecure Telnet/rlogin

#### How SSH works

1. **TCP connect** to port 22.
2. **Protocol/Key exchange**: negotiate algorithms, perform Diffie-Hellman key exchange -> shared session key.
3. **Server authentication**: client verifies the server's **host key** (stored in known_hosts) mismatch = possible MITM warning.
4. **Client authentication** — via password or, preferably, **public key**:
	
	- Client proves possession of a private key by signing a challenge.
	- Server checks the matching public key in `~/.ssh/authorized_keys`.
	
5. **Encrypted session** begins — shell, commands, or port forwarding.

#### Features and uses

- **Public-key auth** — passwordless, more secure; protect the private key with a passphrase.
- **SCP / SFTP** — file transfer over SSH.

#### Quick Reference

| Protocol | Port(s)    | Transport | Purpose                   | Secure version  |
| -------- | ---------- | --------- | ------------------------- | --------------- |
| HTTP     | 80         | TCP       | Web (Plaintext)           | HTTPS           |
| HTTPS    | 443        | TCP       | Web (Encrypted)           | ---             |
| DNS      | 443        | TCP/UDP   | Name -> IP                | DoH/DoT, DNSSEC |
| DHCP     | 67/68      | UDP       | Auto IP config            | DHCP snooping   |
| FTP      | 20/21      | TCP       | File transfer (plaintext) | FTPS / SFTP     |
| SMTP     | 25/587/465 | TCP       | Send email                | SPF/DKIM/DMARC  |
| SSH      | 22         | TCP       | Secure remote access      | ---             |

---
## Reference

- [TryHackMe - Networking Concepts](https://tryhackme.com/room/networkingconcepts)
- [TryHackMe - Essentials](https://tryhackme.com/room/networkingessentials)














