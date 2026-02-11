int soilMoisturePin = A0; // Analog pin for soil moisture sensor
int relayPin = 7; // Digital pin for relay module
int moistureValue = 0;
int threshold = 40; 
 // Threshold value
void setup()
{
 Serial.begin(9600);
 pinMode(relayPin, OUTPUT);
}
void loop() 
{
 moistureValue = analogRead(soilMoisturePin);
 Serial.print("Moisture value: ");
 Serial.println(moistureValue);
 delay(1000);
 if (moistureValue < threshold)
{
 digitalWrite(relayPin, HIGH);
 Serial.println("Soil is dry. Pump ON.");
 } 
else 
{
 digitalWrite(relayPin, LOW);
 Serial.println("Soil is moist enough. Pump OFF.");
 }
}
