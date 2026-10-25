# Chroma Client Security Policy

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

Last updated: 2026-10-25

## Supported versions

Security support is provided on a best-effort basis for the latest public Chroma Client (formerly MineLock) beta only. The current version is 0.9.0-beta.2. Older builds, private development builds, and files from unofficial sources are not promised security updates.

No public beta executable is currently offered from this documentation repository. Current beta executables are not Authenticode-signed. Chroma Client has no automatic updater; updates are installed manually.

## Reporting a vulnerability

Report a suspected Chroma Client vulnerability privately by email:

- To: [minelock@proton.me](mailto:minelock@proton.me)
- Subject: `[Chroma Client Security]`

Include, where possible:

- The Chroma Client version, whether it is the installer, portable, or unpacked build, and whether the data folder came from an older MineLock version.
- Windows version and relevant environment details.
- Clear reproduction steps and whether the issue reproduces consistently.
- Expected behavior, actual behavior, and potential security impact.
- Minimal, redacted screenshots, logs, or proof-of-concept details needed to understand the report.

Do not place passwords, live tokens, refresh tokens, device codes, private keys, or full unredacted logs in a report. If highly sensitive evidence is necessary, first send a brief description and ask how to proceed.

Do not open a public GitHub issue containing an unpatched vulnerability, exploit details, secrets, account information, tokens, device codes, or unredacted logs.

## What happens after a report

Reports are reviewed on a best-effort basis. The maintainer may ask for clarification, attempt reproduction, prepare a fix, or determine that the issue belongs to Microsoft, Minecraft, a loader, a mod, Electron, or another provider.

Chroma Client does not promise a response or resolution time. There is currently no bug bounty, paid reward, service-level agreement, or promised PGP reporting channel. Please allow a reasonable opportunity to investigate before public disclosure, but this request does not override applicable law.

Account compromise, suspicious Microsoft sign-in activity, purchases, billing, and entitlement issues should also be reported directly to Microsoft or Minecraft Support. Chroma Client cannot recover or secure provider accounts.

## Security architecture summary

- Microsoft sign-in uses MSAL with the Windows Account Manager (WAM) native broker, the `consumers` authority, and scopes `XboxLive.signin`, `openid`, `profile`, and `offline_access`. Windows displays the sign-in dialog.
- Chroma Client never receives a Microsoft password, has no client secret, and has no developer-operated authentication backend or proxy.
- Authentication and content requests are sent directly to Microsoft, Xbox Live, XSTS, Minecraft, Mojang, and relevant content providers. Downloads use HTTPS only, from a fixed list of provider hosts, with redirects re-checked and file hashes verified where the provider supplies them.
- The short-lived Minecraft access token is kept in memory for the active session.
- If Electron `safeStorage` is available and secure, the MSAL account cache (stored without access or ID tokens) and account mapping can persist encrypted on the local device.
- If secure storage is unavailable or insecure, authentication is session-only instead of being persisted in plaintext.
- Removing an account from Chroma Client deletes its account mapping and clears its in-memory session; it does not sign the account out of Windows. Closing the app clears the in-memory session.
- The interface runs under a restrictive Content Security Policy that blocks scripted network requests, denies browser permission requests, and does not open new windows.
- Offline profiles are local only, involve no authentication, and are stored unencrypted.
- Chroma Client contains no telemetry, crash reporting, or automatic updater.

These controls reduce certain risks but do not guarantee that Chroma Client, the device, third-party services, mods, or downloaded content are secure.

## Download authenticity

Current beta executables are not Authenticode-signed and may trigger Microsoft Defender SmartScreen. This is a disclosure, not an instruction to ignore a warning. Users should stop if the file source or integrity cannot be verified. Future builds may be signed or unsigned, and each release should be checked separately.

If a public build is published:

1. Obtain it only from the canonical [Chroma Client Releases page](https://github.com/plisanko/minelock/releases).
2. Read that release's stated Authenticode signing status.
3. Calculate the downloaded file's SHA-256 hash with a trusted local tool.
4. Compare the complete hash with the SHA-256 value published on the same release page before running the file.

A matching hash checks the file against the value published on the release page. It does not by itself prove that a file is safe or that the user's device is uncompromised.

## User security guidance

- Never send anyone a Microsoft or Minecraft password, token, device code, or full unredacted log.
- Enter Microsoft credentials only in the genuine Windows account dialog opened by a trusted sign-in flow.
- Review mods and other third-party files before installation and obtain them from sources the user trusts.
- Keep Windows, Chroma Client, Java, Minecraft, loaders, and relevant dependencies updated.
- Back up valuable worlds and instances before beta updates or major mod changes. Deleting an instance in Chroma Client is permanent.
- Use [Microsoft Support](https://support.microsoft.com/contactus) or [Minecraft Help](https://help.minecraft.net/hc/en-us) for provider account or billing problems.

For non-security questions, see [Contact](CONTACT.md). For local data handling, see the [Privacy Policy](PRIVACY.md).
