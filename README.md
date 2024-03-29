# RNSES-Cynthia-P5
## Tabla de contenidos 
* [Información](#info)
* [Tarea 1. Establece un “chat” Bluetooth](#technologies)

## Tarea 1
Establecer un “chat” Bluetooth con perfil SPP con una APP en el móvil: https://github.com/espressif/arduino-esp32/tree/master/libraries/BluetoothSerial
```
/*TAREA 1: Establecer un “chat” Bluetooth con perfil SPP con una APP en el móvil
*/
#include "BluetoothSerial.h"
// crea un puente entre Bluetooth serial y clásico (SPP)
#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to and enable it
#endif

BluetoothSerial SerialBT;

void setup() {
  Serial.begin(115200);
  SerialBT.begin("ESP32test"); //Bluetooth device name
  Serial.println("The device started, now you can pair it with bluetooth!");
}

void loop() {
  if (Serial.available()) {
    SerialBT.write(Serial.read());
  }
  if (SerialBT.available()) {
    Serial.write(SerialBT.read());
  }
  delay(20);
}
```
![bluetooth1](https://github.com/Cynthia-696529/Imagenes/blob/d84dff60b65b7e2d64eb665fbd70c20d90f4bdb9/espblue.jpeg)
![bluetooth](https://github.com/Cynthia-696529/Imagenes/blob/d84dff60b65b7e2d64eb665fbd70c20d90f4bdb9/teminal.jpeg)
![bluetooth2](https://github.com/Cynthia-696529/Imagenes/blob/d84dff60b65b7e2d64eb665fbd70c20d90f4bdb9/espblue2.png)
