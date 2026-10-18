```table-of-contents
```
---
# Introducción a la computación sin servidor

> [!tip] Servicios que necesitan menos administración que EC2
> 
> EC2 es ideal para todo tipo de casos prácticos, como lanzar servidores web básicos o clústeres informáticos de alto rendimiento, entre otros usos. Si tienes aplicaciones que quieres ejecutar en Amazon EC2, debes hacer lo siguiente:
> 1. Aprovisionar instancias (servidores virtuales).   
> 2. Cargar el código.
> 3. Seguir administrando las instancias mientras la aplicación se ejecuta.
> 

El término "==sin servidor==" significa que el código se ejecuta en servidores, pero no es necesario aprovisionar ni administrar dichos servidores. La computación sin servidor puede ajustar la capacidad de las aplicaciones modificando las unidades de consumo, como el rendimiento y la memoria. 

Con la computación sin servidor, puedes ejecutar aplicaciones sin administrar la infraestructura subyacente.

Conoce AWS Lambda, una solución sin servidor que gestiona automáticamente el escalado, la disponibilidad y el mantenimiento. También descubrirás servicios como Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS) y AWS Elastic Beanstalk, que hacen que la administración de contenedores y el despliegue de aplicaciones sean más fáciles de administrar. 

## Tipos de servicios

### Servicios sin administrar
Con servicios de computación sin administrar, como Amazon EC2, AWS se encarga de la infraestructura física subyacente, pero tú eres responsable de configurar, proteger y mantener el sistema operativo, las configuraciones de red y las aplicaciones de tus instancias. 

### Servicios administrados
Los servicios administrados, por otro lado, reducen la cantidad de infraestructura que tienes que administrar. Si bien AWS gestiona gran parte de la sobrecarga operativa, es posible que tengas que realizar algún tipo de aprovisionamiento o configuración en función del servicio.

### Servicios totalmente administrados

Los servicios totalmente administrados, como los sin servidor, llevan la abstracción aún más lejos y eliminan la necesidad de aprovisionar o administrar ningún servidor. AWS administra completamente la infraestructura subyacente, por lo que puedes centrarte en exclusiva en escribir y desplegar código. Más adelante en este módulo, verás Lambda. Lambda es un servicio de computación sin servidor en el que AWS se encarga de la infraestructura, el escalado y la disponibilidad, mientras que tú sigues siendo responsable de proteger y administrar el código de la aplicación.

![[tipos-de-servicios.png]]

---
# AWS Lambda
Lambda es un servicio de computación sin servidor que ejecuta código en respuesta a eventos sin necesidad de aprovisionar o administrar servidores. Administra automáticamente la infraestructura subyacente, escalando los recursos en función del volumen de solicitudes. Solo se te cobra por el tiempo de computación consumido, hasta el milisegundo. Lambda gestiona la ejecución, el escalado y la asignación de recursos. Puedes optimizar el rendimiento configurando la cantidad de memoria adecuada para tu función.

Por ejemplo, una función Lambda sencilla podría ser cambiar automáticamente el tamaño de las imágenes subidas a la nube de AWS. En este caso, la función se activa cuando se carga una nueva imagen.

![[Pasted image 20251003102733.png]]

---
# Contenedores
En AWS, también puedes crear y ejecutar aplicaciones en **contenedores**.

Los **contenedores** te ofrecen un método estándar para empaquetar el código de la aplicación y las dependencias en un solo objeto. También puedes usar los contenedores para procesos y flujos de trabajo en los que existan requisitos esenciales de seguridad, fiabilidad y escalabilidad.

Los servicios de coordinación de contenedores te ayudan a desplegar, administrar y escalar las aplicaciones en contenedores. AWS proporciona dos servicios que facilitan la coordinación en contenedores: Amazon Elastic Container Service y Amazon Elastic Kubernetes Service.

## Amazon Elastic Container Service (Amazon ECS)

Amazon Elastic Container Service (Amazon ECS) es un servicio escalable de orquestación de contenedores para ejecutar y administrar contenedores en AWS, como los contenedores Docker. Docker es una plataforma de software para crear, probar y desplegar aplicaciones rápidamente.

**Tipos de inicio de Amazon ECS**:

- Amazon ECS con Amazon EC2 -> control total de la infraestructura. Para apps personalizadas que requieren configuraciones de red o hardware específicas, con la flexibilidad de Amazon EC2 y la simplicidad de Amazon ECS.

- Amazon ECS con AWS Fargate es ideal para empresas emergentes o equipos pequeños que crean aplicaciones web con tráfico variable. Es una opción sin servidor (no se requiere administración de servidores), por lo que los equipos pueden centrarse en el desarrollo mientras ECS se ocupa del escalado y la orquestación.

## Amazon Elastic Kubernetes Service (Amazon EKS)

