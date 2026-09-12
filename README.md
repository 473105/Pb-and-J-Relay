### ![](https://img.shields.io/badge/-Why%20tho-84D0FC?style=for-the-badge) 

**Pb&J Relay: Plex-to-Jellyfin Migration Tool** started from a decision of distancing myself from Plex, but after years of curating my libraries, moving to Jellyfin felt like starting from scratch. Sure there was an app here, and an addon there, but they only handled parts of the migration, leaving out much of the data I actually cared about preserving. It's the little things that make your libraries personal, and when you've spent years shaping a library around your watch history with all the small adjustments you've made along the way, it starts to carry personal value. I wanted a way to move to Jellyfin without leaving all of that behind.

This tool is built to preserve that work. It reads Plex and Jellyfin installations, compares the two, lets the user review and revise differences in matches, and then applies the selected Plex metadata to Jellyfin. It also allows the user to start with an absolutely bare Jellyfin server and populates it by fully cloning your Plex metadata and artwork onto it.

<br>

##
### ![](https://img.shields.io/badge/-Main%20App-FFA270?style=for-the-badge)


<div align="center">
  <img width="337" height="98" alt="PBandJRelay_full_logo" src="https://github.com/user-attachments/assets/c2fd8b58-5b88-48a0-ad77-754c90fb3d5b" />
</div>

This project is a **Windows** migration tool for moving curated **Plex** library metadata into **Jellyfin**. Pb&J Relay preserves the work you have put into customizing your Plex media and carries it over to your Jellyfin server.
The uncertainty of whether a migration is worth the time and effort of rebuilding everything in Jellyfin can make it easy to put off the decision to switch. Meanwhile, your libraries continue to grow, anchoring you to Plex even further. 
Migrating to a new service usually meant that your edited titles, posters, and backgrounds would be reset to their defaults; watched history and resume states would be erased; personal ratings, tags, and labels would disappear; and if you relied on Added Date to sort your libraries, your choices were either to manually correct each item or accept a completely different order of sorting your media.
You don't need another layer of anxiety around a hobby that should be enjoyable. Let Pb&J Relay handle the heavy lifting of transferring that data for you, so you can kick back and focus on watching your favorite movies, shows, and enjoying your music backups.
<div align="center"> 
**Tested on Plex 1.41.3.9 and Jellyfin 10.10.7 Media Servers.
</div>
<br>
<div align="center">
<img width="707" height="426" alt="example2" src="https://github.com/user-attachments/assets/7632f462-7b98-4d5b-b5bd-588dcfad00db" />
</div>

## 

**The project includes Jelly Toast, a companion utility for launching a isolated Jellyfin test servers on a separate folder and port so migration features can be tested without touching a real Jellyfin server.

****The app does not copy the actual movies, shows, music, audiobooks, or photo files.** It only ports metadata and cover/background artwork onto the existing Jellyfin installation. The understanding is that your Plex media server is the same machine where your new Jellyfin server will reside, and of your media files are already present in their respective directory.

##

<br>

### ![](https://img.shields.io/badge/-Download%20and%20Launch-8FD0A0?style=for-the-badge)


The standalone package does not require Python to be installed on the target machine:

```text
PbandJRelay_v#.##_standalone.zip
```

After extracting the package, launch:
```text
\PbandJRelay_v#.##\PbandJRelay_v#.##.exe
```

A small companion app, Jelly Toast, is included in the standalone package:
```text
\PbandJRelay_v#.##\JellyToast\JellyToast_v#.##.exe
```

For convenience, Pb&J Relay can launch Jelly Toast from within the main window and you can also launch the main app from the companion app as well (that option will be hidden if either app is moved from its extracted folder).

<br>

## 
### Upcoming Features
At the moment Pb&J Relay only gathers the admin user's account history (watched count, resume position, last viewed, personal ratings and favorites). However, a feature is in development for all local Plex account cloning into Jellyfin, and will include account mapping so a user can choose which Plex account should transfer its data into which Jellyfin account.

The next upgrade to that feature would be another lightweight companion app for remote Plex users, which would let them collect their own watch-state metadata so this data can be transferred into their own Jellyfin account history.

Please consider supporting the project with a donation to help with the release of these features.

<br>

## 
### ![](https://img.shields.io/badge/Donations-EDFF99?style=for-the-badge)


<div align="center">
<h2 align="center">Support the Project</h2>

If this tool saves you time, consider supporting ongoing development through the official GitHub page.

Use only the official project page for donation or support links.

