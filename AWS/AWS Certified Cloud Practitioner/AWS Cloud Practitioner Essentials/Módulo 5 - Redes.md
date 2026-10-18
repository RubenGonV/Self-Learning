```table-of-contents
```
---
# Introducción a las redes

>Las redes en la nube de AWS constan de la infraestructura y los servicios que trabajan en conjunto para alojar tus aplicaciones, datos y cualquier otro recurso que puedas necesitar.


## Componentes de red

### Amazon Virtual Private Cloud (Amazon VPC)

Una VPC de Amazon te permite aprovisionar una sección aislada de forma lógica de la nube de AWS, en la que puedes iniciar recursos de AWS en una red virtual que definas.

### Subred

**Las subredes** son básicamente segmentos de la VPC, lo que te permite dividir la VPC en secciones más pequeñas y fáciles de administrar. Una subred es un rango de direcciones IP de una VPC.

Las subredes se utilizan para organizar los recursos y se pueden hacer accesibles de forma pública o privada. 
- Por lo general, se usa una subred pública para recursos como un sitio web orientado a clientes.
- Por lo general, una subred privada se usa para contener recursos como una base de datos que almacena información de clientes o transacciones. 

## Diagramas de red

![[Pasted image 20251014100836.png]]

**Las subredes privadas** están diseñadas para aislar los recursos que no deberían exponerse directamente a la red pública de internet. En los diagramas, se representan como cajas sólidas.
En cambio, **las subredes públicas** se dibujan con cajas discontinuas.

---
# Organización de los recursos en la nube de AWS

## Establecimiento de límites en torno a los recursos de AWS

Al organizar tus recursos en la nube de AWS, debes poder agrupar determinadas funciones y aislarlas del público o ponerlas a su disposición.

### Beneficios de Amazon VPC

Con Amazon VPC, puedes aprovisionar una sección aislada de la nube de AWS. En esta sección aislada, puedes iniciar recursos en una red virtual que definas. 

Proporciona tres beneficios principales:
- Aumentar la seguridad, ya que puedes proteger y supervisar las conexiones, controlar el tráfico y restringir el acceso a las instancias.
- Control total sobre la ubicación de los recursos, la conectividad y la seguridad. 
- Menos tiempo para configurar, administrar y validar tu red virtual en comparación con la administración de redes locales.

## Conectar los recursos con una puerta de enlace de internet

Para permitir que el tráfico público de internet acceda a tu VPC, asocias una **puerta de enlace de internet** a la VPC. Una puerta de enlace de internet es una conexión entre una VPC e internet.

![[Pasted image 20251014102051.png]]

### Puertas de enlace privadas virtuales

Si tu VPC solo contiene recursos privados, el acceso a ella no se hace directamente desde internet. En su lugar, se usa una **puerta de enlace privada virtual (Virtual Private Gateway)**. Aquí es donde entra en juego una conexión de red privada virtual (VPN).

La VPN crea una conexión similar a un túnel seguro por internet.: protege los datos para que no puedan ser vistos ni interceptados. Así, el tráfico hacia y desde la VPC viaja de forma **segura y privada**, y solo se permite la entrada de redes **autorizadas**.

Con una puerta de enlace privada virtual, puedes establecer una conexión de VPN entre la VPC y una red privada, como un centro de datos local o una red corporativa interna.

![[Pasted image 20251014102328.png]]

---

# Más formas de conectarse a la nube de AWS

En esta lección, explorarás más conexiones de nube híbrida con la nube de AWS. En concreto, aprenderás más formas de conectar tus clientes, centros de datos y sitios a la nube de AWS.

En la siguiente sección, descubrirás cuatro maneras de conectarte a la nube de AWS:
- AWS Client VPN
- AWS Site-to-Site VPN
- AWS PrivateLink
- AWS Direct Connect

## AWS Client VPN

AWS Client VPN conecta tu personal remoto o local a AWS mediante una VPN.

