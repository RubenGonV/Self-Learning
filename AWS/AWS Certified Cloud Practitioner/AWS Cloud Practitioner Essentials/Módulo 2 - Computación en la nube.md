```table-of-contents
```
---
**Objetivos de aprendizaje**
En este módulo aprenderás a:

- Describir los beneficios de Amazon EC2 a nivel básico.
- Identificar los distintos tipos de instancias de Amazon EC2.
- Diferenciar entre las distintas opciones de facturación de Amazon EC2.
- Resumir los beneficios de Amazon EC2 Auto Scaling.
- Resumir los beneficios de Elastic Load Balancing.
- Dar un ejemplo de los usos de Elastic Load Balancing.
- Resumir las diferencias entre Amazon Simple Notification Service (Amazon SNS) y Amazon Simple Queue Service (Amazon SQS).
- Resumir las opciones de computación adicionales de AWS.

---
# Amazon Elastic Compute Cloud (EC2)

Centros de datos (servidores físicos) gestionados por amazon. EC2 permite solicitar las instancias (máquinas virtuales) que necesites, encender/apagar cuando quieras con la configuración que quieras. Tenencia múltiple, protegidas individualmente. 

Servicio de **computación en la nube** con instancias virtuales.
Alternativa a comprar/instalar servidores físicos.
Características:
  - Lanzar instancias en **minutos**.  
  - **Apagar/terminar** cuando no se usan.  
  - **Pago por uso** (solo cuando se ejecutan).  
  - **Escalabilidad y ahorro de costes**.  

---
## Tipos de instancias EC2

### 1. Propósito general
- Balance entre **CPU, memoria y red**.  
- Usos: apps web, juegos, backends, BBDD pequeñas/medianas.  

### 2. Computación optimizada
- **Alto rendimiento de CPU**.  
- Usos: servidores web de alto tráfico, procesamiento por lotes, juegos intensivos. 
- Adecuadas para cargas de trabajo de procesamiento por lotes

### 3. Memoria optimizada
- **Grandes conjuntos de datos en memoria**.  
- Usos: BBDD de alto rendimiento, analítica en tiempo real.  

### 4. Computación acelerada
- Uso de **GPU/FPGA/aceleradores**.  
- Usos: gráficos, machine learning, streaming de juegos.  

### 5. Almacenamiento optimizado
- **Alta E/S secuencial** y **IOPS elevados**.  
- Usos: sistemas de archivos distribuidos, data lakes, OLTP.  

---
## Amazon EC2 - Precios
- **Pago por uso**: solo por el tiempo de computación.  
- Opciones según necesidades de **coste, flexibilidad y compromiso**.  

### 1. Bajo demanda
- Pago por segundo/hora, **sin costes iniciales ni contratos**.  
- Idóneo: cargas irregulares, cortas, no interrumpibles.  
- Ej: desarrollo, pruebas, apps con uso impredecible.  
- No recomendable a largo plazo (+1 año).  

### 2. Instancias reservadas
- Descuento sobre instancias bajo demanda (1 o 3 años).  
- Tipos:
  - **Standard**: mayor ahorro, menos flexibilidad. Requiere fijar tipo/tamaño, SO, región y tenencia. 
  - **Convertibles**: permiten cambiar tipo/instancia, más flexibilidad, menor ahorro.  
- Posibilidad de **reserva de capacidad** (si se fija zona de disponibilidad).  
- Al terminar el plazo: sigue funcionando como bajo demanda salvo renovación.  

### 3. Savings Plans
- Compromiso de **gasto/hora** (1 o 3 años).  
- Ahorro hasta **72 %**.  
- Más flexibles que las reservadas:
  - No fijan tipo exacto, SO ni tenencia.  
  - No hay reserva de capacidad.  
- Idóneos si necesitas **flexibilidad de uso**.  
- Herramienta útil: **AWS Cost Explorer** → analiza uso y da recomendaciones.  

