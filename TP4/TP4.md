# Comunicaciones de Datos - Trabajo Práctico N° 4

**Nombres**  
_Gianluca Ferraris; Ezequiel J. Marredo; Juan M. Painenao; Alejandro R. Stangaferro;_  
**Xi JinPING**

**Facultad de Ciencias Exactas, Físicas y Naturales**  
**Comunicaciones de Datos**
**Profesores**
_Facundo O. Cuneo; Santiago M. Henn;_
**15-11-2025**

---

### Información de los autores
 
- **Información de contacto**: _gianlucaferraris@mi.unc.edu.ar; ezequiel.marredo@mi.unc.edu.ar; juanpainenao@mi.unc.edu.ar; alejandro.stangaferro@mi.unc.edu.ar;_  

---

## Resumen
El presente trabajo aborda los principios fundamentales de la segmentación de redes mediante VLANs y su implementación práctica en entornos simulados con Cisco Packet Tracer. Se analizan los conceptos teóricos esenciales, incluyendo la clasificación de redes, el funcionamiento del estándar IEEE 802.1Q y el proceso de tagging, así como las distintas modalidades de VLAN. Posteriormente, se desarrolla la configuración completa de una topología de switches y estaciones finales, aplicando buenas prácticas de administración y seguridad. Las pruebas de conectividad permiten validar el funcionamiento de la segmentación lógica y la correcta operación de los enlaces configurados. El trabajo integra teoría y práctica para comprender cómo se estructura, organiza y administra una red moderna en capas.

**Palabras clave**: _VLAN, IEEE 802.1Q, Ethernet, Segmentación de red, Switching, Enlace trunk, Packet Tracer_

---

## Introducción
La segmentación lógica mediante VLANs es una herramienta fundamental para organizar el tráfico y mejorar la seguridad en redes que comparten la misma infraestructura física. Este trabajo práctico aborda los conceptos esenciales vinculados a las VLANs, el estándar IEEE 802.1Q y el mecanismo de tagging, junto con la clasificación básica de redes. Además, se desarrolla la implementación de una topología en Cisco Packet Tracer, donde se configuran switches, se crean VLANs y se realizan pruebas de conectividad para verificar su funcionamiento. El objetivo es integrar teoría y práctica para comprender cómo se administra y estructura una red moderna basada en switching.

## Resultados

### Consigna 1
**a)** Clasificación de las redes según su alcance

Las redes pueden clasificarse de acuerdo con la extensión geográfica que abarcan y esta clasificación permite ordenar los distintos escenarios de comunicación que utiliza una organización o un usuario común. Una red de área personal se denomina PAN y se utiliza para conectar dispositivos muy cercanos entre sí. Tiene un alcance de unos pocos metros y se utiliza para resolver comunicaciones de distancias cortas sin una infraestructura compleja.

Luego exiten las redes LAN, su alcance suele estar limitado a un edificio o a un campus pequeño. Una LAN está pensada para brindar altas velocidades y baja latencia porque su funcionamiento se estructura sobre medios físicos o inalámbricos de corta distancia y administrados centralmente.

A una escala algo mayor aparece la red de área metropolitana llamada MAN que abarca una ciudad o un conjunto de edificios distribuidos dentro de un distrito urbano. Las MAN suelen ser utilizadas por universidades, municipios o proveedores que interconectan sucursales y poseen enlaces que requieren tecnologías de transporte más robustas. Suelen basarse en fibras ópticas y tecnologías de portadora capaces de cubrir varios kilómetros manteniendo velocidades aceptables.

Por ultimo existe la red de área amplia llamada WAN. Este tipo de red se extiende a nivel nacional, regional o incluso internacional. Una WAN integra múltiples LAN y MAN a través de infraestructuras como enlaces de fibra, tecnologías de transporte de proveedores y sistemas satelitales. La WAN es el nivel donde se ubica Internet, que constituye la red pública y global más grande existente.

**b)** Concepto y clasificación de las VLAN

Una VLAN es una red de área local virtual que permite agrupar dispositivos de manera lógica independientemente de su ubicación física dentro de una misma infraestructura de switches. Este concepto introduce una forma de segmentación que mejora la seguridad, la organización y el rendimiento, porque cada VLAN actúa como si fuera una red independiente, aunque comparta el mismo hardware.

| **Tipo de VLAN**                | **Descripción**                                                                                         |
|---------------------------------|---------------------------------------------------------------------------------------------------------|
| **Basadas en puertos**          | El administrador asigna manualmente cada puerto del switch a una VLAN específica.                      |
| **Basadas en direcciones MAC**  | El switch clasifica dispositivos según su dirección MAC, independientemente del puerto utilizado.       |
| **Basadas en protocolos**       | La VLAN se determina según el protocolo de nivel superior que utiliza el tráfico.                      |
| **Basadas en subredes (Layer 3)** | La segmentación se realiza según la subred IP, permitiendo una asignación más dinámica y flexible.     |


**c)** Protocolo IEEE 802.1Q y su relación con las VLAN

El estándar IEEE 802.1Q define el mecanismo más utilizado para transportar información de VLAN a través de enlaces Ethernet. Su propósito es permitir que dos switches intercambien tramas y sepan a qué VLAN pertenece cada una. Para lograr esto el estándar introduce un campo adicional dentro de la trama Ethernet llamado campo de etiquetado o campo de VLAN Tag. Este campo se inserta entre la dirección MAC de origen y el identificador del protocolo y contiene información sobre la VLAN de la cual proviene la trama.

