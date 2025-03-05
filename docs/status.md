
## `008` Module status
```
Bit15\-\--Bit12:All 0 Bit11:0 Peak Not Detected/1 Detected

Bit10:0 valley not detected/1 detected Bit9:0 normal/overload (V1.3)

Bit8:0 General/1 Smart Sensor Bit7:0 Non-Zero/1 Zero

Bit6:0 normal/1 overflow Bit5:0 stable/1 unstable

Bit4:0 power on not cleared/1 power on cleared

Bit3:0 plus sign/1 minus sign Bit2-0:Decimal point position
```
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

|                     | Bit15-Bit12 | Bit11   | Bit10               | Bit9     | Bit8    | Bit7     | Bit6     | Bit5      | Bit4                 | Bit3                          | Bit2-0           |
|---------------------|-------------|---------|---------------------|----------|---------|----------|----------|-----------|----------------------|-------------------------------|------------------|
| binary data         | 0000        | 1       | 0                   | 0        | 0       | 0        | 0        | 0         | 0                    | 0                             | 010              |
| decimal system      | 0000        | 1       | 0                   | 0        | 0       | 0        | 0        | 0         | 0                    | 0                             | 2                |
| corresponding state |             | sensing | Trough not detected | normalcy | routine | non-zero | normalcy | stabilise | Power on not cleared | positive value sign + (math.) | 2 decimal places |

## `030` Reading the measured value

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

## `044` Reading AD internal code

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

## `080` Reading of weights/measurements

**Command:** `01 03 00 50 00 02 C4 1A`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         50 | 00                   02  | C4              1A  |

**Return data:** `01 03 04 00 00 00 00 84 FA 50` (data varies according to
the actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | 00                         00  | 00                        84  | FA              50  |

## `082` Net weight reading

**Command:** `01 03 00 52 00 02 65 DA`

| module address | function code | Register Starting Address     | Number of registers      | CRC16 checksum      |
|----------------|---------------|-------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         52 | 00                   02  | 65              DA  |

**Return data:** `01 03 04 FF FF C1 EF EA 0B` (data vary according to the actual situation)

| module address | function code | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 03            | 04         | FF                         FF  | C1                        EF  | EA              OB  |

Net Weight= Weight-Tare
