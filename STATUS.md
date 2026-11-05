# Release status — Vynalth AI VPN

Last verified: 2026-11-05 (UTC+8). Public **beta**, not production-approved.

Official beta tag: [v1.1.0-beta-20261104](https://github.com/vyncuslim/vynalth-vpn-downloads/releases/tag/v1.1.0-beta-20261104)

| Client | Publication | SHA-256 | Source |
|---|---|---|---|
| Windows 1.1.0 EXE | **PUBLISHED** (GitHub Release asset) | `AC75B97C22EC9AD59955BC37E8AF0BA7136AE4E1717C95F70C402903390D58DA` | [Download EXE](https://github.com/vyncuslim/vynalth-vpn-downloads/releases/download/v1.1.0-beta-20261104/Windows-Vynalth-AI-VPN-Setup-1.1.0.exe) |
| Android 1.2.1 APK | **PUBLISHED** (GitHub Release asset) | `09FD8CE9B4F8146C0D09B23151C70BDE08E69572940A72579A52137BE2D4CD11` | [Download APK](https://github.com/vyncuslim/vynalth-vpn-downloads/releases/download/v1.1.0-beta-20261104/Android-Vynalth-AI-VPN-1.2.1-security-fix.apk) |
| Linux Desktop 1.1.0 | **NOT PUBLISHED** — corrected Beta archive awaits transfer to public hosting | Expected `9109F105C62FA9BF738AB199A8BAE0C49162338436CE30A990CE07F152CDE334` | No public URL |
| Linux CLI 1.1.0 | **PUBLISHED** (Vercel Beta) | `64F32CE669A0FE56E81B29CD4D4FFA9316E777AC3AA64CE3FD4F1EF860AAFBCF` | [Download CLI](https://vynalth-ai-vpn.vercel.app/downloads/Linux-CLI-vynalth-vpn) |

Windows and Android publication evidence:
- GitHub Actions recovery workflow run [42050658850](https://github.com/vyncuslim/vynalth-vpn-downloads/actions/runs/42050658850) **SUCCESS**.
- GitHub REST release metadata reports `prerelease: true`, both asset sizes matching the expected binaries, and both matching `sha256:` digests.
- Windows 83,399,896 bytes; Android 15,255,790 bytes.

Linux GUI build note:
- The original user-supplied 107,850,966-byte tarball SHA-256 `9E15AC9E...` has all 76 tar entries marked `0777`; **do not publish as a trusted build**.
- The corrected candidate is 107,747,536 bytes with SHA-256 `9109F105...`, but live Linux installation and Electron sandbox still require acceptance.
- Source transfer remains pending; do not invent a downloadable URL or mark it published.

Pending acceptance: Windows Authenticode publisher signing, Android real-device connectivity and update testing, Linux GUI installation and sandbox testing, Linux CLI live SG-01 dual-stack validation. SHA-256 only proves matching bytes, not application safety.