[![Donate with PayPal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/donate/?hosted_button_id=MEUXL5RKQQ84U)
</div>

##


<br>

### ![](https://img.shields.io/badge/-Where%20App%20Data%20is%20Saved-ACACDD?style=for-the-badge)


Pb&J Relay saves its working data in a user-selected data folder (for Jellyfin users). By default, this is inside the user's Documents folder.
That folder can contain harvested Plex archives, harvested Jellyfin archives, match previews, migration plans, reports, cached credentials, exported lists, and UI settings.

****Depending on library size and selected options, this data can take many gigabytes of storage.** Artwork is usually the largest part. If you harvest large libraries with posters, backdrops, and logos enabled, make sure the selected data folder is on a drive with enough free space.


### ![](https://img.shields.io/badge/-What%20The%20App%20Transfers-E29EA6?style=for-the-badge)
Pb&J Relay can transfer these Plex values to matched Jellyfin items:

- Titles, original titles, and sort titles.
- Date added, using either Plex added date or a physical file/folder date source.
- Overview, summary, and tagline.
- Posters, backdrops, and logo artwork.
- Genres, tags, labels, and collections when available.
- People, roles, studios, countries, directors, writers, and related credits where Jellyfin accepts them.
- Ratings and personal ratings where supported.
- Watched state, play count, last viewed time, and resume position for the selected Jellyfin user.

Not every Plex field has a perfect Jellyfin equivalent. The migration plan shows what will be applied and what may be skipped or partially applied.


### ![](https://img.shields.io/badge/-Safety%20Protocol-BED698?style=for-the-badge)
This app is designed around reviewable steps:

- Plex data is harvested into a Plex archive first.
- Jellyfin data is harvested into a Jellyfin archive separately.
- The app compares those archives before applying migrated metadata.
- Migration plans are saved before applying changes.
- Applying a plan writes only to Jellyfin through the Jellyfin API.

The app should not modify, move, rename, delete, or rewrite the physical media files in your library folders.

Jellyfin itself can write `.nfo`, artwork, subtitle, or metadata files to media folders if those Jellyfin features are enabled. Pb&J Relay tries to prevent those behaviors during migration workflows because they can clutter folders and change folder modified times.

<br>

## 
### ![](https://img.shields.io/badge/Simple/Advanced%20Modes-C8CDE5?style=for-the-badge)

### Simple Mode
Simple mode is for the automated workflow.

The main action is in the Jellyfin tab:

```text
Automated Full Migration
```

This workflow is intended for a fresh or mostly empty Jellyfin setup where the user wants Jellyfin library folders to be created from the Plex library structure, then scanned, compared, planned, applied, and scanned again.

The automated workflow goes through the following steps:

- Plex scan.
- Plex data harvest.
- Jellyfin authentication.
- Checking library differences.
- User confirmation.
- Creating missing Jellyfin libraries.
- Jellyfin scan.
- Jellyfin data harvest.
- Matching Plex items to Jellyfin items.
- Preparing the migration plan.
- Applying data to Jellyfin.
- Final Jellyfin rescan.

### Advanced Mode
Advanced mode is for manual control. 
Use this mode when you want to:

- Harvest selected Plex libraries.
- Harvest selected Jellyfin libraries.
- Compare archives manually.
- Resolve conflicts one by one.
- Exclude specific match groups.
- Build a migration plan only from selected rows.
- Apply metadata to a small test set before a larger migration.
- Re-run only targeted comparisons or migrations.

Advanced mode is the better choice when the library has unusual folder structures, duplicate titles, split libraries across multiple drives, or old Plex phantom records from missing drives.

<br>

## 
### ![](https://img.shields.io/badge/-Typical%20Workflow-A1CCC5?style=for-the-badge)

1. Start Plex and Jellyfin media servers.
2. Load Plex libraries.
3. Harvest the Plex libraries you want to preserve.
4. Move to Jellyfin.
5. Enter the Jellyfin URL and API key.
6. Select the Jellyfin user whose watched/resume state should be updated.
7. Load Jellyfin libraries.
8. Harvest Jellyfin archive data.
9. Compare Plex and Jellyfin archives.
10. Resolve conflicts and review likely or similar matches.
11. Prepare a migration plan.
12. Apply the current plan to Jellyfin.
13. Let Jellyfin perform the final scan.
14. Review Jellyfin in the browser or app.

**The `Guide me` overlay, Simple/Advanced mode switch, and `Notes & Tips` switch are there to help users follow the workflow without having to memorize every step.**

<br>

## 
### ![](https://img.shields.io/badge/-App%20Specific%20Terminology-D4CC08?style=for-the-badge)

- `Harvest`: collects curated data from your server and stores it locally. I felt like this word is a good fit here because gathering data that has grown from your valuable time is not just a backup/archive/pull/transfer, but is more analogous to collecting the fruits of your labor.
- `Archive`: the saved result of a harvest. An archive is a structured local copy of metadata and optional artwork that the app can compare and reuse later.
- `Plex archive`: harvested Plex metadata and artwork. This is the source side of the migration.
- `Jellyfin archive`: harvested Jellyfin metadata. This is the destination side of the migration.
- `Migration plan`: a reviewable list of exactly what the app intends to write to Jellyfin.
- `Saved Preview`: a saved matching process from the last comparison between Plex and Jellyfin archives.
- `Physical items`: file or folder is present on disk at the path recorded by the archive.
- `Phantom`: the archive contains metadata for an item whose file or folder is not currently present on disk.

<br>

### ![](https://img.shields.io/badge/-Phantom%20Items-C4A3ED?style=for-the-badge)

Phantom items are important for recovery because Plex can keep metadata for a file that no longer exists on disk, especially if a drive failed or a library was not rescanned after files disappeared. it is important not to have Plex automatically scan this library because it will think that it was a deliberate deletion of those items and will remove them from your library completely
Pb&J Relay can harvest that Plex metadata, but Jellyfin still needs an item record before the Jellyfin API can update it. 
That means:
- Plex phantom metadata can be applied to a Jellyfin item if Jellyfin already has a matching item ID.
- Plex phantom metadata cannot be applied directly when Jellyfin has no matching item at all.
If a file is restored later, scan it into Jellyfin first, then run the compare and migration workflow again from the existing Plex archive.

**IMPORTANT** if files are missing and you want to save their customization:
Do not rescan affected Plex libraries until after Pb&J Relay harvests them.
Disable “Empty trash automatically after every scan” in Plex before working with failed/missing drives.
Avoid manually using Empty Trash on those libraries.
Harvest the Plex archive first, because that captures the remaining metadata while Plex still has it.
##

<br>

### ![](https://img.shields.io/badge/-Libraries%20and%20Drives-9BB1FB?style=for-the-badge)

Pb&J Relay understands different library layout staging:

- A single library can span multiple drives.
- A single drive can contain multiple libraries.
- Some libraries may be fully present while others are partially missing.
- Old Plex records may point to drives that no longer exist.

<br>

### ![](https://img.shields.io/badge/-Artwork%20Storage-83FF85?style=for-the-badge)

Archived artwork can take a large amount of disk space, but you do have an option to choose image size cap from 100 KB to 2 MB, or leave the option unchecked for the artwork to be copied without imposing a limit (resizing will increase migration time).
The size cap only affects larger than the cap images. Smaller images are not enlarged to match the size cap.
When artwork is applied to Jellyfin, Jellyfin stores its own copy in its server data/cache. Deleting the Pb&J Relay archive later would not remove artwork that Jellyfin server has already accepted into its own storage.

<br>

### ![](https://img.shields.io/badge/-Data%20Folder-E7D727?style=for-the-badge)

By default, Pb&J Relay stores working data in a `PbandJRelay` folder under the current Windows user's Documents folder:

```text
Documents\PbandJRelay
```

To eliminate the chance of overwriting archive data when testing multiple Plex or Jellyfin servers, the app keeps this data separate:

```text
Plex\Servers\<server-id>\Archive
Jellyfin\Servers\<server-id>\Archive
Jellyfin\Servers\<server-id>\MigrationPlans
Config
```

The data folder can be changed from the app, but keeping one shared data folder is usually safest because archives, previews, selections, plans, reports, cached credentials, and UI settings stay synchronized.

<br>

### ![](https://img.shields.io/badge/-Remote%20Access%20Setup-B4B4B4?style=for-the-badge)

The Remote Setup tab helps configure private Jellyfin access through Tailscale.

Important notes:
- Pb&J Relay must be running on the Jellyfin server machine for setup changes to apply correctly.
- Tailscale must be installed and signed in on the server and client devices.
- Tailscale Serve is optional and is only needed for the shorter HTTPS MagicDNS-style URL without a port.
- Creating a Windows Firewall rule requires administrator approval.

<br>

## 
### ![](https://img.shields.io/badge/-Companion%20App-A2B4FF?style=for-the-badge)

<div align="center">
  <img width="337" height="98" alt="JellyToast_full_logo" src="https://github.com/user-attachments/assets/aab7f37d-69ea-4f0f-a11b-d25ce076307c" />
</div>

**Jelly Toast: Jellyfin Test Server** is a small companion utility for creating and running isolated Jellyfin test servers.
Use it when you want to test or troubleshoot your library creation, app scanning, and migration behavior without touching your real Jellyfin server.
After choosing a separate directory where the test server data will be created, it will write config, cache, and log files to disk.

<div align="center">
<img width="457" height="331" alt="JellyToast_ui_example" src="https://github.com/user-attachments/assets/e666f83e-59f9-4c3f-bdd8-595155939bd0" />
</div>

<br>

Test servers are intended to run on a different HTTP port (for example `8097`, while the real Jellyfin server can keep using the default port of `8096`).
This companion app will not erase or modify the actual Jellyfin server, and will refuse ports that are in use.

##

<br>
  
### ![](https://img.shields.io/badge/Requirements-CAB2B2?style=for-the-badge)
- Windows 10 or 11 (I haven't tested on other Windows versions yet)
- Plex and Jellyfin Media Server reachable from the machine running this migration app.
- Jellyfin API key and Plex tokens.
- Tailscale app only if using the **Remote Access Setup** tab.
- Administrator approval (required by one optional selection `Remote Access Setup tab > Isolated Options > Allow Port in Windows Firewall` to setup Tailscale access through the user specified port).

<br>

## 
### ![](https://img.shields.io/badge/-Reporting%20Bugs-D1D1D1?style=for-the-badge)

When reporting a problem, include:

- Pb&J Relay version.
- Jelly Toast version if relevant.
- Windows version.
- Plex server version.
- Jellyfin version.
- The exact action that failed.
- A screenshot if the problem is visual.
- The saved migration summary or technical report log file when migration failed.

IMPORTANT: Don't forget to remove private Plex tokens, Jellyfin API keys, and account details before posting logs publicly.

<br>

## 
### ![](https://img.shields.io/badge/-Known%20Limitations-70F1FD?style=for-the-badge)
- Jellyfin must have an item record before the API can apply metadata to that item.
- Some Plex metadata fields do not have exact Jellyfin equivalents.
- Jellyfin can still identify or rename media according to its own rules unless metadata locking/prevention options are enabled (the app enables this by default before writing migration).
- Remote access setup depends on Tailscale account/device status, Jellyfin networking settings, firewall rules, and client device restrictions.
- Very large artwork archives and large migration plans can take significant time to process.
  If you would like to contribute to narrowing down these time frames please share some info:
  **Windows version.
  Duration of migration in Simple mode or in Advanced mode (if advanced mode, include only the duration after you clicked on 'Apply Current Plan to Jellyfin' button). 
  library size, if selected options under the 'Migrate Metadata' tab included 'watched/resume state', if the artwork has been archived from Plex and what size it was limited to**. 
  example templates:
  ```
  OS: Windows 11 Pro, 24H2
  Duration (only the migration process): Advanced mode, 2 hours 15 minutes
  Movies: 500
  TV: 50 shows, 150 seasons, 2,000 episodes
  Music: 250 albums, 3,500 tracks
  Artwork: Included, limited to 500 KB per image
  Watched/resume state: Included
  ```
  ```
  OS: Windows 10 LTSC, 21H2
  Duration (only the migration process): Simple mode, 1 hour 30 minutes
  Movies: 500
  TV: 50 shows, 150 seasons, 2,000 episodes
  Music: 250 albums, 3,500 tracks
  Artwork: Included, no limit
  Watched/resume state: not included
  ```
  Once there is a meaningful amount of data I will upload a chart and a calculator for estimating how long your library migration would likely take.

##

  ### ![](https://img.shields.io/badge/-A%20Helpful%20Note-EDFF99?style=for-the-badge)
Two quality of life features are built into the app - **"Guide me"** and **"Notes & tips"**:
<br>
**"Guide me"** is a user-friendly walkthrough of the migration process. When enabled, it displays numbered steps with hover explanations for the Simple and Advanced workflows. 
<br>
**"Notes & tips"** provides hover explanations for buttons and settings.

<br>
<div align="center">
<img width="757" height="197" alt="guideme_arrow" src="https://github.com/user-attachments/assets/d7a673bb-b575-473f-a02a-8107c4ec5b75" />
</div>



##
<br>
<div align="center">
<details>
<summary><b>I hope you enjoy the app.</b></summary>

<br>
<br>
<br>
  <div align="center">
  <img width="80" height="80" alt="dancing-banana-transparent-trymstene com" src="https://github.com/user-attachments/assets/12692b9b-bc91-4285-8907-41c3f9135884" />
  </div>
</details>
</div>
