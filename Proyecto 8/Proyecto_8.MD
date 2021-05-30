# PRÁCTICA 8: Buses de comunicación IV (uart):
## Codigo fuente operativo:

```
#include <Arduino.h>

void setup() {
  Serial.begin(115200);
  Serial2.begin(115200);
}

void loop() {
  if(Serial.available()){
    Serial2.write(Serial.read());
    delay(2);
    if(Serial2.available()){
      Serial.write(Serial2.read());
    } 
  }
}
```

## Descricion del mismo:
Declaramos la libreria de arduino:
```
#include <Arduino.h>
```
Iniciamos las dos comunicaciones seriales en el setup:
```
void setup() {
  Serial.begin(115200);
  Serial2.begin(115200);
}
```

En el loop, con el "serial.avaliable()" leemos por el puerto serie los caracteres que recojemos al monitorear el programa. Seguidamente con "Serial2.write(Serial.read())" escribiomos nuestro mensaje y seguidamente este sera leido por el primer serial. Ponemos también un delay para dejar un poco de tiempo al escribir. En la última condición consiste en que si se lee alguna cosa por el puerto serie se escribira también el mensaje y se leera por el serial2.
```
void loop() {
  if(Serial.available()){
    Serial2.write(Serial.read());
    delay(2);
    if(Serial2.available()){
      Serial.write(Serial2.read());
    } 
  }
}
```

## Salidas y entradas de consola:
Por la consola se muestra lo que se introduce por teclados despues de compilar, subir a la placa y monitorizarlo.

![alt text](Captura.JPG)