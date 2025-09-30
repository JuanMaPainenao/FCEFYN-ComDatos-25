# Comunicaciones de Datos - Trabajo Práctico N° 3

**Nombres**  
_Gianluca Ferraris; Ezequiel J. Marredo; Juan M. Painenao; Alejandro R. Stangaferro;_  

**Xi JinPING**

**Facultad de Ciencias Exactas, Físicas y Naturales**  

**Comunicaciones de Datos**

**Profesores**

_Facundo O. Cuneo; Santiago M. Henn;_

**29-09-2025**

---

### Información de los autores
 
- **Información de contacto**: _gianlucaferraris@mi.unc.edu.ar; ezequiel.marredo@mi.unc.edu.ar; juanpainenao@mi.unc.edu.ar; alejandro.stangaferro@mi.unc.edu.ar;_  

---

## Resumen
Este trabajo práctico aborda distintos aspectos fundamentales de las comunicaciones de datos, desde los estándares de redes alámbricas e inalámbricas, hasta tecnologías emergentes y su aplicación en entornos críticos como la conectividad aérea. Se analizan las características de los protocolos IEEE 802.3 (Ethernet) y 802.11 (Wi-Fi), la transmisión por fibra óptica y su relación con medios inalámbricos, y una comparación de estándares relevantes como Bluetooth, ZigBee, LTE, 5G y LoRa. Finalmente, se estudian las tecnologías que permiten el acceso a Internet en vuelos comerciales.

**Palabras clave**: _IEEE, Fibra Óptica, Protocolos de comunicación Inalámbrica_

---

## Introducción
Las comunicaciones digitales comprenden la base de la conexión global de la actualidad. En este contexto, comprender los estándares y tecnologías que gobiernan estas comunicaciones es esencial tanto en el ámbito académico como profesional.

Un aspecto central en la teoría de redes es la clasificación de los medios de transmisión:

- Medios guiados: que confinan la señal dentro de un conductor o núcleo dieléctrico, minimizando la interferencia.

- Medios no guiados: utilizan el espacio libre como canal de propagación, siendo más flexibles pero más vulnerables a fenómenos como el ruido electromagnético, el efecto Doppler y la atenuación.

El IEEE y organismos como 3GPP o ITU han desarrollado estándares que regulan estas tecnologías. Dentro de ellos destacan IEEE 802.3 (Ethernet) para redes cableadas y IEEE 802.11 (Wi-Fi) para redes inalámbricas, que representan los cimientos de la conectividad moderna.

En este trabajo también se estudian las propiedades físicas de la fibra óptica, se presenta una tabla comparativa de protocolos y tecnologías. Finalmente se profundiza en un caso de aplicación actual como lo es la conectividad a internet a bordo de aviones. 

## Resultados
### Consigna 1
**a)** El estándar **IEEE 802.3** es parte de la familia de tecnologías Ethernet (redes por cable) que el IEEE ha estandarizado tanto para investigación como industria.  Su procedencia se remonta a los trabajos de *Xerox PARC* y las labores en conjunto de la consorcia *DIX* (colaboración entre las empresas *Digital*, *Intel* y *Xerox* para crear los estándares de la industria) durante la década del setenta.  Se formalizó como estándar IEEE a principios de los años 80. La versión inicial de IEEE 802.3 fue aprobada en 1983 y publicada aproximadamente en 1985, bajo el nombre IEEE 802.3-1985; incluyendo en principio Ethernet de 10 Mbps sobre cable coaxial (10BASE5). Desde ese momento, el estándar ha progresado a través de varias modificaciones para admitir nuevos medios (fibra óptica, par trenzado), velocidades más altas (de 100 Mbps, 1 Gbps y 10 Gbps a 40/100 Gbps, 200/400 Gbps y demás) así como funciones adicionales, por ejemplo la transmisión de energía a través del cable (PoE o *Power over Ethernet*).  IEEE 802.3 tiene la función de determinar las capas de enlace de datos (MAC) y física (PHY) para las redes con cable, configurando mecanismos para acceder al medio (como el CSMA/CD en versiones anteriores) y formatos de trama estándar. Esto permite que todos los dispositivos, independientemente del fabricante, sean capaces de interactuar dentro de redes Ethernet.
Por su parte, el estándar **IEEE 802.11** se ocupa de redes inalámbricas de área local (WLAN, “Wi-Fi”). IEEE 802.11 nació en la década de 1990 como la especificación para la comunicación inalámbrica en bandas sin licencia (ISM). A lo largo de los años se han agregado múltiples enmiendas (como 802.11a, b, g, n, ac, ax, be, etc.) para mejorar el rendimiento, cobertura, eficiencia en entornos densos, y robustez frente a interferencias. El estándar 802.11 define las capas física y MAC para comunicación inalámbrica, en diferentes bandas (2,4 GHz, 5 GHz, 6 GHz en extensiones recientes), y proporciona mecanismos de acceso múltiple, modulación, codificación, control de errores, gestión de potencia, etc. El campo de aplicación de IEEE 802.11 abarca redes domésticas, empresariales, campus universitarios, puntos de acceso públicos, aplicaciones móviles, IoT, etc.