Amazon Elastic Kubernetes Service (Amazon EKS) es un servicio completamente administrado para ejecutar Kubernetes en AWS. Simplifica el despliegue, la administración y el escalado de aplicaciones en contenedores mediante Kubernetes de código abierto, con soporte y actualizaciones continuos de la comunidad en general.

**Tipos de inicio de Amazon EKS**:

- Amazon EKS con Amazon EC2: -> control total de la infraestructura. Ofrece una personalización profunda de las instancias de EC2 junto con la escalabilidad de Kubernetes, lo que resulta perfecto para cargas de trabajo complejas a gran escala.

- Amazon EKS con AWS Fargate: -> flexibilidad de Kubernetes sin tener que administrar servidores. Combina la potencia de Kubernetes con la simplicidad que ofrece trabajar sin servidores, lo que ayuda a escalar las aplicaciones rápidamente en varios casos prácticos.

## Amazon ECR

Amazon Elastic Container Registry (Amazon ECR) es el lugar donde puedes almacenar, administrar y desplegar imágenes de contenedores. Admite imágenes de contenedores que siguen los estándares de la Open Container Initiative (OCI). Puedes incorporar, extraer y administrar imágenes en los repositorios de Amazon ECR mediante herramientas de contenedores e interfaces de línea de comandos (CLI) estándar.

## AWS Fargate

AWS Fargate es un motor de computación sin servidor para contenedores. Funciona tanto con Amazon ECS como con Amazon EKS. Fargate es una plataforma de alojamiento de contenedores, a diferencia de Amazon ECS y Amazon EKS, que son servicios de orquestación de contenedores.

Con Fargate no es necesario aprovisionar ni administrar servidores. Fargate administra la infraestructura de servidores por ti. Puedes centrarte más en innovar y desarrollar tus aplicaciones, y solo pagarás por los recursos necesarios para ejecutar tus contenedores.


---

# Servicios de computación adicionales

AWS ofrece servicios diseñados específicamente para necesidades específicas, como la optimización del despliegue de aplicaciones web, la administración de cargas de trabajo por lotes, el suministro de servidores virtuales y la ampliación de la infraestructura de nube a los centros de datos locales.

- Elastic Beanstalk optimiza el aprovisionamiento y la administración del entorno.
- AWS Batch administra las tareas de computación a gran escala y ajusta automáticamente los recursos en función de la demanda.
- Amazon Lightsail optimiza la configuración y la administración de las aplicaciones web sin necesidad de una infraestructura compleja.
- AWS Outposts extiende los servicios de AWS a los entornos locales y admite arquitecturas de nube híbrida.


## Elastic Beanstalk

Elastic Beanstalk es un servicio completamente administrado que optimiza el despliegue, la administración y el escalado de las aplicaciones web. Los desarrolladores pueden cargar su código y Elastic Beanstalk gestiona automáticamente el aprovisionamiento de la infraestructura, el escalado, el equilibrio de carga y la supervisión del estado de las aplicaciones. Es compatible con varios lenguajes y marcos de programación, como Java, .NET, Python, Node.js, Docker y más. Proporciona un control total sobre los recursos subyacentes de AWS y, al mismo tiempo, automatiza muchas tareas operativas.

**Ideal para:** desplegar y administrar aplicaciones web, API RESTful, servicios de backend móviles y arquitecturas de microservicios, con escalado automatizado y administración simplificada de la infraestructura.

## AWS Batch

AWS Batch es un servicio completamente administrado que puedes utilizar para ejecutar cargas de trabajo de computación por lotes en AWS. Programa, administra y escala automáticamente los recursos de computación para los trabajos por lotes, lo que optimiza la asignación de recursos en función de los requisitos del trabajo.

**Ideal para**: procesar cargas de trabajo paralelas a gran escala en áreas como la computación científica, el análisis de riesgos financieros, la transcodificación de archivos multimedia, el procesamiento de big data, el entrenamiento de machine learning y la investigación genómica.

## Lightsail

Amazon Lightsail es un servicio en la nube que ofrece servidores privados virtuales (VPS), almacenamiento, bases de datos y redes a un precio mensual predecible. Es ideal para pequeñas empresas, cargas de trabajo básicas y desarrolladores que buscan una experiencia de AWS sencilla sin la complejidad que supone la consola de administración de AWS completa.

**Ideal para**: aplicaciones web básicas, sitios web con poco tráfico, entornos de desarrollo y pruebas, sitios web de pequeñas empresas, blogs y servicios de aprendizaje en la nube.

## Outposts

AWS Outposts es una solución de nube híbrida completamente administrada que extiende la infraestructura y los servicios de AWS a los centros de datos locales. Proporciona una experiencia uniforme entre las instalaciones y la nube de AWS, y ofrece componentes de computación, almacenamiento y redes.

**Ideal para**: aplicaciones de baja latencia, procesamiento de datos en ubicaciones remotas, migración y modernización de aplicaciones heredadas y cumplimiento de los requisitos de residencia de datos o conformidad normativa.

