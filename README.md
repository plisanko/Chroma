# MineLock

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

A free Windows desktop launcher for managing Minecraft: Java Edition instances.

MineLock is an independent, non-commercial hobby project maintained by [@plisanko](https://github.com/plisanko) in Croatia. It is in beta and is intended for public distribution.

## Overview

MineLock creates isolated Minecraft: Java Edition instances and helps users install, manage, and launch them. It obtains official Mojang version metadata, game files, assets, and libraries as needed. MineLock does not bundle or redistribute paid Minecraft files.

Using MineLock requires a legitimate Microsoft account with a valid Minecraft: Java Edition entitlement. MineLock is not an authentication, licensing, or ownership bypass.

## Features

- Separate directories and settings for isolated game instances.
- Vanilla installation from official Mojang metadata and file services.
- Instance setup for Fabric, Quilt, Forge, and NeoForge.
- Local mod file management.
- Minecraft: Java Edition launch and game-generated log access.

Loader compatibility describes technical support only. It does not imply approval, sponsorship, or endorsement by Fabric, Quilt, Forge, NeoForge, or their contributors.

## Current application review status

MineLock uses a Microsoft Entra public Client ID. Approval of that Client ID by Minecraft Services is currently pending.

Microsoft OAuth device-code authentication and the Minecraft-targeted Xbox Live/XSTS exchange are working. The final Minecraft `login_with_xbox` request currently returns `HTTP 403 Invalid app registration`, so Microsoft account login cannot complete until the app registration is accepted for Minecraft Services.

Submitting this repository or a review request does not mean that MineLock has been approved. No Client ID is published in this documentation.

## Authentication and entitlement flow

1. MineLock starts Microsoft-hosted OAuth 2.0 device authorization through MSAL using the `consumers` authority.
2. It requests only `XboxLive.signin` and `offline_access` for this sign-in flow. The user completes authorization on a Microsoft-hosted page.
3. MineLock never accepts the user's Microsoft password. As a public desktop client, it has no client secret.
4. Tokens are exchanged directly with Microsoft, Xbox Live, XSTS, and Minecraft services. MineLock has no developer-operated backend, authentication proxy, or token relay.
5. Minecraft services verify the user's Minecraft: Java Edition entitlement and profile before launch-related access can complete.
6. The short-lived Minecraft access token is held in memory for the active app session.

See [Privacy](PRIVACY.md) for local token-cache behavior and third-party data processing.

## Data and security summary

- MineLock has no developer telemetry, analytics, advertising, in-app purchases, or remote MineLock backend.
- Launcher settings, instances, game files, mods, game logs, profile metadata, and eligible authentication cache data are stored on the user's Windows device.
- If Electron `safeStorage` encryption is available and secure, MineLock can persist the MSAL cache and its account mapping in encrypted local storage. Otherwise, authentication is session-only rather than being persisted in plaintext.
- Authentication and content requests go directly to the relevant external provider. Those providers receive the network, request, and account information needed to serve the request under their own policies.
- Current local beta executables are not Authenticode-signed and may trigger Microsoft Defender SmartScreen. Signing status can change for future builds.

Never send anyone a password, access token, refresh token, device code, or full unredacted log.

## Downloads

Current local beta executables are not offered from this documentation repository.

If a future public build is published, the canonical location will be the [MineLock Releases page](https://github.com/plisanko/minelock/releases). Each release will state its signing status and provide SHA-256 hashes so users can verify downloaded files. A future build is not guaranteed to remain unsigned.

Do not trust MineLock binaries from an unofficial download location.

## Project and repository status

This repository contains public information and policy documents for MineLock. It does not contain the application source.

MineLock is not currently represented as open source; source publication is undecided. The presence of this public documentation repository grants no license to application source. Terms and notices accompanying an app release govern that binary.

## Documentation

- [Privacy Policy](PRIVACY.md)
- [Terms of Use](TERMS.md)
- [Security Policy](SECURITY.md)
- [Contact](CONTACT.md)

## Contact

MineLock is maintained by [@plisanko](https://github.com/plisanko). For project or privacy questions, email [minelock@proton.me](mailto:minelock@proton.me). See [Contact](CONTACT.md) before sending logs or account information.

Microsoft account recovery, purchases, billing, and Minecraft entitlement problems must be handled by Microsoft or Minecraft Support. MineLock cannot access or change provider accounts.

## Official policies and provider information

MineLock users are also subject to the applicable provider terms and policies, including:

- [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement)
- [Microsoft Services Agreement](https://www.microsoft.com/en-us/servicesagreement/)
- [Minecraft End User License Agreement](https://www.minecraft.net/en-us/eula)
- [Minecraft Usage Guidelines](https://www.minecraft.net/en-us/usage-guidelines)
- [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
- [Fabric](https://fabricmc.net/)
- [Quilt](https://quiltmc.org/)
- [Minecraft Forge](https://minecraftforge.net/)
- [NeoForge](https://neoforged.net/)

These external projects and services are independent from MineLock, and their own terms and privacy practices apply.
