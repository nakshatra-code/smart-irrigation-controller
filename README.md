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
