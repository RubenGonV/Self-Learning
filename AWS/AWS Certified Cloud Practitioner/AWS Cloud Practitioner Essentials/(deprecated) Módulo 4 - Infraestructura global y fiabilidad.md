```table-of-contents

```
---
# Introducción

- Las ==regiones== son áreas aisladas geográficamente en las que puedes acceder a los servicios para que tu empresa funcione. 
- Las regiones contienen ==zonas de disponibilidad== que te permiten usar instalaciones separadas físicamente por decenas de kilómetros y, a la vez, mantener las aplicaciones unificadas lógicamente. Las zonas de disponibilidad ayudan a ofrecer alta disponibilidad y a recuperarse de desastres sin que tengas que hacer nada. 
- Las ==ubicaciones periféricas== de AWS utilizan **Amazon CloudFront** (CDN) para acercar el contenido a tus clientes, sin importar en qué parte del mundo estén.

---
# Regiones

Una región es un área geográfica que contiene recursos de AWS.

En todo el mundo, AWS crea regiones para estar más cerca de la demanda de tráfico de la empresa, ubicaciones como París, Tokio, São Paulo, Dublín u Ohio. En cada región, tenemos varios centros de datos con todos los servicios de computación, almacenamiento y otros necesarios para lanzar tus aplicaciones. Las regiones se pueden conectar entre sí a través de una red de fibra de alta velocidad controlada por AWS, una operación verdaderamente global de punto a punto si es necesario. 

Antes de entrar en la arquitectura de la creación de cada región, es importante que sepas que como responsable de las decisiones de tu empresa, puedes elegir qué regiones quieres usar. Cada región está aislada de las demás en el sentido de que ningún dato entra ni sale de tu entorno en esa región si no concedes explícitamente permiso para traspasar esos datos. Es una decisión fundamental de seguridad que tienes que tomar.
## Selección de una región

Al determinar la región adecuada para sus servicios, datos y aplicaciones, ten en cuenta los siguientes cuatro factores empresariales.

1. **Conformidad con los requisitos legales y de gobernanza de datos**: algunos datos deben almacenarse en regiones específicas por normativa.
2. **Proximidad a los clientes**: elegir regiones cercanas reduce la latencia y mejora la experiencia.
3. **Servicios disponibles en una región**: no todas las regiones ofrecen los mismos servicios, hay que comprobar compatibilidad.
4. **Precios**: los costes varían entre regiones, incluso para la misma carga de trabajo.

---
# Zonas de disponibilidad ("AZ")

Cada región consta de varias **zonas de disponibilidad** aisladas y físicamente independientes dentro de una región geográfica . 

Cada zona de disponibilidad, o "AZ" es uno o más centros de datos distintos con alimentación, redes y conectividad redundantes. Al lanzar una instancia de Amazon EC2, esta lanza una máquina virtual en un hardware físico instalado en una zona de disponibilidad.

Una práctica recomendada es ejecutar aplicaciones en, al menos, dos zonas de disponibilidad de una región. Si se produce un desastre, tus aplicaciones no se inmutarán, ya que este desastre solo habrá afectado a una parte de tu capacidad. Muchos de los servicios de AWS se ejecutan a nivel de región, es decir, se ejecutan de forma síncrona en varias AZ, sin coste adicional y sin que tengas que hacer nada.

---
## Ubicaciones periféricas

Una ubicación periférica es un sitio que Amazon CloudFront usa para almacenar en la memoria caché copias de tu contenido más cerca de tus clientes para una entrega más rápida.

> [!example] Ejemplo
> Si tienes clientes en Bombay que necesitan acceder a tus datos, pero los datos se alojan en la región de Tokio, en lugar de hacer que todos los clientes de Bombay envíen solicitudes a Tokio para acceder a los datos, es mejor tener una copia local o almacenarla en caché en Bombay

