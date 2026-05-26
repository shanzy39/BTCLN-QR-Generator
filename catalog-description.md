# BTCLN QR Generator

A Flipper Zero app for receiving Bitcoin over the Lightning Network. Generate scannable Lightning Address QR codes for **Speed**, **Strike**, or **Wallet of Satoshi**, with on-device username editing and NDEF tag file export for writing physical NFC stickers.

## Features

- **Multi-wallet support.** Three preset wallets: Speed, Strike, and Wallet of Satoshi.
- **On-device username editor.** Type your Lightning Address username right on the Flipper using the built-in keyboard. The wallet suffix is appended automatically.
- **Persistent storage.** Usernames are saved to the SD card per wallet and survive reboots and reinstalls.
- **Equal-sized QR codes.** Every QR renders at the same on-screen size regardless of how much data is encoded.
- **Haptic feedback.** A vibration buzz confirms the QR is shown.
- **NFC tag file export.** Generate an NFC tag file for each wallet that the stock Flipper NFC app can write to a blank NTAG213 sticker. When someone taps the sticker with their phone, their Lightning wallet opens with the address pre-filled.

## How to use

Open the app. The wallet picker opens directly. Choose Speed, Strike, or Wallet of Satoshi and press OK. From the wallet menu, choose **Show QR** to display the Lightning Address QR code, **Edit Username** to set or change your handle, or **Write NFC Tag** to export an NFC tag file.

## Hardware

- Flipper Zero with the latest official firmware. No add-ons required.
- Optional: Blank NTAG213 NFC sticker for the NFC tag export feature.

## Privacy

The app runs entirely offline. No network requests are made. Usernames stay on the SD card only.

## License

MIT. The embedded qrcodegen library is by Project Nayuki and is also MIT licensed.
