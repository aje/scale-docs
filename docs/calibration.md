
## `038` Zero point calibration 

**Command:** `01 10 00 26 00 02 04 00 00 00 00 71 9D`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         26  | 00                   02  | 04         | 00                         00  | 00                        00  | 71              9D  |

**Return data:** `01 10 00 26 00 02 A0 03`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         26  | 00                   02  | A0              03  |

## `042` Gain weights calibration 

**Command:** `01 10 00 2A 00 02 04 4E 20 27 10 16 7D`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         2A  | 00                   02  | 04         | 4E                         20  | 27                        10  | 16              7D  |

**Return data:** `01 10 00 2A 00 02 60 00`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         2A  | 00                   02  | 60              00  |

Place a weight and enter the value you want to calibrate, for example, place a 1KG weight on a 10KG pressure sensor and set the weight weight value to 1000. when the calibration is done, place a 2KG weight on the pressure sensor and the measured value read is 2000.


## `046` Sensor sensitivity 

If the sensitivity of the sensor is 2.000mv/V, write 20000 (keep 4 digits after the decimal point), 20000 is converted to hexadecimal as 4E20.

**Command:** `01 10 00 2E 00 02 04 00 00 4E 20 44 43`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         2E  | 00                   02  | 04         | 00                         00  | 4E                        20  | 44              43  |

**Return data:** `01 10 00 2E 00 02 21 C1`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         2E  | 00                   02  | 21              C1  |

## `048` Sensor range 

If the sensor range is 100kg, to be accurate to 1g, enter 100000, 100000 into hexadecimal as 186A0

**Command:** `01 10 00 30 00 02 04 00 01 86 A0 C3 63`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         30  | 00                   02  | 04         | 00                         01  | 86                        A0  | C3              63  |

**Return data:** `01 10 00 30 00 02 41 C7`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         30  | 00                   02  | 41              C7  |

## `060` Multi-point correction closure 

**Command:** `01 10 00 3C 00 01 02 00 01 62 AC`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         3C  | 00                   01  | 02         | 00             01  | 62              AC  |

**Return data:** `01 10 00 3C 00 01 C1 C5`

| module address | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|--------------------------------|--------------------------|---------------------|
| 01             | 00                         3C  | 00                   01  | C1              C5  |

This register is write-only, writing any non-zero value turns off multipoint correction, reading this register will return 0


## `084` Tare 

**Command:** `01 10 00 54 00 02 04 00 00 00 00 64 F6 8B` (assuming a tare weight of 100)

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         54  | 00                   02  | 04         | 00                         00  | 00                        64  | F6              8B  |

**Return data:** `01 10 00 54 00 02 00 18`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         54  | 00                   02  | 00              18  |

Tare Value;Range:-8000000\~8000000;Write 0x7fffffff to execute auto tare

When the item weighed by the device has a package, if we only need to weigh the item itself, we have to pre-remove the package as a tare. It is possible to physically place the package directly on the weighing platform and tare it, writing 0x7fffffff to perform the automatic tare removal. If the package is inconveniently separated and the weight of the package is known, the tare weight can be entered into the weighing device by sending a command, this is called digital tare.

## `086` Setting maximum range 

**Command:** `01 10 00 56 00 02 04 00 00 27 10 6C 85` (assuming 10000 is entered)

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         56  | 00                   02  | 04         | 00                         00  | 27                        10  | 6C              85  |

**Return data:** `01 10 00 56 00 02 A1 D8`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         56  | 00                   02  | A1              D8  |

For example: there is a weighing equipment, it can weigh the maximum weight is 100.00KG, weighing the minimum number of digital jump change is 0.02KG, then the maximum weighing of this weighing is 100.00KG, that is to say, 100.00KG is the maximum weighing of this weighing can weigh, the index value is 0.02KG, the calibration needs to be set up before the maximum weighing and indexing.

## `088` Setting the index value 

**Command:** `01 10 00 58 00 01 02 00 09 6B 4E` (set to 0x09:0.1)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         58  | 00                   01  | 02         | 00             09  | 6B              4E  |

**Return data:** `01 10 00 58 00 01 80 1A`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         58  | 00                   01  | 80              1A  |

The index value of the weighing platform; you need to set this value before using the weighing platform function.

```
0x00:0.0001 0x01:0.0002 0x02:0x0005  
0x03:0.001 0x04:0.002 0x05:0.005  
0x06:0.01 0x07:0.02 0x08;0.05  
0x09:0.1 0x0A:0.2 0x0B:0.5  
0x0C:1 0x0D:2 0x0E:5  
0x0F:10 0x10:20 0x11:50
```
