# Automatic-Motion-Activated-Security-using-PIR-Sensor
## AIM:
             To detect motion using a PIR sensor connected to an Arduino and trigger an LED (using the built-in LED) when motion is sensed.
             
## Hardware / Software Tools required:
1.	 Arduino Uno R3 – 1 No
2.	PIR Sensor – 1 No
3.	LED (in-built on Arduino pin 13) – 1 No
4.	220-ohm resistor – 1 No (used with external LED if necessary)
5.	Breadboard – 1 No
6.	Jumper wires – As required
7.	USB Cable – 1 No (for uploading code and powering Arduino)
8.	Computer with Tinkercad or Arduino IDE installed

## Theory:

     Passive Infrared (PIR) sensors are electronic devices that detect motion by sensing infrared radiation emitted by objects. Every object with a temperature above absolute zero emits infrared radiation. The PIR sensor detects this radiation and can sense motion when a warm object, such as a human body, passes within its detection range. The sensor contains a pair of pyroelectric sensors housed under a Fresnel lens, which focuses the infrared signals onto the sensor surface. When the infrared levels change rapidly between the two pyroelectric sensors—such as when a person walks by—the sensor outputs a HIGH signal indicating motion detection.
PIR sensors are widely used in motion detection systems, security alarms, automatic lighting systems, and smart surveillance. They are popular due to their low power consumption, affordability, and ease of integration with microcontrollers such as the Arduino Uno. The sensor typically has three pins: VCC (power), GND (ground), and OUT (signal). When idle, the output pin remains LOW. Once motion is detected, the sensor sends a HIGH signal to the microcontroller, which can be used to trigger a response such as turning on an LED or activating an alarm.
In this experiment, the PIR sensor is connected to an Arduino Uno board. The VCC pin of the sensor is connected to the 5V supply of the Arduino to power the sensor. The GND pin is connected to the Arduino’s ground. The OUT pin is connected to a digital input pin (pin 2 in this case) of the Arduino. The Arduino continuously monitors the state of the signal pin. If the signal pin goes HIGH, it means the sensor has detected motion, and the Arduino is programmed to turn ON the built-in LED on pin 13. If no motion is detected, the signal remains LOW, and the LED is turned OFF.
Circuit Diagram:
<img width="912" height="412" alt="image" src="https://github.com/user-attachments/assets/ce9854fd-f6f8-4692-9aff-82aef09dae9b" />

## Procedure: //Modify based on your circuit

Step 1: Set Up the Tinkercad Environment
1.	Log in to Tinkercad: Open https://www.tinkercad.com in your browser and log in to your account.
2.	Create a New Circuit: In the Tinkercad dashboard, click on “Circuits” and then select “Create New Circuit” to open a new simulation workspace.
3.	
Step 2: Add Components to the Circuit
1.	Arduino Uno: Drag and drop the Arduino Uno R3 board from the components panel into your workspace.
2.	PIR Sensor: Search for the PIR sensor in the components panel and drag it into the workspace.
3.	LED (optional): The project uses the built-in LED on pin 13, but if preferred, you can add an external LED to visualize the output.
4.	Resistor (for external LED): Use a 220-ohm resistor in series with the external LED (if added) to limit current.
5.	Jumper Wires: Use jumper wires to make all necessary connections between the Arduino, sensor, and other components.

Step 3: Connect the PIR Sensor to the Arduino
1.	PIR Sensor Pin Connections:
o	VCC (Power Pin): Connect to the 5V pin on the Arduino.
o	GND (Ground Pin): Connect to the GND pin on the Arduino.
o	OUT (Signal Pin): Connect to digital pin 2 on the Arduino.
2.	Optional LED Wiring (if external LED used):
o	Anode (+) of LED: Connect to digital pin 13 via a 220-ohm resistor.
o	Cathode (–) of LED: Connect to GND on the Arduino.

Step 4: Write the Arduino Code
1.	Open Code Editor: In the Tinkercad workspace, click on the “Code” button at the top right to access the code editor.
2.	Switch to Text Mode: Select “Text” from the drop-down to write custom C/C++ code.
   
Step 5: Simulate the Circuit
1.	Start Simulation: Click the “Start Simulation” button at the top of the workspace.
2.	Test PIR Sensor: Move the virtual motion object (blue ball) into the sensor range. The LED should turn ON when motion is detected and OFF when no motion is detected.
   
Step 6: Troubleshoot and Refine
1.	Check Wiring: Ensure all connections between the PIR sensor, Arduino, and (optional) LED are correctly made.
2.	Review Code: Make sure the code is properly uploaded and written without syntax errors.
3.	Adjust Sensor Angle: If necessary, reposition the sensor or increase detection range in simulation to trigger motion detection.
   
Step 7: Save Your Work
1.	Stop Simulation: Click the “Stop Simulation” button once testing is complete.
2.	Save the Circuit: Click “Save” at the top of the screen to store your design and code for future use.


# Code:

    #include <LiquidCrystal.h>
    
    // Initialize LCD (RS, E, D4, D5, D6, D7)
    LiquidCrystal lcd(7, 6, 5, 4, 3, 2);
    
    int pirPin = 8;   // PIR sensor output pin
    int ledPin = 9;   // LED pin
    int pirState = LOW;
    int val = 0;
    
    void setup() {
      pinMode(pirPin, INPUT);
      pinMode(ledPin, OUTPUT);
    
      lcd.begin(16, 2);
      lcd.print("Motion Detector");
      delay(2000);
      lcd.clear();
    }
    
    void loop() {
      val = digitalRead(pirPin);
    
      if (val == HIGH) {
        digitalWrite(ledPin, HIGH);
        if (pirState == LOW) {
          lcd.clear();
          lcd.setCursor(0, 0);
          lcd.print("Motion Detected");
          pirState = HIGH;
        }
      } else {
        digitalWrite(ledPin, LOW);
        if (pirState == HIGH) {
          lcd.clear();
          lcd.setCursor(0, 0);
          lcd.print("No Motion");
          pirState = LOW;
        }
      }
    }
    

# Output:

https://github.com/user-attachments/assets/0724f353-6b19-42f8-80aa-eb89f355d1d3

# Result:
The PIR sensor successfully detected motion and triggered the Arduino to turn ON the built-in LED. The LED remained OFF when no motion was present, confirming correct circuit and code functionality.