En conclusión, IEEE 802.3 da soporte al estándar universal de redes cableadas (Ethernet) y ha sido la estándar aceptado de la mayoría de las redes LAN en el mundo, mientras que IEEE 802.11 habilitas redes inalámbricas ubicuas (Wi-Fi), permitiendo movilidad y acceso sin cables, con la gran ventaja de interoperabilidad entre dispositivos gracias a la este estándar.

**b)** Para determinar la versión del protocolo IEEE 802.11 que está usando una conexión inalámbrica una vez que uno se haya conectado a una red (por ejemplo, en nuestro caso UNC-LIBRE), un método práctico en Windows consiste en el uso del comando:
```netsh wlan show interfaces```
Este comando muestra información de las interfaces inalámbricas activas, incluyendo campos como “Tipo de radio”, “Banda”, “Canal”, “Velocidad de recepción/transmisión (Mbps)”, etc. En la captura presentada, la salida muestra:
- **Descripción**: Intel(R) Wi-Fi 6E AX211 160MHz
- **Tipo de radio**: 802.11ac
- **Banda**: 5 GHz
- **Velocidad de recepción / transmisión (Mbps)**: 162 / 180
- **Autenticación**: Abierta
- **Cifrado**: Ninguna

Ese campo **Tipo de radio** indica la versión del estándar *IEEE 802.11* con que fue negociado el enlace entre la NIC (tarjeta inalámbrica) y el punto de acceso (AP). En este caso muestra *802.11ac*, que corresponde a Wi-Fi 5. Dado que la tarjeta es *Wi-Fi 6E AX211*, indica que la NIC tiene capacidad de operar con versiones más recientes, pero el enlace actual se está usando en modo *802.11ac* porque es lo que negocian ambos extremos. Obviamente, para investigar otras redes (cómo FCEFyN) basta con desconectarse de la red actual, conectarse a la nueva red, y ejecutar de nuevo ```netsh wlan show interfaces``` para ver los valores correspondientes del tipo de radio y otros parámetros de nuestro interés.

![Img1](https://hackmd.io/_uploads/Bknu-su2xe.jpg)


**c)** Cuando un punto de acceso inalámbrico está configurado para operar bajo una versión más reciente del estándar 802.11 (por ejemplo *802.11ax* o *802.11be*) pero un dispositivo cliente tiene una NIC que no soporta esa versión (por ejemplo, solo soporta hasta *802.11n* o *802.11ac*), hay dos escenarios posibles:

En el primer escenario, el punto de acceso admite retrocompatibilidad (modo de operación mixto). Muchos *Access Point* modernos permiten funcionar simultáneamente en versiones antiguas y nuevas (modo *mixed*). En tal caso, el AP y el cliente negocian la versión común más alta que ambos soportan, y el cliente antiguo se conecta utilizando esa versión más antigua. Por lo tanto, la conexión funciona, aunque sin aprovechar las mejoras del estándar más reciente.

En el segundo escenario, si el AP está configurado de modo estricto (por ejemplo *802.11ax-only* o *802.11be only*) y no admite versiones anteriores, un cliente que no soporte esa versión no podrá asociarse en absoluto. La falta de compatibilidad impide la conexión.

