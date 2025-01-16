# smart-irrigation

int water;
void setup() {
  pinMode(3, OUTPUT);
  pinMode(6, INPUT);
  Serial.begin(9600);

  water = digitalRead(6);
  Serial.print("Moisture Sensor Value: ");
  Serial.println(water);

  if (water == HIGH) {
    Serial.println("Water Pump Status: OFF");
    digitalWrite(3, LOW);
  } else {
    Serial.println("Water Pump Status: ON");
    digitalWrite(3, LOW); 
  }
}

void loop() {
  int newWater = digitalRead(6);

  if (newWater != water) {
    water = newWater;
    Serial.print("Moisture Sensor Value: ");
    Serial.println(water);

    if (water == HIGH) {
      Serial.println("Water Pump Status: OFF");
      digitalWrite(3, LOW);
    } else {
      Serial.println("Water Pump Status: ON");
      digitalWrite(3, LOW);
    }
  }
  delay(400);
}
