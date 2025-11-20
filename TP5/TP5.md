# Comunicaciones de Datos - Trabajo Práctico N° 5

**Nombres**  
_Gianluca Ferraris; Ezequiel J. Marredo; Juan M. Painenao; Alejandro R. Stangaferro;_  
**Xi JinPING**

**Facultad de Ciencias Exactas, Físicas y Naturales**  
**Comunicaciones de Datos**
**Profesores**
_Facundo O. Cuneo; Santiago M. Henn;_
**20-11-2025**

---

### Información de los autores
 
- **Información de contacto**: _gianlucaferraris@mi.unc.edu.ar; ezequiel.marredo@mi.unc.edu.ar; juanpainenao@mi.unc.edu.ar; alejandro.stangaferro@mi.unc.edu.ar;_  

---
## Resultados

### Consigna 1

MQTT (Message Queuing Telemtry Transport) es un protocolo diseñado para comunicaciones en redes con bajo ancho de banda, alta latencia, dispositivos con recursos limitados o conexiones inestables, pensado para aplicaciones IoT.
Las características principales de MQTT son:
- Modelo publisher/suscriber a través de un broker central
- Usa TCP como transporte, lo cual asegura la fiabilidad
- Tiene tres niveles de QoS que se detallan en la consigna 6
- Tiene un formato de mensaje muy liviano
- Permite retención de mensajes, mensajes persistentes y sesiones durables
- Soporta seguridad mediante TLS, autenticación y listas de control

Ventajas de MQTT:
- Es liviano y eficiente
- Tiene bajo consumo energético
- Desacoplamiento total, no se necesita conocer la OP entre emisores y receptores
- Escalabilidad
- QoS configurable en base a la aplicación, explicado en el punto 6.
- Funciona frente a enlaces inestables: mantiene sesiones, reintentos y reconexiones.

Desventajas de MQTT:
- Dependencia del broker: si cae toda la comunicación se cancela
- No cifra datos nativamente
- El tráfico debe pasar siempre por el broker
- Menos adecuado para aplicaciones de tiempo real estricto

El protocolo MQTT se utiliza principalmente en IoT y sistemas distribuidos, como:
- Domótica
- Telemetría industrial
- Agricultura inteligente
- Monitoreo remoto
- Vehículos conectados (GPS)
- Comunicaciones M2M (Machine-to-Machine)

---
### Consigna 2

Detalles de nuestro Cluster:

