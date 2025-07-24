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


**#fakeserial_irrigationcontroller.py**
import random
import time

CROP_THRESHOLD = 600  # threshold for irrigation decision

def should_irrigate(moisture, rain_expected=False):
    return (moisture < CROP_THRESHOLD) and not rain_expected

while True:
    # Simulate reading moisture sensor
    moisture = random.randint(300, 800)
    rain_expected = False  # skip rain forecast for now

   print(f"Moisture: {moisture}, Rain: {rain_expected}")

  if should_irrigate(moisture, rain_expected):
        print("Irrigation ON")
    else:
        print("Irrigation OFF")

   time.sleep(2)




    





