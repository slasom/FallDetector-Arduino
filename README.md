# FALL DETECTOR

```
José Manuel Romero Muelas
Sergio Laso Mangas
Sergio Zabala Mesonero
```
```
Descripción de Sistemas Hardware
2018 / 2019
Universidad de Extremadura
```
## ESCENARIO

Fernando es un señor viudo que tiene 80 años. El año pasado sufrió una caída debido a un mareo
y lo grave no fue la caída en sí, sino que debido al golpe, estuvo tendido en el suelo varias horas
hasta que su hijo único Pedro fue a realizar su visita diaria y se lo encontró en esa situación.
Debido a estar tantas horas en el suelo y en mala posición su recuperación ha sido aún más lenta.

Fernando ya está recuperado pero su hijo Pedro teme que pueda tener un accidente similar y con
consecuencias aún más graves. Es por esto que a Fernando le encantaría tener algún dispositivo
que detectara si su padre volviese a sufrir una caída, fuera avisado inmediatamente o avisar
directamente a los servicios de emergencias.

## RESUMEN

El objetivo del proyecto sería desarrollar un dispositivo que iría integrado en la ropa y que permita
la detección de caídas a través de varios sensores. La funcionalidad sería la siguiente:

```
● Detectar posibles caídas a través de sensores como el acelerómetro y giroscopio.
● Si se produce alguna caída, se envía una alerta a un familiar o servicio de emergencia.
● Si está alerta no fuese real, el usuario puede cancelar dicha alerta ya que dispondrá de
un botón para cancelar dicha falsa alerta y un emisor de sonido para detectar la alerta.
● En la alerta se indicará las coordenadas de localización del usuario por si se produjese
fuera de su hogar de residencia.
```
## PROYECTOS RELACIONADOS:


Proyecto 1: el objetivo de este proyecto es igual al nuestro pero ellos utilizan otro tipo de sensores
(Tilt) que mide el grado de inclinación. La desventaja con respecto al nuestro es que tienen
implementada una aplicación móvil para conectarse con el dispositivo de detección para
posteriormente emitir la alerta vía SMS, en cambio nosotros, directamente incluimos un módulo
3G en el propio dispositivo de detección para realizar dicha tarea.

Proyecto 2: como el proyecto anterior, el objetivo es igual que el nuestro, la tecnología usada es
similar a la nuestra, incluyendo el módulo 3G. En este caso solo utiliza el sensor de acelerómetro
para detectar las caídas, en cambio nuestro proyecto añade otro sensor más (giroscopio) para
tener una precisión más alta.

## 1. DISPOSITIVO(S) INTELIGENTE(S):

**Tecnologías analizadas, elegidas, por qué y precio:**

**Lista de dispositivos utilizados:**

```
● NodeMCU: elegimos esta placa ya que necesitábamos reducir el espacio lo máximo
posible ya que va a ser un dispositivo que vamos a llevar encima. Aparte de que su
programación es igual que programar una placa de Arduino ya que “imita” a un Arduino
Mini Pro, y el grado de complejidad algorítmica no es alto, es el dispositivo perfecto para
controlar todo el sistema. Su precio ronda entre los 2€ y 6€.
```
```
● Conversor FTDI FT232R: este dispositivo ha sido necesario para programar el NodeMCU
ya que no consta de puerto USB. Su precio ronda entre los 3€ y 11€.
```
```
● Módulo Acelerómetro y Giroscopio GY-521: Este módulo es el más importante de este
sistema ya que va a ser el detectar si se produce o no una caída. Combina en un único
chip un giroscopio y un acelerómetro de tres ejes cada uno para detectar movimiento,
orientación y posición espacial con respecto al plano. Su precio ronda entre los 3€ y 7€.
```

```
● Módulo Adafruit Fona Sim800L: este es un módulo GSM/GPRS. Este módulo de
telefonía móvil te permite añadir voz, SMS y datos (TCP/IP, HTTP, etc...) a un proyecto,
todo ello concentrado en un tamaño compacto. En este proyecto ha sido utilizado ya que
su tamaño es compacto y nos cumple la función de alertar una caída a los servicios de
emergencias y familiares del usuario a través de SMS ya que si se produce en el exterior
no necesita ninguna conexión wifi, solo depender de la cobertura. Su precio ronda entre
los 4€ y 40€.
```
```
● Buzzer: este es un dispositivo para emitir sonidos, en nuestro caso para alertar cuando
se produce una caída, ya que si esta no es cierta (pej. algún tropiezo), el usuario
pueda cancelar dicha alerta antes de avisar a los servicios de emergencias. Este tipo
de dispositivos apenas supera el euro.
```
```
● Botón pulsador: este actuador lo hemos utilizado en nuestro el proyecto para cancelar
una alerta, y lo más sencillo para cancelar una acción y que sea lo más sensato es un
simple botón. Este tipo de actuador no supera el euro.
```
## 2. ESQUEMA DE CONEXIONES DEL PROYECTO:


Las partes que conforman este proyecto desarrollado son las siguientes:

- **Buzzer** : emite un sonido al producirse una caída
- **Botón** : ofrece la posibilidad de abortar falsos positivos de caídas a través de éste
- **Módulo Sim** : permite enviar comunicaciones, se debe de insertar una tarjeta SIM y así
    poder alertar a emergencias y a las personas de contacto una vez se ha producido una
    caída
- **NodeMCU** : es una plataforma de IoT de código abierto para realizar las conexiones
    necesarias de los elementos que conforman este sistema
- **Módulo para programar NodeMCU** : módulo para llevar a cabo el desarrollo de este
    proyecto
- **Acelerómetro / Giroscopio** : permite medir las aceleraciones y la orientación del
    dispositivo con el fin de obtener diferentes valores que permiten interpretar las caídas

## 3. INTERACCIÓN(ES) INTELIGENTE(S):

**Tecnologías analizadas:**

```
● Calcular el umbral de caída para emitir alerta
● Enviar mensaje de emergencia a persona de contacto
```

**Tecnologías elegidas, por qué y precio:**

**Calcular el umbral de caída para emitir** : para calcular el umbral de caída ha sido necesario
aplicar la fórmula del _valor absoluto_ a cada eje y se han sumado dichos ejes, por una parte los del
giroscopio y por otra los del acelerómetro, con esto se han realizado diferentes pruebas para
ajustar los valores con el fin de adaptar el umbral del dispositivo a las posibles caídas reduciendo
así los falsos positivos.

**Enviar mensaje de emergencia a persona de contacto** : construido el proyecto se implementó
a través del _Módulo Adafruit Fona Sim800L_ la posibilidad de enviar una alerta vía SMS a los
familiares y/o servicios de emergencias con las coordenadas donde se ha producido la caída.

## PROBLEMAS PREVISIBLES DURANTE LAS FASES DE DESARROLLO O

## IMPLANTACIÓN:

```
● El módulo SIM no llega a realizar su función correctamente ya que algunas de las tarjetas
SIM probadas no permite realizar todas las funciones.
● Problemas para interpretar los valores del acelerómetro y giroscopio. En un inicio se
mostraban diferentes valores que procedían del giroscopio y acelerómetro produciendo
equivocaciones al interpretar los valores ofrecidos por este elemento. Se aplicaron ciertas
funciones que solucionaron este problema.
```
**Video de Presentación**

https://www.youtube.com/watch?v=XQmJIhHOFyo&t=4s


