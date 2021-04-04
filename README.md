# Buttercup Desktop
> Buttercup for Desktop - Mac, Linux and Windows

[![Buttercup](https://cdn.rawgit.com/buttercup-pw/buttercup-assets/6582a033/badge/buttercup-slim.svg)](https://buttercup.pw) ![Latest version](https://img.shields.io/github/tag/buttercup/buttercup-desktop.svg?label=latest) [![Chat securely on Keybase](https://img.shields.io/badge/keybase-bcup-blueviolet)](https://keybase.io/team/bcup) [![Discuss on Reddit](https://img.shields.io/badge/reddit-bcup-red)](https://www.reddit.com/r/bcup/)

## About

Buttercup is a free, open-source and cross-platform **password manager**, built on NodeJS with Typescript. It uses strong industry-standard encryption to protect your passwords and credentials (among other data you store in Buttercup vaults) at rest, within vault files (`.bcup`). Vaults can be loaded from and saved to a number of sources, such as the **local filesystem**, **Dropbox**, **Google Drive** or any **WebDAV**-enabled service (like _ownCloud_ or _Nextcloud_ ¹).

### Why you need a password manager

Password management is a crucial tool when you have _any_ online presence. It's vital that all of your accounts online use strong and unique passwords so that they're much more difficult to break in to. Even if one of your accounts are breached, having unique passwords means that the likelihood of the attacker gaining further access to your accounts portfolio is greatly reduced.

Without a password manager, such as Buttercup, it would be very tedious to manage different passwords for each service. If you remember your passwords it's a good sign that they're not strong enough. Ideally you should memorise a primary password for your vault, and not know any of the account-specific passwords off the top of your head.

### Precautions

Buttercup securely encrypts your data in protected files, but this security is only as strong as the weakest component - and this is very often the primary password used to lock and unlock your vault. Follow these basic guidelines to ensure that your vault is safe even if exposed:

 * Choose a **unique** password that is not used elsewhere
 * Use a highly-varied set of different characters - such as alpha-numeric, symbols and spaces
 * Use a long password - the longer the better
 * Don't include words or names in the password
 * Never share your password with anyone

_It is very important to note that no one associated with Buttercup will ever request your personal vault or its primary password. Do not share it or any of its related details with anyone. Developers or contributors working with Buttercup may request **example** vaults created via your system to try and reproduce issues, but please ensure to never use your real password or store actual credentails within such vaults._

### Versions

The current stable version is **2**. We recommend upgrading if you're still on v1, as it is no longer being actively maintained. You can still browse the v1 source and documentation [here](https://github.com/buttercup/buttercup-desktop/tree/v1).

### Operating Systems

Buttercup Desktop is officially supported on:

 * Most linux distributions (x64), such as Ubuntu
 * MacOS (x64, non-ARM)
 * Windows 10 (x64)

#### Arch Linux

Buttercup is also available for [Arch via the AUR](https://aur.archlinux.org/packages/buttercup-desktop/). This release channel is maintained by our community.

Some Arch users have reported the occasional segfault - if you experience this please try [this solution](https://github.com/buttercup/buttercup-desktop/issues/643#issuecomment-413852760) before creating an issue.

#### Portability

Buttercup provides a portable **Windows** version. Look for the release with the name `Buttercup-win-x64-2.0.0-portable.exe` where `2.0.0` is the version.

Although not explicitly portable, both the Mac **zip** and Linux **AppImage** formats are more or less standalone. They still write to the standard config/log destinations, however.

## Configuration

Configuration files are stored in OS-specific locations.

### App config

Application configuration.

 * Linux: `$XDG_CONFIG_HOME/Buttercup/desktop.config.json`
 * Mac: `~/Library/Preferences/Buttercup/desktop.config.json`
 * Windows: `$APPDATA/Buttercup/Config/desktop.config.json`

### Vault storage

Storage of connected vaults (not actual vault contents).

 * Linux: `$XDG_DATA_HOME/Buttercup/vaults.json`
 * Mac: `~/Library/Application\ Support/Buttercup/vaults.json`
 * Windows: `$LOCALAPPDATA/Buttercup/Data/vaults.json`

### Offline vault cache

Stored copies of vaults for offline use.

 * Linux: `$(node -e "console.log(os.tmpdir())")/$(whoami)/Buttercup/vaults-offline.cache.json`
 * Mac: `$(node -e "console.log(os.tmpdir())")/Buttercup/vaults-offline.cache.json`
 * Windows: `$(node -e "console.log(os.tmpdir())")/Buttercup/vaults-offline.cache.json`

### Logs

Logs are written for all app sessions.

 * Linux: `~/.local/state/Buttercup-nodejs` or `$XDG_STATE_HOME/Buttercup-nodejs`
 * Mac: `~/Library/Logs/Buttercup-nodejs`
 * Windows: `%LOCALAPPDATA%\Buttercup-nodejs\Log`

_Note that logs for portable Windows applications will be written to the same directory that the executable resides in._

## Published Applications

You can view the current releases on the [Buttercup Desktop releases page](https://github.com/buttercup/buttercup-desktop/releases). Under each release are some assets - the various binaries and installers for each platform Buttercup supports. When installing or downloading, make sure to pick the right operating system and architecture for your machine.

_Note that at this time, Buttercup only supports x64 (64 bit) machines._

### Linux

We provide an **AppImage** build for Linux, because it is the most desirable format for us to release. AppImages support auto-updating, a crucial feature (we feel) for a security application. The other build types do not.

We won't be supporting formats like Snapcraft, deb or rpm images as they do not align with our requirements. Issues requesting these formats will be closed immediately. Discussion on topics like this should be started on other social channels.

## Contributing

There are a number of ways you can contribute to Buttercup!

### Features & Bug fixes

We welcome pull-requests and issues that serve to better Buttercup as a platform. Please remain respecful (this is free & open source after all) with your ideas and observations, and always consider opening an issue before starting on a substantial pull request.

### Translations

Buttercup relies on the community for translating its interfaces into languages besides English. We use British English (en_GB) as the base language, and translate into all others that our contributors are kind enough to provide.

To add support for a language, make sure to add the translations for our [**vault UI**](https://github.com/buttercup/ui#translations--i18n) first. After that, you can follow these instructions to add another language to the desktop application:

 * Copy the `source/shared/i18n/translations/en.json` file to the language code you're providing (eg. `fi.json` for Finnish).
 * Edit the `source/shared/i18n/translations/index.ts` file and:
   * Import the new JSON file: `import fi from "./fi.json";`.
   * Export the imported constant inside the default export already in that file.

## Notes and Caveats

 * ¹ External services like Nextcloud and ownCloud must be configured correctly to support access via the web (using WebDAV). CORS must permit access from any source.