La relación entre el estándar IEEE 802.1Q y las VLAN es directa porque sin el mecanismo de etiquetado sería imposible transportar varias VLAN sobre un único enlace físico. Cada switch utilizaría puertos independientes y perdería flexibilidad.

**d)** Tagging en el contexto de redes y VLAN

El concepto de tagging se refiere al proceso mediante el cual un switch añade la etiqueta definida por IEEE 802.1Q a una trama Ethernet para indicar a qué VLAN pertenece. Este etiquetado ocurre cuando la trama atraviesa un enlace configurado como trunk, ya que necesita conservar la información sobre su VLAN de origen. La etiqueta incorpora cuatro bytes adicionales que incluyen un identificador de protocolo y el identificador de la VLAN, lo que permite que el dispositivo receptor interprete correctamente a qué red virtual corresponde la trama y la reenvíe dentro del dominio de broadcast adecuado.

### Consigna 2
Implementación de la topología en Cisco Packet Tracer:
![image](https://hackmd.io/_uploads/SJ8xkLrxZe.png)

A) 
Nombramiento de los switches:

![image](https://hackmd.io/_uploads/r1vMJLHgWx.png)

B)
Asignación de contraseñas privilegiadas, de consola y vty

![image](https://hackmd.io/_uploads/rypXJLHeZg.png)

C)
Encriptación de contraseñas:

![image](https://hackmd.io/_uploads/B1frJLrxZl.png)

E)
Desconexión de todas las interfaces que no están siendo utilizadas

![image](https://hackmd.io/_uploads/rk401Lre-e.png)

F)
Guardado de configuración

![image](https://hackmd.io/_uploads/HkTkx8rlZe.png)

G)
Test de comunicación utilizando ping entre las computadoras

![image](https://hackmd.io/_uploads/SyebxIBxbl.png)

H)
Creación de VLANs

![image](https://hackmd.io/_uploads/SkxMgUHlWg.png)

I)
Visualización de la VLAN utilizada por defecto

![image](https://hackmd.io/_uploads/B1gXxUHgbe.png)

J, K, L)

![image](https://hackmd.io/_uploads/rkSSxIBgWe.png)

N)
Conectividad entre PC-A y PC-B

![image](https://hackmd.io/_uploads/SJrdgLSlWe.png)

Conectividad entre sw-1 y sw-2

![image](https://hackmd.io/_uploads/SycOeLHx-e.png)

Se configuraron ambos switches asignando hostnames, contraseñas y encriptación, se crearon las VLANs requeridas y se migró la IP de gestión desde VLAN 1 a VLAN 99. Se asignaron PC-A y PC-B a la VLAN 10 y se deshabilitaron interfaces no utilizadas como buena práctica de seguridad. Las pruebas de conectividad mostraron que los hosts en la misma VLAN pueden comunicarse correctamente entre switches.

---
### Consigna 3

En el ejercicio 3 se simuló el despliegue de una red LAN a bordo de una aeronave, utilizando VLANs para segmentar distintos perfiles de usuarios (Turista, Business y Administración), junto con ACLs y NAT para aplicar políticas de acceso diferenciadas.

La segmentación se implementó mediante tres VLANs:
- **VLAN 10 – Turista:** acceso únicamente al servidor local.
- **VLAN 20 – Business:** acceso al servidor e Internet.
- **VLAN 99 – Administración:** acceso completo a todos los segmentos.
- **Enlace WAN (ISP) 200.0.0.0/30:** utilizado para simular Internet.

Las subinterfaces del router permitieron el enrutamiento inter-VLAN y la asignación de gateways, mientras que el switch se encargó de asociar cada puerto físico a la VLAN correspondiente.  
Las ACLs bloquearon correctamente el acceso a Internet desde Turista, permitiendo únicamente el tráfico hacia el servidor de entretenimiento.  
El NAT se aplicó de forma selectiva únicamente a la VLAN Business, tal como pedía el ejercicio.

Las pruebas demostraron que:
- Turista puede acceder al servidor (ping + HTTP).
- Turista tiene el acceso a Internet correctamente bloqueado.
- Business accede al servidor y también a Internet.
- Administración tiene comunicación con todos los segmentos.
- El servidor responde desde todas las VLANs.
- La topología cumple el “espíritu” del ejercicio: aislar perfiles según políticas de acceso.

En resumen, se logró implementar con éxito un esquema de red segmentado, seguro y funcional que replica un escenario real de conectividad a bordo de una aeronave.

---


#### Topología del Ejercicio 3 en Packet Tracer
- Red completa del avión (Switch + Router + Server + PCs).

![topologia](https://hackmd.io/_uploads/r1wjA_Sg-g.png)

---

#### Pruebas de ping Turista-Server

![ping t-server](https://hackmd.io/_uploads/S1iARdBl-l.png)

---

#### Pruebas de ping Turista-HTTP

![image](https://hackmd.io/_uploads/HJmnz9Bl-l.png)


---

#### Pruebas de ping Turista-Internet
![ping t-internet](https://hackmd.io/_uploads/rJhIf9HlZg.png)


---

#### Pruebas de ping Bussines-HHTP

![image](https://hackmd.io/_uploads/SyukVqHebl.png)


---
#### Pruebas de ping Bussines-Internet

![image](https://hackmd.io/_uploads/S1QuX9HeWe.png)
---

#### Pruebas de ping Admin-Internet

![image](https://hackmd.io/_uploads/HkMgjRBxWg.png)

---

#### Pruebas de ping Admin-HTTP

![image](https://hackmd.io/_uploads/ryLKi0SxWg.png)

---

