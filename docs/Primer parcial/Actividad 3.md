
---
En la clase de hoy vimos cómo funciona un motor L298. Primero, el profesor nos explicó su funcionamiento utilizando un motor físico y una fuente de poder. Observamos que, al conectar el motor de una manera, este comenzaba a girar en un sentido y, al invertir las conexiones, giraba en el sentido contrario.
Después de esto, realizamos un circuito en Tinkercad utilizando una placa Arduino. En este circuito programamos dos motores para que giraran en la misma dirección. Con esta práctica pudimos observar de una manera más clara cómo se puede controlar el movimiento de los motores mediante Arduino y cómo la programación influye en su funcionamiento.
```cpp
void setup()
{
  //MOTOR1
  pinMode(6, OUTPUT); //OUT1
  pinMode(7, OUTPUT); //OUT2
  pinMode(12, OUTPUT); //OUT1
  pinMode(13, OUTPUT); //OUT2
  pinMode(5, OUTPUT); //ENABLE
  digitalWrite(5, HIGH);
  pinMode(4, OUTPUT); //ENABLE
  digitalWrite(4, HIGH);
}

void loop()
{
  digitalWrite(6, HIGH);
  digitalWrite(7, LOW);
  delay(1000);

  digitalWrite(7, HIGH);
  digitalWrite(6, LOW);
  delay(1000);

  digitalWrite(12, HIGH);
  digitalWrite(13, LOW);
  delay(1000);

  digitalWrite(13, HIGH);
  digitalWrite(12, LOW);
  delay(1000);
}
```
<iframe width="560" height="315" src="https://www.youtube.com/embed/QCtgiOJMJZ4?si=utm7qT6s119l6PW3" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---
Luego de eso, hicimos que los dos motores giraran en la misma dirección y después cambiaran a la dirección contraria utilizando un código diferente.
```cpp
void adelante(){
  digitalWrite (6, HIGH);
  digitalWrite (7, LOW);
  digitalWrite (13, HIGH);
  digitalWrite (12, LOW);

}

void atras(){
  digitalWrite (7, HIGH);
  digitalWrite (6, LOW);
  digitalWrite (12, HIGH);
  digitalWrite (13, LOW);

}

void setup()
{
  //MOTOR1
  pinMode (6, OUTPUT);//OUT1
  pinMode (7, OUTPUT);//OUT2

  pinMode (5, OUTPUT);//ENABLE
  digitalWrite (5, HIGH);

  //Motor2
  pinMode (12, OUTPUT);//OUT1
  pinMode (13, OUTPUT);//OUT2
  pinMode (4, OUTPUT);//ENABLE
  digitalWrite (4, HIGH);

}

void loop()
{
  adelante();
  delay (1000);

  atras();
  delay (1000);
}
```
<iframe width="560" height="315" src="https://www.youtube.com/embed/QCtgiOJMJZ4?si=Dc3nmNkFKcSWGVmy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
---
Después hicimos un circuito con los mismos motores, en el que primero giraban hacia delante y después hacia atrás. Posteriormente, los motores hacían un giro hacia el lado izquierdo.

```cpp
#include <Servo.h>

Servo arduino;

void adelante(){
  digitalWrite (6, HIGH);
  digitalWrite (7, LOW);
  digitalWrite (13, HIGH);
  digitalWrite (12, LOW);

}

void atras(){
  digitalWrite (7, HIGH);
  digitalWrite (6, LOW);
  digitalWrite (12, HIGH);
  digitalWrite (13, LOW);

}

void izq(){
  digitalWrite (6, HIGH);
  digitalWrite (7, LOW);
  digitalWrite (13, LOW);
  digitalWrite (12, HIGH);
}

void setup()
{
  //SERVO
  arduino.attach(9);

  //MOTOR1
  pinMode (6, OUTPUT);//OUT1
  pinMode (7, OUTPUT);//OUT2

  pinMode (5, OUTPUT);//ENABLE
  digitalWrite(5, HIGH);

  //Motor2
  pinMode (12, OUTPUT);//OUT1
  pinMode (13, OUTPUT);//OUT2
  pinMode (4, OUTPUT);//ENABLE
  digitalWrite(4, HIGH);

}

void loop()
{
  arduino.write(0);

  adelante();
  delay(1000);

  atras();
  delay(1000);

  arduino.write(90);

  izq();

  arduino.write(180);
  delay(1000);
}
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/uqWpfjc-PlE?si=iVkS6sFqC0TZ2eQ1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---
En esta práctica aprendimos cómo funciona el controlador L298 y cómo utilizarlo para controlar dos motores con Arduino. Pudimos hacer que los motores giraran hacia adelante, hacia atrás y hacia un lado mediante diferentes instrucciones. También comprendimos mejor cómo la programación se relaciona con el movimiento de los motores y cómo podemos controlar su dirección dependiendo de las conexiones y el código utilizado.
