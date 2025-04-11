# SwayFX ARM Debian Package

This document describes how to build and install the SwayFX Debian package for ARM-based systems like Kali Linux on ARM.

## Building the Debian Package

The Debian package for ARM architectures is automatically built by GitHub Actions when:

1. Code is pushed to the main branch
2. A pull request is submitted against the main branch
3. A tag is pushed (which creates a release with the package attached)
4. The workflow is manually triggered

To manually trigger a build:

1. Go to the GitHub repository
2. Click on "Actions"
3. Select "Build ARM Debian Package" workflow
4. Click "Run workflow" dropdown
5. Select the branch and click "Run workflow"

## Installing the Package

### Option 1: Download from GitHub Actions artifacts

1. Go to the GitHub repository
2. Click on "Actions"
3. Select a successful workflow run of "Build ARM Debian Package"
4. Scroll down to the "Artifacts" section
5. Download the `swayfx-arm64-deb` artifact
6. Extract the ZIP file to get the .deb package
7. Install with: `sudo apt install ./swayfx_*.deb`

### Option 2: Download from Releases (if available)

If the package was built from a tag:

1. Go to the GitHub repository
2. Click on "Releases"
3. Find the latest release
4. Download the .deb file for your architecture
5. Install with: `sudo apt install ./swayfx_*.deb`

## Dependencies

The package has dependencies that should be automatically resolved by apt. If not, you may need to install:

```bash
sudo apt install libc6 libcairo2 libgdk-pixbuf2.0-0 libglib2.0-0 libjson-c5 libpango-1.0-0 \
  libpangocairo-1.0-0 libpcre2-8-0 libwayland-client0 libwayland-cursor0 libwayland-server0 \
  libwlroots10 libxkbcommon0 libpixman-1-0 libinput10
```

Additionally, it's recommended to install:

```bash
sudo apt install swaybg swaylock xdg-desktop-portal xdg-desktop-portal-wlr
```

## Usage

After installation, you can start SwayFX with:

```bash
sway
```

If you have another display manager installed, you might need to create a desktop entry by placing a file at `/usr/share/wayland-sessions/sway.desktop`.