# EnigmaRoboTaskPhase
Project: LDR-Controlled Automatic Street Light
This project is a task for the Enigma Robotics Club, designed to demonstrate basic Arduino programming, sensor integration, and circuitry using the Tinkercad virtual environment. The goal was to create a "smart street light" that automatically turns an LED on when it's dark and off when it's bright.

Components Used
The following components were used in the Tinkercad simulation:

Arduino Uno R3

1 x LED (Red)

1 x Photoresistor (LDR)

1 x 220 Ω Resistor (for the LED)

1 x 10 kΩ Resistor (for the LDR)

Breadboard

Jumper Wires

Circuit Diagram and Explanation
https://github.com/ashdjsf/README.md/blob/main/image.png

The circuit consists of two main parts:

The LED Circuit (Output): The LED is connected to digital pin 13 on the Arduino through a 220 Ω current-limiting resistor. The Arduino sends a HIGH or LOW signal to this pin to turn the LED on or off.

The LDR Sensor Circuit (Input): The Light Dependent Resistor (LDR) is used to detect the ambient light level. It is connected in a voltage divider circuit with a 10 kΩ resistor.

In bright light, the LDR has low resistance, which results in a high voltage reading at analog pin A0.

In darkness, the LDR has high resistance, which results in a low voltage reading at analog pin A0.

The Arduino's analogRead() function converts this changing voltage into a number between 0 and 1023.

Final Arduino Code
This is the final code uploaded to the Arduino to run the simulation. It reads the sensor value from pin A0 and controls the LED on pin 13.
// LDR Controlled Street Light 
// Defining the pins
const int ldrPin = A0;  //sensor is connected to analog pin A0
const int ledPin = 13;   //LED is connected to digital pin 13

// variable stores the value from the sensor
int ldrValue = 0;
// light more or less sensitive.
int threshold = 400;

void setup() {
  // Start the communication
  Serial.begin(9600);
  
  //Setting the LED pin as an output pin
  pinMode(ledPin, OUTPUT);
}

void loop() {
  //Reading the analog value from the LDR
  ldrValue = analogRead(ldrPin);
  
  // Print the value to the Serial Monitor
  Serial.print("Sensor Value: ");
  Serial.println(ldrValue);
  
  // Check if level is below the threshold
  if (ldrValue < threshold) {
    // If it is dark, turn LED ON
    digitalWrite(ledPin, HIGH);
  } else {
    // If it is bright, turn LED OFF
    digitalWrite(ledPin, LOW);
  } 
  //delay to check the sim.
  delay(100); 
}
// End of the code

Challenges and Learning Outcomes:

This project provided several learning opportunities, primarily through debugging challenges:

Simulation Freezing: The simulation would often become unresponsive. I learned this was due to a missing delay(100);

Unstable Sensor Readings: At one point, the sensor values were jumping around randomly Re checking all the wires for the sensor circuit from pin A0, to the LDR/resistor junction, to ground fixed the issue.


