### HONDA KEIHIN KLINE PROTOCOL (DIAGNOSTIC)

#### STEPS 1:
1. Pin Tx = Low (70 ms)
2. Pin Tx = High (120 ms)
3. Set Baudrate = 10400 bps
4. Wake Up with send to ECU code = FE 04 72 8C
5. ECU Response with code = 0E 04 72 7C
6. Send Initialise code = 72 05 00 F0 99 
7. ECU Response = 02 04 00 FA
8. Repeat point 1 if there is no response from the ECU. And continue the next Steps if there is a response from the ECU

#### STEPS 2:
1. Send Request ECM ID = 72 05 71 00 18 
2. ECU Response (eg) = 02 0F 71 00 01 02 32 0F 01 00 00 00 00 00 39
3. Send Request data table 11 = 72 05 71 11 07
4. ECU Response data table 11 (eg) = 02 19 71 11 00 00 00 00 FF 0A AA 0A FF B2 FF FF 79 00 00 00 80 53 09 F1 5C
5. If the ecu response data in table 11 is = 02 05 71 11 77
6. then continue to request data table 17. Send to ECU = 72 05 71 17 01
7. ECU will respond to data table 17 (eg) = 02 18 71 17 00 00 00 00 FF 0A FF FF FF FF 79 00 00 80 8D 00 00 00 00 D3

In addition to using  query table 71, you can also use  query table 72 for example for table 17.

Requests :
72 07 72 17 00 0F EF

Response (eg):
02 15 72 17 00 00 00 17 00 33 7A FF FF FF FF 7D 00 00 62 80 41

Description:
* Request = 72 AA BB CC CS
* 72 = Request Header Code
* AA = Number of Bytes (including the Checksum)
* BB = Query Table
* CC = Table
* CS = Checksum

CHECKSUM
* Usually to make a data table can be started from 00 to FF. With code 72 05 71 ZZ CS
* Where ZZ = data table 00 to FF and CS = Checksum
* The formula checksum = (100 - sumbyte) and FF
* For example the data request Table 13 = 72 05 71 13 CS Then the checksum value = (100 - (72 + 05 + 71 + 13)) AND FF , result CS = 05
* So the data request table 13 = 72 05 71 13 05

All processes are carried out for a maximum of 2 seconds otherwise the ECU will sleep again.
For that, do step 1 and step 2 sequentially

#### K-LINE SCHEMATIC
![IMAGE](https://github.com/AutotronicCommunity/Honda_Keihin_KLine_Protocol/blob/main/FTDI%20KLINE.png)
