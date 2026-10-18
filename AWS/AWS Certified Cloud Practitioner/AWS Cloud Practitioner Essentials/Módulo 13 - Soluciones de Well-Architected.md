
```table-of-contents
```
---

# Servicios especializados de AWS

Los servicios de AWS están diseñados específicamente para casos prácticos determinados. En la siguiente sección, obtendrás más información sobre estos cuatro tipos de servicios especializados de AWS:

- Servicios de desarrollo
- Servicios de aplicaciones empresariales
- Servicios de computación para el usuario final
- Servicios de IoT

## Servicios de desarrollo

AWS ofrece varios servicios para ayudar a los desarrolladores a automatizar las canalizaciones de CI/CD, supervisar y depurar aplicaciones, crear API de GraphQL, y desplegar aplicaciones web y móviles en AWS. Veamos estos servicios con un poco más de detalle.

### AWS CodeBuild
CodeBuild es un servicio de integración continua completamente administrado que compila código fuente, ejecuta pruebas y genera artefactos listos para despliegue. Escala automáticamente según la demanda y solo pagas por el tiempo real de construcción. Ideal si no quieres mantener un servidor de builds eternamente gruñendo.

### AWS CodePipeline
CodePipeline es un servicio de CI/CD administrado que automatiza las etapas de creación, prueba y despliegue. Permite ensamblar flujos de lanzamiento fiables sin tener que gestionar servidores. Básicamente, una cinta transportadora para tu software: entra código, sale despliegue.

> Las canalizaciones de CI/CD automatizan integración, pruebas y despliegues para ofrecer software más rápido y sin drama.

### AWS X-Ray
X-Ray ofrece trazabilidad, depuración y análisis de rendimiento para aplicaciones distribuidas. Ayuda a detectar cuellos de botella, fallos y comportamientos extraños antes de que lo hagan los usuarios… o peor, el jefe.

### AWS AppSync
AppSync es un servicio administrado de GraphQL que permite crear una única API para consultar, manipular y combinar datos desde varios orígenes. Perfecto para conectar frontend y backend sin sufrir tormentas REST infinitas.

> Con GraphQL, los clientes piden solo los datos que necesitan — ni más, ni menos.

### AWS Amplify
Amplify acelera el desarrollo y despliegue de aplicaciones full-stack seguras y escalables. Permite integrar funcionalidades como autenticación, almacenamiento, hosting y APIs sin pelearse con la infraestructura.

> Aplicaciones de pila completa = frontend + backend trabajando en equipo (cuando tienen buen día).

---
## Servicios de aplicaciones empresariales

Estos servicios son ideales para gestionar las necesidades de las aplicaciones empresariales, como las operaciones de servicio al cliente y las promociones por correo electrónico. Repasemos un par de ejemplos.
### Amazon Connect
Las empresas pueden usar este servicio de centro de contacto con tecnología de IA para configurar y operar de manera eficiente un centro de llamadas de servicio al cliente escalable. Amazon Connect ofrece funciones de enrutamiento, grabación y análisis de llamadas, a la vez que se integra a la perfección con otros servicios de AWS.

### Amazon Simple Email Service (Amazon SES)
Amazon SES es un proveedor de servicios de correo electrónico escalable y rentable que se puede integrar en cualquier aplicación para una automatización fiable y de gran volumen del correo electrónico. Ayuda a las empresas a optimizar la entrega de correos electrónicos transaccionales y de marketing, lo que se traduce en una mayor participación de los clientes.

---
## Servicios de computación para el usuario final

En las empresas modernas, es habitual que los departamentos de las TI deban proporcionar acceso remoto a recursos como escritorios y aplicaciones virtuales. Analicemos algunos servicios de AWS que pueden usarse para configurar estos entornos para el personal.

### Amazon AppStream 2.0
AppStream 2.0 es un servicio completamente administrado que transmite aplicaciones desde la nube de forma directa a cualquier dispositivo compatible. Esto incluye aplicaciones de software como servicio (SaaS) y aplicaciones convertidas de escritorio a SaaS sin revisiones de código. Esto proporciona acceso instantáneo a un software potente sin requerir un hardware local de alta gama.

>  En SaaS, las aplicaciones se alojan en la nube y se accede a ellas a través de internet, sin requerir una instalación o un mantenimiento local.

