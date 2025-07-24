# smart-irrigation-controller
# sensor value reader(AURDINO SKETCH)
int sensorPin = A0;
int relayPin = 8;

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  Serial.print("Moisture: ");
  Serial.println(sensorValue);

  if (sensorValue < 600) {
    digitalWrite(relayPin, HIGH);  // LED ON
  } else {
    digitalWrite(relayPin, LOW);   // LED OFF
  }
  delay(2000);
}


**#read_serial.py**
<br>
import serial
import time

ser = serial.Serial('COM3', 9600, timeout=1)  # change to COM4 if needed
time.sleep(2)  # give Arduino time to reset

while True:
    if ser.in_waiting > 0:
        data = ser.readline().decode('utf-8').strip()
        if data:
            print("Soil moisture:", data)
    time.sleep(1)

    





