# BTCLN QR Generator

A Flipper Zero app for receiving Bitcoin over the Lightning Network. Generate scannable Lightning Address QR codes for **Speed**, **Strike**, or **Wallet of Satoshi**, with on-device username editing and NDEF tag file export for NTAG213, NTAG215, or NTAG216 stickers.

## Features

- **Home page** — Choose Wallet, Quick QR, and About at the top level.
- **Quick QR** — One-tap shortcut that instantly shows the QR for the wallet you used last. Persisted across reboots.
- **Multi-wallet support** — Three preset wallets: Speed, Strike, and Wallet of Satoshi.
- **On-device username editor** — Type your Lightning Address username on the Flipper. The wallet suffix is appended automatically.
- **Persistent storage** — Usernames and last-used wallet are saved to the SD card; survive reboots and reinstall.
- **Equal-sized QR codes** — Fixed render size regardless of how much data is encoded.
- **Haptic feedback** — Vibration buzz on QR display.
- **NFC tag file export** — Pick NTAG213, NTAG215, or NTAG216 to match your sticker. Generates a Flipper NFC file containing an NDEF URL record with the lightning scheme.

## How to use

Open the app. The home page has Choose Wallet, Quick QR, and About. Use Quick QR for one-tap access to your last wallet, or Choose Wallet to pick a different one. From a wallet's menu, pick Show QR to display the QR, Edit Username to change your handle, or Write NFC Tag to export a tag file. When exporting, you pick the NTAG type that matches your physical sticker.

## Hardware

- Flipper Zero with the latest official firmware. No add-ons required.
- Optional: Blank NTAG213, NTAG215, or NTAG216 sticker for the NFC tag export feature.

## Writing the file to a sticker

Open the stock NFC app, find the file under Saved -> btcln_qr, pick Write, and hold a blank NTAG sticker against the Flipper. The NFC Tools phone app is a reliable fallback if your firmware does not expose Write for NTAG files.

## Privacy

The app runs entirely offline. No network requests are made. Usernames stay on the SD card only.

## License

MIT. The embedded qrcodegen library is by Project Nayuki and is also MIT licensed.
