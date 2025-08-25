# Comunicaciones de Datos - Trabajo Práctico N° 1

**Nombres**  
_Gianluca Ferraris; Ezequiel J. Marredo; Juan M. Painenao; Alejandro R. Stangaferro;_  
**Xi JinPING**

**Facultad de Ciencias Exactas, Físicas y Naturales**  
**Comunicaciones de Datos**
**Profesores**
_Facundo O. Cuneo; Santiago M. Henn;_
**25-08-2025**

---

### Información de los autores
 
- **Información de contacto**: _gianlucaferraris@mi.unc.edu.ar; ezequiel.marredo@mi.unc.edu.ar; juanpainenao@mi.unc.edu.ar; alejandro.stangaferro@mi.unc.edu.ar;_  

---

## Resumen

Este trabajo consiste en comprender conceptos y teoría de las comunicaciones de datos. Se abordan temas como frecuencia y longitud de onda electromagnética, atenuación, ley de la inversa del cuadrado. También se tratan diferentes tipos de modulación, BER y se utiliza el software CISCO Packet Tracer para simular escenarios de red, como una conexión PC - Router - PC y poder realizar diferentes pruebas.

**Palabras clave**: _Comunicaciones de datos, Espectro Electromagnético, CISCO Packet Tracer, modulación_

---

## Introducción
Para comprender como se transmite la información por los distintos medios físicos es necesario y fundamental estudiar las comunicaciones de datos. Desde las conexiones inalámbricas dentro del hogar hasta grandes enlaces internacionales, la comprensión de los principios físicos y técnicos hoy en día son fundamentales para futuros ingenieros.


---
## Marco Teórico
Las ondas electromagnéticas son oscilaciones en el campo eléctrico y magnético que se desplazan a la velocidad de la luz. Estas ondas viajan a través de medios físicos, y son responsables de la transmisión de diversas formas de energía incluyendo luz u ondas de radio. Estas se caracterizan por tener propiedades cómo la frecuencia, longitud de onda y velocidad, las cuales modificamos para poder transmitir información. Las frecuencias utilizadas en las telecomunicaciones van desde 3 KHz (ondas de radio) hasta 300 GHz (microondas). Cada clase de frecuencia se usa para ciertas aplicaciones como radiodifusión, telefonía móvil y comunicaciones digitales.
Se pueden diferenciar los sistemas de comunicación en dos grupos principales.  Los sistemas analógicos utilizan señales continuas que pueden variar de forma gradual, mientras que los sistemas digitales emplean señales discretas que solo pueden tomar valores específicos.
Las señales de tiempo continuo definidas en un rango continuo de tiempo representado como una función de una variable continua, normalmente denominada x(t), pueden tomar cualquier valor dentro del dominio del tiempo continuo (voltaje, presión)
Las señales de tiempo discreto definidas solo en instantes de tiempo discretos representados como una secuencia de valores, normalmente denominados instantes de tiempo x[n], suelen estar espaciadas uniformemente, con un período de muestreo Ts (audio digital, fotogramas de vídeo).
Las diferencias fundamentales son:
- Dominio: señales de tiempo continuo definidas sobre un dominio continuo, mientras que señales de tiempo discreto definidas sobre un dominio discreto
- Representación: señales de tiempo continuo representadas como funciones, mientras que señales de tiempo discreto representadas como secuencias
- Valores: las señales de tiempo continuo pueden tomar cualquier valor dentro del rango continuo, mientras que las señales de tiempo discreto solo pueden tomar valores en instantes de tiempo discretos



## Resultados
### Consigna 1
b) 
Longitud de onda: 
$$
\lambda = 60 \, \text{mm} = 0.06 \, \text{m}
$$
Frecuencia de la onda:
$$
f = \frac{c}{\lambda} = \frac{3 \times 10^8}{0.06} = 5 \times 10^9 \, \text{Hz} = 5 \, \text{GHz}
$$

c) La onda electromagnética de 5GHz se encuentra en la región de microondas del espectro electromagnético y pertenece a la banda, según la clasificación de la ITU, SHF (Super High Frequency) que va desde los 3Ghz hasta los 30GHz.