Client VPN, un servicio de VPN administrado, proporciona acceso seguro a los recursos de AWS y a las redes locales desde cualquier lugar. Utiliza un cliente basado en OpenVPN y funciona con regiones globales mediante la red global de AWS.

Es un servicio de VPN elástico y completamente administrado que escala o desescala verticalmente y de forma automática en función de la demanda de los usuarios.

**Beneficios:** AWS Client VPN proporciona autenticación avanzada y acceso remoto. Es elástica y está completamente administrada.

**Caso práctico:** se puede usar para escalar rápidamente el acceso del personal remoto.

## AWS Site-to-Site VPN

AWS Site-to-Site VPN es una conexión de red cifrada a tus VPC de Amazon.

Site-to-Site VPN crea una conexión segura entre tu centro de datos o las sucursales y los recursos en la nube de AWS.

**Beneficios:** Site-to-Site VPN proporciona alta disponibilidad, sesiones seguras y privadas y agiliza las aplicaciones.

**Casos prácticos:** se puede usar para la migración de aplicaciones y la comunicación segura entre ubicaciones remotas.

## AWS PrivateLink

AWS PrivateLink conecta la VPC de forma privada a los servicios y recursos como si estuvieran en tu VPC.

AWS PrivateLink es una tecnología escalable y de alta disponibilidad que puedes utilizar para conectar de forma privada la VPC a los servicios y recursos como si estuvieran en tu VPC.

Para posibilitar la comunicación con los servicios o recursos de AWS desde tus subredes privadas controlas los puntos de enlace, los sitios, los servicios y los recursos de la API específicos a los que puedes acceder desde la VPC.

**Beneficios:** AWS PrivateLink te ayuda a proteger el tráfico y a conectarte con reglas de administración simplificadas.

**Caso práctico:** se usa para conectar tus clientes en la VPC a recursos, otras VPC y puntos de enlace.

## AWS Direct Connect

AWS Direct Connect es una conexión de AWS privada y específica a tu centro de datos u oficina.

Direct Connect es un servicio que te permite establecer una conexión privada específica entre la red y la VPC en la nube de AWS.

**Beneficios:** AWS Direct Connect reduce los costes de red y **aumenta la cantidad de ancho de banda**.

![[Pasted image 20251014104151.png]]

Direct Connect evita el uso intenso de internet y proporciona una experiencia de red uniforme y de baja latencia. Esto lo hace ideal para aplicaciones como el streaming de vídeo y otras aplicaciones en tiempo real que precisan de un rendimiento elevado.

Direct Connect ayuda a asegurar transferencias de datos fluidas y fiables a escala masiva para el análisis en tiempo real, la copia de seguridad rápida de los datos o el procesamiento de medios de difusión.

Puedes usar Direct Connect para vincular tus redes locales y de AWS con el fin de desarrollar aplicaciones que abarquen entornos sin comprometer el rendimiento.

---
# Servicios de puerta de enlace adicionales

Hay varios tipos diferentes de puertas de enlace que puedes usar para conectar tus recursos de AWS.

## AWS Transit Gateway

AWS Transit Gateway se utiliza para conectar las VPC de Amazon y las redes locales a través de un hub central. A medida que tu infraestructura de nube se expande a nivel mundial, la interconexión interregional conecta las Transit Gateway entre sí mediante la infraestructura global de AWS.

## Puerta de enlace de traducción de direcciones de red (NAT)

Una puerta de enlace de NAT es un servicio de *Network Address Translation*. Puedes utilizar una puerta de enlace de NAT para que las instancias de una subred privada puedan conectarse a servicios fuera de tu VPC, sin que los servicios externos puedan iniciar una conexión con esas instancias.

Antes de que NAT envíe paquetes entre las redes que conecta, traduce las direcciones privadas de la red interna a direcciones legales y únicas a nivel mundial.

