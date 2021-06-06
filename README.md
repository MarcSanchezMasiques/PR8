# PR8: Procedimiento
Empezamos el programa definiendo RXD2 y TXD2
```
#include <Arduino.h>
#define RXD2 16
#define TXD2 17
``` 

Seguimos con el void setup(), donde empezamos estableciendo 2 entradas de comunicacion en serie, las cuales van a tener la Serial1 115200 bauds y la segunda Serial2 9600 bauds además de pasarle los siguientes parametros:
- Protocolo SERIAL_8N1
- Pin RX
- Pin TX

Por ultimo, mostramos por pantalla el pin asignado a cada uno de los serials RX y TX
```
void setup()
{
Serial.begin(115200);
Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2);
Serial.println("Serial Txd is on pin: "+String(TX));
Serial.println("Serial Rxd is on pin: "+String(RX));
}
```
Finalmente tenemos el void loop() donde podemos encontrar un bucle, el cual, mientras el Serial2 este disponible para leer, enviara los datos al Serial1 y seguidamente los imprimira por pantalla.
```
void loop() { 
  while (Serial2.available()) {
    Serial.print(char(Serial2.read()));
  }
}
```
### Resultado de la simulación

Al compilar este programa podemos ver como los datos son leidos por el serial2 y, seguidamente, son recibidos por el serial1, de esta manera, se aclara la conexión entre ellos