d) Los dispositivos de datos que operan en la banda de 5GHz (SHF) son principalmente los dispositivos wifi modernos como IEEE 802.11a/n/ac/ax, Wi-Fi 5 y Wi-Fi 6. Un ejemplo en específico sería un router de casa que transmite a la vez en 2.4GHz y 5GHz. El canal de 5GHz transmite a mayor velocidad los datos, pero con menor alcance, como se explicará a continuación.

e) El fenómeno que se representa con la línea de trazos roja es el fenómeno de atenuación de la onda. El principal concepto físico detrás de este fenómeno es la ley del inverso del cuadrado:
$$
I = \frac{1}{d^2}
$$

![ImgEj1](https://hackmd.io/_uploads/H1uhcyqKge.png) 

Cuando una onda se propaga en el espacio, su energía se distribuye sobre una superficie esférica que crece con la distancia. La intensidad de dicha onda disminuye con el cuadrado de la distancia.
Además de la ley del inverso del cuadrado, también están los fenómenos de absorción del medio, dispersión y difracción y perdidas por materiales.

f) Si, este fenómeno si afecta al router wifi descrito como ejemplo anteriormente. En la práctica se observa como al alejarse del router y cambiar de habitación por ejemplo, llega menos señal, la conexión se vuelve más lenta o se corta.

g) Siempre existe atenuación. Las ondas de telefonía celular sufren este fenómeno, se puede notar como en un edificio o sótano la señal del celular baja.
En la transmisión por cable coaxial, la atenuación ocurre en menor medida. La atenuación existente se puede solucionar con repetidores o amplificadores.
En la transmisión por fibra óptica la atenuación es muy baja comparada con el resto de los medios de transmisión. Pero aun, para distancias muy largas, por ejemplo, para enlaces submarinos, se utilizan amplificadores ópticos.

### Consigna 2
a) Dado el esquema presentado, es posible determinar que es un sistema de transmisión de datos serie, ya que los datos se transmiten uno detrás de otro. Luego, observando la transmisión de los bits del reloj, se establece que la transmisión es de tipo síncrona. Finalmente, dada la direccionalidad del flujo de datos, la transmisión es también modo simplex.

b) No, ya que el esquema presenta unidireccionalidad de datos, pero si se quiere elegir un método de transmisión más rápido y bidireccional, el modo de transmisión adecuado es la transmisión síncrona Full-Duplex.

c) La cuarta letra del grupo corresponde a la letra “i”. El número decimal ASCII que representa es 105, convertido a binario 0110 1001. El diagrama de señal queda de la siguiente manera:

![ImgEj2](https://hackmd.io/_uploads/By0niAYKxg.png)


d) Para determinar el nivel digital de la señal en un instante sería ideal medirla en las marcas de tiempo pares (incluida la marca temporal $T_0$, $T_2$, $T_4$, sucesivamente). 

### Consigna 3
Al momento de transmitir una señal no es conveniente que esta sea escalonada, debido a que los cambios abruptos en los escalones requieren infinitas componentes de frecuencia y esto genera un ancho de banda infinito, por lo que se ocupa todo el espectro electromagnético e imposibilita la transmisión eficiente junto con otras señales de información.
Para solucionar esto se utilizan técnicas de modulación digitales, donde la señal ya no es escalonada.

a) La técnica utilizada en la señal mostrada es BPSK(Binary-Phase-Shift-Keying), donde se alterna entre dos fases de una tono analógico dependiendo de si se transmite un uno o un cero.

b) ![ImgEj2.b](https://hackmd.io/_uploads/HJ11BQ9Fxx.jpg)


c) Existen más técnicas de modulación digitales como ASK,FSK para transmisiones binarias. Además existen QPSK,QAM,FSCM que permiten transmitir más de 1 único bit por división.

d) El BER (Bit Error rate) es una relación que representa los bits errados, que se recibieron erróneos por ruido gaussiano blanco por ejemplo, comparado con los bits totales transmitidos. Nos representan la confiabilidad de la transmisión y se puede expresar como sigue.

$$BER=\frac{\text{Bits errados}}{\text{Bits totales transmitidos}}$$