Para almacenar en caché copias de datos más cerca de los clientes en todo el mundo se usan las redes de entrega de contenido, o CDN. Las CDN se usan habitualmente, y la nuestra se llama Amazon CloudFront. 
### Amazon CloudFront
Amazon CloudFront es un servicio que ayuda a entregar datos, vídeo, aplicaciones y API a clientes de todo el mundo con baja latencia y altas velocidades de transferencia. Utiliza ubicaciones periféricas en todo el mundo para acelerar la comunicación con los usuarios, sin importar dónde se encuentren.

Además, son independientes de las regiones. De este modo, puedes enviar contenido desde una región a numerosas ubicaciones periféricas en todo el mundo para comunicarte y entregar contenido más rápido

### Amazon Route 53
Las ubicaciones periféricas de AWS no solo se usan con CloudFront. Utilizan un servicio de nombres de dominio, o DNS, conocido como Amazon Route 53. Ayudamos a dirigir a los clientes hacia las ubicaciones web correctas con una latencia baja y fiable.

### AWS Outposts
**AWS Outposts** es un servicio que permite llevar la infraestructura y los servicios de AWS directamente a las instalaciones de una empresa. Básicamente, AWS instala y opera una **miniregión local** dentro del centro de datos de la organización, con la misma funcionalidad y herramientas de la nube de AWS, pero ejecutándose en el propio sitio del cliente.

Se utiliza principalmente cuando existen requisitos específicos de latencia, gobernanza o normativas que obligan a mantener los datos y aplicaciones en las instalaciones, sin renunciar a la experiencia de AWS.

---

# Cómo aprovisionar recursos de AWS

Puedes preguntarte: "¿cómo se interactúa con estos servicios?". La respuesta es: "con las API". En AWS, todo es una llamada a API. Una API es una interfaz de programación de aplicaciones. Esto significa que hay modos predeterminados de interactuar con los servicios de AWS. Puedes invocar o hacer llamadas a estas API para aprovisionar, configurar y administrar recursos de AWS.

## Formas de interactuar con los servicios de AWS

### Consola de administración
La **consola de administración de AWS** es una interfaz basada en web para acceder a los servicios de AWS y administrarlos. Puedes acceder rápidamente a los servicios usados recientemente y buscar otros servicios por nombre, palabra clave o acrónimo. La consola incluye asistentes y flujos de trabajo automatizados que pueden simplificar el proceso de realización de tareas.  
  
También puedes usar AWS Console Mobile Application para llevar a cabo tareas como supervisar recursos, ver alarmas y acceder a la información de facturación. En la aplicación móvil de la consola de AWS pueden permanecer iniciadas varias identidades al mismo tiempo.

### Command Line Interface
Para ahorrar tiempo al realizar solicitudes de API, puedes usar **AWS Command Line Interface (AWS CLI)**. AWS CLI te permite controlar varios servicios de AWS directamente desde la línea de comandos en una herramienta. AWS CLI está disponible para los usuarios en Windows, macOS y Linux.   

Mediante AWS CLI, puedes automatizar las acciones que llevan a cabo los servicios y las aplicaciones mediante scripts.

### Kits de desarrollo de software (SDK)
Otra opción para acceder a los servicios de AWS y administrarlos son los **kits de desarrollo de software (SDK)**. Los SDK facilitan el uso de los servicios de AWS a través de una API diseñada para tu lenguaje de programación o tu plataforma. Los SDK permiten usar los servicios de AWS con tus aplicaciones existentes o crear aplicaciones completamente nuevas que se ejecutarán en AWS.

Para ayudarte a empezar a usar los SDK, AWS proporciona documentación y código de muestra para cada lenguaje de programación compatible. Entre los lenguajes de programación compatibles están C++, Java, .NET y otros.

### AWS Elastic Beanstalk

AWS Elastic Beanstalk es un servicio que simplifica el despliegue de aplicaciones al encargarse automáticamente de aprovisionar y gestionar la infraestructura necesaria (EC2, redes, balanceadores, escalado, etc.). Solo necesitas proporcionar tu código y la configuración deseada, y el servicio crea y gestiona el entorno, permitiendo además guardar configuraciones para futuros despliegues.

Con **AWS Elastic Beanstalk**, el usuario proporciona ajustes de código y configuración, y Elastic Beanstalk implementa los recursos necesarios para realizar las siguientes tareas:

