# CORE SENSOR - Changelogs

## Core Body Temperature Service Specification

### Changelog for the version 2.1

In order to conveniently access the heart rate value that the CORE sensor receives from a paired heart rate monitor, we changed the Core Body Temperature characteristic. The current value of the heart rate [BPM] is added along with the live values for the temeperature.

### Changelog for the version 2.0

There are some notable changes in the control point characteristic (UUID 00002102-5B1E-4347-B07C-97B514DAE121).

**changes for Control Point OpCodes**

| OpCode          | HRM type | kind    | description                                                                                                                                                     |
| --------------- | -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x01`          | ANT+     | changed | re-defined to clear only list of paired _ANT+_ monitors instead of both ANT+ and Bluetooth                                                                      |
| `0x02` / `0x03` | ANT+     | changed | use 3 bytes in parameter for both 16bit and 20bit addresses permitted (before: 2 bytes for 16 bit)                                                              |
| `0x05`          | ANT+     | changed | always use 3 bytes for both 16bit and 20bit addresses, whereof byte 3 should be the transmission type. Move state information about the channel to 4th byte.    |
| `0x09`          | BLE      | changed | put state information as LSO and send Bluetooth Local name instead of Bluetooth MAC address.                                                                    |
| `0x0A`          | ANT+     | changed | made this procedure "non-blocking": will not wait until scan is finished anymore, will immediately return with "OK" if procedure could be successfully started. |
| `0x0B`          | BLE      | changed | re-defined this OpCode, it is now used to get the total number of scanned ANT+ heart rate monitors.                                                             |
| `0x0C`          | ANT+     | new     | Get ID of scanned ANT+ heart rate monitor at index _i_.                                                                                                         |
| `0x0D`          | BLE      | new     | Start scan for available BLE heart rate monitors.                                                                                                               |
| `0x0E`          | BLE      | new     | Get total number of scanned BLE heart rate monitors.                                                                                                            |
| `0x0F`          | BLE      | new     | Get name of scanned BLE heart rate monitor at index _i_.                                                                                                        |
| `0x10`          | BLE      | new     | Get MAC of scanned BLE heart rate monitor at index _i_.                                                                                                         |
| `0x11`          | BLE      | new     | Clear list of BLE paired heart rate monitors.                                                                                                                   |
| `0x12`          | BLE      | new     | Get MAC and status of paired BLE heart rate monitor at index _i_.                                                                                               |

## CORE SENSOR - General Bluetooth specification
only relevant BLE interface changes are documented.

### Changelog firmware version 0.8.4 (2023-11-10)
- support `COre Body Temperature Service` (v2.1)

### Changelog firmware version 0.8.3 (2023-10-09)
- support `COre Body Temperature Service` (v2.0)

### Changelog firmware version 0.8.1 (2023-06-20)
- allow up to 3 simultaneous BLE connections (with some restrictions)

### Changelog firmware version 0.8.0 (2023-02-17)
- support `Core Body Temperature Service` (v1.2)
- allow up to 2 simultaneous BLE connections (with some restrictions)
- new advertisement packet structure, as described in v2.1 of `CORE BLE Implementation Notes.pdf`
- device name fixed as "CORE AB:CD" (last 2 hex digits)

### Changelog firmware version 0.6.1 (2021-11-29)
- support  `Core Body Temperature Service` (v1.0)
