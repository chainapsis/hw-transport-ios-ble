# Repository guide

This repository is the Chainapsis fork of Ledger's `hw-transport-ios-ble` Swift
package. Preserve the upstream `main` APIs retained by this fork and the BLE
recovery behavior and device definitions used by Vizor. The fork's
`DisconnectionResponse` callback intentionally differs from upstream.

## Verification

- Run `swift test` from the repository root after changing package code.
- Exercise scan, connection, APDU exchange, disconnect, and retry paths with
  injected radio callbacks in `Tests/BleTransportTests`.
- For Apple demo build checks, use the Xcode project under
  `BleTransportDemo/`. The iOS demo currently needs a command-line deployment
  target override of `IPHONEOS_DEPLOYMENT_TARGET=15.0` with the installed Xcode.
- Treat simulator radio tests as protocol-flow checks; confirm physical BLE
  discovery and pairing on real devices before claiming hardware validation.

## Integration

Vizor pins this package by commit SHA. After changing the fork, update that
pin and run Vizor's Apple Ledger test harness in the separate Vizor checkout.
Keep fork changes and Vizor integration changes in their respective repositories.
