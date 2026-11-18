# CD Pipeline Collection downloads

**Updater stuck in v1.5.0 or v1.5.1?** Use the [v1.5.3 download](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/tag/v1.5.3). Force Quit the stuck Pipeline app and its ApplicationUpdateInstaller helper, then replace only the app in Applications. Keep Application Support, Keychain, and all media. Version 1.5.3 includes the corrected updater and passed the complete GitHub build and test checks, including a real helper replacing and reopening a signed test app.

[Download the latest release](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/latest)

Public downloads for CD Pipeline Collection and its seven standalone tools. Source code is maintained separately in a private repository. No GitHub account is required to download a published release.

## Choose your app

- **CD-Pipeline-Collection-Installer**: one window with Auto Ingest, Auto Upload, CD PP EXT, Folder Builder, Production Tracker, Proxy Tree, Storage Manager, and shared Integrations.
- **CD-PIPELINE-STANDALONE-APPS**: all seven independent apps; install only the tools you need. Each uses the CD logo with its feature name underneath.
- **CD-Pipeline-ingest / upload / extensions / folders / production / proxies / storage**: individual app ZIPs. The `collection` ZIP is the app-only version of the master installer.
- **CD-PP-EXT.zip**: Premiere panel installer.
- **CD-RESOLVE-EXT.zip**: separate native DaVinci Resolve Studio 21.2+ integration installer, with Exporter, Proxy Swapper, Local Relink, Online Master, and Multicam Sync. Automated mock-host checks pass; live Resolve relinking/rendering still needs validation on a project copy.

Mac apps require **Apple Silicon and macOS 14 or later**. Extract the ZIP and move the app into Applications before opening it. Proxy encoding requires a compatible FFmpeg installation with VideoToolbox support. Resolve installation obtains its matching native bridge from the user's installed Resolve SDK; no Blackmagic SDK binary is redistributed.

## New in v1.5.3

The collection opens with **0 tools running** and no selected tab. Choose a tool when needed; a fresh launch does not restore previously open tools.

Premiere **1.0.6** and Resolve **1.0.1** add:

- **Exporter drive search:** choose a drive or folder, including a mounted SMB share, then select the matching project delivery path.
- **Multicam Sync:** preview the entire imported project or filter to a footage folder; choose the production-audio location separately. Recorded timecode aligns camera tracks into new synced timelines per shoot day. Known slow motion, clips without embedded audio, and clips without a verified production-audio match go to B-roll. Ambiguous metadata stays in review.

Creation retains a project backup and adds new generated bins/timelines. It does not use waveform matching. FFprobe is required for read-only media metadata. Do not switch projects or timelines during creation. Automated host tests pass; **live Premiere XML import, Resolve timeline creation, and production-audio channel playback still need validation on a project copy**.

These host installers are also available as an [independent extension update](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/tag/extensions-2026-11-18-01). Use **CD PP EXT → Check for updates**.

## Updates

Use **v1.5.2 or later** for the corrected updater. Versions before v1.5.0 lack it; v1.5.0 and v1.5.1 need the recovery replacement above. After that, use the app's **Check for updates…** menu and **Install and restart** when ready. Each standalone app updates independently.

The apps verify the publisher's signed update feed, the download checksum, app identity, and code signature before replacement. Installation waits until the app is idle, preserves a backup, and leaves user settings and media outside the app bundle. Automatic checks notify you; installation requires your action.

Starting with **v1.5.1**, Premiere and Resolve extension updates come directly from this GitHub repository. Open **CD PP EXT → Check for updates** in the collection or standalone app. Editors enter no update URL or publisher key and need no GitHub sign-in. Quit Premiere before its explicit update action; Resolve uses the verified installer download and its extracted installer command. Signed extension-only releases can update host tools independently while the latest application release keeps serving app updates.

The app bundles currently use local development signatures and are not Apple-notarized. macOS may require approval to open a trusted download. Accounts saved in Keychain can be recovered using **Integrations → Restore saved connections**; macOS may ask for Keychain approval again after an update.

Do not edit or replace published release assets. Future versions receive a new version tag, signed feed, and app downloads.
