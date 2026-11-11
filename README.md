<div align="center">

<img src="snap/gui/pdfcpu.png" alt="pdfcpu logo" width="128" />

# pdfcpu

**Validate, optimize, merge, split, encrypt and watermark PDF files.**

[![pdfcpu](https://snapcraft.io/pdfcpu/badge.svg)](https://snapcraft.io/pdfcpu)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [pdfcpu](https://github.com/pdfcpu/pdfcpu), a command-line PDF processor that validates, optimizes, assembles, protects and extracts content from PDF files.

</div>

---

## Getting Started

<a href="https://snapcraft.io/pdfcpu"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install pdfcpu
cd ~/Documents
pdfcpu validate report.pdf
pdfcpu optimize report.pdf smaller.pdf
pdfcpu merge all.pdf part1.pdf part2.pdf
```

Run `pdfcpu --help` for the list of commands and `pdfcpu <command> --help` for their options. Bash completion is included.

## Configure

This snap has no `snap set` options. pdfcpu creates its configuration on first use, separately from a host installation:

| Data | Location |
| --- | --- |
| Settings | `~/snap/pdfcpu/current/.config/pdfcpu/config.yml` |
| Fonts added with `pdfcpu fonts install` | `~/snap/pdfcpu/current/.config/pdfcpu/fonts` |
| Certificates added with `pdfcpu certificates import` | `~/snap/pdfcpu/current/.config/pdfcpu/certs` |

Edit `config.yml` with a text editor, then check it:

```bash
pdfcpu config validate
pdfcpu config inspect
```

To keep the configuration elsewhere, pass `--conf <folder>` or set `PDFCPU_CONFIG_ROOT` to a folder the snap can access.

Optional access to files under `/media` or `/mnt`:

```bash
sudo snap connect pdfcpu:removable-media
```

## Limitations

- Files must be in a normal folder under your home directory or on connected removable storage. Hidden folders directly under your home directory and system paths are not accessible, and `/tmp` is private to the snap: output written there is not visible outside.
- Directly in your home directory, pdfcpu cannot replace an existing file (in place or with `--force`), and `split`, `extract` and `images extract` cannot write there, because it stages these writes in hidden temporary files. Use a subfolder such as `~/Documents`.
- Replacing a file whose group differs from the group of your new files (for example after `chgrp`) fails with a `preserve group` error. Write to a new file instead.
- System fonts are not visible. Copy a font file into your home directory before running `pdfcpu fonts install`.
- The trusted certificate store starts empty, as in upstream's release binaries. Import the certificates you trust before validating signatures.
- A configuration in the host's `~/.config/pdfcpu` is not read.

## Build

```bash
git clone https://github.com/sidalit/pdfcpu-snap.git
cd pdfcpu-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/pdfcpu-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/pdfcpu/pdfcpu/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/pdfcpu-snap/blob/main/LICENSE).
