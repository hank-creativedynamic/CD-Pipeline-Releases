# CD Pipeline Collection downloads

**Updater stuck in v1.5.0 or v1.5.1?** Use the [v1.5.2 download](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/tag/v1.5.2). Force Quit the stuck Pipeline app and its ApplicationUpdateInstaller helper, then replace only the app in Applications. Keep Application Support, Keychain, and all media. Version 1.5.2 is published and passed the complete GitHub build and test checks, including a real helper replacing and reopening a signed test app.

[Download the latest release](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/latest)

Public downloads for CD Pipeline Collection and its seven standalone tools. Source code is maintained separately in a private repository. No GitHub account is required to download a published release.

## Choose your app

- **CD-Pipeline-Collection-Installer**: one window with Auto Ingest, Auto Upload, CD PP EXT, Folder Builder, Production Tracker, Proxy Tree, Storage Manager, and shared Integrations.
- **CD-PIPELINE-STANDALONE-APPS**: all seven independent apps; install only the tools you need. Each uses the CD logo with its feature name underneath.
- **CD-Pipeline-ingest / upload / extensions / folders / production / proxies / storage**: individual app ZIPs. The `collection` ZIP is the app-only version of the master installer.
- **CD-PP-EXT.zip**: Premiere panel installer.
- **CD-RESOLVE-EXT.zip**: separate native DaVinci Resolve Studio 21.2+ integration installer, with Exporter, Proxy Swapper, Local Relink, and Online Master. Automated mock-host checks pass; live Resolve relinking/rendering still needs validation on a project copy.

Mac apps require **Apple Silicon and macOS 14 or later**. Extract the ZIP and move the app into Applications before opening it. Proxy encoding requires a compatible FFmpeg installation with VideoToolbox support. Resolve installation obtains its matching native bridge from the user's installed Resolve SDK; no Blackmagic SDK binary is redistributed.

## Updates

Use **v1.5.2 or later** for the corrected updater. Versions before v1.5.0 lack it; v1.5.0 and v1.5.1 need the recovery replacement above. After that, use the app's **Check for updates…** menu and **Install and restart** when ready. Each standalone app updates independently.

The apps verify the publisher's signed update feed, the download checksum, app identity, and code signature before replacement. Installation waits until the app is idle, preserves a backup, and leaves user settings and media outside the app bundle. Automatic checks notify you; installation requires your action.

Starting with **v1.5.1**, Premiere and Resolve extension updates come directly from this GitHub repository. Open **CD PP EXT → Check for updates** in the collection or standalone app. Editors enter no update URL or publisher key and need no GitHub sign-in. Quit Premiere before its explicit update action; Resolve uses the verified installer download and its extracted installer command. Signed extension-only releases can update host tools independently while the latest application release keeps serving app updates.

The app bundles currently use local development signatures and are not Apple-notarized. macOS may require approval to open a trusted download. Accounts saved in Keychain can be recovered using **Integrations → Restore saved connections**; macOS may ask for Keychain approval again after an update.

Do not edit or replace published release assets. Future versions receive a new version tag, signed feed, and app downloads.
