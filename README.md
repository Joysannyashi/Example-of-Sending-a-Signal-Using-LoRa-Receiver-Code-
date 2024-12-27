//Example-of-Sending-a-Signal-Using-LoRa-Receiver-Code-
#include <SPI.h>
#include <LoRa.h>

void setup() {
  Serial.begin(9600);
  LoRa.begin(915E6);  // Initialize LoRa on 915 MHz
}

void loop() {
  int packetSize = LoRa.parsePacket();
  if (packetSize) {
    // Read the incoming packet
    while (LoRa.available()) {
      String received = LoRa.readString();
      Serial.print("Received: ");
      Serial.println(received);
    }
  }
}
