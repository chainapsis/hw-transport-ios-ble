# Changelog

Changes in this fork are recorded here until a tagged release exists.

## Unreleased

Based on [LedgerHQ upstream `main`](https://github.com/LedgerHQ/hw-transport-ios-ble/commit/b601ebb92d087a58ec380060e28341abb624e75d).

### Added

- Ledger Flex and Nano Gen 5 BLE service and characteristic UUIDs alongside Nano X and Stax.
- Simulated radio tests for supported devices, connection recovery, and scan lifetime.

### Fixed

- Settle pending APDU exchanges and connection attempts once when the radio disconnects.
- Preserve CoreBluetooth error identity for pairing failures.
- Keep timed-out connection attempts in the queue until radio teardown and reject stale callbacks.
- Complete scans when Bluetooth becomes unavailable without stopping a replacement scan.
- Report handshake failures after cancellation completes so callers can retry on a clean connection.
- Remove stopped scans from the queue even if they have not started yet.
- Serialize discovery callback bookkeeping with CoreBluetooth's main-thread callbacks.

### Compatibility

- Retain upstream `main` async scan, name-based connection, and app information APIs.
- Keep this fork's `DisconnectionResponse` callback contract for its existing callers.
