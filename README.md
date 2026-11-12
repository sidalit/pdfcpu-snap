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
pdfcpu merge all.pdf part1.pdf part2.pdf
```

## Configure

This snap has no `snap set` options. pdfcpu keeps its settings, installed fonts and imported certificates in `~/snap/pdfcpu/current/.config/pdfcpu`, separately from a host installation.

For files under `/media` or `/mnt`:

```bash
sudo snap connect pdfcpu:removable-media
```

## Limitations

- Files must be in a normal folder under your home directory or on connected removable storage. Hidden folders directly under your home directory are not accessible, and `/tmp` is private to the snap.
- pdfcpu cannot replace files or write `split` and `extract` output directly in your home directory, because it uses hidden temporary files there. Work in a subfolder such as `~/Documents`.
- System fonts are not visible: copy a font into your home directory before `pdfcpu fonts install`.

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