### 4. Instancias de spot
- Usan capacidad no empleada de EC2.  
- Ahorro hasta **90 %**.  
- Idóneas: cargas tolerantes a interrupciones, flexibles (ej: procesamiento en segundo plano).  
- Riesgo: pueden **interrumpirse** si sube la demanda o baja la capacidad.  

### 5. Hosts dedicados
- Servidores físicos dedicados.  
- Permiten usar **licencias existentes** por socket/núcleo/VM.  
- Disponibles bajo demanda o reservados.  
- **Más caros** de todas las opciones.  

---

## Amazon EC2 Auto Scaling

![[Pasted image 20251002134524.png]]

![[Pasted image 20251002134751.png]]

---

## Dirección de tráfico con Elastic Load Balancing

**Elastic Load Balancing** es el servicio de AWS que distribuye automáticamente el tráfico entrante de la aplicación entre varios recursos como, por ejemplo, instancias de Amazon EC2.

![[Pasted image 20251003100815.png]]

ELB es regional (una única URL) y escala automáticamente.

---

## Mensajería y cola

Una **aplicación monolítica** tiene todos sus componentes ==fuertemente acoplados== (BD, servidor, UI, lógica de negocio…). Si uno falla, arrastra a los demás y puede tumbar la aplicación entera.

En cambio, con una arquitectura de **microservicios**, los componentes se diseñan como unidades independientes que se comunican entre sí (==acoplamiento débil==). Así, si uno falla, los demás pueden seguir funcionando, lo que mejora la disponibilidad y la resiliencia de la aplicación. 

Al diseñar aplicaciones en AWS, puedes adoptar la estrategia de microservicios con servicios y componentes que cumplan diferentes funciones. Dos servicios facilitan la integración de aplicaciones: Amazon Simple Notification Service (Amazon SNS) y Amazon Simple Queue Service (Amazon SQS).

### Amazon Simple Notification Service (Amazon SNS) *pub/sub*

**Amazon Simple Notification Service (Amazon SNS)** es un servicio de **publicación/suscripción**. Mediante temas de Amazon SNS, un editor publica mensajes a los suscriptores. 

Además, SNS puede utilizarse para difundir las notificaciones a usuarios finales mediante push a móviles, SMS y correo electrónico.
### Amazon Simple Queue Service (Amazon SQS) *P2P*

Es un servicio de cola de mensajes. Con Amazon SQS, puedes enviar, almacenar y recibir mensajes entre componentes de software a cualquier volumen, sin perder mensajes y sin necesidad de que otros servicios estén disponibles. 

---
# Resumen del módulo 2

En estas lecciones sobre computación:
- Has aprendido cómo Amazon EC2 y los recursos en la nube ayudan en el escalado de aplicaciones. 
- Has adquirido conocimientos sobre los tipos de instancias de EC2, las opciones de precios y cómo elegir los mejores tipos de instancias para tus necesidades empresariales exclusivas. 
- También te has familiarizado con el uso de las herramientas y los servicios de AWS, como Elastic Load Balancing, Amazon EC2 Auto Scaling, Amazon SQS y Amazon SNS, que sirven para administrar el tráfico y la comunicación.

**Resumen:**  
La **computación en la nube** consiste en ofrecer recursos de TI (como cómputo, redes, almacenamiento o análisis) bajo demanda y con pago por uso, sin necesidad de invertir por adelantado. **AWS** proporciona una amplia gama de servicios combinables para crear soluciones personalizadas.

Entre ellos destaca **Amazon EC2**, que permite lanzar servidores virtuales (“instancias”) adaptados a distintos fines: uso general, computación optimizada, memoria optimizada, computación acelerada u optimizadas para almacenamiento. Las instancias pueden **escalar verticalmente** (aumentando su tamaño) o **horizontalmente** (añadiendo más instancias), con ayuda de **EC2 Auto Scaling** y **Elastic Load Balancer** para distribuir el tráfico.