El BER es siempre cero para transmisiones ideales, pero con la adición de las implicancias del canal de transmisión comienza a tener relevancia. En ese aspecto las modulaciones más robustas ante el ruido, por ejemplo, son las modulaciones por amplitud y fase ya que la adición del ruido en amplitud no altera su frecuencia o fase fundamental. Aunque depende de la modelación del canal para saber cuál utilizar para transmitir.

### Consigna 4

![ImgEj4.1](https://hackmd.io/_uploads/r1nfrQcYgx.png)


c) El router opera en una frecuencia de 2.412 GHz. Dicha frecuencia corresponde a las ondas de radio dentro de la región de microondas en el espectro electromagnético. Esta frecuencia opera dentro de la banda ISM (Industrial, Scientific and Medical), la cual es una banda de frecuencias reservadas internacionalmente para el uso de energía de radiofrecuencia para fines industriales, científicos y médicos distintos de las telecomunicaciones.

g) Desde la computadora de escritorio, se realizó ping con el router (IP 192.168.0.1) y ping con la notebook (IP 192.168.0.101), los resultados se documentan a continuación. Se puede observar la conexión entre los dispositivos.

~~~
Cisco Packet Tracer PC Command Line 1.0
C:\>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time<1ms TTL=255
Reply from 192.168.0.1: bytes=32 time<1ms TTL=255
Reply from 192.168.0.1: bytes=32 time<1ms TTL=255
Reply from 192.168.0.1: bytes=32 time=9ms TTL=255

Ping statistics for 192.168.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 9ms, Average = 2ms

C:\>ping 192.168.0.101

Pinging 192.168.0.101 with 32 bytes of data:

Reply from 192.168.0.101: bytes=32 time=49ms TTL=128
Reply from 192.168.0.101: bytes=32 time=8ms TTL=128
Reply from 192.168.0.101: bytes=32 time=84ms TTL=128
Reply from 192.168.0.101: bytes=32 time=19ms TTL=128

Ping statistics for 192.168.0.101:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 8ms, Maximum = 84ms, Average = 40ms
~~~

h)
Se observa a continuación, como la computadora colocada dentro del rango de nuestra red wifi, está conectada con el router y también con los demás dispositivos conectados a la red.

~~~
Cisco Packet Tracer PC Command Line 1.0
C:\>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time=39ms TTL=255
Reply from 192.168.0.1: bytes=32 time=22ms TTL=255
Reply from 192.168.0.1: bytes=32 time=23ms TTL=255
Reply from 192.168.0.1: bytes=32 time=16ms TTL=255

Ping statistics for 192.168.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 16ms, Maximum = 39ms, Average = 25ms

C:\>ping 192.168.0.100

Pinging 192.168.0.100 with 32 bytes of data:

Reply from 192.168.0.100: bytes=32 time=19ms TTL=128
Reply from 192.168.0.100: bytes=32 time=21ms TTL=128
Reply from 192.168.0.100: bytes=32 time=24ms TTL=128
Reply from 192.168.0.100: bytes=32 time=17ms TTL=128

Ping statistics for 192.168.0.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 24ms, Average = 20ms
~~~

Sin embargo, la computadora colocada fuera del rango wifi de nuestra red, no es capaz de detectar la red inalámbrica por lo tanto no fue posible conectarnos a la red.

![ImgEj4](https://hackmd.io/_uploads/r1df20KKlx.png)


---

## Conclusión
En conclusión, este primer trabajo practico de la materia Comunicaciones de datos fue de utilidad para recordar conocimientos de las teorías de las comunicaciones, así también como aprender nuevos conceptos relacionados a la transmisión y atenuación de señales. Así también como se integró la teoría con la práctica al utilizar el software CISCO Packet Tracer, donde se practicó el diseño y uso de sistemas básicos de transmisión de datos. 


## Referencias

> * [Stallings, W. (2004). Comunicaciones y redes de computadores (7ª ed.). Pearson Prentice Hall.](https://drive.google.com/file/d/1xmuElCwHET1hQMLfMAqdAfYax0biOwZl/view?usp=sharing)
> * [Wikipedia. (s. f.). *Ley de la inversa del cuadrado*. En **Wikipedia en español**. Recuperado el 20 de agosto de 2025](https://es.wikipedia.org/wiki/Ley_de_la_inversa_del_cuadrado)