- Ajuste de la capacidad
- Equilibrio de carga
- Escalado automático
- Seguimiento del estado de las aplicaciones

### AWS CloudFormation
Por otro lado, **AWS CloudFormation** es una herramienta de **infraestructura como código (IaC)** que permite definir y aprovisionar recursos de AWS de forma **declarativa** mediante plantillas en **JSON o YAML**. Con estas plantillas puedes describir toda tu arquitectura, y CloudFormation se encarga de crear los recursos necesarios —no solo EC2, sino también bases de datos, almacenamiento, análisis o ML— de manera automatizada y reproducible. Además, las plantillas pueden reutilizarse en distintas cuentas o regiones, reduciendo errores y asegurando consistencia entre entornos.

Con **AWS CloudFormation**, puedes tratar tu infraestructura como código. Esto significa que puedes crear un entorno escribiendo líneas de código en lugar de usar la consola de administración de AWS para aprovisionar recursos individualmente.

AWS CloudFormation aprovisiona tus recursos de forma segura y repetible, lo que te permite crear con frecuencia tu infraestructura y aplicaciones sin tener que realizar acciones manuales. Determina las operaciones correctas que deben realizarse al administrar la pila y revierte los cambios automáticamente si detecta errores.

---
# Resumen del módulo 3

En el módulo 3 se han tratado los siguientes conceptos:

- Regiones y zonas de disponibilidad
- Ubicaciones periféricas y Amazon CloudFront
- Consola de administración de AWS, AWS CLI y SDK
- AWS Elastic Beanstalk
- AWS CloudFormation

**Resumen:**  
En este tema se repasó la **infraestructura global de AWS**, compuesta por **regiones** y **zonas de disponibilidad (AZs)** —conjuntos de centros de datos interconectados— distribuidas por todo el mundo. Se recomienda **desplegar la infraestructura en al menos dos zonas de disponibilidad** para garantizar alta disponibilidad y tolerancia a fallos.

También se mencionaron los **servicios que gestionan automáticamente esta redundancia**, como **Elastic Load Balancing**, **Amazon SQS** y **Amazon SNS**.

Además, se abordaron las **ubicaciones periféricas (edge locations)**, que permiten distribuir contenido de forma más rápida y cercana al usuario final, y **AWS Outposts**, que extiende la infraestructura de AWS directamente a centros de datos locales.

Por último, se repasaron las **formas de aprovisionar recursos en AWS**, incluyendo la **consola de administración**, **SDKs**, **CLI**, **Elastic Beanstalk** y **CloudFormation**, destacando el uso de **infraestructura como código (IaC)**.

En resumen, AWS ofrece una red global, flexible y accesible, diseñada para desplegar recursos fácilmente en cualquier parte del mundo.
## Recursos adicionales

Revisa estos recursos para más información sobre los conceptos que se han visto en el módulo 3.

- [Infraestructura global(opens in a new tab)](https://www.infrastructure.aws/)
- [Mapa interactivo de la infraestructura global de AWS(opens in a new tab)](https://aws.amazon.com/about-aws/global-infrastructure/)
- [Regiones y zonas de disponibilidad(opens in a new tab)](https://aws.amazon.com/about-aws/global-infrastructure/regions_az)
- [Blog de redes y entrega de contenido de AWS(opens in a new tab)](https://aws.amazon.com/blogs/networking-and-content-delivery/)
- [Herramientas para crear en AWS(opens in a new tab)](https://aws.amazon.com/tools/)
- [Historias de clientes de AWS: entrega de contenido](https://aws.amazon.com/solutions/case-studies/?customer-references-cards.sort-by=item.additionalFields.publishedDate&customer-references-cards.sort-order=desc&awsf.customer-references-location=*all&awsf.customer-references-segment=*all&awsf.customer-references-product=product%23vpc%7Cproduct%23api-gateway%7Cproduct%23cloudfront%7Cproduct%23route53%7Cproduct%23directconnect%7Cproduct%23elb&awsf.customer-references-category=category%23content-delivery)