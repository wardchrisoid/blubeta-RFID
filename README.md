# blubeta-RFID
This repository contains all the information needed for scanning, registering, and triggering an LED with the corresponding RFID chip.

The necesarry components to create the software for the Arduino RFID reader:

Download and install the Arduino IDE software: https://www.arduino.cc/en/Main/Software

Once the Arduino IDE has been installed, import the MFRC522 Library. 
This library can be downloaded from: https://github.com/miguelbalboa/rfid

Run the code found in RFID-Scanner. Scan your RFID card. 
The output produced on screen should display the hex value followed by the dec value of your RFID Chip.



In order to register the chip and assign it to a certain LED, open RFID-Lightboard.


  Create an array that contains the hexadecimal information of the RFID Chips
  The arrays are named by combining the first letter of a persons first name + arr (short for array).
  Here are some examples of the formatting of these arrays
        Ex: uint32_t Jarr[4] = {0x86,0x61,0xFF,0x4A}; This is Jerry's RFID chip with corresponding hex value
        Ex: uint32_t Tarr[4] = {0x9C,0xB6,0x39,0xD5}; This is Tony's RFID chip with corresponding hex value
        
        
  Create int for every array created that are are initialized to 0. 
  The naming format is similar to the arrays containing Hex info.
  Combine the  first letter of a persons first name + count
      Ex: int Jcount = 0;
      Ex: int Tcount = 0;
  
  
  
  In void setup() declare the pins that will be used for the LEDs 
        Ex: pinMode(6, OUTPUT); Pin number 6 is going to deliver an output
        Ex: pinMode(9, OUTPUT); Pin number 9 is going to deliver an output
        
        
  The formula for getting the light to swtich on or off with the RFID chip is as follows
  In this case replace Tarr with whichever array you wish to compare to.
  Correspondingly, replace the Tcount with the int associated with your array.
  Choose which pin this triggers via digitialWrite. The number being the pin num; HIGH being on; LOW being off
  
      if (Tarr[0] == nuidPICC[0] || Tarr[1] == nuidPICC[1] || Tarr[2] == nuidPICC[2] || Tarr[3] == nuidPICC[3]) {
  
      if (Tcount == 0 ){
          digitalWrite(7,HIGH);
          Tcount = 1;
      }
       else{
        digitalWrite(7, LOW);
        Tcount = 0;
       }
        
    }
