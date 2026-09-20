Prender y apagar leds mediante programacion y un boton 
---
En la clase de hoy empezamos armando un circuito en el que utilizamos un ESP32. Después hicimos una programación para poder controlar un LED. El objetivo fue hacer que el LED prendiera y apagara cada 1000 milisegundos, es decir, cada segundo. Con esto pudimos ver de una forma más práctica cómo funciona la programación y cómo podemos controlar los componentes del circuito.
```cpp
void setup() {
  pinMode(32, OUTPUT);
}

void loop() {
  digitalWrite(32, HIGH);
  delay(1000);

  digitalWrite(32, LOW);
  delay(1000);
}
```

![Imagen Carlos](../recursos/imgs/Image%20(2).jpg)

---
Después de eso, hicimos otra programación utilizando el ESP32 y armamos un nuevo circuito en el que agregamos un botón. Hicimos que cada vez que apretáramos el botón, el LED prendiera y se apagara. También hicimos que en Arduino apareciera “Presionado” cada vez que presionábamos el botón, y que apareciera "No" cuando no lo estábamos presionando.

```cpp
void setup() {
  Serial.begin(9600);
  pinMode(32, INPUT);
}

void loop() {
  if(digitalRead(32)==1){
    Serial.println("PRESIONADO");
  }
  else{
    Serial.println("NO");
  }
  delay(100);
}
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/dNi--oStPHc?si=AFxfUhwtikr1Ju_w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---
Luego, con el mismo circuito, pero usando otra programación, hicimos que por medio de Bluetooth pudiéramos controlar el LED desde nuestro celular. Cada vez que escribiéramos “ON” en el celular, el LED prendía, y cuando escribíamos “OFF”, el LED se apagaba.
```cpp
#include "BluetoothSerial.h"
BluetoothSerial Mi_tel;

void setup() {
  Mi_tel.begin("m06");
  Mi_tel.setTimeout(20);
  Serial.begin(9600);
  pinMode(32,OUTPUT);
}

void loop() {
  if(Mi_tel.available()){
    String mensaje = Mi_tel.readStringUntil('\n');
    mensaje.trim();

    if(mensaje == "ON"){
      digitalWrite(32,1);
    }

    if(mensaje == "OFF"){
      digitalWrite(32,0);
    }
  }
}
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/XJUPQ_LAeUg?si=Ys2_jwBiD2xtjKr3" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---
Con esta actividad aprendí un poco más sobre cómo funciona el ESP32 y cómo se puede utilizar para controlar diferentes cosas por medio de una programación. También aprendí cómo conectar un botón y un LED, y cómo usar Bluetooth para controlar el LED desde el celular. Me ayudó a entender mejor cómo la programación y los circuitos trabajan juntos.
