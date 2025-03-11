
## `08` Module status

(Supported by V1.1 firmware and above)

**Command:** `01 03 00 08 00 01 05 C8`

| module address | function code | Register Starting Address       | Number of registers      | CRC16 checksum      |
|----------------|---------------|---------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         08   | 00                   01  | 05              C8  |

**Return data:** `01 03 02 08 02 3E 45`

| module address | function code | bytes | digital      | CRC16 checksum      |
|----------------|---------------|-------|--------------|---------------------|
| 01             | 03            | 02    | 08       02  | 3E              45  |

The return data is 0802, 0802 is hexadecimal data, convert 0802 to binary, the data obtained is 0000100000000010.

|                     | Bit15-Bit12 | Bit2-0           |
|---------------------|-------------|------------------|
| binary data         | 0000        | 010              |
| decimal system      | 0000        | 2                |
| corresponding state |             | 2 decimal places |

| bit   | description | 0                      | 1                |
|-------|-------------|------------------------|------------------| 
| 11    | sensing     | Peak Not Detected      | Detected         |
| 10    | Trough      | valley not detected    | detected         |
| 9     | normalcy    | normal                 | overload (V1.3)  |
| 8     | routine     | General                | Smart Sensor     |
| 7     | zero        | Non-Zero               | Zero             |
| 6     | overflow    | normal                 | overflow         |
| 5     | stabilise   | stable                 | unstable         |
| 4     | Power       | power on not cleared   | power on cleared |
| 3     | positive    | plus sign              | minus sign       | 

## `30` Reading the measured value

**Command:** `01 03 00 1E 00 02 A4 0D`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         1E | 00                   02  | A4              0D  |

**Return data:** `01 03 04 00 00 01 62 7A 4A` (data varies according to the
actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | 00                         00  | 01                        62  | 7A              4A  |

The measured value is the AD internal code value calibrated and
converted by zero and gain.

## `44` Reading AD internal code

**Command:** `01 03 00 2C 00 02 05 C2`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         2C | 00                   02  | 05              C2  |

**Return data:** `01 03 04 00 19 3B 67 79 2E` (data vary according to the
actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | 00                         19  | 3B                        67  | 79              2E  |

The module returns the current AD internal code value to the host.

## `80` Reading of weights/measurements

**Command:** `01 03 00 50 00 02 C4 1A`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         50 | 00                   02  | C4              1A  |

**Return data:** `01 03 04 00 00 00 00 84 FA 50` (data varies according to
the actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | 00                         00  | 00                        84  | FA              50  |

## `82` Net weight reading

**Command:** `01 03 00 52 00 02 65 DA`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         52 | 00                   02  | 65              DA  |

**Return data:** `01 03 04 FF FF C1 EF EA 0B` (data vary according to the actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | FF                         FF  | C1                        EF  | EA              OB  |

Net Weight= Weight-Tare
