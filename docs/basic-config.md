
## `000` Module address 

When 2 or more transmitters/meter are connected to the upper unit, each transmitter/meter must be set to a different address.

**Command:**  `01 10 00 00 00 01 02 00 02 27 91` (unlocked before use) Code format when address is changed from 01 to 02

| module address | function code | Register Starting Address     | Number of registers     | byte count | register data      | CRC16 checksum      |
|----------------|---------------|-------------------------------|-------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                        00  | 00                  01  | 02         | 00             02  | 27              91  |

**Return data:**  `01 10 00 00 00 01 01 C9`

| module address | function code | Register Starting Address     | Number of registers     | CRC16 checksum      |
|----------------|---------------|-------------------------------|-------------------------|---------------------|
| 01             | 10            | 00                        00  | 00                  01  | 01              C9  |

 
## `001` Baud rate setting 

The default baud rate of the transmitter is 0x03:9600 when it is shipped from the factory, and it is changed to 0x07:115200 with the following input format.

**Command:** `01 10 00 01 00 01 02 00 07 E6 43`, selects the system baud rate to 115200 after manually sending the command (unlocked before use)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         01  | 00                   01  | 02         | 00             07  | E6              43  |

**Return data:** `01 10 00 01 00 01 50 09 (the answered data is returned` after the transmitter/meter is switched to the new baud rate, if the host computer is not switched to the new baud rate in time, the data cannot be received)

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         01  | 00                   01  | 50              09  |

## `002` Data frame format 

The transmitter defaults to the 05 (8 data bits, no parity, 1 stop bit) option format when shipped from the factory, and when modified to the 6 (8 data bits, no parity, 2 stop bits) option

**Command:** `01 10 00 02 00 01 02 00 06 27 B0`, manually send the command after the parity bit, data bit, stop bit in the upper computer set to the contents of the 4 (need to be unlocked before use)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         02  | 00                   01  | 02         | 00             06  | 27              B0  |

**Return data:** `01 10 00 02 00 01 A0 09` (the answered data is returned after the transmitter is switched to the new data frame format; if the host computer does not switch to the new data frame format in time, the data cannot be received)

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         02  | 00                   01  | A0              09  |

## `003` Protocol type setting 

Transmitter/instrument default protocol is Modbus RTU, if the protocol is changed to free protocol (unlocked before use)

**Command:** `01 10 00 03 00 01 02 00 00 A6 63`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         03  | 00                   01  | 02         | 00             00  | A6              63  |

**Return data:** `01 10 00 03 00 01 F1 C9`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         03  | 00                   01  | F1              C9  |

00 (Free Protocol), 01 (Modbus RTU), 02 (ASCII), **after the protocol type is switched, the previously modified calibration parameters and other modified parameters are retained, but the digital frame format will be restored to the default value.**

## `004` Command response delay setting 

When the delay is 10ms, it is converted to 0A in hexadecimal.

**Command:** `01 10 00 04 00 01 02 00 0A 27 D3`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         04  | 00                   01  | 02         | 00             0A  | 27              D3  |

**Return data:** `01 10 00 04 00 01 40 08`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         04  | 00                   01  | 40              08  |

The unit is ms, the answer delay is used for RS485 communication, because RS485 is half-duplex, can only send or receive, can not send and receive at the same time. Some hosts are slow to switch between sending and receiving, resulting in the loss of the answer command, so the answer delay time can be reasonably set to avoid the loss of the command.

## `005` Locking/Unlocking System Configuration 

**Command:** `01 10 00 05 00 01 02 5A A5 5C DE`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         05  | 00                   01  | 02         | 5A             A5  | 5C              DE  |

**Return data:** `01 10 00 05 00 01 11 C8`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         05  | 00                   01  | 11              C8  |

Prevents accidental modification of the system configuration due to erroneous commands received during module operation. Once the configuration is locked, the module will not be able to receive external serial port commands for modification until the lock is lifted. 
Including: module address, baud rate, digital frame format, protocol type, restore factory settings and other registers. Write `0x5AA5` Unlocks the system configuration; writing any other value locks the system configuration; reading this register will return 0.

※The transmitter/instrument is locked by default after powering up.

## `006` Firmware version  

Returns the module\'s internal program version number to the host computer, which varies for each transmitter/instrument depending on the model and when it left the factory.

**Command:** `01 03 00 06 00 01 64 0B`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         06  | 00                   01  | 64              0B  |

**Return data:** `01 03 02 00 FA 38 07`

| module address | function code | byte count | High 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|---------------------|
| 01             | 03            | 02         | 00                         FA  | 38              07  |

## `007` Restoration of factory settings 

**Command:** `01 10 00 07 00 01 02 00 55 67 D8`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         07  | 00                   01  | 02         | 00             55  | 67              D8  |

**Return data:** `01 10 00 07 00 01 B0 08`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         07  | 00                   01  | B0              08  |

> Note that this operation will delete all user setup parameters and calibration results inside the transmitter and is not recoverable, so please use with caution!
