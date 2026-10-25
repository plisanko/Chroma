# Chroma Client

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

A free Windows desktop launcher for managing Minecraft: Java Edition instances.

Chroma Client is an independent, non-commercial hobby project maintained by [@plisanko](https://github.com/plisanko) in Croatia. Current version: `0.9.0-beta.2`. Last updated: 2026-10-25.

This documentation covers the launcher only.

## Overview

Chroma Client creates isolated Minecraft: Java Edition instances and helps users install, manage, and launch them. It obtains official Mojang version metadata, game files, assets, and libraries as needed. Chroma Client does not bundle or redistribute paid Minecraft files.

Signing in with a legitimate Microsoft account that has a valid Minecraft: Java Edition entitlement is required for online play and Microsoft/Minecraft account features. Sign-in uses the Windows Account Manager, so the familiar Windows account dialog appears. The launcher can also create local offline profiles that need no Microsoft sign-in and do not verify ownership; they are not an authentication, licensing, or ownership bypass for any online service.

Minecraft is a trademark of Mojang and Microsoft. Chroma Client is not affiliated with them.

## Features

- Separate directories and settings for isolated game instances.
- Vanilla installation from official Mojang metadata and file services.
- Instance setup for Fabric, Quilt, Forge, and NeoForge, including Java runtimes provided by Mojang.
- Local mod file management, plus optional search and install of mods, resource packs, and shaders from Modrinth.
- Instance backups, a server list with status checks, local offline skins, and Minecraft patch notes.
- Minecraft: Java Edition launch and game-generated log access.

Loader compatibility describes technical support only. It does not imply approval, sponsorship, or endorsement by Fabric, Quilt, Forge, NeoForge, Modrinth, or their contributors.

## Authentication and entitlement flow

1. Chroma Client starts Microsoft sign-in through MSAL and the Windows Account Manager (WAM) native broker using the `consumers` authority. Windows shows its own account dialog attached to the launcher window.
2. It requests only `XboxLive.signin`, `openid`, `profile`, and `offline_access` for this sign-in flow.
3. Chroma Client never receives the user's Microsoft password. As a public desktop client, it has no client secret.
4. Tokens are exchanged directly with Microsoft, Xbox Live, XSTS, and Minecraft services. Chroma Client has no developer-operated backend, authentication proxy, or token relay.
5. Minecraft services verify the user's Minecraft: Java Edition entitlement and profile before launch-related access can complete.
6. The short-lived Minecraft access token is held in memory for the active app session.

See [Privacy](PRIVACY.md) for local token-cache behavior and third-party data processing.

## Data and security summary

- Chroma Client has no developer telemetry, analytics, crash reporting, advertising, in-app purchases, automatic updater, or remote Chroma Client backend.
- Launcher settings, instances, game files, mods, backups, profile metadata, offline profiles, and eligible authentication cache data are stored on the user's Windows device in `%APPDATA%\ChromaClient`.
- If Electron `safeStorage` encryption is available and secure, Chroma Client can persist the MSAL account cache (without access or ID tokens) and its account mapping in encrypted local storage. Otherwise, authentication is session-only rather than being persisted in plaintext.
- Authentication and content requests go directly to the relevant external provider. Those providers receive the network, request, and account information needed to serve the request under their own policies.
- Builds are currently not Authenticode-signed, so Microsoft Defender SmartScreen may show a warning.

Never send anyone a password, access token, refresh token, device code, or full unredacted log.

## Downloads

Chroma Client builds are published on the [Chroma Client Releases page](https://github.com/plisanko/Chroma/releases). Download builds only from the official GitHub releases page.

Version `0.9.0-beta.2` is built for 64-bit Windows as:

- `Chroma-Client-Setup-0.9.0-beta.2-x64.exe` (installer)
- `Chroma-Client-Portable-0.9.0-beta.2-x64.exe` (portable)
- `Chroma-Client-Unpacked-0.9.0-beta.2-x64.zip` (unpacked archive)

Do not trust Chroma Client binaries from an unofficial download location.

## Project and repository status

This repository contains public information and policy documents for Chroma Client. The application source code is not published here, and this documentation grants no license to it. Terms and notices accompanying an app release govern that binary.

## Documentation

- [Privacy Policy](PRIVACY.md)
- [Terms of Use](TERMS.md)
- [Security Policy](SECURITY.md)
- [Contact](CONTACT.md)

## Contact

Chroma Client is maintained by [@plisanko](https://github.com/plisanko). For project or privacy questions, email [minelock@proton.me](mailto:minelock@proton.me). See [Contact](CONTACT.md) before sending logs or account information.

Microsoft account recovery, purchases, billing, and Minecraft entitlement problems must be handled by Microsoft or Minecraft Support. Chroma Client cannot access or change provider accounts.

## Official policies and provider information

Chroma Client users are also subject to the applicable provider terms and policies, including:

- [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement)
- [Microsoft Services Agreement](https://www.microsoft.com/en-us/servicesagreement/)
- [Minecraft End User License Agreement](https://www.minecraft.net/en-us/eula)
- [Minecraft Usage Guidelines](https://www.minecraft.net/en-us/usage-guidelines)
- [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
- [Modrinth](https://modrinth.com/)
- [Fabric](https://fabricmc.net/)
- [Quilt](https://quiltmc.org/)
- [Minecraft Forge](https://minecraftforge.net/)
- [NeoForge](https://neoforged.net/)

These external projects and services are independent from Chroma Client, and their own terms and privacy practices apply.
