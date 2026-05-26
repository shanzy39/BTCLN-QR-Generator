# BTCLN QR Generator

A Flipper Zero app for receiving Bitcoin over the Lightning Network. Generate scannable Lightning Address QR codes for **Speed**, **Strike**, or **Wallet of Satoshi**, with on-device username editing and NDEF `.nfc` tag file export for writing physical NFC stickers.

## Features

- **Multi-wallet support.** Three preset wallets out of the box: Speed (`@speed.app`), Strike (`@strike.me`), and Wallet of Satoshi (`@walletofsatoshi.com`).
- **On-device username editor.** Type your Lightning Address username right on the Flipper using the built-in keyboard. The wallet suffix is appended automatically so you never need to enter `@` or `.`.
- **Persistent storage.** Usernames are saved to the SD card per wallet and survive reboots and uninstall/reinstall.
- **Equal-sized QR codes.** Every QR renders at the same on-screen size regardless of how much data is encoded, for a consistent look.
- **Haptic feedback.** A single vibration buzz confirms the QR is shown.
- **NFC tag file export.** Generate a `.nfc` file for each wallet that the stock Flipper NFC app can write to a blank NTAG213 sticker. When someone taps the sticker with their phone, their Lightning wallet opens with your address pre-filled.

## Hardware Requirements

- **Flipper Zero** (stock hardware, no add-ons required)
- Firmware: Latest official Release or Release Candidate
- Optional: Blank NTAG213 NFC sticker (for the NFC tag export feature)

## Installation

### Option 1: Flipper Application Catalog

Once approved on the catalog, search **"BTCLN QR Generator"** at [lab.flipper.net](https://lab.flipper.net) and click Install.

### Option 2: Build from source

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

The app installs to **Apps → Tools → BTCLN QR Generator** on your Flipper.

## How to use

### Choose a wallet and show your QR

1. Open the app. The wallet picker opens directly.
2. Highlight Speed, Strike, or Wallet of Satoshi and press OK.
3. Choose **Show QR**. The screen draws your Lightning Address QR code with the address text underneath.
4. Press Back to return to the wallet menu.

### Edit your username for a wallet

1. From the wallet menu, choose **Edit Username**.
2. The on-device keyboard opens with the current username pre-filled.
3. Type your new handle (no `@` or domain needed) and press Save.
4. The new username is written to the SD card and used on the next Show QR.

### Export an NFC tag file

1. From the wallet menu, choose **Write NFC Tag**.
2. The app writes a `.nfc` file to `SD:/nfc/btcln_qr/<wallet>.nfc`.
3. Open the stock Flipper **NFC** app, navigate to **Saved → btcln_qr**, open the file, and write it to a blank NTAG213 sticker.
4. When someone taps the sticker with their phone, their Lightning wallet opens with your address.

## File reference

| File | Purpose |
|---|---|
| `application.fam` | Flipper app manifest |
| `btcln_qr.c` | Main app source |
| `qrcodegen.c` / `qrcodegen.h` | Project Nayuki's QR code generator (MIT) |
| `icon.png` | 10x10 1-bit app icon |
| `make_icon.py` | Helper to regenerate `icon.png` |
| `LICENSE` | MIT License |
| `changelog.md` | Version history |

## Technical notes

- Renders QR codes at a fixed 50x50 pixel size regardless of QR version by distributing target pixels across modules.
- NFC tag files are formatted as Flipper `.nfc` files with NTAG213 memory layout and a standards-compliant NDEF URL record using the `lightning:` URI scheme.
- All user data (usernames) stays on the SD card. The app makes no network calls and contains no telemetry.

## Acknowledgements

- QR encoding: [Project Nayuki QR Code generator](https://www.nayuki.io/page/qr-code-generator-library) (MIT)
- Flipper Zero SDK: [Flipper Devices](https://flipper.net/)

## License

MIT. See `LICENSE`.