---

# Resumen del módulo

Este módulo te ha proporcionado conocimientos prácticos sobre los servicios de computación de AWS, para que puedas elegir las herramientas adecuadas para tus aplicaciones. Has aprendido cuándo utilizar opciones completamente administradas, como Lambda o Fargate, y cuándo tiene sentido mantener el control total con Amazon EC2. Has visto cómo los contenedores resuelven los problemas de coherencia en el despliegue y cómo los servicios de AWS, como Amazon ECS y Amazon EKS, simplifican la gestión y el escalado de las aplicaciones en contenedores. También has descubierto servicios como Elastic Beanstalk, AWS Batch, Lightsail y Outposts, y cómo cada uno de ellos admite casos prácticos específicos, desde el alojamiento web básico hasta el procesamiento por lotes a gran escala o los entornos de la nube híbrida.

## Recursos
| Enlace del recurso                                                                                                                                                                                                                                                                                                                                                          | Descripción                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Contenedores en AWS](https://aws.amazon.com/containers/services/)                                                                                                                                                                                                                                                                            | La página de AWS Containers Services ofrece una información general de las ofertas de contenedores de AWS, incluidos los servicios de almacenamiento, orquestación y computación de imágenes de contenedores. Estas ofertas están diseñadas para optimizar el despliegue y la administración de aplicaciones en contenedores. |
| [Amazon Elastic Container Registry](https://aws.amazon.com/ecr/)                                                                                                                                                                                                                                                                              | Amazon ECR es un servicio completamente administrado que sirve para almacenar, administrar y desplegar imágenes de contenedores de forma segura y a escala.                                                                                                                                                                   |
| [Amazon Elastic Container Service](https://aws.amazon.com/ecs/)                                                                                                                                                                                                                                                                               | Amazon ECS es un servicio completamente administrado que optimiza el despliegue, la administración y el escalado de las aplicaciones en contenedores en AWS.                                                                                                                                                                  |
| [Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/)                                                                                                                                                                                                                                                                              | Amazon EKS es un servicio de Kubernetes completamente administrado que optimiza la ejecución de clústeres de Kubernetes tanto en AWS como en las instalaciones. Automatiza la administración de la infraestructura y se integra con los servicios de red, seguridad y almacenamiento de AWS.                                  |
| [AWS Fargate](https://aws.amazon.com/fargate/)                                                                                                                                                                                                                                                                                                | Fargate es un motor de computación sin servidor para ejecutar contenedores sin administrar servidores. Está integrado con Amazon ECS y Amazon EKS.                                                                                                                                                                            |
| [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/?gclid=EAIaIQobChMIpb-UsKDfjAMVfWJHAR2d6xQ1EAAYASAAEgLN5PD_BwE&trk=b1c3dd7d-1b94-4b82-99e3-c1505e3a55fb&sc_channel=ps&ef_id=EAIaIQobChMIpb-UsKDfjAMVfWJHAR2d6xQ1EAAYASAAEgLN5PD_BwE:G:s&s_kwcid=AL!4422!3!651737511569!e!!g!!elastic%20bean%20stalk!19845796021!146736269029) | Elastic Beanstalk es un servicio completamente administrado para desplegar y escalar aplicaciones web sin necesidad de administrar la infraestructura.                                                                                                                                                                        |
| [AWS Batch](https://aws.amazon.com/batch/)                                                                                                                                                                                                                                                                                                    | AWS Batch es un servicio completamente administrado que ejecuta de manera eficiente trabajos de computación por lotes a gran escala en AWS.                                                                                                                                                                                   |
| [¿Qué es Amazon Lightsail?](https://docs.aws.amazon.com/lightsail/latest/userguide/what-is-amazon-lightsail.html)                                                                                                                                                                                                                             | Lightsail es una plataforma en la nube simplificada que ofrece VPS, contenedores y bases de datos con precios predecibles.                                                                                                                                                                                                    |
| [¿Qué es AWS Outposts?](https://docs.aws.amazon.com/outposts/latest/server-userguide/what-is-outposts.html)                                                                                                                                                                                                                                   | AWS Outposts extiende la infraestructura y los servicios de AWS a ubicaciones locales para un procesamiento de datos local de baja latencia.                                                                                                                                                                                  |
| [Elegir una estrategia de aplicación moderna](https://docs.aws.amazon.com/decision-guides/latest/modern-apps-strategy-on-aws-how-to-choose/modern-apps-strategy-on-aws-how-to-choose.html)                                                                                                                                                    | La guía de toma de decisiones de AWS para una estrategia de aplicación modernas ayuda a las organizaciones a determinar el enfoque de desarrollo más adecuado (sin servidor o Kubernetes) en función de su modelo operativo, estructura de equipo y requisitos de carga de trabajo.                                           |