### Amazon WorkSpaces
WorkSpaces es un servicio de computación de escritorio basado en la nube y completamente administrado. 

Con WorkSpaces, el personal puede acceder de forma segura a su entorno de trabajo desde cualquier dispositivo con conexión a internet. 

El personal puede hacer las mismas tareas que si estuviera en un equipo físico de la oficina, mientras que las empresas pueden beneficiarse de la rentabilidad y la facilidad de administración.

### Amazon WorkSpaces Secure Browser (anteriormente Amazon WorkSpaces Web)

WorkSpaces Secure Browser es un navegador empresarial remoto completamente administrado. Proporciona un entorno protegido para que el personal acceda a sitios web privados, aplicaciones SaaS e internet pública. 

Con WorkSpaces Secure Browser, los departamentos de las TI no deben administrar software de cliente especializado, infraestructuras o conexiones de VPN.

---
## Servicios de IoT

El internet de las cosas (IoT) es una red de dispositivos físicos conectados con sensores y software que recopilan e intercambian datos a través de internet. Estos dispositivos se pueden supervisar y controlar de forma remota para aumentar la eficiencia, ofrecer nuevos servicios y mejorar la calidad de vida.

### AWS IoT Core
AWS IoT Core es un servicio de nube administrado que se utiliza para conectar de forma segura dispositivos físicos con aplicaciones en la nube. Ayuda a crear soluciones de IoT eficientes al agilizar el complejo proceso de ingesta, procesamiento y actuación sobre los datos del dispositivo. Las conexiones y los datos de los dispositivos están protegidos con autenticación mutua y cifrado de extremo a extremo, y se puede elegir entre varios protocolos de comunicación.

Algunas soluciones de IoT incluyen las siguientes:

- **Cámaras de seguridad inteligentes:** supervisión doméstica que envía alertas a tu teléfono
- **Comederos inteligentes para mascotas:** un comedero para mascotas que puedes controlar de forma remota
- **Sistemas de riego inteligentes:** una máquina de lluvia que ajusta el riego según las condiciones climáticas y del suelo

---
# AWS Well-Architected Framework
## Aprendizajes clave: pilares del Well-Architected Framework

| Pilar                          | Descripción                                                                                                                                                       |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Excelencia operativa**       | Se centra en operaciones eficientes, monitorización adecuada, automatización y mejora continua. Que todo funcione, se mida y se refine sin drama.                 |
| **Seguridad**                  | Protege sistemas y datos aplicando buenas prácticas como mínimo privilegio, cifrado e integridad. Básicamente: cero confianza, cero sustos.                       |
| **Fiabilidad**                 | Garantiza que el sistema se recupere ante fallos y pueda adaptarse a cambios de carga o requisitos. Que no se rompa… y si se rompe, que se levante rápido.        |
| **Eficiencia del rendimiento** | Optimiza el uso de los recursos adecuados según la carga y las necesidades del sistema. Ni infra sobredimensionada ni servidores sudando como en verano.          |
| **Optimización de costes**     | Minimiza gastos mediante aprovisionamiento inteligente y uso eficiente de recursos. "¿De verdad hace falta esa instancia XXL para servir tres peticiones al día?" |
| **Sostenibilidad**             | Diseña sistemas energéticamente eficientes y responsables con el entorno. Tecnología sí, pero sin quemar el planeta en el proceso.                                |

## Herramienta de AWS Well-Architected

La Herramienta de AWS Well-Architected (Herramienta de AWS WA) es un servicio gratuito que ayuda a evaluar y mejorar las cargas de trabajo en la nube en función de los seis pilares clave.

Ofrece revisiones de la carga de trabajo, seguimiento de hitos y lentes personalizados para evaluaciones y planes de mejora a medida. 

Está integrado con los servicios de AWS, como AWS Identity and Access Management (AWS IAM) y las API, y permite la colaboración en equipo y el seguimiento continuo del progreso. 

La Herramienta AWS WA es ideal para profesionales de la arquitectura e ingeniería, así como equipos de conformidad, y fomenta las revisiones de arquitectura coherentes, procesables y bien documentadas.

