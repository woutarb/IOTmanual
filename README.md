# A start with Arduino RFID programming
*Getting information from an RFID card to your Serial Monitor*

This manual was initially written for the IOT subject from the Designing for Emerging Technologies semester and aims to guide you through the process of connecting your nodeMCU with a RFID module. It will also allow you to read information from RFID cards.

## RFID Arduino programming
The forget-me-not system has a comprehensive web of mostly borrowed sensors and actuators.
One part that it doesn't hijack from existing products is it's NFC pad and the interaction with the objects you shouldn't forget.

The RFID interaction is what I want to show a vital first step for.
As shown in my design manual it's important that the user can use an object with an NFC tag to communicate with the system.

Prototyped will be how a system can read out RFID, so it's easier to understand how such things work.. 

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

This library is the be all, end all of starting RFID arduino progamming, and is used in most related tutorials for arduino.

There will be three parts to the instructional part of this manual.
1. Physical set-up
2. Library set-up
3. Reading out RFID

## Physical set-up:
![More or less what it should look like](https://github.com/wouterBijns/IOTmanual/blob/master/images/setup.png "Physical setup")
For this part I followed the quick start guide but because I use a NodeMCU board, the connections are a little different. The other detail is that SDA is called SS in the code.

*If there's a red light burning, it has power.*

## Code set-up:
If you haven't already have done so, we will install the MFRC522 library to your Arduino library depository.
If you have done this already, you can skip ahead to "Using the RFID kit"
1. Download the [library](https://github.com/miguelbalboa/rfid).
![Where to click](https://github.com/wouterBijns/IOTmanual/blob/master/images/downloading.png)
2. Open the Arduino IDE, go to Sketch > Include Library. Click the option to "Add .ZIP Library..."
3. A window will open, navigate to where you left the zipped library and select it. Once it has installed, the IDE should tell you that ` "Library added to your libraries, check "include library"`
4. Include the library by going to Sketch > Include Library > MFRC522 to see if it has been added.

*If the following code has been added, adding the library was succesful*
``` 
#include <deprecated.h>
#include <MFRC522.h>
#include <MFRC522Extended.h>
#include <require_cpp11.h> 
```

## Reading out RFID
1. Restart the Arduino development environment
2. Click "file", and get the DumpInfo example from the MFRC522 example collection.
3. Change the pin definitions to the accurate versions of your hardware. My RST_PIN got defined as D4, and my SS_PIN as D8. (Like mentioned before, SS_PIN is the same as SDA in the physical set-up.)

*How the code should look if you followed the manual so far*
![How the code should look](https://github.com/wouterBijns/IOTmanual/blob/master/images/desiredCode.png "Desired code input")

4. Upload it to your Arduino.
5. If you open your Serial monitor on 9600 baud, it will activate.
6. If you now scan a card or RFID tag, it will dump all the info about it in the serial monitor. This is info you can use if you want to further program with the information on the card or tag

*This is what the serial should show you if you tap the reader with your card*
![The desired serial output](https://github.com/wouterBijns/IOTmanual/blob/master/images/desiredOutput.png "Desired output")

## Used RFID hardware: 
Except the cables and nodeMCU board I assume you already own, seeing how you searched for this manual I used a Arduino friendly RFID kit that can be found on [Amazon](https://www.amazon.co.uk/AZDelivery-Reader-Arduino-Raspberry-including/dp/B01M28JAAZ?psc=1&SubscriptionId=AKIAILSHYYTFIVPWUY6Q&tag=duc08-21&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B01M28JAAZ). If you're not a fan of Amazon, [here's an alternative link](https://www.az-delivery.de/products/rfid-set).

## Used sources and further reading:
I got my information from the following sources, they are also great if you want to learn mroe about what we did here in a more detailed manner.

* [Physical set-up image and other information:](https://www.addicore.com/v/vspfiles/downloadables/Product%20Downloadables/RFID_RC522/RFIDQuickStartGuide.pdf/)

>* [The library from the quickstart above which I personally did not use.](https://github.com/steigeia/RFID_UNID_LOGGER)

* [Here's another quickstart, which you can also use to learn how to write to a RFID card](https://www.teachmemicro.com/arduino-rfid-rc522-tutorial/)

* [The used library, which has more information about how you can fix certain problems](https://github.com/miguelbalboa/rfid)

* [What is RFID?](https://www.epc-rfid.info/rfid)

* [The Arduino Project Hub with all kinds of cool RFID projects](https://create.arduino.cc/projecthub/projects/tags/rfid)

* [Top 10 RFID-security concerns](https://securitywing.com/top-10-rfid-security-concerns-threats/)