## Amazon API Gateway

Ya has aprendido acerca de las interfaces de programación de aplicaciones (API). Actualización rápida: una API define cómo los diferentes sistemas de software pueden interactuar y comunicarse entre sí. Amazon API Gateway es un servicio de AWS para crear, publicar, mantener, supervisar y proteger las API a cualquier escala. Para obtener más

---
# Subredes, grupos de seguridad y listas de control de acceso a la red

Ahora que conoces los componentes básicos de una red, es hora de empezar a pensar en la seguridad. Dos formas muy eficaces y flexibles de controlar el tráfico de red en la VPC son los grupos de seguridad y las listas de control de acceso a la red, o ACL de red.

## Subredes

Una **subred** es una sección de una VPC en la que puedes agrupar recursos en función de las necesidades operativas o de seguridad. Las subredes pueden ser públicas o privadas.

Las **subredes públicas** contienen recursos que deben ser accesibles para el público, como un sitio web de una tienda en línea.

Las **subredes privadas** contienen recursos a los que solo se debe tener acceso a través de tu red privada, como una base de datos que contiene los datos personales y el historial de pedidos de los clientes.

En una VPC, puedes definir reglas para facilitar que los recursos de diferentes subredes se comuniquen entre sí. Por ejemplo, puedes tener una aplicación que utilice instancias de Amazon EC2 de una subred pública que se comuniquen con bases de datos situadas en una subred privada.

---
## Tráfico de red en una VPC

Cuando el cliente solicita datos de una aplicación alojada en la nube de AWS, esta solicitud se envía como un paquete. 

Entra en una VPC a través de una puerta de enlace de internet. Antes de que un paquete pueda entrar en una subred o salir de ella, se someterá a varias comprobaciones de permisos, una de las cuales es una ACL de red asociada a la subred a la que se dirige el paquete. Los permisos definidos por las ACL de red indican lo que está permitido o prohibido. Se basa en quién ha enviado el paquete y en cómo el paquete intenta comunicarse con los recursos de una subred.

![[Pasted image 20251014110726.png]]

### ACL de red

Una ACL de red es un firewall virtual que controla el tráfico de entrada y salida de la subred.

Cada cuenta de AWS tiene una ACL de red predeterminada. Al configurar la VPC, puedes usar la ACL de red predeterminada de tu cuenta o crear ACL de red personalizadas. De forma predeterminada, la ACL de red predeterminada de tu cuenta permite todo el tráfico de entrada y salida, pero puedes modificarlo añadiendo tus propias reglas.

En el caso de las ACL de red personalizadas, todo el tráfico de entrada y salida se deniega hasta que se añaden reglas para especificar qué tráfico se va a permitir. 

>[!info] Filtrado de paquetes sin estado (stateless)
>Las ACL de red realizan un filtrado de paquetes sin estado. No recuerdan nada y comprueban los paquetes que cruzan la frontera de la subred en cada sentido: de entrada y salida.


---
## Grupos de seguridad

Una vez que un paquete se ha introducido en una subred, se deben evaluar sus permisos para los recursos de la subred, como las instancias de Amazon EC2. 

Un grupo de seguridad es el componente de VPC que comprueba los permisos de paquetes de una instancia de Amazon EC2. Es un firewall virtual que controla el tráfico de entrada y salida de recursos de AWS específicos, como las instancias de Amazon EC2.

De forma predeterminada, un grupo de seguridad deniega todo el tráfico de entrada y permite todo el tráfico de salida. Con los grupos de seguridad, puedes añadir reglas personalizadas para configurar qué tráfico se debe permitir.

**Nota:** Si tienes varias instancias de Amazon EC2 en la misma VPC, puedes asociarlas al mismo grupo de seguridad o utilizar grupos de seguridad distintos para cada instancia.

