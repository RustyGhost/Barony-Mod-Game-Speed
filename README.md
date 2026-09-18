# Barony Mod: Game Speed

A code-level game-speed mod for **Barony** that lets you slow down or accelerate the entire game simulation during single-player gameplay.

The mod adds four configurable game-speed hotkeys. Each hotkey can be assigned its own speed multiplier from **0.1× to 8.0×**, allowing you to switch between different simulation speeds instantly while playing.

This mod is distributed as a modified `barony.exe` and requires an existing legitimate installation of Barony.

## Features

* Whole-game simulation speed control from **0.1× to 8.0×**
* Four independently configurable game-speed slots
* Custom keybinding for each speed slot
* Speed multipliers configurable in **0.1× increments**
* Speed values saved between game sessions
* Keybindings saved normally through Barony's settings
* Restore Defaults and Discard Changes support
* Keyboard and controller navigation in the settings menu
* HUD notification whenever the game speed changes
* `/gamespeed` console variable for manual speed control
* Single-player restriction to avoid multiplayer simulation/desync issues

Default speed slots:

```text
Slot 1: 0.5x
Slot 2: 1.0x
Slot 3: 2.0x
Slot 4: 8.0x
```

All four values can be changed in the controls/settings menu.

## How It Works

The mod changes how quickly Barony accumulates simulation time.

It does **not** change Barony's internal tick rate or redefine how long a simulated second is. Instead, elapsed real time is multiplied by the selected game-speed value before Barony processes its simulation ticks.

As a result, changing the game speed affects the game as a whole, including things such as:

* Player movement
* Enemy AI
* Projectiles
* Combat
* Cooldowns
* Status effects
* Hunger
* Traps
* Tick-driven animations

For example:

```text
0.5x = half-speed simulation
1.0x = normal Barony speed
2.0x = double-speed simulation
8.0x = up to eight-times simulation speed
```

The selected speed remains active until another game-speed slot is activated.

## Installation

> **Back up your original `barony.exe` before installing.**

1. Make sure you have Barony installed normally.
2. Download the modified `barony.exe` from this repository's **Releases** page.
3. Open your Barony installation directory.
4. Rename or otherwise back up the original executable:

```text
barony.exe -> barony-original.exe
```

5. Copy the modded `barony.exe` into the Barony installation directory.
6. Launch Barony normally.

The modified executable uses your existing Barony installation and game data.

This repository does **not** provide the commercial Barony game assets.

## First-Time Setup

The four Game Speed Slot bindings are unbound by default.

Open Barony's controls/settings menu and find:

```text
Game Speed Slot 1
Game Speed Slot 2
Game Speed Slot 3
Game Speed Slot 4
```

Assign whichever keys or controller inputs you want.

Each entry also has an associated speed setting.

The defaults are:

```text
Game Speed Slot 1 = 0.5x
Game Speed Slot 2 = 1.0x
Game Speed Slot 3 = 2.0x
Game Speed Slot 4 = 8.0x
```

Each slot can be configured anywhere between:

```text
0.1x – 8.0x
```

in:

```text
0.1x
```

increments.

## In-Game Use

Press one of your configured Game Speed Slot bindings while playing.

For example:

```text
Slot 1 -> 0.5x
Slot 2 -> 1.0x
Slot 3 -> 2.0x
Slot 4 -> 8.0x
```

A small message will appear on the HUD:

```text
Game Speed: 0.5x
Game Speed: 1.0x
Game Speed: 2.0x
Game Speed: 8.0x
```

The selected speed remains active until you select another speed.

The mod also provides the console variable:

```text
/gamespeed
```

Examples:

```text
/gamespeed 0.5
/gamespeed 1
/gamespeed 2
/gamespeed 8
```

## Compatibility

Current build:

```text
Barony: 5.0.2
Platform: Windows x64
Multiplayer: No / Single-player only
```

Development and testing were performed using an **Epic Games installation of Barony v5.0.2**.

Compatibility with other Windows storefront builds may depend on whether they use the same Barony version and executable configuration.

This mod should not be assumed to work with other versions of Barony.

A future Barony update may overwrite the modified executable or make the mod incompatible.

## Multiplayer

This mod is intentionally restricted to:

```text
multiplayer == SINGLE
```

Game-speed switching is therefore available only during single-player gameplay.

Changing the simulation speed in multiplayer could cause synchronization problems between clients, so multiplayer support is not provided.

## Performance

Higher game speeds require Barony to process considerably more simulation ticks per second of real time.

The mod increases Barony's tick catch-up allowance to better support high simulation speeds, but your CPU still has to execute those game ticks.

As a result, selecting:

```text
8.0x
```

does not guarantee that the game will achieve exactly eight times normal real-world speed on every system or in every situation.

If the CPU cannot process the required simulation workload quickly enough, the effective speed may be lower than the selected multiplier.

## Uninstallation

Restore your original:

```text
barony.exe
```

If you no longer have the original executable, use your storefront's file-verification or repair feature to restore the official Barony files.

For Steam, this is normally:

```text
Barony
-> Properties
-> Installed Files
-> Verify integrity of game files
```

For Epic Games, use the corresponding **Verify** option for the installed game.

Verifying or updating the game may overwrite the modded executable.

## Security Notice

This mod replaces Barony's official `barony.exe` with a custom-compiled executable.

Because the executable is not signed or distributed by Turning Wheel or your game storefront, Windows, your browser, or antivirus software may display a warning.

Only download the mod from this repository's official **Releases** page.

### Verifying the Download

The SHA-256 hash for the released `barony.exe` is:

```A53BB801874EE4CE93E03F41FCF3C20982020B6AD6EB91E60B74EEA3A37BD81E```

To verify your downloaded file, open PowerShell in the folder containing `barony.exe` and run:

```powershell
Get-FileHash .\barony.exe -Algorithm SHA256
```

The `Hash` value shown by PowerShell should match the SHA-256 value above exactly. If it does, your downloaded file is identical to the executable published with this release.


## Source Code

This project is based on the official open-source Barony source code.

The current version is based on:

```text
Barony v5.0.2
```

Upstream source:

https://github.com/TurningWheel/Barony

The primary modifications include:

* Simulation-time scaling
* Increased tick catch-up allowance
* Four configurable game-speed actions
* Configurable speed multipliers
* Settings persistence
* Controls-menu integration
* Runtime hotkey handling
* HUD speed-change notifications

## License

Barony's open-source source code is distributed under the **BSD 2-Clause License**.

The modifications made by this project are also distributed under the BSD 2-Clause License unless otherwise stated.

See [`LICENSE.txt`](LICENSE.txt) for the applicable copyright notices, license conditions, disclaimers, and third-party notices.

This repository does **not** grant a license to Barony's commercial game assets, including artwork, models, textures, sounds, music, maps, or other proprietary game content.

You must obtain Barony separately.

## Disclaimer

This is an unofficial community modification of Barony.

It is not affiliated with, endorsed by, sponsored by, or supported by Turning Wheel LLC.

Barony and its associated names, trademarks, game assets, and other intellectual property remain the property of their respective owners.

The modified software is provided without warranty. Use it at your own risk.
