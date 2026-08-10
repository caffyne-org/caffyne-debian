# caffyne-deb

Debian/Ubuntu packaging for caffyne-shell and its dependencies.

## Packages

| Package | Version | Description |
|---|---|---|
| `caffyne-shell` | 1.0.0 | The shell itself |
| `awww` | 0.12.1 | Wayland wallpaper daemon |
| `matugen` | 4.1.0 | Material You color generator |
| `fabric-cli` | 0~git20260810 | Fabric framework CLI |
| `python-fabric-widgets` | 0.0.2 | Fabric Python framework |
| `python-thefuzz` | 0.22.1 | Fuzzy string matching |

## Targets

- Ubuntu 24.04 (noble)
- Debian 12 (bookworm) via backports

## Building a package locally

```bash
cd <package-dir>
dpkg-buildpackage -us -uc -b
```

## Building all packages (in dependency order)

Build and install dependencies first before building caffyne-shell:

```bash
for pkg in awww matugen fabric-cli python-fabric-widgets python-thefuzz; do
    cd $pkg
    dpkg-buildpackage -us -uc -b
    sudo dpkg -i ../${pkg}_*.deb
    cd ..
done

cd caffyne-shell
dpkg-buildpackage -us -uc -b
```

## Notes

- `python-fabric-widgets` carries a patch (`fabric-pygobject.patch`) to fix
  enum subclass handling against the system PyGObject version.
- `fabric-cli` is versioned as a git snapshot (`0~git20260810`) since upstream
  has no release tags yet.
- All changelogs have entries for both `noble` and `bookworm-backports`.
  When building for Debian, update the suite in the changelog accordingly.
