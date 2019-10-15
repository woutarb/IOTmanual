# IOTmanual
Manual for the IOT subject from the Designing for Emerging Technologies semester.

## RFID Arduino programming
The forget-me-not system has a comprehensive system of mostly borrowed sensors and actuators.
One part that it doesn't hijack from existing products is it's NFC pad and the interaction with the objects you shouldn't forget.
NFC is the part that I will try to work out in this manual.
As shown in the designmanual it's important that the user can use an object with an NFC tag to communicate with the system.
Prototyped will be the communication of NFC and system, so it's easier to understand. 
NFC will also occasionally be called RFID in this manual.


### Needed:
Physical stuff:
* An arduino board, ESP-12E module.
You need some sort of computing power to make sure something happens with the RFID information.

* Wires to connect the NFC tag with said board
Through the wires the tag will communicate with the board and get power. Which requires less electricity then if it were to use wifi to communicate with, for example.

* A RFID kit with reader, chip and card.
Can't get the NFC part going without it, after all.

### Libraries

https://github.com/miguelbalboa/rfid


### Physical set-up:
![More or less what it should look like](https://github.com/wouterBijns/IOTmanual/blob/master/setup.png "Physical setup")
For this part I followed the quick start guide.
For digital 10 through thirteen, I used D0 through D3. For digital 5, I used D5.
If there's a red light burning, it has power.

### Code set-up:
#### Library:
If you don't already have done so, you will need to add the MFRC522 library to your Arduino library depository.
1. Download the library.
2. Open the Arduino IDE, go to Sketch > Include Library. Click the option to "Add .ZIP Library..."
3. A window will open, navigate to where you downloaded the library and open it. Once it has installed, the IDE should tell you that ` "Library added to your libraries, check "include library"`
4. Include the library by going to Sketch > Include Library > MFRC522.

---

#### Actual Code
1. Restart Arduino
2. Go to file, and get the DumpInfo example from the MFRC522 example collection.
3. Upload it to your Arduino.
4. If you open your Serial monitor on 9600 baud, you will probably see the same errors I do.

```14:04:35.806 -> ⸮E⸮|vAM⸮⸮⸮$⸮⸮⸮⸮Firmware Version: 0xFF = (unknown)``` and 
```14:04:36.110 -> WARNING: Communication failure, is the MFRC522 properly connected?```

After that, I constantly got the error:
```esptool.FatalError: Failed to connect to ESP8266: Timed out waiting for packet header```.
Which even happened during the Blink example, and the other library. (See sources)

Even while 
---

## Used RFID: 
https://www.amazon.co.uk/AZDelivery-Reader-Arduino-Raspberry-including/dp/B01M28JAAZ?psc=1&SubscriptionId=AKIAILSHYYTFIVPWUY6Q&tag=duc08-21&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B01M28JAAZ

## Sources:
* Physical set-up image and other information: https://www.addicore.com/v/vspfiles/downloadables/Product%20Downloadables/RFID_RC522/RFIDQuickStartGuide.pdf/

* The library from the quickstart above, which could work if I wasn't stuk on the error. https://github.com/steigeia/RFID_UNID_LOGGER

* https://www.teachmemicro.com/arduino-rfid-rc522-tutorial/

* Used library: https://github.com/miguelbalboa/rfid

