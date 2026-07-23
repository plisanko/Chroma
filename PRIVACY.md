# MineLock Privacy Policy

Effective date: 2026-07-23

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

## 1. Scope and operator

This policy explains how the MineLock Windows desktop launcher handles information. It also covers information voluntarily sent to MineLock support. It does not replace the privacy policies of Microsoft, Mojang, Minecraft, GitHub, loader projects, or other external services.

MineLock is an independent, non-commercial hobby project operated and maintained by [@plisanko](https://github.com/plisanko) in Croatia. Privacy questions can be sent to [minelock@proton.me](mailto:minelock@proton.me).

## 2. Privacy design

MineLock has no developer-operated telemetry, analytics, advertising, purchasing system, or remote MineLock backend. Authentication is not routed through a MineLock server or proxy.

This does not mean that no information is processed. The app processes data on the user's device and makes direct requests to external services needed for authentication, entitlement checks, downloads, loader support, and launch. Those services receive information under their own policies.

## 3. Information processed on the device

MineLock may process and store the following information locally:

- Launcher preferences, configuration, and instance definitions.
- Official Minecraft metadata, game files, assets, and libraries downloaded for the user's instances.
- Locally managed mods and files for Vanilla, Fabric, Quilt, Forge, or NeoForge instances.
- Game-generated logs and other files created by Minecraft or installed components.
- Minecraft profile metadata used by the launcher, including UUID, player name, skin, and cape metadata.
- MSAL account linkage, account mapping, and authentication cache data, subject to the storage rules below.

Game logs and mod files can contain information produced by Minecraft, third-party components, or the user. Users should review and redact logs before sharing them.

### Authentication storage

MineLock uses Microsoft Authentication Library (MSAL) device authorization with the Microsoft `consumers` authority and the scopes `XboxLive.signin` and `offline_access`.

- MineLock never accepts or stores the user's Microsoft password.
- The app is a public client and has no client secret.
- A short-lived Minecraft access token is held in memory for the active app session.
- If Electron `safeStorage` encryption is available and reports secure storage, the MSAL cache and MineLock's account mapping can persist encrypted on the device.
- If secure local encryption is unavailable or insecure, authentication is session-only. MineLock does not fall back to persisting that authentication data in plaintext.
- Closing MineLock clears the in-memory authentication session.

## 4. External services and disclosure

MineLock sends requests directly to the services required for the selected operation. Normal network, request, device, and account information can be received by those providers, such as an IP address, request headers, service identifiers, authentication data, profile data, entitlement status, and requested file information.

### Microsoft, Xbox, Minecraft, and Mojang

Microsoft-hosted OAuth 2.0 device authorization is used for sign-in. MineLock then communicates directly with Microsoft, Xbox Live, XSTS, Minecraft, and Mojang endpoints for authentication, entitlement and profile checks, metadata, and game content.

The following provider documents apply:

- [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement)
- [Microsoft Services Agreement](https://www.microsoft.com/en-us/servicesagreement/)
- [Minecraft End User License Agreement](https://www.minecraft.net/en-us/eula)
- [Minecraft Usage Guidelines](https://www.minecraft.net/en-us/usage-guidelines)

MineLock requires a legitimate Microsoft account and Minecraft: Java Edition entitlement. MineLock cannot inspect, recover, bill, or modify a user's Microsoft or Minecraft account outside the access returned to the app by those services.

### Loader and distribution providers

When a user selects a supported loader or related content, MineLock may request metadata or files from the relevant external provider:

- [Fabric](https://fabricmc.net/)
- [Quilt](https://quiltmc.org/)
- [Minecraft Forge](https://minecraftforge.net/)
- [NeoForge](https://neoforged.net/)

Those providers are independent and apply their own privacy practices and terms. Technical compatibility does not imply their endorsement of MineLock.

### GitHub

This documentation is hosted on GitHub. A future public MineLock release may also be provided through GitHub Releases. Visiting the repository or downloading a release causes GitHub to process information under the [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).

## 5. Support communications

The support address receives only information a person voluntarily sends by email. That may include the sender's email address, message, attachments, and any diagnostic information the sender chooses to provide. Email providers necessarily process those messages.

Do not send Microsoft or Minecraft passwords, access or refresh tokens, device codes, private keys, or full unredacted logs. MineLock support does not need them. Redact account identifiers and unrelated personal information whenever possible.

Support messages may be retained as needed to respond, investigate a reported problem, preserve security context, and meet applicable obligations. A sender may request deletion, although some information may need to be retained where required for security or legal reasons.

## 6. Retention and deletion

Local launcher and game data remains on the user's device until the user, the game, or MineLock removes it.

- Signing out removes the selected account's MSAL cache record and MineLock account mapping.
- Signing out does not automatically delete instances, game files, mods, logs, or unrelated provider-side account data.
- Closing the app clears the in-memory session, including the short-lived Minecraft token.
- Uninstalling MineLock may not remove its app data.
- To remove remaining local MineLock data, close the app and delete MineLock's Electron user-data folder, normally located under `%APPDATA%` on Windows. Back up any instances or files the user wants to keep first.

Deleting local MineLock data does not delete information held by Microsoft, Minecraft, GitHub, loader providers, email providers, or other external services. Contact the relevant provider and follow its policy for that data.

## 7. Security

MineLock uses available Electron secure local storage for eligible persisted authentication cache data and otherwise keeps authentication session-only. It also limits the Minecraft access token to app memory for the active session. These measures reduce risk but cannot guarantee security.

The device owner is responsible for operating-system security, malware protection, local account access, backups, and the security of installed mods. Current local beta executables are not Authenticode-signed and may trigger Microsoft Defender SmartScreen. See the [Security Policy](SECURITY.md) for release verification and vulnerability reporting.

## 8. Children

MineLock does not provide its own online account system and does not knowingly solicit children's personal information through a developer-operated backend. Microsoft and Minecraft account age, consent, and family requirements still apply.

A parent or guardian should supervise a child's use of MineLock, external accounts, mods, logs, and support email. A parent or guardian may contact MineLock about information a child voluntarily sent to the support address.

## 9. Choices and privacy requests

Users can inspect, copy, or delete MineLock's local files using their own Windows account, subject to files that are in use. They can sign out to remove the selected local authentication cache record and mapping.

Depending on applicable law, a person may have rights concerning personal information included in support correspondence. Requests can be sent to [minelock@proton.me](mailto:minelock@proton.me). MineLock may need enough information to identify the relevant correspondence and verify the request. Provider account or billing requests must be directed to the relevant external provider.

## 10. Changes

This policy may change as MineLock develops, its distribution changes, or legal and technical requirements change. Updates will be published in this repository with a revised effective date. Continued use after a change is subject to the updated policy to the extent permitted by applicable law.

See [Contact](CONTACT.md) for support and provider contact guidance.
