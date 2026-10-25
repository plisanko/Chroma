# Chroma Client Privacy Policy

Effective date: 2026-10-25

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

## 1. Scope and operator

This policy explains how the Chroma Client Windows desktop launcher, version 0.9.0-beta.2, handles information. It also covers information voluntarily sent to Chroma Client support. It covers the launcher only and does not replace the privacy policies of Microsoft, Mojang, Minecraft, GitHub, Modrinth, loader projects, or other external services.

Chroma Client is an independent, non-commercial hobby project operated and maintained by [@plisanko](https://github.com/plisanko) in Croatia. Privacy questions can be sent to [minelock@proton.me](mailto:minelock@proton.me).

## 2. Privacy design

Chroma Client has no developer-operated telemetry, analytics, crash reporting, advertising, purchasing system, automatic updater, or remote Chroma Client backend. Authentication is not routed through a Chroma Client server or proxy.

This does not mean that no information is processed. The app processes data on the user's device and makes direct requests to external services needed for authentication, entitlement checks, downloads, mod and loader support, and launch. Those services receive information under their own policies.

## 3. Information processed on the device

Chroma Client may process and store the following information locally, in its Electron user-data folder `%APPDATA%\ChromaClient`:

- Launcher preferences, configuration, and instance definitions.
- Official Minecraft metadata, game files, assets, libraries, and Java runtimes downloaded for the user's instances.
- Locally managed mods, resource packs, shaders, and other files for Vanilla, Fabric, Quilt, Forge, or NeoForge instances.
- Backups: world (saves) backup archives in `%APPDATA%\ChromaClient\backups`, created manually by the user or optionally before deleting an instance (a checkbox, ticked by default), and mod-update backups kept in a `.chroma-mods-backup` folder inside the instance folder.
- Offline profiles: a username chosen by the user, a UUID derived from it, a creation time, and an optional skin image the user selects.
- Minecraft profile metadata used by the launcher, including UUID, player name, skin, and cape metadata.
- MSAL account linkage, account mapping, and authentication cache data, subject to the storage rules below.
- Game-generated logs and other files created by Minecraft or installed components inside instance folders. The launcher's live console output is kept in memory.

Game logs and mod files can contain information produced by Minecraft, third-party components, or the user. Users should review and redact logs before sharing them.

### Authentication storage

Chroma Client uses Microsoft Authentication Library (MSAL) with the Windows Account Manager (WAM) native broker, the Microsoft `consumers` authority, and the scopes `XboxLive.signin`, `openid`, `profile`, and `offline_access`. Windows displays the sign-in dialog.

- Chroma Client never receives or stores the user's Microsoft password.
- The app is a public client and has no client secret.
- A short-lived Minecraft access token is held in memory for the active app session.
- If Electron `safeStorage` encryption is available and reports secure storage, the MSAL account cache and Chroma Client's account mapping can persist encrypted on the device. Access tokens and ID tokens are removed from the cache before it is written.
- If secure local encryption is unavailable or insecure, authentication is session-only. Chroma Client does not fall back to persisting that authentication data in plaintext.
- Closing Chroma Client clears the in-memory authentication session.
- Windows itself may keep the Microsoft account connected to Windows independently of Chroma Client.

Offline profiles involve no authentication. They are stored unencrypted in the launcher's state file and `offline-skins` folder.

## 4. External services and disclosure

Chroma Client sends requests directly to the services required for the selected operation. Normal network, request, device, and account information can be received by those providers, such as an IP address, request headers, service identifiers, authentication data, profile data, entitlement status, and requested file information. Network requests and downloads are made by the launcher's main process and are restricted to HTTPS addresses on a fixed list of provider hosts. The interface itself is not allowed to make scripted network requests; it only loads images, such as skins and project icons.

### Microsoft, Xbox, Minecraft, and Mojang

Microsoft sign-in is performed through Windows (WAM). Chroma Client then communicates directly with Microsoft, Xbox Live, XSTS, Minecraft, and Mojang endpoints for authentication, entitlement and profile checks, metadata, Java runtimes, game content, skin images (`textures.minecraft.net`), and Minecraft patch notes.

The following provider documents apply:

- [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement)
- [Microsoft Services Agreement](https://www.microsoft.com/en-us/servicesagreement/)
- [Minecraft End User License Agreement](https://www.minecraft.net/en-us/eula)
- [Minecraft Usage Guidelines](https://www.minecraft.net/en-us/usage-guidelines)

Online play requires a legitimate Microsoft account and Minecraft: Java Edition entitlement. Chroma Client cannot inspect, recover, bill, or modify a user's Microsoft or Minecraft account outside the access returned to the app by those services.

### Loader, library, and distribution providers

When a user selects a supported loader or related content, Chroma Client may request metadata or files from the relevant external provider:

- [Fabric](https://fabricmc.net/)
- [Quilt](https://quiltmc.org/)
- [Minecraft Forge](https://minecraftforge.net/)
- [NeoForge](https://neoforged.net/)
- Library repositories used by those loaders, such as Maven Central, SpongePowered, and ParchmentMC.

Those providers are independent and apply their own privacy practices and terms. Technical compatibility does not imply their endorsement of Chroma Client.

### Modrinth

When a user searches for or installs mods, resource packs, or shaders (including Fabric API), Chroma Client sends requests to `api.modrinth.com` and downloads files from `cdn.modrinth.com`. Requests can include the search text, project and version identifiers, and the instance's Minecraft version and loader, together with a `ChromaClient/<version>` user agent. Project icons in search results are loaded by the interface from the image address Modrinth returns. Downloaded files are checked against the hashes Modrinth provides. Modrinth's own policies apply.

### Minecraft servers

If a user adds a server to the launcher's server list, Chroma Client connects directly to that address to read its public status. It also looks up the DNS SRV record `_minecraft._tcp.<host>` through the system DNS resolver. The server operator can see the connecting IP address. Minecraft and its mods make their own connections once a game is launched, under their own policies.

### GitHub

This documentation is hosted on GitHub, and Chroma Client releases are provided through GitHub Releases. Visiting the repository or downloading a release causes GitHub to process information under the [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).

## 5. Support communications

The support address receives only information a person voluntarily sends by email. That may include the sender's email address, message, attachments, and any diagnostic information the sender chooses to provide. Email providers necessarily process those messages.

Do not send Microsoft or Minecraft passwords, access or refresh tokens, device codes, private keys, or full unredacted logs. Chroma Client support does not need them. Redact account identifiers and unrelated personal information whenever possible.

Support messages may be retained as needed to respond, investigate a reported problem, preserve security context, and meet applicable obligations. A sender may request deletion, although some information may need to be retained where required for security or legal reasons.

## 6. Retention and deletion

Local launcher and game data remains on the user's device until the user, the game, or Chroma Client removes it.

- Removing a Microsoft account from Chroma Client deletes Chroma Client's account mapping and clears its in-memory session. It does not sign the account out of Windows, and the encrypted MSAL cache file stays until the data folder is deleted.
- Removing an offline profile deletes its record and its stored skin image.
- Deleting an instance in Chroma Client permanently deletes that instance's folder; it is not moved to the Recycle Bin. World backup archives in the `backups` folder are separate files, but mod-update backups in the instance's `.chroma-mods-backup` folder are deleted together with the instance. Removing a mod moves it to the Windows Recycle Bin.
- Signing out or removing an account does not automatically delete instances, game files, mods, logs, or provider-side account data.
- Closing the app clears the in-memory session, including the short-lived Minecraft token.
- Uninstalling Chroma Client does not remove its app data. The installed and portable versions both use `%APPDATA%\ChromaClient`.
- To remove all local Chroma Client data, close the app and delete `%APPDATA%\ChromaClient`. Back up any instances or files the user wants to keep first.
- If a data folder from an earlier version exists (`%APPDATA%\MineLock`), the launcher moves or copies it to `%APPDATA%\ChromaClient` and never deletes it automatically; to remove old data, delete that folder yourself.

Deleting local Chroma Client data does not delete information held by Microsoft, Minecraft, GitHub, Modrinth, loader providers, email providers, or other external services. Contact the relevant provider and follow its policy for that data.

## 7. Security

Chroma Client uses available Electron secure local storage for eligible persisted authentication cache data and otherwise keeps authentication session-only. It also limits the Minecraft access token to app memory for the active session. These measures reduce risk but cannot guarantee security.

The device owner is responsible for operating-system security, malware protection, local account access, backups, and the security of installed mods. Builds are currently not Authenticode-signed, so Microsoft Defender SmartScreen may show a warning. See the [Security Policy](SECURITY.md) for download guidance and vulnerability reporting.

## 8. Children

Chroma Client does not provide its own online account system and does not knowingly solicit children's personal information through a developer-operated backend. Microsoft and Minecraft account age, consent, and family requirements still apply.

A parent or guardian should supervise a child's use of Chroma Client, external accounts, mods, logs, and support email. A parent or guardian may contact Chroma Client about information a child voluntarily sent to the support address.

## 9. Choices and privacy requests

Users can inspect, copy, or delete Chroma Client's local files using their own Windows account, subject to files that are in use. They can remove an account from the launcher to delete its local mapping.

Depending on applicable law, a person may have rights concerning personal information included in support correspondence. Requests can be sent to [minelock@proton.me](mailto:minelock@proton.me). Chroma Client may need enough information to identify the relevant correspondence and verify the request. Provider account or billing requests must be directed to the relevant external provider.

## 10. Changes

This policy may change as Chroma Client develops, its distribution changes, or legal and technical requirements change. Updates will be published in this repository with a revised effective date. Continued use after a change is subject to the updated policy to the extent permitted by applicable law.

See [Contact](CONTACT.md) for support and provider contact guidance.