>[!info] Filtrado de paquetes con estado
>Los grupos de seguridad realizan un filtrado de paquetes con estado. Recuerdan las decisiones previas tomadas respecto a los paquetes de entrada.
>
>Piensa en el mismo ejemplo de enviar una solicitud desde una instancia de Amazon EC2 a internet. Cuando una respuesta de paquete para esa solicitud vuelve a la instancia, el grupo de seguridad recuerda la solicitud anterior.


---

¿Te acuerdas del modelo de responsabilidad compartida de AWS? Cuando se trata de proteger las subredes y los recursos de tu VPC con ACL de red y grupos de seguridad, es tu responsabilidad. Estos componentes constituyen la protección del tráfico de red y son defensas fundamentales para proteger tus aplicaciones _EN_ la nube. ![[Pasted image 20251014111655.png]]

---
## Set-up de una Amazon VPC

Pasos:
1. **Creación de la VPC de Amazon**: Crear tu propia VPC de Amazon y especificar la región.
2. **Creación de las subredes**: Crearás subredes públicas y privadas en varias zonas de disponibilidad. Esta es una práctica recomendada para lograr una alta disponibilidad.
3. **Creación de una puerta de enlace de internet y enrutamiento del tráfico**: En primer lugar, se crea la puerta de enlace de internet. A continuación, creas tablas de enrutamiento para dirigir el tráfico y permitir la entrada del tráfico de internet y la salida del tráfico local.
4. En este punto, debes considerar qué tipo de seguridad necesitas y filtrar el tráfico que entra y sale. ¿Te acuerdas de los grupos de seguridad y las ACL de red? Ahí es donde son útiles. Finalmente, tendrás todo listo para incorporar los recursos, como instancias de EC2 o bases de datos, en tus subredes.

---
# Redes globales

En esta lección, aprenderás:
- Qué es el sistema de nombres de dominio (DNS) y para qué sirve.
- Cuáles son los beneficios y los casos prácticos de Amazon Route 53.
- Cuáles son los beneficios y los casos prácticos de Amazon CloudFront.

## Servicios de redes periféricas

Las redes periféricas son el proceso de acercar las capacidades de computación y de almacenamiento de información a los dispositivos que producen esa información y a los usuarios que la consumen. La computación periférica es importante porque las organizaciones suelen necesitar un acceso de menor latencia a sus datos y contenidos. También hay muchos servicios diferentes que se alojan en la periferia, como el servicio de DNS, Amazon Route 53.

>[!INFO] Traducción de nombres de dominio a direcciones IP con DNS
>Supongamos que EmpresaX tiene un sitio web alojado en la nube de AWS. El cliente introduce la dirección web en el navegador y puede acceder al sitio web. 
>
>Esto ocurre debido a la resolución de DNS, es decir, el proceso de traducir un nombre de dominio a una dirección IP.
>
>![[Pasted image 20251014115347.png]]

### Amazon Route 53

Route 53 es un DNS que proporciona una forma fiable y rentable de enrutar a los usuarios finales a las aplicaciones de internet. 

Route 53 dirige a los usuarios finales a tus recursos con servidores de DNS dispersos por todo el mundo y escalado automático. Ofrece a los desarrolladores y las empresas una forma fiable de enrutar a los usuarios finales a aplicaciones de internet alojadas en AWS. Conecta las solicitudes de los usuarios a la infraestructura que se ejecuta en AWS (como instancias de Amazon EC2 y equilibradores de carga). También puede enrutar a los usuarios a infraestructuras fuera de AWS.

Otra característica de Route 53 es la capacidad de administrar los registros de DNS de los nombres de dominio. Se pueden registrar nuevos nombres de dominio directamente en Route 53. También se pueden transferir registros de DNS para nombres de dominio existentes administrados por otros registradores de dominio. Esto te permite administrar todos los nombres de dominio en una sola ubicación.

### Amazon CloudFront

CloudFront es un servicio de red de entrega de contenido (CDN) que distribuye tu contenido con tiempos de carga más rápidos, ahorros de costes y fiabilidad.

