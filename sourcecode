#define BLYNK_TEMPLATE_ID "TMPL3sPP4gzVm"
#define BLYNK_TEMPLATE_NAME "IOT"
#define BLYNK_AUTH_TOKEN "_jD4uO4LpJKDYMjMejrNgcK_1g7JYZS4"

#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>
#include <DHT.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

// ==== Blynk Auth & WiFi ====
char auth[] = "_jD4uO4LpJKDYMjMejrNgcK_1g7JYZS4";
char ssid[] = "Niranjan";
char pass[] = "Srinivas@451";

// ==== DHT11 Sensor Setup ====
#define DHTPIN D1  // GPIO5
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

// ==== Soil Moisture Setup ====
#define SOIL_PIN A0

// ==== OLED Setup ====
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
#define OLED_RESET -1
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// ==== Blynk Virtual Pins ====
#define VPIN_TEMP V0
#define VPIN_HUM  V1
#define VPIN_SOIL V2

void setup() {
  Serial.begin(9600);
  
  Blynk.begin(auth, ssid, pass);
  dht.begin();

  if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    Serial.println(F("OLED allocation failed"));
    while(true);
  }

  display.clearDisplay();
  display.setTextColor(WHITE);
  display.setTextSize(1);
  display.setCursor(0,0);
  display.println("Env Monitoring System");
  display.display();
  delay(2000);
}

void loop() {
  Blynk.run();

  float temp = dht.readTemperature();
  float hum = dht.readHumidity();
  int soilValue = analogRead(SOIL_PIN);
  int soilPercent = map(soilValue, 1023, 0, 0, 100);

  // Print to Serial Monitor
  Serial.print("Temp: "); Serial.print(temp);
  Serial.print("°C, Hum: "); Serial.print(hum);
  Serial.print("%, Soil: "); Serial.print(soilPercent); Serial.println("%");

  // Send data to Blynk
  Blynk.virtualWrite(VPIN_TEMP, temp);
  Blynk.virtualWrite(VPIN_HUM, hum);
  Blynk.virtualWrite(VPIN_SOIL, soilPercent);

  // Display on OLED
  display.clearDisplay();
  display.setCursor(0, 0);
  display.setTextSize(1);
  display.println("Env Monitor");
  display.setTextSize(1);
  display.setCursor(0, 16);
  display.print("Temp: "); display.print(temp); display.println(" C");
  display.print("Hum : "); display.print(hum); display.println(" %");
  display.print("Soil: "); display.print(soilPercent); display.println(" %");
  display.display();

  delay(2000); // Update every 2 seconds
}
