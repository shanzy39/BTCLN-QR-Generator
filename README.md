# BTCLN QR Generator

A Flipper Zero app for receiving Bitcoin over the Lightning Network. Generate scannable Lightning Address QR codes for **Speed**, **Strike**, or **Wallet of Satoshi**, with on-device username editing and NDEF `.nfc` tag file export for NTAG213, NTAG215, or NTAG216 stickers.

## Features

- **Home page with About** — Top-level menu with **Choose Wallet** and **About** options.
- **Multi-wallet support** — Three preset wallets: Speed (`@speed.app`), Strike (`@strike.me`), and Wallet of Satoshi (`@walletofsatoshi.com`).
- **On-device username editor** — Type your Lightning Address username on the Flipper. The wallet suffix is appended automatically.
- **Persistent storage** — Usernames saved per wallet to the SD card; survive reboots and reinstall.
- **Equal-sized QR codes** — Fixed render size regardless of how much data is encoded.
- **Haptic feedback** — Vibration buzz on QR display.
- **NFC tag file export** — Pick **NTAG213 / NTAG215 / NTAG216** to match your sticker. Generates a Flipper `.nfc` file containing an NDEF URL record with `lightning:<address>`.

## Hardware Requirements

- **Flipper Zero** (stock hardware, no add-ons required)
- Firmware: Latest official Release or Release Candidate
- Optional: Blank NTAG213 / NTAG215 / NTAG216 sticker

## Installation

### Build from source

Requirements: Python 3 + a USB cable.

```bash
# Install the Flipper build tool (once)
pip3 install --upgrade ufbt

# Clone this repo
git clone https://github.com/shanzy39/BTCLN-QR-Generator.git
cd BTCLN-QR-Generator

# Plug in your Flipper, then:
python3 -m ufbt launch
```

The app installs to **Apps → Tools → BTCLN QR Generator**.

## How to use

### Home page

Opens at start. Two options:

1. **Choose Wallet** — Opens the wallet picker.
2. **About** — A scrolling page describing what the app does. Use Up/Down to scroll, Back to return.

### Display your QR

1. Choose Wallet → pick Speed / Strike / Wallet of Satoshi.
2. **Show QR** — Renders your Lightning Address as a QR with the address text below.
3. Anyone can scan the QR with a Lightning wallet to pay you.

### Edit your username

1. From a wallet's menu, choose **Edit Username**.
2. Type your handle on the built-in keyboard (no `@` or domain needed).
3. Save. The username is persisted to the SD card.

### Export an NFC tag file

1. From a wallet's menu, choose **Write NFC Tag**.
2. The **Select Tag Type** screen appears with NTAG213 / NTAG215 / NTAG216.
3. Pick the type that matches your physical sticker.
4. The file is saved to `SD:/nfc/btcln_qr/<wallet>_<ntagtype>.nfc`.

### Writing the file to a physical sticker

Current stock Flipper firmware does **not** include a direct "Write" option for saved NFC files. To get the URL onto a sticker, use one of these:

- **NFC Tools app on phone** (free, Android/iOS) — Open the app, choose Write → Add a record → URL, enter `lightning:<your-username>@<wallet-domain>`, then tap your sticker. Fastest option.
- **Custom Flipper firmware** — Momentum, Xtreme, or RogueMaster firmware restores a direct Write option in the NFC app's saved file menu, which works with our `.nfc` file.

## File reference

| File | Purpose |
|---|---|
| `application.fam` | Flipper app manifest |
| `btcln_qr.c` | Main app source |
| `qrcodegen.c` / `qrcodegen.h` | Project Nayuki's QR code generator (MIT) |
| `icon.png` | 10x10 1-bit lightning bolt icon |
| `make_icon.py` | Helper to regenerate `icon.png` |
| `LICENSE` | MIT License |
| `changelog.md` | Version history |

## Technical notes

- QR rendered at fixed 50x50 pixels regardless of QR version, with module-distribution that produces a consistent on-screen size.
- NFC tag files use the standard Flipper `.nfc` format with the chosen NTAG type's CC byte (`0x12` / `0x3E` / `0x6D`) and page count (45 / 135 / 231).
- NDEF payload is a single URL record with the `lightning:` scheme — recognized by every major Lightning wallet on iOS and Android.
- All data stays on the SD card. The app makes no network calls and contains no telemetry.

## Acknowledgements

- QR encoding: [Project Nayuki QR Code generator](https://www.nayuki.io/page/qr-code-generator-library) (MIT)
- Flipper Zero SDK: [Flipper Devices](https://flipper.net/)

## License

MIT. See `LICENSE`.