En lugar de que todas las solicitudes viajen a un almacén central (tu servidor original), CloudFront almacena copias del contenido en ubicaciones más cercanas a los usuarios.

![[Pasted image 20251014115733.png]]

1. **Solicitud del cliente**: Una persona solicita datos de la aplicación y, para ello, se dirige al sitio web de EmpresaX.
2. **Amazon Route 53**: Amazon Route 53 utiliza la resolución de DNS para identificar la dirección IP correspondiente de EmpresaX.com, 192.0.2.0. Esta información se devuelve a la persona.
3. **CloudFront**: La solicitud se envía a la ubicación periférica más cercana a través de CloudFront. 
4. **Equilibrador de carga de aplicación**: Amazon CloudFront se conecta al equilibrador de carga de aplicación, que envía el paquete de entrada a una instancia de Amazon EC2.

### AWS Global Accelerator

Global Accelerator es un servicio de red diseñado para mejorar la disponibilidad y el rendimiento de las aplicaciones para los usuarios en todo el mundo. Para ello, proporciona direcciones IP estáticas, dirige el tráfico a través de la red global de AWS y lo enruta a puntos de enlace óptimos en función del estado, la ubicación de los usuarios y las políticas.

En lugar de que las solicitudes de los usuarios tomen las rutas de internet habituales, a veces saturadas, Global Accelerator dirige el tráfico a través de la red global privada de AWS para que los usuarios accedan a tu aplicación de forma más rápida y fiable.

---
# Arquitecturas globales: Ejemplos

![[Pasted image 20251014120400.png]]
Las ventajas de una VPN son que es segura, flexible, para transferencias de datos a pequeña escala.
Las desventajas de una VPN es que va por internet público, y puede ser lento. 

![[Pasted image 20251014120444.png]]
Las ventajas de Direct Connect son el alto ancho de banda, la baja latencia, y disponibilidad.


## Entrega de contenido a varias regiones diferentes a nivel mundial

![[Pasted image 20251014121242.png]]

---

# Resumen del módulo

En este módulo de redes, has identificado los componentes principales de la red y cómo se conectan en la nube de AWS. Hemos explicado los aspectos básicos de una VPC, la forma en que aíslas la carga de trabajo en AWS, las puertas de enlace, las ACL de red y los grupos de seguridad. También has revisado las formas de conectarte a AWS a través de una VPN y Direct Connect, conexiones seguras que están cifradas a través de la red pública de internet o conexiones exclusivas que solo tú utilizas.

También has aprendido acerca de las ubicaciones periféricas de AWS, Route 53 para DNS y CloudFront para almacenar contenido en caché más cerca del público.

