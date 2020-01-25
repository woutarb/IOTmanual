# Getting information from an RFID card to your Serial Monitor
This manual was initially written for the IOT subject from the Designing for Emerging Technologies semester and aims to guide you through the process of connecting your nodeMCU with a RFID module. It will also allow you to read information from RFID cards.= ir tags.

## RFID Arduino programming
The forget-me-not system has a comprehensive system of mostly borrowed sensors and actuators.
One part that it doesn't hijack from existing products is it's NFC pad and the interaction with the objects you shouldn't forget.
NFC is the part that I will try to work out in this manual.
As shown in the designmanual it's important that the user can use an object with an NFC tag to communicate with the system.
Prototyped will be the communication of NFC and system, so it's easier to understand. 
NFC will also occasionally be called RFID in this manual.

## Needs
### Physical :
Physical stuff:
* An arduino board, ESP-12E module.
You need some sort of computing power to make sure something happens with the RFID information.

* Wires to connect the NFC tag with said board
Through the wires the tag will communicate with the board and get power. Which requires less electricity than if it were to use Wi-Fi to communicate with, for example.

* A RFID kit with reader, chip and card.
Can't get the NFC part going without it, after all.

### Software:
For this guide you will need the [RFID library from Miguel Balboa.](https://github.com/miguelbalboa/rfid) 

This library is the be all, end all of starting RFID arduino programming, and is used in most related tutorials for arduino.

### Physical set-up:
![More or less what it should look like](https://github.com/wouterBijns/IOTmanual/blob/master/setup.png "Physical setup")
For this part I followed the quick start guide but because I use a NodeMCU board, the connections are a little different.
D4 - RST
D5 - SCK
D6 - MISO
D7 - MOSI
D8 - SDA(SS)
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
3. Change the pin definitions to the accurate versions of your hardware. My RST_PIN got defined as D4, and my SS_PIN as D8. (SS_PIN is namelijk SDA in de afbeelding)
4. Upload it to your Arduino.
5. If you open your Serial monitor on 9600 baud, it will activate.
6. If you now scan a card or RFID tag, it will dump all the info about it in the serial monitor. This is info you can use if you want to further program with the information on the card or tag


---

## Used RFID hardware: 
https://www.amazon.co.uk/AZDelivery-Reader-Arduino-Raspberry-including/dp/B01M28JAAZ?psc=1&SubscriptionId=AKIAILSHYYTFIVPWUY6Q&tag=duc08-21&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B01M28JAAZ

## Sources:
* Physical set-up image and other information: https://www.addicore.com/v/vspfiles/downloadables/Product%20Downloadables/RFID_RC522/RFIDQuickStartGuide.pdf/

* The library from the quickstart above, which could work if I wasn't stuk on the error. https://github.com/steigeia/RFID_UNID_LOGGER

* https://www.teachmemicro.com/arduino-rfid-rc522-tutorial/

* Used library: https://github.com/miguelbalboa/rfid

