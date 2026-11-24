# -Home-Automation-IOT-NodeMCU-ESP32-Sinricpro-Google-home-Amazon-Alexa-
Developed an IoT-based home automation system using the NodeMCU (ESP8266) microcontroller. Integrated the     Sinricpro platform with Google Home and Amazon Alexa to enable remote and voice-controlled operation of  home appliances, demonstrating skills in IoT and cloud-based smart home systems.
#CODE#
#define WIFI_SSID "YOUR-WIFI-NAME"
#define WIFI_PASS "YOUR-WIFI-PASSWORD"
#define APP_KEY "YOUR-APP-KEY" // Should look like "de0bxxxx-1x3x-4x3x-ax2x5dabxxxxxxxx"
#define APP_SECRET "YOUR-APP-SECRET“
}
#endif
flipSwitch.second.lastFlipSwitchState = flipSwitchState; // update
lastFlipSwitchState
}
}
}
}
void setupWiFi()
{
Serial.printf("\r\n[Wifi]: Connecting");
WiFi.begin(WIFI_SSID, WIFI_PASS);
while (WiFi.status() != WL_CONNECTED)
{
Serial.printf(".");
delay(250);
} digitalWrite(wifiLed, LOW);
Serial.printf("connected!\r\n[WiFi]: IP-Address is %s\r\n",
WiFi.localIP().toString().c_str());
}
void setupSinricPro()
{
for (auto &device : devices)
{
SinricPro.begin(APP_KEY, APP_SECRET);
SinricPro.restoreDeviceStates(true);
}
void setup()
{
setupFlipSwitches();
setupWiFi();
setupSinricPro();
}
void loop()
{
SinricPro.handle();
handleFlipSwitches();
} Serial.begin(BAUD_RATE);
}
SinricPro.begin(APP_KEY, APP_SECRET);
SinricPro.restoreDeviceStates(true);
}
void setup()
{
Serial.begin(BAUD_RATE);
pinMode(wifiLed, OUTPUT);
digitalWrite(wifiLed, HIGH);
setupRelays();
setupFlipSwitches();
setupWiFi();
setupSinricPro();
}
void loop()
{
SinricPro.handle();
handleFlipSwitches();
}