>[!tip] ## Optimización de una arquitectura en la nube
>![[Pasted image 20251125121419.png]]
>
> Un negocio online de floristería necesita una arquitectura en la nube capaz de soportar picos extremos de demanda (San Valentín, Día de la Madre, caos floral en general).
> 
> ### Situación inicial
> - Arquitectura clásica de e-commerce: EC2 para servidor web, RDS para base de datos, S3 para imágenes.
> - Funciona… pero en fechas punta suda frío.
> 
> ### Excelencia operativa
> - Automatización del escalado con EC2 Auto Scaling y IaC.
> - Recuperación automática para evitar que una instancia caída arruine ventas masivas.
> - **Mejora clave:** EC2 Auto Scaling.
> 
> ### Seguridad
> - Base segura con VPC, pero todavía hay trabajo:
>   - Parcheo regular.
>   - IAM mínimo privilegio.
>   - Cifrado en tránsito y en reposo.
> - **Mejora clave:** reforzar cifrado e IAM.
> 
> ### Fiabilidad
> - Despliegue en múltiples AZ ✨ bien.
> - Añadir monitorización con CloudWatch y acciones automáticas.
> - **Mejora clave:** usar Amazon CloudWatch.
> 
> ### Rendimiento
> - Usar AWS Compute Optimizer para ajustar tamaños de EC2/RDS.
> - Lambda ya cubre tareas event-driven (procesar imágenes sin llorar por servidores).
> - CloudFront mejora la entrega global de imágenes.
> - **Mejora clave:** AWS Compute Optimizer.
> 
> ### Optimización de costes
> - Migrar de instancias On-Demand a Spot y Savings Plans.
> - Controlar gasto con AWS Budgets y Cost Explorer (antes de que Finanzas grite).
> - **Mejora clave:** Savings Plans, Budgets y Cost Explorer.
> 
> ### Sostenibilidad
> - Ajustar tamaños, usar serverless y eliminar recursos innecesarios.
> - Beneficio doble: menos coste y menor impacto ambiental.
> - **Mejora clave:** informe de coste y uso de AWS.
> 
> ![[Pasted image 20251125121130.png]]

---
# Casos prácticos especializados

## Backend web sin servidor supervisado mediante X-Ray

Se trata de un backend web sin servidor habitual con X-Ray que supervisa el entorno. Para revisar los componentes de esta solución, haz clic en cada uno de los tres marcadores numerados.

![[Pasted image 20251125121925.png]]

1. **Recibir tráfico**: Una Amazon API Gateway recibe y valida las solicitudes HTTP. 
2. **Desencadenar la función de Lambda**: La API Gateway desencadena una función de Lambda que envía solicitudes a Amazon DynamoDB.
3. **Supervisar el tráfico**: X-Ray hace un seguimiento de las solicitudes a través de API Gateway, Lambda y DynamoDB y las devuelve al cliente. Esto ayuda a los desarrolladores a solucionar cualquier problema.

## Sitio web estático sin servidor con formulario de contacto

Esta configuración sin servidor muestra un sitio web estático con un formulario de contacto alojado en Amazon S3. Para revisar los componentes de esta solución, haz clic en cada uno de los tres marcadores numerados.

![[Pasted image 20251125122041.png]]
1. **Aceptar las entradas de clientes**: La clientela envía sus preguntas mediante un formulario de contacto que se encuentra en un sitio web estático de Amazon S3.
2. **Recibir la solicitud**: Una API Gateway recibe y valida la solicitud del formulario de contacto.
3. **Enviar el correo electrónico**: A continuación, la API Gateway invoca una función de Lambda que envía un correo electrónico a la persona propietaria de la empresa mediante Amazon SES.

## Servicio de atención al cliente con opción de devolución de llamada

Esta solución de atención al cliente ofrece un canal alternativo y una opción de devolución de llamadas para que la clientela pueda evitar largos tiempos de espera. Para revisar los componentes de esta solución, haz clic en cada uno de los tres marcadores numerados.

![[Pasted image 20251125122233.png]]

1. **Iniciar contacto**: Una persona llama o envía un mensaje de texto a un centro de atención al cliente. Las llamadas se pasan al sistema de respuestas por voz interactivo (IVR) de Amazon Connect. Los mensajes de texto se envían a Amazon Connect desde CloudFront.
2. **Conectarse con agente**: Amazon Connect intenta conectar al cliente con una persona activa del equipo de agentes.
3. **Ofrecer opciones**: En el caso de las llamadas con largas colas de espera, la clientela puede optar por recibir una llamada de agente o puede cambiar a mensajes de texto mediante una función de Lambda.

