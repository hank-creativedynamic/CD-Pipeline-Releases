# CD Pipeline Collection downloads

**Updater stuck in v1.5.0 or v1.5.1?** Use the [v1.5.5 download](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/tag/v1.5.5). Force Quit the stuck Pipeline app and its ApplicationUpdateInstaller helper, then replace only the app in Applications. Keep Application Support, Keychain, and all media. Version 1.5.5 includes the corrected updater and passed the complete GitHub build and test checks, including a real helper replacing and reopening a signed test app.

[Download the latest release](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/latest)

Public downloads for CD Pipeline Collection and its seven standalone tools. Source code is maintained separately in a private repository. No GitHub account is required to download a published release.

## Choose your app

- **CD-Pipeline-Collection-Installer**: one window with Auto Ingest, Auto Upload, CD PP EXT, Folder Builder, Production Tracker, Proxy Tree, Storage Manager, and shared Integrations.
- **CD-PIPELINE-STANDALONE-APPS**: all seven independent apps; install only the tools you need. Each uses the CD logo with its feature name underneath.
- **CD-Pipeline-ingest / upload / extensions / folders / production / proxies / storage**: individual app ZIPs. The `collection` ZIP is the app-only version of the master installer.
- **CD-PP-EXT.zip**: Premiere panel installer.
- **CD-RESOLVE-EXT.zip**: separate native DaVinci Resolve Studio 21.2+ integration installer, with Exporter, Proxy Swapper, Local Relink, Online Master, and Multicam Sync. Automated mock-host checks pass; live Resolve relinking/rendering still needs validation on a project copy.

Mac apps require **Apple Silicon and macOS 14 or later**. Extract the ZIP and move the app into Applications before opening it. Proxy encoding requires a compatible FFmpeg installation with VideoToolbox support. Resolve installation obtains its matching native bridge from the user's installed Resolve SDK; no Blackmagic SDK binary is redistributed.

## New in v1.5.5

**Production Tracker and Storage Manager email tests are fixed.** Both now have **Test email connection**, which sends a short message to the tool's configured recipients and shows progress and a result. This test does not wait for Google Sheets, drive scans, OFTV, or Slack. Storage Manager can test email during a drive scan.

**Send test report** remains separate and prepares a fresh full report. Production refreshes Google Sheets first; Storage scans its drives. A full Storage test is disabled during an active scan so a click is not silently ignored.

Messages now use Apple Mail's supported text body and attach the complete formatted report as **Report.html**. Storage also attaches its charts and embeds them in the HTML report. The apps require an explicit successful response from Mail before reporting acceptance; failures do not consume the scheduled email success marker. Requests run outside the app's UI thread, have a time limit, and stop when their tool closes.

Set up an enabled sending account in **Apple Mail** and allow the Pipeline app under **System Settings → Privacy & Security → Automation → Mail**. The Google integration connects Sheets; it does not configure email sending. If Mail accepts the message but it does not arrive, check Mail's Outbox and Connection Doctor. If a request times out or is stopped, check Outbox before retrying to avoid duplicates.

Isolated Mail delivery, AppleScript compilation, Production report and lifecycle checks pass. The initial setup probe and a later live connection test both timed out; **inbox delivery has not been confirmed**. Check Mail's setup/sign-in prompts, Automation permissions, and Outbox before retrying. The update now displays such failures clearly. Existing accounts, settings and media are preserved. Collection and standalone apps update through **Check for updates… → Install and restart**. Premiere 1.0.7 and Resolve 1.0.2 installers remain unchanged.

## Multicam Sync in v1.5.4

Premiere **1.0.7** and Resolve **1.0.2** add **Timecode + waveform** as the default Multicam Sync mode. Recorded timecode narrows the search, and local audio comparison checks independent sections of the camera's scratch audio against production sound. **Waveform only** handles missing or unreliable camera timecode; **Timecode only** keeps the faster metadata-only workflow.

- Preview the entire imported project or filter to a footage folder, and choose the production-audio location separately.
- Review match confidence, offsets, conflicting timecode, incomplete searches, and audio drift before creating timelines. Weak or ambiguous matches remain in review. No automatic audio stretching is applied.
- Matching is local, uses one audio-decoding process with bounded memory and search time, and has a **Stop matching** control. FFmpeg and FFprobe are required for waveform analysis; timecode-only mode does not decode audio.
- Create new synced timelines with each camera on its own track and the matched production sound. Known slow motion, clips without embedded audio, and confirmed production-audio nonmatches go to B-roll. Missing metadata or an incomplete search stays in review.

Placement is accurate to video frames; this is not sample-accurate audio alignment. Preview does not modify source media. Creation retains a project backup and adds new generated bins/timelines. Do not switch projects or timelines during creation. Generated-media tests and automated host tests pass; **live Premiere XML import, Resolve timeline creation, and production-audio channel playback still need validation on a project copy**.

These host installers are available as an [independent extension update](https://github.com/hank-creativedynamic/CD-Pipeline-Releases/releases/tag/extensions-2026-11-18-02). Use **CD PP EXT → Check for updates** in the collection or standalone app. An installed v1.5.3 collection can update the extensions without reinstalling the collection. The v1.5.4 collection also includes the new offline installers.

The collection continues to open with **0 tools running** and no selected tab. Exporter drive search lets you choose a drive or folder, including a mounted SMB share, then select the matching project delivery path.

## Updates

Use **v1.5.2 or later** for the corrected updater. Versions before v1.5.0 lack it; v1.5.0 and v1.5.1 need the recovery replacement above. After that, use the app's **Check for updates…** menu and **Install and restart** when ready. Each standalone app updates independently.

The apps verify the publisher's signed update feed, the download checksum, app identity, and code signature before replacement. Installation waits until the app is idle, preserves a backup, and leaves user settings and media outside the app bundle. Automatic checks notify you; installation requires your action.

Starting with **v1.5.1**, Premiere and Resolve extension updates come directly from this GitHub repository. Open **CD PP EXT → Check for updates** in the collection or standalone app. Editors enter no update URL or publisher key and need no GitHub sign-in. Quit Premiere before its explicit update action; Resolve uses the verified installer download and its extracted installer command. Signed extension-only releases can update host tools independently while the latest application release keeps serving app updates.

The app bundles currently use local development signatures and are not Apple-notarized. macOS may require approval to open a trusted download. Accounts saved in Keychain can be recovered using **Integrations → Restore saved connections**; macOS may ask for Keychain approval again after an update.

Do not edit or replace published release assets. Future versions receive a new version tag, signed feed, and app downloads.