Además, la presencia de clientes *legacy* en una red puede impactar negativamente en el rendimiento global: debido a la necesidad de compartir el medio inalámbrico, el AP puede tener que usar intervalos más largos, técnicas de protección (por ejemplo, RTS/CTS), y reducir la eficiencia general para acomodar dispositivos lentos, degradando la experiencia de usuarios más modernos.

Por lo tanto, si el dispositivo no soporta la versión del protocolo que la red desea usar y no hay modo mixto, la conexión simplemente no será posible. Sí hay soporte mixto, la conexión se realizará con la versión inferior que ambos puedan soportar.

**d)** La versión del protocolo **IEEE 802.11** (por ejemplo *ac, ax, be*) va de la mano con los esquemas de seguridad que pueden emplearse. Las versiones antiguas de Wi-Fi usaban mecanismos de seguridad poco robustos, como **WEP**, que hoy día son considerados inseguros. En la evolución del estándar Wi-Fi se incorporó el estándar *802.11i*(*WPA/WPA2*) y más recientemente *WPA3* como mecanismo más seguro.

Wi-Fi 5 (*802.11ac*) generalmente utiliza **WPA2** con cifrado AES-CCMP, lo cual proporciona confidencialidad del tráfico de enlace y autenticación mediante clave (PSK) o 802.1X (modo empresarial). Versiones modernas (Wi-Fi 6/802.11ax) mantuvieron la compatibilidad con WPA2 y añadieron soporte para **WPA3**, que introduce mejoras significativas: autenticación basada en SAE (*Simultaneous Authentication of Equals*), protección contra ataques de diccionario offline, y mejoras de privacidad en redes abiertas. En Wi-Fi 7 (*802.11be*) se espera que el mecanismo de seguridad de referencia siga siendo WPA3, en sus versiones más robustas, aprovechando las capacidades del nuevo estándar para minimizar vulnerabilidades. 

En la captura presentada, el SSID ```unc-libre``` opera con ```Autenticación: Abierta``` y ```Cifrado: Ninguno```, lo cual significa que no hay seguridad en la capa de acceso inalámbrico mismo: el tráfico no está cifrado en la capa de enlace, y cualquiera que esté en el mismo canal podría potencialmente capturar tramas. Esta configuración puede estar compensada por un portal cautivo (autenticación vía web), pero no protege el tráfico en sí mismo mientras transita por el aire. Esto contrasta con redes protegidas con WPA2 o WPA3, donde el tráfico se cifra entre cliente y AP y sólo dispositivos autenticados pueden descifrarlo.

La diferencia fundamental entre una red abierta y una red protegida con WPA2/WPA3 es que en esta última se garantiza que sólo los clientes autorizados participen y que el contenido de las comunicaciones no pueda ser leído por escuchas pasivas (*sniffers*). WPA3 añade además mayor resistencia frente a ataques offline (porque la clave no se deriva directamente de la contraseña) y protección de privacidad de dirección MAC, mitigando ciertos ataques de rastreo. En comparación, versiones muy antiguas de Wi-Fi con WEP o **WPA** (TKIP) sufren vulnerabilidades conocidas que permiten romper el cifrado fácilmente.

Por lo tanto, al reconectarse a las redes de la Facultad y aplicar de nuevo ```netsh wlan show interfaces```, se puede leer el campo ```Autenticación / Cifrado``` para deducir qué esquema están usando (WPA2, WPA3, abierto, 802.1X) y compararlo con lo que la versión del protocolo permite o recomienda.

**e)**
| Característica               | Wi-Fi 5 (802.11ac)                           | Wi-Fi 6 (802.11ax)                           | Wi-Fi 7 (802.11be / EHT)                          |
|-----------------------------|---------------------------------------------|---------------------------------------------|--------------------------------------------------|
| Versión IEEE                 | 802.11ac                                     | 802.11ax                                      | 802.11be / EHT                                     |
| Tasa de datos máxima (teórica) | ~ 3,5 Gbps (escenario ideal)                    | ~ 9,6 Gbps (escenario ideal)                    | ~ 46 Gbps (valor ideal citado en literatura) :contentReference[oaicite:0]{index=0} |
| Banda(s)                     | 5 GHz                                         | 2,4 GHz y 5 GHz (y 6 GHz en “Wi-Fi 6E”) :contentReference[oaicite:1]{index=1} | 2,4 GHz, 5 GHz y 6 GHz (operación multi-link posible) :contentReference[oaicite:2]{index=2} |
| Ancho de banda de canal      | Hasta 160 MHz                                  | Hasta 160 MHz (o agregados 80+80) :contentReference[oaicite:3]{index=3} | Hasta 320 MHz (canal ultraancho permitido) :contentReference[oaicite:4]{index=4} |
| Modulación máxima            | 256-QAM                                        | 1024-QAM :contentReference[oaicite:5]{index=5}       | 4096-QAM (4K QAM) :contentReference[oaicite:6]{index=6}        |
| Sistema de seguridad habitual | WPA2 (AES-CCMP)                                | WPA2 / soporte de WPA3                         | WPA3 como referencia en implementaciones modernas     |