---
# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| Enlace del recurso                                                                                                                                                                                                                                                                                   | Descripción                                                                                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AWS CodeBuild](https://aws.amazon.com/codebuild/)                                                                                                                                                                                                                     | Crea scripts para compilar, probar y empaquetar tu código.                                                                                                                                                                                           |
| [AWS CodePipeline](https://aws.amazon.com/codepipeline/)                                                                                                                                                                                                               | Automatiza y supervisa las canalizaciones de CI/CD.                                                                                                                                                                                                  |
| [AWS X-Ray](https://aws.amazon.com/xray/)                                                                                                                                                                                                                              | Supervisa y depura las aplicaciones.                                                                                                                                                                                                                 |
| [AWS AppSync](https://aws.amazon.com/appsync/)                                                                                                                                                                                                                         | Conecta aplicaciones a varios orígenes de datos mediante una única solicitud de API de GraphQL.                                                                                                                                                      |
| [AWS Amplify](https://aws.amazon.com/amplify/)                                                                                                                                                                                                                         | Desarrolla, despliega y administra rápidamente aplicaciones de pila completa en AWS.                                                                                                                                                                 |
| [Amazon Connect](https://aws.amazon.com/connect/)                                                                                                                                                                                                                      | Administra las operaciones de servicio al cliente con inteligencia artificial.                                                                                                                                                                       |
| [Amazon SES](https://aws.amazon.com/ses/)                                                                                                                                                                                                                              | Usa la automatización para enviar grandes volúmenes de correos electrónicos transaccionales y de marketing.                                                                                                                                          |
| [Amazon AppStream 2.0](https://aws.amazon.com/appstream2/)                                                                                                                                                                                                             | Transmite aplicaciones de escritorio y basadas en la nube a las personas que disponen de dispositivos compatibles.                                                                                                                                   |
| [Amazon WorkSpaces](https://aws.amazon.com/workspaces-family/workspaces/)                                                                                                                                                                                              | Proporciona al personal escritorios virtuales seguros.                                                                                                                                                                                               |
| [Amazon WorkSpaces Secure Browser](https://aws.amazon.com/workspaces-family/secure-browser/)                                                                                                                                                                           | Proporciona al personal un acceso seguro a sitios y aplicaciones basados en la web.                                                                                                                                                                  |
| [AWS IoT Core](https://aws.amazon.com/iot-core/)                                                                                                                                                                                                                       | Conecta de forma segura los dispositivos con las aplicaciones en la nube para crear soluciones de IoT.                                                                                                                                               |
| [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/)                                                                                                                                                                                          | AWS Well-Architected Framework proporciona un enfoque estructurado para diseñar y operar una infraestructura segura, de alto rendimiento, resistente y eficiente para las aplicaciones y cargas de trabajo en AWS, guiándose por seis pilares clave. |
| [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)                                                                                                                                                            | Este sitio web es la documentación oficial de AWS Well-Architected Framework.                                                                                                                                                                        |
| [¿Qué es la Herramienta de AWS Well-Architected?](https://docs.aws.amazon.com/wellarchitected/latest/userguide/intro.html)                                                                                                                                             | La Herramienta de AWS Well-Architected proporciona un proceso uniforme para medir tu arquitectura mediante las prácticas recomendadas de AWS.                                                                                                        |
| [Centro de arquitectura de AWS](https://aws.amazon.com/architecture/?cards-all.sort-by=item.additionalFields.sortDate&cards-all.sort-order=desc&awsf.content-type=*all&awsf.methodology=*all&awsf.tech-category=*all&awsf.industries=*all&awsf.business-category=*all) | El Centro de arquitectura de AWS proporciona arquitecturas de referencia y prácticas recomendadas para crear soluciones seguras, eficientes y escalables en AWS.                                                                                     |
| [Blog de arquitectura de AWS:](https://aws.amazon.com/blogs/architecture/)                                                                                                                                                                                             | El Blog de arquitectura de AWS comparte información técnica y prácticas recomendadas para crear soluciones eficaces en AWS.                                                                                                                          |