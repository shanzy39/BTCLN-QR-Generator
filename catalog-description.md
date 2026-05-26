# BTCLN QR Generator

A Flipper Zero app for receiving Bitcoin over the Lightning Network. Generate scannable Lightning Address QR codes for **Speed**, **Strike**, or **Wallet of Satoshi**, with on-device username editing and NDEF tag file export for NTAG213, NTAG215, or NTAG216 stickers.

## Features

- **Home page with About** — Top-level menu with Choose Wallet and About options.
- **Multi-wallet support** — Three preset wallets: Speed, Strike, and Wallet of Satoshi.
- **On-device username editor** — Type your Lightning Address username on the Flipper. The wallet suffix is appended automatically.
- **Persistent storage** — Usernames saved per wallet to the SD card; survive reboots and reinstall.
- **Equal-sized QR codes** — Fixed render size regardless of how much data is encoded.
- **Haptic feedback** — Vibration buzz on QR display.
- **NFC tag file export** — Pick NTAG213, NTAG215, or NTAG216 to match your sticker. Generates a Flipper NFC file containing an NDEF URL record with the lightning scheme.

## How to use

Open the app. The home page has Choose Wallet and About. Choose a wallet, then pick Show QR to display the QR, Edit Username to change your handle, or Write NFC Tag to export a tag file. When exporting, you pick the NTAG type that matches your physical sticker.

## Hardware

- Flipper Zero with the latest official firmware. No add-ons required.
- Optional: Blank NTAG213, NTAG215, or NTAG216 sticker for the NFC tag export feature.

## Writing the file to a sticker

The saved NFC file can be written to a physical sticker using the NFC Tools phone app (free, Android and iOS) or via custom Flipper firmware that exposes a direct Write action.

## Privacy

The app runs entirely offline. No network requests are made. Usernames stay on the SD card only.

## License

MIT. The embedded qrcodegen library is by Project Nayuki and is also MIT licensed.