| **Enlace del recurso**                                                                                                                                 | **Descripción**                                                                                                                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Amazon Virtual Private Cloud](https://aws.amazon.com/vpc/)                                                              | Amazon VPC es un servicio para aprovisionar una sección aislada de forma lógica de la nube de AWS, en la que puedes iniciar recursos de AWS en una red virtual que definas.                                                                                                                                                                           |
| [Subred](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html)                                        | Una subred es una sección de una VPC que puede contener recursos y se usa para organizar tus recursos. Pueden ser públicas o privadas.                                                                                                                                                                                                                |
| [Puerta de enlace de internet](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)               | Una puerta de enlace de internet es una conexión entre una VPC e internet. Permite que el tráfico público de internet acceda a tu VPC..                                                                                                                                                                                                               |
| [Puerta de enlace privada virtual](https://docs.aws.amazon.com/vpn/latest/s2svpn/how_it_works.html#VPNGateway)           | Una puerta de enlace privada virtual es el componente que permite que el tráfico de internet protegido entre en la VPC. Permite la conexión entre tu VPC y una red privada solo si proviene de una red aprobada.                                                                                                                                      |
| [AWS Client VPN](https://aws.amazon.com/vpn/client-vpn/)                                                                 | Amazon Client VPN es un servicio de red que puedes utilizar para conectar tus redes locales y de personal remoto a la nube. Es un servicio de VPN elástico y completamente administrado que escala o desescala verticalmente y de forma automática en función de la demanda de los usuarios.                                                          |
| [AWS Site-to-Site VPN](https://aws.amazon.com/vpn/site-to-site-vpn/)                                                     | AWS Site-to-Site VPN crea una conexión segura entre tu centro de datos o las sucursales y los recursos en la nube de AWS.                                                                                                                                                                                                                             |
| [AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)                           | AWS PrivateLink es una tecnología escalable y de alta disponibilidad que puedes utilizar para conectar de forma privada la VPC a los servicios y recursos como si estuvieran en tu VPC.                                                                                                                                                               |
| [AWS Direct Connect](https://aws.amazon.com/directconnect/)                                                              | AWS Direct Connect es un servicio que proporciona una conexión privada específica entre tu centro de datos y una VPC.                                                                                                                                                                                                                                 |
| [Lista de control de acceso de red (ACL de red)](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html) | Una ACL de red permite o deniega el tráfico de entrada y salida en el nivel de la subred mediante el filtrado de paquetes sin estado.                                                                                                                                                                                                                 |
| [Grupos de seguridad](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html)                         | Los grupos de seguridad controlan el tráfico de entrada y salida de un recurso a nivel de instancia mediante el filtrado de paquetes con estado.                                                                                                                                                                                                      |
| [Sistema de nombres de dominio (DNS)](https://aws.amazon.com/route53/what-is-dns/)                                       | El DNS traduce los nombres de dominio legibles por humanos a direcciones IP aptas para máquinas (por ejemplo, 192.0.2.0).                                                                                                                                                                                                                             |
| [Amazon Route 53](https://aws.amazon.com/route53/)                                                                       | Route 53 es un servicio web de DNS escalable y fiable que ayuda a los desarrolladores y a las empresas a dirigir a los usuarios finales a las aplicaciones de internet, tanto si están alojadas en AWS como en otro lugar. También admite el registro de dominios, las comprobaciones de estado y las políticas avanzadas de enrutamiento de tráfico. |
| [Amazon CloudFront](https://aws.amazon.com/cloudfront/)                                                                  | CloudFront es un servicio web que agiliza la distribución del contenido web a los usuarios a través de una red mundial de centros de datos denominada ubicaciones periféricas. Ofrece contenido de forma segura con baja latencia y altas velocidades de transferencia.                                                                               |
| [AWS Global Accelerator](https://aws.amazon.com/global-accelerator/)                                                     | Global Accelerator es un servicio de red que ayuda a mejorar la disponibilidad y el rendimiento de las aplicaciones para los usuarios de todo el mundo mediante el enrutamiento del tráfico a través de la red global de AWS. Ayuda a mejorar la disponibilidad, el rendimiento y la seguridad de las aplicaciones.                                   |
| [Amazon Transit Gateway](https://aws.amazon.com/transit-gateway/)                                                        | Amazon VPC Transit Gateways es un centro de tránsito de red que se utiliza para interconectar las VPC y las redes locales.                                                                                                                                                                                                                            |
| [Puerta de enlace de NAT](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)                         | La puerta de enlace de traducción de direcciones de red (NAT) permite que las instancias de una subred privada se conecten con servicios fuera de la VPC. Los servicios externos no pueden iniciar una conexión con esas instancias.                                                                                                                  |
| [API Gateway](https://aws.amazon.com/api-gateway/)                                                                       | Amazon API Gateway es un servicio de AWS para crear, publicar, mantener, supervisar y proteger las API a cualquier escala. Gestiona todas las tareas involucradas en la aceptación y el procesamiento de hasta cientos de miles de llamadas a la API simultáneas.                                                                                     |