### Consigna 2

a) En la figura se ven los siguientes tipos de transmisión:  
- **Fibra Monomodo**: Solo permite un modo de propagación de la luz, un haz viaja en línea recta por el núcleo.  
- **Fibra Multimodo**: Permite que viajen varios rayos de luz rebotando en el interior.  

La fibra monomodo recorre mayores distancias, pero requiere fuentes de luz más precisas y costosas. En cambio, la fibra multimodo es más barata de implementar, pero tiene limitaciones en la distancia de transmisión.  


b) La ley de Snell describe cómo la luz cambia de dirección al pasar de un medio a otro y es descrita por la siguiente fórmula:  

$$n_1 \cdot \sin(\theta_1) = n_2 \cdot \sin(\theta_2)$$  

En fibra óptica se tienen dos medios:  
- Núcleo: con índice de refracción mayor ($n_1$).  
- Revestimiento: con índice de refracción menor ($n_2$).  

De esta ley se deduce el ángulo crítico $\theta_c$ que define cuándo ocurre la reflexión interna total, que produce que la luz quede atrapada dentro del núcleo de la fibra:  

$$\sin(\theta_c)=\frac{n_2}{n_1}\quad \text{con}\quad n_1>n_2$$  

En la fibra multimodo, varios ángulos de incidencia cumplen la reflexión interna total, por lo que se propagan varios modos, aunque los rayos llegan en tiempos distintos (dispersión modal). En cambio, en fibra monomodo, solo el ángulo más cercano al eje cumple la condición, se propaga un único modo, esto elimina la dispersión modal y permite mayores distancias y velocidades.  


c) La fibra óptica se relaciona con las transmisiones inalámbricas en que ambas utilizan ondas electromagnéticas, aunque de diferente frecuencia, para transmitir la información.  

Ambas siguen esquemas de transmisión similares, pero difieren mucho en el modelado del canal ya que la fibra es guiada y tiene baja interferencia, mientras que las conexiones inalámbricas no son guiadas, se envían al aire y se ven muy afectadas por interferencias y obstáculos del mundo real.  




### Consigna 3

| Protocolo   | ¿Está estandarizado? | ¿Cuál(es) estándares? (última versión)                                |
|-------------|----------------------|-----------------------------------------------------------------------|
| Wi-Fi       | Sí                   | IEEE 802.11 (Última versión: 802.11be - Wi-Fi 7)                     |
| Bluetooth   | Sí                   | IEEE 802.15.1 (Última versión: Bluetooth 5.3)                         |
| ZigBee      | Sí                   | IEEE 802.15.4 (Última versión: Zigbee 3.0)                            |
| NFC         | Sí                   | ISO/IEC 14443, ISO/IEC 18092 (Última versión: NFC Forum Technical Specification 2.0) |
| LTE         | Sí                   | 3GPP (Última versión: LTE Advanced Pro, Release 15)                   |
| GSM         | Sí                   | ETSI (Última versión: GSM Release 1997, pero ahora sustituido por 3G/4G) |
| 5G (3GPP)   | Sí                   | 3GPP (Última versión: 5G NR, Release 16/17)                           |
| LoRa        | Sí                   | LoRa Alliance (Última versión: LoRaWAN 1.1.0)                         |
| NB-IoT      | Sí                   | 3GPP (Última versión: Release 14, NB-IoT)                             |
| SigFox      | Sí                   | Sigfox (Última versión: No hay un estándar formal, pero se mantiene bajo la especificación Sigfox) |
| Z-Wave      | Sí                   | Z-Wave Alliance (Última versión: Z-Wave S2, con compatibilidad hacia Z-Wave 700) |

