
## `032` AD conversion speed 

The default AD conversion speeds of different versions of transmitters are different, the high speed version AD conversion speed is 0x07:800, the medium speed version is 0x04:120, and the low speed version is 0x02:640, take the low speed version as an example, when the default speed 0x02:640 is changed to 0x03:1280

**Command:** `01 10 00 20 00 01 02 00 02 20 F1`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         20  | 00                   01  | 02         | 00             02  | 20              F1  |

**Return data:** `01 10 00 20 00 01 00 03`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         20  | 00                   01  | 00              03  |

The conversion of analog signals to digital signals, referred to as AD conversion, the faster the AD conversion, the lower the sampling accuracy.

The AD sampling rate is the detection speed of the weighing equipment for the weight of the items on the platform, usually between a few times per second to several hundred times, high-speed weighing applications, up to several thousand times, for an established weighing equipment, the faster the AD rate, the worse the accuracy of the data detected by the AD will be, and the slower the rate of the AD, the higher the accuracy of the AD detection will be relative. Therefore, according to the real weighing needs on the rate, reasonable choice can meet the needs of the lowest gear rate for AD sampling, can maximize the detection accuracy, so as to achieve the best balance on the speed and accuracy.

## `034` Filter types 

Default is 09: Sliding Average Filtering+ First Order Filtering, change to 08: Median Filtering+ First Order Filtering when **Command:** `01 10 00 22 00 01 02 00 08 A1 14`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         22  | 00                   01  | 02         | 00             08  | A1              14  |

**Return data:** `01 10 00 22 00 01 A1 C3`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         22  | 00                   01  | A1              C3  |

Select the appropriate filtering method according to different applications
```
0x00:Not used 0x01:Mean value filtering  
0x02:Median Filter 0x03:First Order Filter  
0x04:Sliding average filter 0x05:Median value average filter  
0x06:Sliding Median Filter  
0x07:Mean filter + First order filter  
0x08:Median Filter + First Order Filter  
0x09:Sliding Average Filter + First Order Filter  
0x0A:median mean filter + first order filter
```

## `035` baud intensity 

When baud strength is changed to 10

**Command:** `01 10 00 23 00 01 02 00 10 A0 CF`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         23  | 00                   01  | 02         | 00             10  | A0              CF  |

**Return data:** `01 10 00 23 00 01 F0 03`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         23  | 00                   01  | F0              03  |

Range: 0\~50, the larger the number, the stronger the filtering

Filter strength: AD sampling data, due to a variety of reasons, often mixed with a variety of noise from different reasons in which, in order to get a weighing data as close as possible to the real weighing data, weighing equipment will be used in the way of digital filtering data signal processing, and the AD filter strength is an important parameter of the data processing, in general, the smaller the filter strength, the faster the response speed of the data output signal, but the effect of noise filtering is also worse; while the larger the filter strength, the slower the response speed of the output signal, but the effect of noise filtering will be better, between the response speed and filtering effect is reasonable. Generally speaking, the smaller the filter strength, the faster the response of the data output signal, but the worse the effect of noise filtering; and the larger the filter strength, the slower the response of the output signal, but for the effect of noise filtering will be the better, between the response speed and filtering effect, reasonable trade-offs, looking for the optimal balance point, is to use a good weighing equipment is a key step, there is no definite standard, the need for users to do a trade-off based on the site, whether it is the speed priority, or stability priority, according to the customer\'s actual situation, or the stability priority, according to the customer\'s actual situation. There is no definite standard, users need to make a trade-off according to the site conditions, whether it is speed priority, or stability priority, according to the actual needs of customers.




## `093` Manual zeroing range 

**Command:** `01 10 00 5D 00 01 02 00 0A 2B 1A` (set 10%)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         5D  | 00                   01  | 02         | 00             0A  | 2B              1A  |

**Return data:** `01 10 00 5D 00 01 90 1B`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         5D  | 00                   01  | 90              1B  |

Manual zero setting is to allow the weighing equipment to take the current weighing data as the current zero point through external keys or commands. As long as the current weighing value does not exceed the range of manual zero setting, the weighing equipment will show the zero reset immediately when the manual zero setting is executed.

## `094` Perform manual zeroing 

**Command:** `01 10 00 5E 00 01 02 00 01 6A EE`

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         5E  | 00                   01  | 02         | 00             01  | 6A              EE  |

**Return data:** `01 10 00 5E 00 01 60 1B`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         5E  | 00                   01  | 60              1B  |

When multiple channels of transmitters are zeroed simultaneously, the command is `01 10 00 5E 00 01 02 00 FF EB 6E`

## `095` Power-on zero setting range 

**Command:** `01 10 00 5F 00 01 02 00 0A 2A F8` (set 10%)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         5F  | 00                   01  | 02         | 00             0A  | 2A              F8  |

**Return data:** `01 10 00 5F 00 01 31 DB`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         5F  | 00                   01  | 31              DB  |

## `096` Setting the automatic zero tracking range 

**Command:** `01 10 00 60 00 01 02 00 64 AE 1B` (when 10d is set)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         60  | 00                   01  | 02         | 00             64  | AE              1B  |

**Return data:** `01 10 00 60 00 01 01 D7`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         60  | 00                   01  | 01              D7  |

Parameter range: 0\~10000; unit: 0.1d; zero tracking function is turned off when setting 0

When the weighing equipment is turned on and in use, the AD signal output will drift because of various reasons such as AD temperature drift, sensor temperature drift creep, etc. The zero tracking calibration program in the equipment will automatically track this very slow drift to offset it, but the zero tracking method has a speed and range.

