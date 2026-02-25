
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
#include <reg51.h>

void main(void)
{
    TMOD = 0x20;      // Timer1 Mode2
    TH1  = 0xFD;      // 9600 baud rate
    SCON = 0x50;      // Serial mode1
    TR1  = 1;         // Start Timer1

    SBUF = 'A';       // Send character 'A'
    while(TI == 0);   // Wait until transmitted
    TI = 0;           // Clear flag

    while(1);         // Stop here
}


```
### (ii) Serial Port to Transfer a Message

```
#include <reg51.h>

void main(void)
{
    unsigned char msg[] = "GEETHA";
    unsigned char i;

    TMOD = 0x20;      // Timer1 Mode2
    TH1  = 0xFD;      // 9600 baud rate
    SCON = 0x50;      // Serial mode1
    TR1  = 1;         // Start Timer1

    for(i = 0; msg[i] != '\0'; i++)
    {
        SBUF = msg[i];
        while(TI == 0);
        TI = 0;
    }

    while(1);
}

```

### OUTPUT:
<img width="1600" height="965" alt="image" src="https://github.com/user-attachments/assets/4f88c53e-6710-4c3b-b2e4-3a19fd650043" />

<img width="1906" height="1088" alt="image" src="https://github.com/user-attachments/assets/820555ad-b6ae-4311-ab58-bc359fccbc9b" />


### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
