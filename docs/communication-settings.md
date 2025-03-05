## `130` Analog types 

**Command:** `01 10 00 82 00 01 02 00 00 B8 72` (when setting 4\~20mA)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         82  | 00                   01  | 02         | 00             00  | B8              72  |

**Return data:** `01 10 00 82 00 01 A1 E1`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         82  | 00                   01  | A1              E1  |

## `131` Output data types 

**Command:** `01 10 00 83 00 01 02 00 01 78 63` (when setting gross weight value)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         83  | 00                   01  | 02         | 00             01  | 78              63  |

**Return data:** `01 10 00 83 00 01 F0 21`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         83  | 00                   01  | F0              21  |

## `132` First point analog 

**Command:** `01 10 00 84 00 01 02 0F A0 BD 9C` (4000 for 4mA setting)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         84  | 00                   01  | 02         | 0F             A0  | BD              9C  |

**Return data:** `01 10 00 84 00 01 41 E0`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         84  | 00                   01  | 41              E0  |

## `133` First point analog correction 

**Command:** `01 10 00 85 00 01 02 00 64 B8 2E` (fill in 100 when
setting 0.1mA)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         85  | 00                   01  | 02         | 00             64  | B8              2E  |

**Return data:** `01 10 00 85 00 01 10 20`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         85  | 00                   01  | 10              20  |

## `134` First point weight value 

**Command:** `01 10 00 86 00 02 04 00 00 00 00 7B E5` (when setting full scale 0g)

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data     | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|------------------------------|---------------------|
| 01             | 10            | 00                         86  | 00                   02  | 04         | 00                         00  | 00                       00  | 7B              E5  |

**Return data:** `01 10 00 86 00 02 A0 21`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         86  | 00                   02  | A0              21  |

## `136` Second point analog 

**Command:** `01 10 00 88 00 01 02 4E 20 8C A0` (fill in 20000 when setting full scale 20mA)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         88  | 00                   01  | 02         | 4E             20  | 8C              A0  |

**Return data:** `01 10 00 88 00 01 81 E3`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         88  | 00                   01  | 81              E3  |

## `137` Second point analog correction 

**Command:** `01 10 00 89 00 01 02 00 64 B8 E2` (fill in 100 when setting full scale 0.1mA)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         89  | 00                   01  | 02         | 00             64  | B8              E2  |

**Return data:** `01 10 00 89 00 01 D0 23`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         89  | 00                   01  | D0              23  |

## `138` Second point weight value 

**Command:** `01 10 00 8A 00 02 04 00 00 27 10 61 8C` (when setting full scale 10000g)

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data     | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|------------------------------|---------------------|
| 01             | 10            | 00                         8A  | 00                   02  | 04         | 00                         00  | 27                       10  | 61              8C  |

**Return data:** `01 10 00 8A 00 02 60 22`

| module address | function code | Register Starting Address  Number of registers  CRC16 checksum 
|----------------|---------------|----------------------------------------------------------------
> Return data varies according to actual situation)