## `097` Setting the automatic zero tracking time 

**Command:** `01 10 00 61 00 01 02 00 0A 2E 26` (when setting 1s)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         61  | 00                   01  | 02         | 00             0A  | 2E              26  |

**Return data:** `01 10 00 61 00 01 50 17`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         61  | 00                   01  | 50              17  |

## `098` Stabilization range 

**Command:** `01 10 00 62 00 01 02 00 0A 2E 15` (when 10d is set)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         62  | 00                   01  | 02         | 00             0A  | 2E              15  |

**Return data:** `01 10 00 62 00 01 A0 17`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         62  | 00                   01  | A0              17  |

## `099` Stabilization time 

**Command:** `01 10 00 63 00 01 02 00 0A 2F C4` (when setting 1s)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         63  | 00                   01  | 02         | 00             0A  | 2F              C4  |

**Return data:** `01 10 00 63 00 01 F1 D7`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         63  | 00                   01  | F1              D7  |

## `100` Zero Point Range 

**Command:** `01 10 00 64 00 02 04 00 00 00 0A 74 73` (when 10 is
set)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         64  | 00                   02  | 04         | 00             0A  | 74              73  |

**Return data:** `01 10 00 64 00 02 00 17`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         64  | 00                   02  | 00              17  |

## `102` Creep tracking range 

**Command:** `01 10 00 66 00 01 02 00 64 AE 7D` (when 10d is set)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         66  | 00                   01  | 02         | 00             64  | AE              7D  |

**Return data:** `01 10 00 66 00 01 E1 D6`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         66  | 00                   01  | E1              D6  |

## `103` Creep tracking time 

**Command:** `01 10 00 67 00 01 02 00 0A 2E 40` (when setting 1s)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         67  | 00                   01  | 02         | 00             0A  | 2E              40  |

**Return data:** `01 10 00 67 00 01 B0 16`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         67  | 00                   01  | B0              16  |

## `104` Weight units 

**Command:** `01 10 00 68 00 01 02 00 01 6F 78` (when setting 1-g)

| module address | function code | Register Starting Address      | Number of registers      | byte count | register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------|---------------------|
| 01             | 10            | 00                         68  | 00                   01  | 02         | 00             01  | 6F              78  |

**Return data:** `01 10 00 68 00 01 80 15`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         68  | 00                   01  | 80              15  |


## `036` 15 Code value within zero point

**Command:** `01 10 00 24 00 02 04 7F FF FF FF FF 10 D8`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         24  | 00                   02  | 04         | 7F                         FF  | FF                        FF  | 10              D8  |

**Return data:** `01 10 00 24 00 02 01 C3`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         24  | 00                   02  | 01              C3  |

AD internal code value corresponding to zero point;
range:-8000000\~8000000  
Write:0x7fffffff to set the current internal code to the zero internal
code

The zero point is the reference point for weighing, and the weight added or subtracted from this reference point is the actual weighed weight. Zero point calibration, as the name suggests, is a zero point recorded as a benchmark during calibration, and then the weight calibration done on this basis.

## `061` Number of multipoint amendments

**Command:** `01 03 00 3D 00 01 15 C6`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 03            | 00                         3D  | 00                   01  | 15              C6  |

**Return data:** `01 03 02 00 00 B8 44`

| module address | function code | byte count | register data      | CRC16 checksum      |
|----------------|---------------|------------|--------------------|---------------------|
| 01             | 03            | 02         | 00             00  | B4              44  |

This register is read-only. Reading this register returns the number of
internal multipoint corrections; writing this register is invalid.

## `062` Nth point internal code value

**Command:** `01 10 00 3E 00 02 04 7F FF FF FF FF 59 63`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         3E  | 00                   02  | 04         | 7F                         FF  | FF                        FF  | 59              63  |

**Return data:** `01 10 00 3E 00 02 20 04`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         3E  | 00                   02  | 20              04  |

The value of AD internal code corresponding to the Nth point;
Range:-8000000\~8000000; If 0x7fffffff is written to this register, it
will be replaced by the current AD internal code value;

## `064` Point N weight value

**Command:** `01 10 00 40 00 02 04 00 01 00 00 A6 5F`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | Low 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|-------------------------------|---------------------|
| 01             | 10            | 00                         40  | 00                   02  | 04         | 00                         01  | 00                        02  | A6              5F  |

**Return data:** `01 10 00 40 00 02 40 1C`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         40  | 00                   02  | 40              1C  |

Measured value corresponding to the Nth point; Range: -8000000\~8000000.

## `066` Insert correction

**Command:** `01 10 00 42 00 01 02 00 01 68 B2`

| module address | function code | Register Starting Address      | Number of registers      | byte count | High 16-bit register data      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|------------|--------------------------------|---------------------|
| 01             | 10            | 00                         42  | 00                   01  | 02         | 00                         01  | 68              B2  |

**Return data:** `01 10 00 42 00 01 A1 DD`

| module address | function code | Register Starting Address      | Number of registers      | CRC16 checksum      |
|----------------|---------------|--------------------------------|--------------------------|---------------------|
| 01             | 10            | 00                         42  | 00                   01  | A1              DD  |

First write the AD internal code into the Nth point internal code value register; then write the Nth point weight value to the register; then write 0x01 to this register, the module will insert the data into the internal multi-point correction data table; the data table supports a maximum of 50 points (economy type is 10 points), the register is write-only; read return 0

