# PulsePointer for Arch Linux

**PulsePointer for Arch Linux** is an Arch Linux port of [PulsePointer](https://github.com/simonskrede/pulsepointer), bringing audio-reactive mouse cursor visualizations to KDE Plasma 6.

This fork adapts the original project for Arch Linux and Arch-based distributions, with a unified installation script that automatically detects the graphical session, installs the required dependencies, builds the project locally, and installs the necessary files.

## Features

- All original PulsePointer visualization modes.
- Native KDE Plasma 6 KWin effect.
- Rust audio-processing daemon.
- Wayland and X11 installation paths.
- Automatic graphical session detection.
- Automatic dependency installation using pacman.
- Local compilation optimized for the installed system.
- Interactive installation and complete uninstallation.
- No AUR, PKGBUILD, or prebuilt packages required.

## Compatibility

| Component | Supported versions |
|---|---|
| Arch Linux | Supported |
| Arch-based distributions | Supported, provided the required packages and KWin development files are available |
| KDE Plasma | 6.x |
| KWin | 6.6, 6.7, 6.8 |
| Qt | Qt 6 |
| Wayland | Supported |
| X11 | Build and installation path included; practical testing pending |

**Tested configuration:** CachyOS, KDE Plasma 6, KWin 6.8.2, Wayland.

KWin effects use native APIs and are tied to the KWin version against which they are built. PulsePointer is therefore compiled locally against the installed KWin development files.

Rebuild PulsePointer after significant KWin upgrades if necessary.

Other Wayland compositors are not supported.

## Installation

### Requirements

- Arch Linux or a compatible Arch-based distribution.
- KDE Plasma 6.
- KWin 6.6, 6.7, or 6.8.
- An active Wayland or X11 session.
- Internet connection for installing dependencies and downloading Rust dependencies during the first build.
- `sudo` privileges.

### Quick start

Clone the repository:

```bash
git clone https://github.com/bequietbro/pulsepointer-arch.git
cd pulsepointer-arch
```

Make the installer executable and launch it:

```bash
chmod +x install.sh
./install.sh
```

The installer automatically:

1. Detects the Linux distribution and graphical session.
2. Installs the required build dependencies using pacman.
3. Checks the build environment.
4. Builds the Rust daemon.
5. Compiles the appropriate native KWin effect.
6. Installs PulsePointer and enables its user service.

No manual compilation or configuration is required.

### After installation

Log out of KDE Plasma and log back in once so KWin discovers the native effect.

The installer enables the KWin effect and the `pulsepointer.service` user service for graphical sessions.

Open:

**System Settings → Desktop Effects → PulsePointer**

You can configure the visualization mode, intensity, responsiveness, beat ring, color, and overlay size.

## Uninstallation

Run the same installer:

```bash
./install.sh
```

Select **Uninstall PulsePointer** from the interactive menu.

The uninstaller removes PulsePointer's installed files, restores previously backed-up files, and cleans up its installation records.

**System dependencies are intentionally preserved.**

Rust, Cargo, CMake, Ninja, Qt, KDE Frameworks, KWin, and other system packages are never automatically removed.

The source repository and user configuration are also left untouched.

## Building and installation details

Unlike the original Ubuntu distribution, this fork does not provide `.deb` packages or use APT.

The installer builds the project directly on the target machine using the locally installed development libraries and tools.

This approach avoids distributing KWin effect binaries built against a different distribution or KWin ABI.

The installation is local and does not require an AUR package, a third-party package repository, or a prebuilt binary release.

## Original project

This repository is a community-maintained Arch Linux fork of the original project:

**[simonskrede/pulsepointer](https://github.com/simonskrede/pulsepointer)**

The original project provides the Rust daemon, native KWin effect, visualization modes, and configuration interface.

This fork focuses on Arch Linux compatibility, KWin version compatibility, local compilation, and automated installation and uninstallation.

Upstream contributions are welcome.

## License

MIT License. See [LICENSE](LICENSE).

Original project: [PulsePointer](https://github.com/simonskrede/pulsepointer).
