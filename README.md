# WandEnhancer V2.3 — Community Executable

**WandEnhancer 2.3.0.0 • Remote Web updates • Brazilian Portuguese support**

An independent community continuation of WandEnhancer, originally created by **k1tbyte** with contributions from the upstream community. This repository documents the compiled **WandEnhancer.exe**, its main features and the updated Remote Web connection process.

[Original project](https://github.com/k1tbyte/Wand-Enhancer)

## Download and requirements

Community builds, when available, will be published under [Releases](../../releases). Download **WandEnhancer.exe** from the assets of a published release. This documentation package contains no executable. Run the compiled application directly; compilation tools and GitHub Actions are not needed to use it.

You need:

- A Windows PC with Wand installed.
- **.NET Framework 4.8**.
- For Remote Web, a phone or tablet with a modern browser and network access to the PC.

The current Release packaging combines the application's managed dependencies into one executable. The .NET Framework runtime is still required. Preferences and installation files are stored separately as part of normal use; “one executable” describes the distributed application, not every file it creates.

This repository does not include a Wand installer, games, an account or a subscription. It documents a community build, not an official executable released or endorsed by the original author.

## Version and compatibility

| Item | Details |
| --- | --- |
| Window label | V2.3 |
| Executable version | 2.3.0.0 |
| Current installation shown in the screenshots | Wand 12.73.0 |
| Versions checked against the source patch pipeline | Wand 12.72.0 and 12.73.0 |
| Remote Web default port | TCP 3223 |
| Remote Web address format | `http://PC-IP:PORT/remote/` |

The latest community changes retain version **2.3.0.0**. Two builds with that version can therefore contain different fixes.

Phone access and Brazilian Portuguese have been reported working in the tested setup. Structural compatibility checks do not establish support for every game, trainer, Windows setup, beta client or future Wand update.

## Main features

- Select or automatically detect a local Wand installation.
- Apply selected client changes and restore the saved original installation files.
- Enable the browser-based **Remote Web** panel for a phone or tablet.
- Enable the F12 DevTools shortcut or disable Wand updates through the available options.
- Optionally reapply the saved selection after a Wand update.
- Remember the selected installation, language and patch options.
- Check installation integrity and copy or export diagnostic logs.
- Use Brazilian Portuguese in both the desktop application and remote panel.

The existing **Activate WeMod Pro** option affects the account state presented by the local client. It does not create a paid subscription or grant services that require authorization from Wand's servers.

## First use

1. Close Wand and finish any ongoing Wand update.
2. Open **WandEnhancer.exe**.
3. Check **Folder path**. If detection fails, select the Wand installation folder or drag the folder or `Wand.exe` onto the window.
4. Click **Enhance** to open the options.
5. Select the features you want. For phone access, enable **Enable remote access (beta)**.
6. Leave **Static (recommended)** selected for the standard setup, or use **Supervised (runtime)** if that is the method you intend to use.
7. Click **Start** and wait for completion. Review any error instead of assuming the patch succeeded.
8. Open Wand normally. For remote trainer controls, start a supported game and load its trainer.

**Static** changes the selected installation on disk. **Supervised** applies runtime changes through a deployed launcher. Both modify the local setup; the method is not a switch between an official and unofficial client.

If the installation is already patched and you want to change the selected options, use **Restore** first, then apply the new selection. Do not remove the original backups before restoration succeeds.

## Remote Web: desktop controls and pairing

![WandEnhancer Remote Web address, connection count and pairing code](assets/screenshots/remote-web-desktop.png)

The Remote Web card provides the information needed to connect a browser to the selected Wand installation.

| Control or field | What it does |
| --- | --- |
| **Test Remote Web** | Finds and checks the running bridge for the selected installation, then displays its address, connection count and temporary pairing code. It does not start Wand or enable the patch for you. |
| **Address** | The URL to open in the phone browser. Use the address shown on your own PC. |
| **Paired connections** | The number of currently authenticated browser connections. It is not a permanent list of every device ever paired. |
| **Pairing code** | A temporary six-digit code used to authorize a browser connection. |
| **Expires at** | The expiry time of the displayed pairing code. A code lasts five minutes. |
| **Disconnect devices** | Revokes remote authorizations, disconnects the paired browsers and generates a fresh code. It does not stop the running game. |
| **Check installation** | Compares installation and backup files with the recorded integrity state. It does not repair files or prove that a trainer works in a game. |

**The screenshot's `111111` code is illustrative.** Enter the current code shown by your own running WandEnhancer. The example IP address and expiry time also belong to the screenshot, not to every installation.

When a code expires, click **Test Remote Web** to obtain the current code. Pairing-code expiry does not, by itself, disconnect a browser that is already authorized.

### Before connecting

- Keep Wand running with the Remote Web option applied.
- Connect the PC and phone to the same reachable local network. A PC connected by Ethernet and a phone connected by Wi-Fi can work together on that network.
- Use the displayed URL. Port **3223** is the default; if another port is selected because it is occupied, use that actual port.
- A guest Wi-Fi network or client isolation can prevent devices from communicating.

## Connect through the QR code

![Wand Connect popover with the Remote Web QR code and local address](assets/screenshots/remote-web-qr.png)

1. Open Wand with Remote Web enabled.
2. Hover over **CONNECT** in Wand's top bar to display the QR code.
3. Scan it using your phone's camera or QR scanner.
4. Open the link in the phone's browser.
5. **Enter the six-digit pairing code displayed in WandEnhancer**, under **Test Remote Web**.
6. Wait for the connection and session synchronization to finish before using the controls.

The QR code opens the panel address. **Scanning it does not replace entering the pairing code.**

You can also type the displayed address manually. No separate mobile app is needed for this browser panel. Use this local Remote Web flow rather than Wand's official mobile-app activation flow.

## Using the connected panel

<img src="assets/screenshots/remote-web-connected.jpeg" alt="Remote Web connected on a phone: LIVE status with no active game session" width="360">

This screenshot shows the panel after connecting from the phone, before starting a game.

| On-screen item | Meaning |
| --- | --- |
| **LIVE** | The panel is connected to Wand's local Remote Web bridge. |
| **Idle · no game** | No game is currently active in the reported session. |
| **No session** | There is no active game/trainer session to display yet. This can appear while the connection is LIVE. |
| **Select a game / Browse library** | Opens the detected-game library so you can select a game. Available launch actions depend on Wand and the selected game. |
| **Settings gear** | Opens the panel settings, including language, connection information and accent color. |

**LIVE confirms the connection; it does not mean a trainer is already loaded.** Start a supported game and its trainer in Wand, then wait for the panel to receive the active session and available controls. You can also open the library from the panel.

Once connected, the panel reflects the game and trainer information supplied by the running Wand client.

Depending on the active trainer and the capabilities available in that session, the panel provides:

- Trainer toggles, action buttons, numeric controls, sliders and selections.
- Updates between desktop and phone when trainer values change.
- A detected-game library with search and favorites; available launch/stop actions depend on the session.
- Pinned controls and locally saved quick presets.
- Session and connection status.
- Language and accent-color settings.

A connected panel can still have no active trainer. If you see a waiting or empty-session message, start the game and trainer in Wand, then wait for synchronization.

Controls wait for confirmation from Wand. Rejected commands, errors and timeouts are handled so the panel does not leave a change displayed as successful when it was not confirmed. Features still depend on the individual trainer and game.

### Brazilian Portuguese

On the phone, open **Settings > Language > Português (Brasil)**.

A new browser session with no saved language preference selects Portuguese automatically when its browser language is Portuguese. An existing saved choice takes priority.

Panel labels and pairing messages are translated. Game-specific mod names and descriptions continue to depend on the metadata and translations provided by Wand.

## How the remote session behaves

Pairing authorizes this browser session. It is not a Wand account login.

| Situation | Expected behavior |
| --- | --- |
| First visit | Enter the current six-digit code. |
| Code expires before pairing | Request the current code with **Test Remote Web** and try again. |
| Brief network interruption | The open tab can reconnect using its in-memory authorization while it remains valid. |
| Return to the browser after switching apps | The panel requests a fresh session snapshot and waits for synchronization before enabling controls. |
| Reload the page or close and reopen the tab | Pair again; the authorization token is not saved persistently in browser storage. |
| Authorization token expires | A new pairing is required for a later reconnection. Tokens have a twelve-hour lifetime. |
| Restart Wand | Previous remote authorizations are lost; pair again. |
| Click **Disconnect devices** | All remote authorizations are revoked and a new code is generated. |

Unconfirmed commands are discarded during session recovery instead of being replayed against a potentially different game or trainer. Interface preferences, favorites and presets can remain saved locally even when the authorization session is gone.

Remote Web uses local **HTTP/WebSocket**, without transport encryption. Pairing restricts access but does not encrypt traffic. Use a trusted local network and do not expose the listening port directly to the internet.

## Update and fix changelog

### Current community revision — version 2.3.0.0 retained

**Remote Web and session fixes**

- Improved confirmation of trainer commands, including rejected requests, errors and timeouts.
- Corrected pending-control behavior during session synchronization and trainer translation updates.
- Fixed repeated remote-link refreshes and improved reconnection handling.
- Added controlled handling for invalid WebSocket addresses and a localhost fallback when LAN discovery fails.
- Added connection-opening and synchronization deadlines.
- Prevented session data from enabling controls before a compatible connection is acknowledged and synchronization completes.
- Refreshes the snapshot when the phone browser returns to the foreground.
- Discards unconfirmed writes during recovery instead of replaying them.
- Contains network-send failures and bounds queued traffic and port fallback.

**Pairing and desktop controls**

- Added temporary six-digit device pairing and authorization revocation.
- Added **Test Remote Web**, the address/connection card and **Disconnect devices**.
- Separates the green code from its expiry instructions and hides expired code details.
- Added **Check installation** and clearer diagnostic reporting.

**Language and usability**

- Added Brazilian Portuguese to the remote panel, including pairing messages.
- Added browser-language detection while preserving a saved language selection.
- Improved the desktop header and Remote Web card layout.
- Improved privacy filtering for copied/exported logs and handling of log-export failures.

**Packaging and preferences**

- Prepared single-executable Release packaging with validation before removing generated companion files.
- Moved desktop preferences to `%LocalAppData%\WandEnhancer\appsettings.json`.
- Added migration of older settings without deleting the old settings file.
- Saves preferences atomically and preserves language, installation path and selected options.

**Compatibility work**

- Completed missing source components in the community reconstruction.
- Checked the patch pipeline against Wand 12.72.0 and 12.73.0.
- Retained the **V2.3 / 2.3.0.0** version labels.

These notes describe the reviewed community source revision. They do not mean that every older executable carrying version 2.3.0.0 includes these changes.

## Restore, updates and diagnostics

### Restore the original installation

1. Open WandEnhancer and select the matching Wand installation.
2. Click **Restore**.
3. Wait for a successful completion message before reopening Wand.

Restore uses the saved original archive and unpacked files, reverses the associated launcher/executable changes and removes the associated auto-apply setup. Diagnostic launcher logs are retained.

If the required backups are incomplete, Restore reports an error. Do not mix backups from different Wand versions.

### After a Wand update

Use the re-detect button beside **Folder path** and check the selected version. An old `app-*` folder can remain after an update.

**Auto-apply after updates** saves the chosen options and uses a background watcher to apply them to a newly installed version. It does not guarantee compatibility with future versions. **Disable updates** is a separate option.

When deploying this revision over an earlier patched build, restore the matching installation, run the updated executable and reapply the Remote Web option so the updated panel files are installed.

### Common problems

| Problem | What to check |
| --- | --- |
| **Test Remote Web** finds nothing | Wand must be running, Remote Web must be applied, and the selected installation must match the running client. |
| Phone cannot load the page | Check the displayed IP/port, local connectivity, guest-network isolation and inbound access in Windows Firewall for that port on the trusted private network. |
| Address contains `localhost` or `127.0.0.1` | That address works on the PC itself. A phone needs the PC's reachable LAN address. |
| Pairing fails | Use the current code, check expiry and retry after the brief limit if too many attempts were made. |
| Connected but no trainer controls | Start a supported game and its trainer in Wand; wait for synchronization. |
| Files differ in **Check installation** | An update or other file change may have occurred. Review the log; the check does not repair the installation. |
| No integrity record | Older revisions did not create one. This result alone does not mean the installation is corrupt. |

**Copy diagnostics** copies version/runtime information, installation state, recent diagnostic summaries and the session log. **Copy logs** copies the session log; **Export logs** saves filtered text to a chosen local file. These actions do not upload a report.

## Support

Report community-build issues in this repository’s [Issues](../../issues).

Include the exact WandEnhancer build, Wand version, Windows version, selected options, affected game, steps to reproduce and relevant logs. Review diagnostics before posting and remove credentials, account tokens and personal information. Do not send proprietary game/client files or account storage.

## Credits and license

- **Original creator:** [k1tbyte](https://github.com/k1tbyte).
- **Original project and contributors:** [k1tbyte/Wand-Enhancer](https://github.com/k1tbyte/Wand-Enhancer).
- **Community continuation, source reconstruction, updates, fixes and documentation:** [lmedeiros01](https://github.com/lmedeiros01).
- **Project license:** [Apache License 2.0](LICENSE.md).

Original authorship and upstream contributor credit remain intact. The original project does not distribute official prebuilt executables; builds published here are separate community distributions. It is not endorsed by k1tbyte or Wand/WeMod.

Preserve the license and applicable notices with redistributed builds. The upstream repository also carries a DMCA-related notice; this repository does not claim to resolve that notice or third-party rights.

