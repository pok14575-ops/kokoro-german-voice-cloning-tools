# Kokoro German Voice Cloning Tools

Utilities for training and extracting German voices in Kokoro voicepack format.

This repository provides helper scripts for creating German Kokoro TTS voices using StyleTTS2-based fine-tuning workflows. The focus is on solving the practical parts of the pipeline that are often missing from upstream documentation: dataset preparation, phoneme generation, training conversion, voicepack extraction, and validation.

---

## Features

### `prepare_dataset.py`

Builds a German TTS dataset from source audio.

Features:

* Whisper transcription
* German language filtering
* Audio quality filtering
* Speaker clustering
* MP3 → WAV conversion
* IPA phoneme generation
* Dataset statistics

---

### `prepare_training.py`

Converts a prepared dataset into StyleTTS2 training format.

Features:

* Train / validation split generation
* Kokoro weight conversion
* Kokoro vocabulary alignment fixes
* Training verification
* Optional mel/F0 precomputation

---

### `extract_voicepack.py`

Extracts a Kokoro-compatible voicepack from a trained StyleTTS2 checkpoint.

Features:

* Stage 1 checkpoint support
* Stage 2 checkpoint support
* Acoustic embedding extraction
* Prosodic embedding extraction
* Automatic voicepack generation

---

### `test_inference.py`

Tests trained checkpoints using a German phonetic validation set.

Covers:

* Umlauts (ä, ö, ü)
* Ich-Laut / Ach-Laut
* ß handling
* Consonant clusters
* Numbers
* Prosody and punctuation

---

## Why This Exists

Kokoro inference is relatively simple.

Training custom German voices requires several additional steps that are not fully documented in a single place. These scripts automate those steps and provide a reproducible workflow for creating German Kokoro-compatible voicepacks.

---

## Typical Workflow

```text
Source Audio
      ↓
prepare_dataset.py
      ↓
Prepared Dataset
      ↓
prepare_training.py
      ↓
StyleTTS2 Training
      ↓
extract_voicepack.py
      ↓
Kokoro Voicepack (.pt)
      ↓
test_inference.py
```

---

## Upstream Projects

This repository builds upon:

### Kokoro TTS

https://github.com/hexgrad/kokoro

### StyleTTS2

https://github.com/yl4579/StyleTTS2

Please refer to the original projects for model architecture, training code, and licensing information.

---

## Keywords

German TTS, Kokoro TTS, Voice Cloning, German Voice Cloning, StyleTTS2, Speech Synthesis, Voicepack Extraction, German Speech Synthesis, Text To Speech, TTS Training, Kokoro Voicepack, IPA Phonemes, Neural Voice Cloning, Fine-Tuning

---

## Disclaimer

This repository contains utility scripts only.

No trained models, voicepacks, datasets, copyrighted audio, or third-party voice assets are included.

Any voices created using these tools are the responsibility of the user.