Los **modelos de precios** de EC2 incluyendo
- **Bajo demanda** (flexible, sin compromiso)
- **Spot** (uso de capacidad no utilizada con descuento)
- **Instancias reservadas / Savings Plans** (compromiso de uso a cambio de descuento)
- **Savings Plans de computación**, aplicables también a **Lambda** y **Fargate**

AWS también ofrece **servicios de mensajería**:
- **SQS (Simple Queue Service)**: desacopla componentes mediante colas de mensajes.
- **SNS (Simple Notification Service)**: envía notificaciones a múltiples destinatarios (correo, SMS, HTTP, etc.).

## Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| Enlace del recurso                                                                                                                                                                                                             | Descripción                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Computación en AWS](https://aws.amazon.com/products/compute)                                                                                                                                    | Este recurso proporciona una información general de los diferentes servicios de computación en la nube que ofrece AWS.                                                                                                                                                                                                             |
| [AWS Compute Blog](https://aws.amazon.com/blogs/compute/)                                                                                                                                        | En este blog puedes consultar actualizaciones, tutoriales y prácticas recomendadas para usar los servicios de computación de AWS, como Amazon EC2, AWS Lambda, Amazon ECS y más.                                                                                                                                                   |
| [Servicios de computación de AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/compute-services.html)                                                                             | Esta referencia proporciona una introducción detallada a los servicios de computación disponibles en la nube de AWS.                                                                                                                                                                                                               |
| [Tutoriales prácticos: computación](https://aws.amazon.com/getting-started/hands-on/?awsf.getting-started-category=category%23compute&awsf.getting-started-content-type=content-type%23hands-on) | Este recurso proporciona tutoriales prácticos paso a paso diseñados para ayudar a los usuarios a adquirir experiencia práctica con los servicios de computación de AWS. Es ideal para principiantes y para quienes dan sus primeros pasos en la computación en la nube.                                                            |
| [Amazon EC2](https://aws.amazon.com/ec2/)                                                                                                                                                        | Amazon EC2 ejecuta servidores virtuales en la nube con una capacidad de computación flexible.                                                                                                                                                                                                                                      |
| [Tipos de instancias de Amazon EC2](https://aws.amazon.com/ec2/instance-types/)                                                                                                                  | En esta guía se proporciona información detallada sobre los diferentes tipos de instancias de EC2, incluidas sus especificaciones, capacidades y casos prácticos. Te ayuda a elegir el tipo de instancia correcto en función de tus necesidades de carga de trabajo, como los requisitos de computación, memoria y almacenamiento. |
| [Precios de Amazon EC2](https://aws.amazon.com/ec2/pricing/)                                                                                                                                     | En esta guía se explican los diferentes modelos de precios de las instancias de EC2, incluidas las instancias bajo demanda, reservadas y de spot, para que puedas elegir la mejor opción en función del uso que hagas.                                                                                                             |
| [Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/)                                                                                                                               | Amazon EC2 Auto Scaling ajusta automáticamente el recuento de instancias en función de la demanda de alta disponibilidad y rentabilidad.                                                                                                                                                                                           |
| [Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/)                                                                                                                           | Elastic Load Balancing distribuye automáticamente el tráfico de entrada de aplicaciones en varias instancias de EC2 para lograr una alta disponibilidad y tolerancia a errores.                                                                                                                                                    |
| [Amazon Simple Notification Service](https://aws.amazon.com/sns/)                                                                                                                                | SNS es un servicio de mensajería para enviar notificaciones a los usuarios o a otras aplicaciones a través de SMS, correo electrónico o notificaciones push móviles.                                                                                                                                                               |
| [Amazon Simple Queue Service](https://aws.amazon.com/sqs/)                                                                                                                                       | Amazon SQS desacopla los componentes de la aplicación mediante la puesta en cola de mensajes, almacenando y procesando los mensajes de forma fiable.                                                                                                                                                                               |