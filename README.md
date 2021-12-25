### Honda_Keihin_KLine_Protocol

#### STEPS 1:
1. Pin Tx = Low (70 ms)
2. Pin Tx = High (120 ms)
3. Set Baudrate = 10400 bps
4. Wake Up with send to ECU code FE 04 72 8C
5. ECU Response with code 0E 04 72 7C
6. Send Initialise code  72 05 00 F0 99 
7. ECU Response 02 04 00 FA
8. Repeat point 1 if there is no response from the ECU. And continue the next Steps if there is a response from the ECU

#### STEPS 2:



