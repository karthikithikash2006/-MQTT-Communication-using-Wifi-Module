# MQTT-Communication-using-WIFI-Module

# AIM: 
  To make a Lamp at home (230 V AC) On / Off using ESP8266, IFTT Google Assistance and Blynk IoT mobile application.          
           
# COMPONENTS REQUIRED:
PC with Internet connection
Micro USB cable
Wifi connection for ESP8266 (Use any mobile hotspot or Router)
	ESP8266 Board
	Mobile Phone with Blynk App installed
            IFTT for Google Voice Assistance
	9 W Bulb and Relay control
Arduino software 
Jumper Wires

## Theory: 
Blynk is an IoT platform for iOS or Android smartphones that is used to control Arduino, Raspberry Pi and NodeMCU via the Internet. This application is used to create a graphical interface or human machine interface (HMI) by compiling and providing the appropriate address on the available widgets.In this experiment we use ESP8266 to control a 220-volt lamp from a web server. But you can also use the same procedure to control fans, lights, AC, or other electrical devices that you want to control remotely.
Relay is an electromechanical device that is used as a switch between high current and low current devices. When the coil in the relay gets fully energized, the contact shifts from the normally open position to the normally closed position. Light bulbs usually operate on 120V or 220V AC power supply. We cannot interface these AC loads directly with the ESP8266 development board, or it will damage the board. We have to use a relay between the ESP8266 and the lamp. 
Google Assistant and IFTTT work together to let you control services with voice commands. When you say a set phrase, Google Assistant processes it and sends it to IFTTT as a trigger. If the phrase matches an applet you've created, IFTTT performs the linked action—like turning on a light or sending a message. Everything runs in the cloud, making it easy to automate tasks with just your voice, as long as the command is correctly matched and all services are online.
When we apply an active high signal to the signal pin of the relay module from any microcontroller like ESP8266, the relay contact moves from the normally open to the normally closed position. It makes the circuit complete, and the output load turns on.

# PROCEDURE:

•	Connect the Arduino UNO R4 WiFi to the PC/laptop using a suitable USB cable. Install and open Arduino IDE on the computer. Install/select the Arduino UNO R4 WiFi board from the Arduino board package. Install the Blynk library in Arduino IDE. Download and install the Blynk IoT application on the mobile phone and create/login to a Blynk account. Create a new Blynk template/device and add a Button widget. Configure the button as a switch and assign a virtual datastream, such as V0. Configure the Wi-Fi SSID and password in the Arduino program along with the required Blynk authentication details. In the Arduino program, configure the built-in LED as the output and associate the Blynk button with the LED control. Select Arduino UNO R4 WiFi as the board and select the appropriate COM port. Compile and upload the program to the Arduino UNO R4 WiFi. Connect the Arduino UNO R4 WiFi to the Internet through a Wi-Fi network or mobile hotspot. Open the Blynk application on the mobile phone. Press the ON button in the Blynk application. The command is sent through the Internet to the Arduino UNO R4 WiFi, and the built-in LED turns ON. Press the OFF button. The Arduino receives the command and the built-in LED turns OFF. Thus, the built-in LED of the Arduino UNO R4 WiFi is successfully controlled remotely using the Blynk IoT application.

# CIRCUIT DIAGRAM:

<img width="663" height="400" alt="image" src="https://github.com/user-attachments/assets/bfebc70d-25b4-4b4a-a7e1-2a02c09bf423" />


 
# PROGRAM:
```
#define BLYNK_TEMPLATE_ID "TMPL3g_KFR7Zi"
#define BLYNK_TEMPLATE_NAME "Arduino Led Control"
#define BLYNK_AUTH_TOKEN            "xxxxxxxxxxxxxxx"

// Enables terminal prints for debugging
#define BLYNK_PRINT Serial

// 2. The CORRECT headers for the Arduino UNO R4 WiFi
#include <WiFiS3.h>
#include <BlynkSimpleWifi.h>

// 3. Add your Wi-Fi credentials here
char ssid[] = "_karthik_";
char pass[] = "20061210";

// This function runs every time the state of Virtual Pin V0 changes in the app
BLYNK_WRITE(V0) {
  int buttonState = param.asInt(); // Read the value from the Blynk app
  
  if (buttonState == 1) {
    digitalWrite(LED_BUILTIN, HIGH); // Turn ON the built-in LED
    Serial.println("LED is ON");
  } else {
    digitalWrite(LED_BUILTIN, LOW);  // Turn OFF the built-in LED
    Serial.println("LED is OFF");
  }
}

void setup() {
  // Start the serial monitor
  Serial.begin(115200);

  // Initialize the built-in LED pin as an output
  pinMode(LED_BUILTIN, OUTPUT);
  digitalWrite(LED_BUILTIN, LOW); // Start with the LED off

  // Connect to Wi-Fi and the Blynk Cloud
  Serial.println("Connecting to Blynk...");
  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
}

void loop() {
  // Keep the Blynk connection alive
  Blynk.run();
}
```

 
# Output:

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/93652c44-feb5-4164-ad8b-dfbbf8ab9aa9" />


<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/0c6bf35e-edbc-4258-a610-e2d356c4e8ed" />


## Result:

Hence an home automation system is implemented using the Blynk app.