![image](https://hackmd.io/_uploads/Hy7iRND3el.png)

| Característica | UTP | Fibra Óptica | Wi-Fi 802.11be (Wi-Fi 7) | Bluetooth 5.4 | 5G |
|----------------|-----|--------------|--------------------------|---------------|----|
| **Ancho de banda** | Hasta 10 Gbps (Cat 6a/7), 40 Gbps en Cat 8 | >100 Gbps (terabits en DWDM) | Hasta 40 Gbps | ~2 Mbps (BLE) / hasta 10 Mbps (teórico) | Hasta 10 Gbps (pico) |
| **Distancias** | Hasta 100 m (Ethernet) | Hasta 40-100 km sin repetidor | ~30-100 m | ~10-100 m | Varios km en celdas urbanas, más en rurales |
| **Inmunidad a EMI / RFI** | Baja (sensible a interferencias) | Muy alta (no le afecta EMI/RFI) | Media (afectado por interferencias) | Media-baja (afectado por interferencias) | Media (mejora con modulación y bandas licenciadas) |
| **Costos de medios/conectores/dispositivos** | Bajo (cables y conectores baratos) | Alto (fibra y transceptores caros) | Medio (routers/AP gama alta son costosos) | Muy bajo (integrado en casi todos los dispositivos) | Alto (infraestructura y equipos de red costosos) |
| **¿Disponible en Packet Tracer?** | Sí | No | Sí (Wi-Fi genérico, no 802.11be) | No | No |

### Consigna 4

a)	Existen tres principales tecnologías que permiten la conexión a internet a bordo:
1)	ATG (Air To Ground transmisión system): Se hace uso de antenas instaladas en el avión las cuales reciben señales de las torres en tierra, las envían al server en cabina y se distribuye vía un router wifi. Este sistema opera de forma similar a la conexión de los celulares con las torres en tierra.
Este sistema es adecuado para vuelos domésticos y áreas donde existan gran densidad de antenas, ya que, para mayores escalas o vuelos internacionales, donde el avión cruza océanos o áreas despobladas, no se puede brindar cobertura wifi.
Este sistema ofrece velocidades de internet de hasta 10Mbps, suficiente para enviar y recibir mensajes, correos y navegación liviana por internet.
2)	Servicio Satelital Ku-Band: Brinda conectividad a bordo a través de satélites en orbita geoestacionaria. Las antenas del avión reciben la señal de los satélites, la decodifican en el servidor del avión y se distribuye por un router wifi. 
Características:
    -	Opera en banda Ku (12-18 GHz)
    -	Velocidades de hasta 50 Mbps
    -	Cobertura global, como vuelos internacionales
    
Uno de los principales problemas es que el ancho de banda se debe compartir entre múltiples usuarios del vuelo, y debido a que existe una limitada cantidad de satélites, la velocidad de internet tiende a disminuir cuando varios aviones intentan conectarse a un satélite.
3)	Servicio satelital Ka-Band: Similar al servicio Ku-Band pero este servicio es más rápido y confiable, debido a que utiliza frecuencias más altas para ofrecer mayor capacidad. Ofrece velocidades de hasta 70 Mbps a bordo.
Actualmente es el servicio más rápido que disponen las aerolíneas, aunque una de sus limitaciones sean el requerimiento de antenas en el avión más avanzadas y costosas.

Desde el punto de vista de las comunicaciones digitales estos servicios y tecnologías se pueden analizar en:
Capa física.
-	ATG: dependencia de línea de vista con torres.
-	Satélite: dependencia de propagación en altas frecuencias.

Capa de enlace de datos.
-	Uso de multiplexación para compartir el canal entre múltiples usuarios.
-	Problemas de colisiones y necesidad de control de acceso eficiente.

Capa de red y transporte.
-	Latencia: factor crítico que impacta en protocolos como TCP.
-	QoS: priorización de tráfico.

b)	Articulo: A First Look at Starlink In-Flight Performance: An Intercontinental Empirical Study

Autores: Muhammad Asad Ullah, Luca Borgianni, Heikki Kokkinen, Antti Anttonen, Stefano Giordano