![image](https://hackmd.io/_uploads/rJEX1xpxWg.png)


Detalles de la conexión:

![image](https://hackmd.io/_uploads/HJimyxTlZl.png)

Perfil creado para el trabajo:

![image](https://hackmd.io/_uploads/rJAVygpl-x.png)

---
### Consigna 3

Conexión con Web Client:

![image](https://hackmd.io/_uploads/BkXSklTxbx.png)

Mensaje enviado:

![image](https://hackmd.io/_uploads/Sy8rJlTlWl.png)

---
### Consigna 4
A)
Para la simulación se utilizó Python, se crearon 3 archivos:
- config_mqtt.py: Con este archivo se evita repetir la configuración en cada script

Parte del código de `config_mqtt.py`:
```
HOST = "67635b7fd3b648408b9df44d8faa9cbb.s1.eu.hivemq.cloud"
PORT = 8883  # TLS

USERNAME = "JinPing"     
PASSWORD = "AguanteTCP4"   
```
- device_b.py: Simula un dispositivo que recibe los mensajes que publica A:

```
# device_b.py
import time
from config_mqtt import create_client, HOST, PORT

TOPIC = "lan/deviceA/status"


def on_connect(client, userdata, flags, reason_code, properties=None):
    print("Conectado con código:", reason_code)
    client.subscribe(TOPIC)
    print("Suscripto a", TOPIC)


def on_message(client, userdata, msg):
    print(f"[{msg.topic}] {msg.payload.decode('utf-8')}")


def main():
    client = create_client("DeviceB")
    client.on_connect = on_connect
    client.on_message = on_message

    client.connect(HOST, PORT, keepalive=60)
    client.loop_start()

    try:
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        print("Saliendo…")
    finally:
        client.loop_stop()
        client.disconnect()


if __name__ == "__main__":
    main()

```
- device_a.py: Simula un dispositivo que envía datos a la red. Publica cada 2 segundos.

```
# device_a.py
import time
from config_mqtt import create_client, HOST, PORT

TOPIC = "lan/deviceA/status"


def main():
    client = create_client("DeviceA")
    client.connect(HOST, PORT, keepalive=60)
    client.loop_start()

    try:
        i = 0
        while True:
            payload = f"Mensaje #{i} desde DeviceA"
            print("Publicando:", payload)
            client.publish(TOPIC, payload=payload, qos=1)
            i += 1
            time.sleep(2)   # cada 2 segundos
    except KeyboardInterrupt:
        print("Saliendo…")
    finally:
        client.loop_stop()
        client.disconnect()


if __name__ == "__main__":
    main()

```
Resultados, comunicación satisfactoria:
![image](https://hackmd.io/_uploads/SyFeve6lbl.png)

4)B)
Para esta parte se realizaron 2 clientes suscriptores y un nodo central encargado de enviar mensajes a todos ellos a través de un tópico general.
Se utilizaron 2 scripts además del `config_mqtt.py`. 
- `broadcast_sub.py`: Son los dispositivos de red que se suscriben al tópico general: `lan/broadcast/#`
- `broadcast_central.py`: simula un nodo central que envía los mensajes globales.

Imagen de 3 terminales con la simulación funcionando, a la izquierda el suscriptor 1, en el centro el nodo publicador y a la derecha el suscriptor 2:

![image](https://hackmd.io/_uploads/ryjxqxpe-x.png)

---
### Consigna 5

FALTA CONSIGNA 5

---
### Consigna 6
A) En esta actividad se trabaja principalmente con TCP. El protocolo que se usa en el modelo publish/subscribe, el MQTT, funciona por defecto sobre TCP. EL protocolo MQTT funciona sobre TCP ya que se diseñó para una comunicación confiable, orientada a conexión y con control de errores.

B) 
Integridad: 
- Se garantiza en parte gracias a las características de TCP: numeración de secuencias, retransmisión, checksum y control de flujo.
- MQTT agrega control de entrega mediante los niveles de QoS.

Confidencialidad:
- MQTT no cifra los mensajes, por ende, la confidencialidad depende de agregar TLS/SSL entre cliente-broker-cliente.
- SI no se usa TLS, cualquier dispositivo dentro de la LAN puede saber que se está enviando.

Disponibilidad:
- En este caso depende del broker central, en nuestro caso podría ser HiveMQ Cloud, por lo que debe estar operativo para permitir la comunicación.
- Si el broker se cae toda la arquitectura deja de funcionar

C)
Los niveles de QoS determinan la garantía de la entrega del mensaje entre cliente y servidor. MQTT define tres niveles de calidad de servicio, cada uno con un impacto claro:
- QoS 0 (At most once): 
	- No tiene garantías de entrega
	- Se envía el mensaje una sola vez
	- Posee alta velocidad, pero baja fiabilidad
- QoS 1 (At least once):
	- El broker, en nuestro caso HiveMq, confirma la recepción con un PUBACK, seria una confirmación de que lo recibió.  
	- Se transmiten más de una copia del mensaje
- QoS 2 (Exactly once):
	- Protocolo de 4 pasos (PUBREC, PUBREL, PUCBOMP)
	- Se asegura de que el mensaje se entregue una sola vez y sin duplicados
	- Mayor latencia y sobrecarga

Se selecciona entre los distintos niveles de QoS según la aplicación:
- Sensores de alta velocidad: QoS 0
- Control general y telemetría confiable: QoS 1
- Aplicaciones criticas: QoS 2

D) Las principales ventajas que ofrece el modelo pub/sub frente al cliente/servidor son:
- Desacoplamiento completo: No es necesario que los clientes se conozcan entre si
- Asincronía total: El publicador no necesita esperar al suscriptor
- Escalabilidad sencilla: Un solo mensaje enviado puede llegar a miles de suscriptores
- Uso eficiente de la red
- Gestión centralizada: El broker se encarga del control de sesiones, autenticación, retención de mensajes y distribución.

E)
Las limitaciones que tiene MQTT respecto a una red LAN real son: 
- MQTT depende del broker para que exista la comunicación
- Overhead de TCP: a tráfico intenso se pueden generar latencias innecesarias
- Bajo throughput: MQTT esta optimizado para mensajes pequeños, no para mensajes grandes.
- Escalabilidad limitada: Lo que antes se mencionó como ventaja puede ser una desventaja al saturar al broker si no se configura adecuadamente.

F)
Las implicaciones de depender de un broker son:
- Punto único de fallo: como ya se nombró anteriormente, si el broker se cae, toda la red queda incomunicada.
- Cuello de botella: Todo el tráfico pasa por el broker, si este esa sobrecargado o mal dimensionado, baja el rendimiento de todo el sistema
- Mayor dependencia del hardware/servidor: Mas consumo de CPU y memoria, por lo que se debe monitorear el broker
- Seguridad centralizada: Si el broker es comprometido toda la red queda expuesta
- Facilita el control central: El broker es el punto ideal para registrar logs, auditorias y aplicar políticas.
