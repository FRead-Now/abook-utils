# abook-utils

`abook`, the tool FRead's audio editors prepare LibriVox recordings with: it
finds a work's recordings, downloads one, trims the LibriVox preamble and
outro from every track, and aligns the recording word by word to the text,
writing the alignment FRead imports. For Apple Silicon Macs, macOS 14 or
later. Each [release](https://github.com/FRead-Now/abook-utils/releases)
says which commit it was built from and which alignment format it writes.

| Command | What it does |
| --- | --- |
| `abook search <title>` | List a work's LibriVox recordings, one line each |
| `abook fetch <id> <folder>` | Download one, and write its `recording.json` |
| `abook strip-intro` | Trim the preamble and outro from every track |
| `abook align` | Align a recording to the text's export |
| `abook play`, `abook at` | Listen to a block, or see what is under a time |

## Install

With [Homebrew](https://brew.sh):

```sh
brew install fread-now/tap/abook-utils
```

Homebrew installs ffmpeg and Python with it, and abook's Python packages
from PyPI (about 350 MB to download, 1.2 GB installed), each checked against
the hash its release lists. Upgrade with `brew upgrade abook-utils` when the
operator tells you a new release is out. Check what you have with
`abook --version`:

```
abook v0.2.0 (fread-audio-alignment 0.1)
```

The speech models download the first time a command needs them, into
`~/.cache`: Whisper `base.en` (about 150 MB) for `strip-intro`, then
`whisper-large-v3-turbo` (1.6 GB) and torchaudio's `MMS_FA` (1.2 GB) for
`align`. They stay there across upgrades.

The editors' other tools, `ingest-work` and `ingest-audiobook` among them,
are [fread-tools](https://github.com/FRead-Now/fread-tools).

## Licence

© FRead Inc. All rights reserved. You may download and run abook to prepare
recordings for FRead.

This repository holds the releases only. abook is built from FRead's private
sources, and the release and the tap are published by that build; the files
here are overwritten at every release.
