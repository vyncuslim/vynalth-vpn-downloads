# Vynalth AI VPN — Dual-Stack Beta, 2026-11-06

**Published:** 2026-11-07 (Malaysia time), prerelease only. No production QA certificate.

GitHub Release: https://github.com/vyncuslim/vynalth-vpn-downloads/releases/tag/v1.2.0-beta-dualstack-20261106

| Client | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| Windows 1.2.0 | `Windows-Vynalth-AI-VPN-Setup-1.2.0.exe` | 83,400,381 | `43C0E57C394D3155320CE1C06DC6182DA03FC687764A4678D429F1AF64629A4D` |
| Android 1.2.3 | `Android-Vynalth-AI-VPN-1.2.3-dual-stack.apk` | 15,255,790 | `E63F2846A0E6E7A4A6B59F5DD57A593E1A18326E0AE893942DB8DC1EA94A62AF` |
| Linux GUI 1.2.0 — corrected packaging | `Linux-vynalth-vpn-app-1.2.0-x86_64.tar.gz` | 107,747,265 | `CC1DCF09E1D29AD3F86BD5D1A0639F9EDEC8D8C7F87E311169E6BB4218B3E40E` |

## Verified

- Uploaded ZIP `Vynalth_AI_VPN_All_Platforms_DualStack_20261106.zip`: archive CRC OK and all four contained file SHA-256 digests match individually supplied files.
- Corrected Linux Desktop Beta tarball contains 76 regular files/directories, no symlinks or path traversal, no group/other-write permissions. Directories and ELF executables are 0755; other content 0644. Its contents are repackaged from the user-provided source file.
- Public GitHub release asset byte counts and digests matched all three expected values.
- GitHub Actions publish workflow: https://github.com/vyncuslim/vynalth-vpn-downloads/actions/runs/42357538425 — SUCCESS.
- Linux CLI **not** updated to the 6291-byte uploaded script. That file's SHA-256 is `B14995AED85FBC5AA39D69FB33BB102B6AA49DE37FF98E53603FBB33442DD064`; previously identified handshake/dual-stack status detection defects remain. The separately reviewed 6039-byte CLI retains the public download at https://vynalth-ai-vpn.vercel.app/downloads/Linux-CLI-vynalth-vpn, SHA-256 `64F32CE669A0FE56E81B29CD4D4FFA9316E777AC3AA64CE3FD4F1EF860AAFBCF`.

## Open release gates

- None of the four platform clients has completed actual end-to-end SG-01 dual-stack WireGuard device testing.
- Windows EXE Authenticode signing and native Windows user acceptance pending.
- Android APK install, upgrade, background, and IPv4/IPv6 tunnel acceptance pending.
- Linux GUI Electron sandbox mechanism and distro-specific installation pending. **Do not use `--no-sandbox` as an implied safety fix.**
- No stable-production qualification or compliance attestation is claimed.
- Signed temporary staging URLs in one-time upload Actions workflows have expiration dates and are not long-term public distribution links; official distribution is the GitHub Release above.

## Previous versions

The November 4 prerelease remains available for reproducibility:
https://github.com/vyncuslim/vynalth-vpn-downloads/releases/tag/v1.1.0-beta-20261104
