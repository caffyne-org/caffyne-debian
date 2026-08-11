# caffyne-debian

Official Debian/Ubuntu apt repository for [Caffyne Shell](https://github.com/caffyne-org/caffyne-shell).

## Installation

### Ubuntu 24.04 (Noble)

```bash
# Add the signing key
sudo mkdir -p /etc/apt/keyrings
sudo curl -fsSL https://caffyne-org.github.io/caffyne-debian/caffyne-apt.gpg.pub \
  | gpg --dearmor | sudo tee /etc/apt/keyrings/caffyne.gpg > /dev/null

# Add the repository
echo "deb [signed-by=/etc/apt/keyrings/caffyne.gpg] https://caffyne-org.github.io/caffyne-debian noble main" \
  | sudo tee /etc/apt/sources.list.d/caffyne.list

# Install
sudo apt-get update
sudo apt-get install caffyne-shell
```

### Debian 13 (Trixie)

```bash
# Add the signing key
sudo mkdir -p /etc/apt/keyrings
sudo curl -fsSL https://caffyne-org.github.io/caffyne-debian/caffyne-apt.gpg.pub \
  | gpg --dearmor | sudo tee /etc/apt/keyrings/caffyne.gpg > /dev/null

# Add the repository
echo "deb [signed-by=/etc/apt/keyrings/caffyne.gpg] https://caffyne-org.github.io/caffyne-debian trixie main" \
  | sudo tee /etc/apt/sources.list.d/caffyne.list

# Install
sudo apt-get update
sudo apt-get install caffyne-shell
```

## Packaged dependencies

The following packages are not available in the official Debian/Ubuntu repositories and are provided here:

| Package | Description |
|---|---|
| `awww` | Wayland wallpaper daemon |
| `matugen` | Material You color generation tool |
| `fabric-cli` | Fabric framework CLI |
| `python3-fabric-widgets` | Fabric Python framework |
| `python3-thefuzz` | Fuzzy string matching |
| `libgtk-session-lock0` | GTK3 screen locker library |
| `gir1.2-gtk-session-lock-0.1` | GObject introspection data for gtk-session-lock |

All other dependencies are pulled automatically from the standard Debian/Ubuntu repositories.

## Supported distributions

| Distribution | Status |
|---|---|
| Ubuntu 24.04 (Noble) | ✅ Supported |
| Debian 13 (Trixie) | ✅ Supported |
| Linux Mint 22 | ✅ Should work (Noble based) |

## Arch Linux

For Arch Linux, a separate install script is available in the main [caffyne-shell](https://github.com/caffyne-org/caffyne-shell) repository.

## Fedora

For Fedora, packages are available via [COPR](https://copr.fedorainfracloud.org/coprs/caffyne/).

## Issues

If you run into any packaging issues, please open an issue on this repository. For issues with the shell itself, please open an issue on the [caffyne-shell](https://github.com/caffyne-org/caffyne-shell) repository.