Resumen:
El artículo estudia por primera vez de forma sistemática el desempeño de Starlink en vuelos comerciales, un tema poco explorado hasta ahora en la comunidad científica.
Contexto:
-	Starlink es la mayor constelación de satélites en órbita baja (LEO), con más de 8.000 satélites en 2025.
-	Ya se ofrecen servicios en tierra, mar y aire, pero faltaban datos objetivos en aeronaves.

Metodología:
-	Dos vuelos comerciales medidos:
-	Pacífico (Honolulu–Japón, 5.5 h).
-	Báltico (Múnich–Helsinki, 30 min).
-	Se usaron Ping, Tracert y Ookla Speedtest en laptops y smartphones de pasajeros.
-	Comparación con un terminal residencial en Pisa, Italia.

Conclusiones:
El estudio demuestra que Starlink puede proporcionar conectividad aérea robusta y de alta velocidad, suficiente para navegación, mensajería, videollamadas y hasta streaming 4K sin interrupciones.
Sin embargo:
-	El rendimiento varía con altitud, congestión de usuarios y condiciones atmosféricas.
-	La latencia es mayor que en tierra, aunque sigue siendo mucho más baja que en sistemas GEO.
-	Es probable que las aerolíneas apliquen limitaciones por usuario para repartir ancho de banda.


Link: https://arxiv.org/html/2508.09839v1

c)	El Sistema diferencia entre contenidos locales y contenidos externos. De esta manera, el contenido a bordo no utiliza el ancho de banda satelital que es caro y limitado si no que utiliza un servidor local que abastece a todos los usuarios. El ancho de banda queda limitado entonces a navegación, correos y mensajes de texto evitando que se sobrecargue el canal. Si las películas se transmitieran desde Internet en lugar de estar almacenadas localmente, se saturaría rápidamente la conexión y se degradaría la experiencia de los pasajeros.


## Referencias  

- Bluetooth SIG. (2023). Bluetooth Core Specification Version 5.4. Retrieved from https://www.bluetooth.com/specifications/

- IEEE Standards Association. (2021). IEEE Draft Standard for Information Technology – Telecommunications and Information Exchange Between Systems Local and Metropolitan Area Networks – Specific Requirements – Part 11: Wireless LAN Medium Access Control (MAC) and Physical Layer (PHY) Specifications Amendment: Enhanced Throughput for Extremely High Throughput (EHT) – IEEE 802.11be.

- ITU. (2020). IMT-2020 (5G) standards. International Telecommunication Union. Retrieved from https://www.itu.int/en/mediacentre/backgrounders/Pages/imt-2020-5g.aspx

- 3GPP. (2019). Release 15 Description; Summary of Rel-15 Work Items. 3rd Generation Partnership Project (3GPP). Retrieved from https://www.3gpp.org/release-15


- Stallings, W. (2004). *Comunicaciones y redes de computadores* (7ª ed.). Pearson Prentice Hall. [https://drive.google.com/file/d/1xmuElCwHET1hQMLfMAqdAfYax0biOwZl/view?usp=sharing](https://drive.google.com/file/d/1xmuElCwHET1hQMLfMAqdAfYax0biOwZl/view?usp=sharing)   
- Ariat Tech. (2023). *The radio spectrum: Understanding ITU frequency bands from VLF to UHF*. Recuperado de [https://www.ariat-tech.es/blog/the-radio-spectrum-understanding-itu-frequency-bands-from-vlf-to-uhf.html](https://www.ariat-tech.es/blog/the-radio-spectrum-understanding-itu-frequency-bands-from-vlf-to-uhf.html)  
- Wikipedia. (s. f.). *Efecto Doppler*. En **Wikipedia en español**. Recuperado de [https://es.wikipedia.org/wiki/Efecto_Doppler](https://es.wikipedia.org/wiki/Efecto_Doppler)  
- EA1URO. (s. f.). *Doppler y Satélites*. Recuperado de [https://www.ea1uro.com/eb1dgh/Satelites/Doppler.html](https://www.ea1uro.com/eb1dgh/Satelites/Doppler.html)  

- Rosen Aviation. (2022, 18 de abril). What Technologies Allow Airplanes to Carry On-Board Wi-Fi? Recuperado de https://www.rosenaviation.com/blog/what-technologies-allow-airplanes-to-carry-on-board-wi-fi/
