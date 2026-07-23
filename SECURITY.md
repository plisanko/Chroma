# MineLock Security Policy

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

## Supported versions

Security support is provided on a best-effort basis for the latest public MineLock beta only. Older builds, private development builds, and files from unofficial sources are not promised security updates.

No public beta executable is currently offered from this documentation repository. Current local beta executables are not Authenticode-signed.

## Reporting a vulnerability

Report a suspected MineLock vulnerability privately by email:

- To: [minelock@proton.me](mailto:minelock@proton.me)
- Subject: `[MineLock Security]`

Include, where possible:

- The MineLock version, edition, and whether it is installed or portable.
- Windows version and relevant environment details.
- Clear reproduction steps and whether the issue reproduces consistently.
- Expected behavior, actual behavior, and potential security impact.
- Minimal, redacted screenshots, logs, or proof-of-concept details needed to understand the report.

Do not place passwords, live tokens, refresh tokens, device codes, private keys, or full unredacted logs in a report. If highly sensitive evidence is necessary, first send a brief description and ask how to proceed.

Do not open a public GitHub issue containing an unpatched vulnerability, exploit details, secrets, account information, tokens, device codes, or unredacted logs.

## What happens after a report

Reports are reviewed on a best-effort basis. The maintainer may ask for clarification, attempt reproduction, prepare a fix, or determine that the issue belongs to Microsoft, Minecraft, a loader, a mod, Electron, or another provider.

MineLock does not promise a response or resolution time. There is currently no bug bounty, paid reward, service-level agreement, or promised PGP reporting channel. Please allow a reasonable opportunity to investigate before public disclosure, but this request does not override applicable law.

Account compromise, suspicious Microsoft sign-in activity, purchases, billing, and entitlement issues should also be reported directly to Microsoft or Minecraft Support. MineLock cannot recover or secure provider accounts.

## Security architecture summary

- Microsoft sign-in uses MSAL OAuth 2.0 device authorization with the `consumers` authority and scopes `XboxLive.signin` and `offline_access`.
- MineLock never accepts a Microsoft password, has no client secret, and has no developer-operated authentication backend or proxy.
- Authentication and content requests are sent directly to Microsoft, Xbox Live, XSTS, Minecraft, Mojang, and relevant content providers.
- The short-lived Minecraft access token is kept in memory for the active session.
- If Electron `safeStorage` is available and secure, the MSAL cache and account mapping can persist encrypted on the local device.
- If secure storage is unavailable or insecure, authentication is session-only instead of being persisted in plaintext.
- Signing out removes the selected account's MSAL cache record and mapping. Closing the app clears the in-memory session.

These controls reduce certain risks but do not guarantee that MineLock, the device, third-party services, mods, or downloaded content are secure.

## Download authenticity

Current local beta executables are not Authenticode-signed and may trigger Microsoft Defender SmartScreen. This is a disclosure, not an instruction to ignore a warning. Users should stop if the file source or integrity cannot be verified. Future builds may be signed or unsigned, and each release should be checked separately.

If a public build is published:

1. Obtain it only from the canonical [MineLock Releases page](https://github.com/plisanko/minelock/releases).
2. Read that release's stated Authenticode signing status.
3. Calculate the downloaded file's SHA-256 hash with a trusted local tool.
4. Compare the complete hash with the SHA-256 value published on the same release page before running the file.

A matching hash checks the file against the value published on the release page. It does not by itself prove that a file is safe or that the user's device is uncompromised.

## User security guidance

- Never send anyone a Microsoft or Minecraft password, token, device code, or full unredacted log.
- Complete device authorization only on a genuine Microsoft-hosted page reached through a trusted flow.
- Review mods and other third-party files before installation and obtain them from sources the user trusts.
- Keep Windows, MineLock, Java, Minecraft, loaders, and relevant dependencies updated.
- Back up valuable worlds and instances before beta updates or major mod changes.
- Use [Microsoft Support](https://support.microsoft.com/contactus) or [Minecraft Help](https://help.minecraft.net/hc/en-us) for provider account or billing problems.

For non-security questions, see [Contact](CONTACT.md). For local data handling, see the [Privacy Policy](PRIVACY.md).
