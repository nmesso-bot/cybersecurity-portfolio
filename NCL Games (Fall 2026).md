## My CTF Experience

I competed in the **National Cyber League (NCL) Fall 2026** season, which includes
a practice game, an individual game, and a team game. NCL challenges are organized
into nine categories, and I trained deliberately across all of them rather than
specializing early:

- **Password Cracking** — hash identification and dictionary, mask, and hybrid
  attacks with `hashcat`
- **Log Analysis** — reconstructing attacker timelines from auth logs, web access
  logs, proxy logs, Sysmon events, and a proprietary binary format
- **Cryptography** — classical ciphers, encodings, steganography, XOR, and RSA
- **OSINT** — EXIF metadata, DNS records, WHOIS, PGP key servers, SSL
  certificates, and barcode decoding
- **Forensics** — Git history recovery, file carving, magic-byte repair, Office
  document internals, and Windows memory analysis
- **Network Traffic Analysis** — DNS, FTP, HTTP, Telnet, custom protocols, CAN bus
  telemetry, and WEP/WPA decryption in Wireshark
- **Scanning & Reconnaissance** — `dig` enumeration, `nmap` fingerprinting, and
  raw service interaction with Netcat
- **Web Application Exploitation** — SQL injection, parameter tampering, type
  confusion, client-side privilege escalation, and directory traversal
- **Enumeration & Exploitation** — stack buffer overflows, debugger-driven code
  invocation, and reversing a Hill-cipher checker

In total I completed **60 preparation challenges across 30 hours**, logging
duration and a reflection for every one. That log is what taught me the most:
writing down *why* a technique worked, not just that it did, is what turned
individual challenges into transferable skills.

## Highlights

**Memory forensics under pressure.** The hardest challenge I completed was a
Windows memory dump analysis using Volatility 3. The framework wouldn't parse the
target's Insider Preview kernel build, so I pinned the repository to a specific
commit and resolved the missing crypto dependencies before I could extract
anything. From there I recovered the hostname, the logged-in user, a suspicious
database file on the desktop, and finally the user's password from the SAM hive via
`windows.hashdump` and offline cracking. The lesson wasn't "Volatility works" — it
was that tooling breaks against non-standard environments and you have to debug the
tool before you can use it.

**Wireless cryptography.** I recovered both a 64-bit and a 128-bit WEP key from
packet captures using `aircrack-ng`, then loaded each key into Wireshark to decrypt
the sessions. Seeing that a larger key size changed nothing about WEP's structural
weakness made the IV-reuse flaw concrete in a way reading about it never did. I
followed that with a WPA-PSK handshake crack and full HTTP decryption.

## NCL Score Reports

Individual and team score reports are published by NCL approximately two weeks
after the team game. Links will be added here as soon as they are released.

- **Individual Game:** <!-- public share link -->
- **Team Game:** <!-- public share link -->
