# Vynalth AI VPN — Beta Downloads

Official download repository for **Vynalth AI VPN experimental builds**. Releases are distributed as **pre-releases**, not stable or fully security-certified products.

## Intended beta release

Tag: `v1.1.0-beta-20261104`

| Platform | Asset name | Expected bytes | SHA-256 |
|---|---|---:|---|
| Windows 1.1.0 | `Windows-Vynalth-AI-VPN-Setup-1.1.0.exe` | 83,399,896 | `AC75B97C22EC9AD59955BC37E8AF0BA7136AE4E1717C95F70C402903390D58DA` |
| Android 1.2.1 | `Android-Vynalth-AI-VPN-1.2.1-security-fix.apk` | 15,255,790 | `09FD8CE9B4F8146C0D09B23151C70BDE08E69572940A72579A52137BE2D4CD11` |
| Linux Desktop 1.1.0 | `Linux-vynalth-vpn-app-1.1.0-x86_64.tar.gz` | 107,747,536 | `9109F105C62FA9BF738AB199A8BAE0C49162338436CE30A990CE07F152CDE334` |

**IMPORTANT:** Use the Linux GUI tarball whose SHA-256 starts `9109F105`. The older archive with SHA-256 `9E15AC9E...` has unsafe world-writable file modes and must **not** be published.

The Linux CLI Beta is currently served independently at [the Vynalth AI VPN website](https://vynalth-ai-vpn.vercel.app/downloads/Linux-CLI-vynalth-vpn).

## Publish and verify

1. On this repository's **Releases** page, select **Draft a new release**.
2. Set tag `v1.1.0-beta-20261104` from `main`.
3. Attach the three exact prevalidated assets listed above; do not upload files to the repository's **Code** tab.
4. Check **Set as a pre-release** and publish.
5. After upload, verify that GitHub's asset sizes and SHA-256 digests match the table above.
6. Visit [live release API](https://vynalth-ai-vpn.vercel.app/api/releases) and confirm `windows.published`, `android.published`, and `linuxGui.published` each become `true`.
7. Check each button at [Get Vynalth AI VPN](https://vynalth-ai-vpn.vercel.app/#downloads).

## Safety and limitations

- Windows installer is not Authenticode signed. Treat publisher warnings and downloaded binary provenance carefully.
- Android APK v2 signing and 64-bit 16 KiB alignment were statically checked, but device upgrade, OAuth, VPN connectivity and 32-bit compatibility are not fully accepted.
- Linux Desktop archive permissions were repaired in the replacement Beta archive, but Linux distro installation and SG-01 VPN operation still require testing.
- Never include VPN private keys, configuration profiles with secrets, API tokens or `.env` files in Release assets.
- A matching SHA-256 proves the download matches the designated artifact; it does not certify the software's safety.
