```table-of-contents
```
---
# Introducción

La migración a la nube se refiere al proceso de trasladar los activos digitales, los recursos de las TI, las aplicaciones y las bases de datos de la organización desde la infraestructura local a la nube de AWS. Esto implica la planificación estratégica, la implementación y la administración continua para lograr una transición fluida y correcta. No suele ser un traslado _de una sola vez_. En el caso de grandes migraciones, las empresas pueden migrar por fases o etapas.

## Tres fases del proceso de migración

AWS ayuda a guiar a las empresas durante el proceso de migración, que se puede dividir en tres fases secuenciales. 

![[Pasted image 20251124172341.png]]
### 1. Evaluación

En esta fase, creas el caso empresarial para la migración y evalúas la preparación. 

Uno de los servicios que se utilizan en esta fase es el **Evaluador de la migración**.

### 2. Traslado

En esta fase, preparas a la organización y trasladas los recursos necesarios para la migración. 

Dos servicios que puedes utilizar en esta fase son **AWS Application Discovery Service** y **AWS Migration Hub.** Si bien AWS Migration Hub te ayuda a movilizar los recursos, puedes usarlo como un lugar único para administrar también durante la fase de migración y modernización.

### 3. Migración y modernización

En esta fase, utilizas la estrategia, el plan y las prácticas recomendadas para migrar y modernizar. 

Las herramientas de ayuda incluyen **AWS Application Migration Service** y **AWS Database Migration Service (AWS DMS)**. 

Si vas a transferir datos, puedes usar **AWS DataSync**, **AWS Transfer Family** y **AWS Snow Family**.

---
# AWS Cloud Adoption Framework

Migrar a AWS implica planificación cuidadosa, coordinación entre múltiples equipos y adopción de buenas prácticas. Puede parecer complicado al inicio, y aquí es donde entra AWS CAF.

AWS Cloud Adoption Framework (CAF) reúne la experiencia y recomendaciones de AWS para ayudar a las organizaciones en su transición a la nube. Este marco acelera la migración, organiza recursos y facilita la alineación entre áreas técnicas y de negocio.

## Beneficios clave

- Reduce riesgos y mejora la transparencia corporativa.
- Permite crear nuevos productos y servicios para aumentar ingresos.
- Reduce costes operativos, mejora productividad y experiencia del cliente.
## ¿Cuándo usarlo?

- Migración de infraestructura y aplicaciones heredadas.
- Optimización de procesos y operaciones.
- Creación de nuevos modelos empresariales basados en la nube.

## Las 6 perspectivas de AWS CAF (cada una con distintos roles):

La migración requiere considerar varios grupos dentro de la organización. AWS CAF organiza estas áreas en seis perspectivas:

| Perspectiva     | Enfoque                                                                     | Roles habituales                                                                                      |
| --------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Empresas**    | Alineación de TI con objetivos del negocio y priorización de iniciativas.   | Gerentes comerciales, financieros, propietarios de presupuesto, stakeholders estratégicos.            |
| **Personas**    | Gestión del cambio, nuevos roles, capacidades y formación.                  | Recursos Humanos, personal técnico, gestores de personal.                                             |
| **Gobernanza**  | Control de riesgos, métricas, estrategia y gestión de inversión en la nube. | CIO, gerentes de programas, arquitectos empresariales, analistas empresariales, gerentes de carteras. |
| **Plataforma**  | Arquitectura, patrones, diseño e implementación de soluciones en la nube.   | CTO, gerentes de TI, arquitectos de soluciones.                                                       |
| **Seguridad**   | Controles, auditoría, cumplimiento y protección del entorno.                | CISO, gerentes de seguridad TI, analistas de seguridad.                                               |
| **Operaciones** | Gestión operativa continua, soporte y mantenimiento.                        | Gerentes de operaciones TI, gerentes de soporte TI.                                                   |

---
# Siete estrategias de migración

| Estrategia | Descripción breve | Cuándo se usa |
|------------|------------------|---------------|
| **Reubicar** | Cambiar la ubicación del alojamiento a la nube sin modificaciones técnicas relevantes. | Cuando las aplicaciones ya están en VM o contenedores y solo necesitan moverse. |
| **Realojar (Lift & Shift)** | Migrar sin cambios. | En migraciones grandes y rápidas donde prima la velocidad. |
| **Redefinir la plataforma (Lift, Tinker & Shift)** | Migrar con optimizaciones menores sin cambiar la arquitectura. | Para obtener mejoras rápidas sin rediseñar la app. |
| **Refactorizar (Rearquitectura)** | Rediseñar usando capacidades nativas de la nube. | Para añadir escalabilidad, rendimiento o nuevas funciones imposibles en el entorno actual. |
| **Recomprar** | Cambiar a un modelo SaaS. | Cuando es más eficiente sustituir software existente por uno en la nube. |
| **Retener** | Conservar ciertas aplicaciones en el entorno original. | Si no están listas para migrar o no aportan valor moviéndolas ahora. |
| **Retirar** | Eliminar aplicaciones innecesarias. | Cuando ya no aportan valor o están obsoletas. |


---
# Servicios y herramientas de migración

## Fase Evaluación

En la fase Evaluación, es importante contar con las herramientas adecuadas para crear el caso empresarial para la migración. Es en este punto donde Evaluador de la migración puede ayudar.

### Evaluador de la migración

Evaluador de la migración es un servicio que te ayuda a crear un caso empresarial para la planificación y la migración a la nube de AWS. 

Lo hace mediante un enfoque basado en datos que analiza el estado actual, el estado objetivo y desarrolla un plan de preparación para la migración con los costes proyectados de la nube.

**Beneficios:** 
- Eliminar las conjeturas a la hora de migrar. 
- Visibilidad de varias situaciones rentables de migración a la nube.
- Información sobre la reutilización de las licencias de software existentes

**Casos prácticos:** 
- Hacer un descubrimiento amplio
- Tomar una instantánea de tu presencia local actual para ajustar las licencias
- Ver las dependencias de los servidores 
- Obtener visibilidad en varias situaciones de migración
- Estimar y reducir los costes de la nube


## Fase Traslado

### Application Discovery Service

Application Discovery Service descubre el inventario y las conexiones de los servidores locales. 

Reúne los detalles de configuración, rendimiento y conexión de los servidores y las bases de datos para crear un plan de migración detallado.

**Beneficios:** 
- Instantánea completa de tu inventario local
- Integrar los datos de descubrimiento con otros servicios, como Migration Hub, y proteger los datos que recopila Application Discovery Service.

**Casos prácticos:** 
- Hacer el descubrimiento y el inventario
- Asignar las conexiones y las dependencias
- Generar un plan de migración

### Migration Hub

Migration Hub es un centro único que te guía desde el descubrimiento hasta la evaluación, la planificación y la ejecución de la migración. 

Proporciona herramientas, orientación y recomendaciones automatizadas para colaborar con tu equipo y hacer un seguimiento de la migración.

**Beneficios:**
- Un solo lugar al que acudir para migrar 
- Orientación de profesionales en forma de plantillas de viaje de preceptivas
- Ahorro de costes, ya que el uso de Migration Hub es gratuito

**Casos prácticos** 
- Evaluar y planificar la migración
- Completar la migración 
- Colaborar con los equipos
- Iniciativas de modernización, como la refactorización rápida de aplicaciones.

## Fase Migración y modernización

A medida que empieces a mover recursos a la nube, puedes seguir usando Migration Hub para hacer un seguimiento de tu progreso. También puedes usar Migration Hub durante la migración para modernizar las aplicaciones.

### Application Migration Service

Application Migration Service es una herramienta para mover y mejorar tus aplicaciones locales y basadas en la nube. Ayuda a la clientela a optimizar, acelerar y reducir el coste de la migración y modernización de las aplicaciones.

**Beneficios:** los beneficios incluyen el soporte para migrar desde cualquier infraestructura de origen que ejecute un sistema operativo (SO) compatible. Permite modernizar las aplicaciones durante la migración. Puedes mantener las operaciones empresariales habituales durante el proceso de replicación de las aplicaciones y también reducir los costes mediante el uso de una sola herramienta para una amplia gama de aplicaciones.

**Casos prácticos:** puedes usar Application Migration Service para aplicaciones locales que se ejecutan en servidores o infraestructuras físicas, aplicaciones basadas en la nube o para moverte entre regiones de AWS. También puedes usarlo para modernizar las aplicaciones.

### Socios con competencias en migración y modernización de AWS

Al migrar a la nube de AWS, no tienes que hacerlo a solas si necesitas ayuda y experiencia. Puedes trabajar con el programa de socios con competencias en AWS. Puedes buscar socios de servicio de migración y modernización de AWS que se especialicen en fases específicas de la migración o en el tipo de ayuda que necesitas. Para obtener más información, consulta [Socios con competencias en migración y modernización de AWS](https://aws.amazon.com/migration/partner-solutions/?blog-posts-cards.sort-by=item.additionalFields.createdDate&blog-posts-cards.sort-order=desc&partner-case-studies-cards.sort-by=item.additionalFields.sortDate&partner-case-studies-cards.sort-order=desc).

---
# Migraciones de bases de datos

> La migración de la base de datos a la nube puede brindar la oportunidad de rediseñar y mejorar la arquitectura de tu base de datos. 

Dado que los requisitos y los sistemas heredados cambian con el tiempo, también puedes considerar la posibilidad de migrar a un servicio de base de datos administrada por AWS o a una base de datos de código abierto para reducir los costes de licencias. 

Es bastante sencillo migrar datos de un servidor a otro cuando ambos utilizan el mismo motor de base de datos, lo que se conoce como **migración homogénea**. 

Pasar a un motor diferente, o hacer una **migración heterogénea**, es más complejo y puede requerir cambios en la aplicación. 

La buena noticia es que, independientemente de que tu migración sea homogénea (de un tipo de base de datos al mismo tipo) o heterogénea (de un tipo de base de datos a otro tipo diferente), existen servicios de AWS que te ayudarán.


## AWS DMS

AWS Database Migration Service (AWS DMS) permite migrar bases de datos de forma rápida y segura, así como hacer tareas continuas de replicación de datos para bases de datos y almacenes de datos activos. 

Proporciona una forma de planificar, evaluar, convertir y migrar bases de datos, incluso con almacenes de datos, en una herramienta central.

**Beneficios:** 
- Alta disponibilidad y un bajo tiempo de inactividad 
- Compatible con migraciones homogéneas y heterogéneas
- Permite migrar bases de datos del tamaño de un terabyte a bajo coste.

**Casos prácticos:** 
- Migrar a bases de datos administradas
- Eliminar los costes de licencias
- Replicar los cambios continuos en tu base de datos 
- Mejorar la integración con los lagos de datos.


Si planeas pasar de una base de datos comercial a una de código abierto durante la migración, debes considerar cómo recrear elementos como el esquema y la estructura de datos en el nuevo motor. Hacerlo manualmente puede ser lento y complejo. Para automatizar gran parte del proceso y simplificar la conversión entre motores diferentes, puedes usar AWS Schema Conversion Tool (AWS SCT).

## AWS SCT

AWS SCT permite convertir esquemas de bases de datos y objetos de código (como procedimientos, vistas y funciones almacenados) de un motor de base de datos a otro. 

AWS SCT puede incluso proporcionarte estimaciones del esfuerzo que supone una conversión, lo que ayuda a planificar.

**Beneficios**
- Automatiza el análisis, recomendaciones y conversión de esquemas.
- Compatible con múltiples bases de datos y servicios de análisis.
- Reduce significativamente el esfuerzo manual, ahorrando semanas o meses de trabajo.

**Casos prácticos**
- Migraciones de bases de datos comerciales a código abierto.
- Migración de grandes cargas de trabajo de almacenes de datos.
- Modernización o actualización de esquemas existentes.

---
# Transferencia de datos a y desde la nube de AWS

Al migrar datos a la nube de AWS, hay algunas consideraciones que debes tener en cuenta. 

Tienes que garantizar:
- La seguridad (¿llegará allí de forma segura?)
- La validación de los datos (¿llegará de una sola pieza?) 
- La programación (¿cuándo es el mejor momento?)

También debes confirmar los requisitos de ancho de banda. Para la mayoría de las cargas de trabajo de migración de datos, AWS DataSync será adecuado.

## AWS DataSync

AWS DataSync optimiza y **acelera** las migraciones de datos seguras. Administra las cargas de trabajo de movimiento de datos con limitación del ancho de banda, programación de la migración, filtrado de tareas e informes de tareas.

DataSync simplifica y acelera la transferencia de grandes cantidades de datos entre el almacenamiento local y los servicios de almacenamiento de AWS, como Amazon Simple Storage Service (Amazon S3). 

Automatiza muchos aspectos del proceso de transferencia, incluida la ejecución de instancias, el cifrado y la optimización de la red.

**Beneficios**
- Optimiza y acelera migraciones de datos seguras.
- Gestiona tareas con limitación de ancho de banda, programación, filtrado e informes.
- Permite replicación rápida de datos.

**Casos prácticos**
- Migración de datos.
- Archivado de datos inactivos.
- Gestión de flujos de trabajo híbridos.

El siguiente servicio proporciona **soporte completamente administrado** para las transferencias de archivos hacia y desde Amazon S3. Es compatible con muchos protocolos de transferencia diferentes. Un protocolo de transferencia es un conjunto de reglas o estándares que rigen la forma en que se trasladan los datos de una ubicación a otra.

## AWS Transfer Family

AWS Transfer Family permite administrar y compartir datos sin problemas mediante transferencias de archivos sencillas, **seguras** y escalables. 

Este servicio proporciona un soporte completamente administrado para transferencias seguras de archivos a través de FTP, Secure File Transfer Protocol (SFTP), File Transfer Protocol Secure (FTPS) y otros protocolos.

Te ayuda a transferir archivos directamente hacia y desde los servicios de almacenamiento de AWS, como Amazon S3 y Amazon EFS.

**Beneficios**  
- Simplifica la configuración y administración de transferencias de archivos  
- Reduce la necesidad de gestionar infraestructura compleja  
- Proporciona transferencia segura con cifrado y autenticación  
- Diseñado para escalar y agilizar flujos de trabajo  

**Casos prácticos**  
- Modernizar y administrar transferencias de archivos  
- Simplificar el intercambio de datos con personal y socios  
- Integrar datos comerciales transaccionales en un lago de datos unificado  


Quizá te acuerdas de Direct Connect del módulo de redes. Con el ancho de banda de una conexión exclusiva, también es una excelente solución para trasladar tus datos en línea a la nube de AWS durante la migración.

## Direct Connect

AWS Direct Connect es un servicio que te permite establecer una conexión privada específica entre la red y la nube virtual privada (VPC) en la nube de AWS. 

Como es tu conexión exclusiva, es una forma rápida, fiable y segura de transferir datos o archivos.

**Beneficios:** Direct Connect ayuda a reducir los costes de red y a aumentar la cantidad de ancho de banda.

---
# Transferencia de datos sin conexión

En esta lección, revisarás un servicio para transferir datos sin conexión cuando AWS DataSync no cumpla los requisitos para transferir datos en línea.

Gran parte de la clientela prefiere las migraciones en línea, pero hay algunas personas que necesitan transferir datos sin conexión. Un ejemplo sería si el ancho de banda es limitado o en ubicaciones remotas sin internet y Direct Connect no es una opción. O, en casos de grandes volúmenes de datos, enviar petabytes de datos a través de internet requeriría más tiempo que simplemente enviar un dispositivo físico.

## Dispositivos Snowball Edge Storage Optimized

Los dispositivos AWS Snowball Edge Storage Optimized son una excelente solución para la migración de datos sin conexión cuando la conexión a internet puede no ser una opción.

Estos dispositivos ofrecen almacenamiento NVMe de alto rendimiento, lo que permite simplificar las migraciones de datos de varios petabytes desde ubicaciones locales a AWS.

**Beneficios:** los beneficios incluyen ofrecer un mejor rendimiento de computación y una mayor capacidad de almacenamiento con gigabytes de datos por segundo para las cargas de trabajo de migración de datos con requisitos sin conexión.

**Casos prácticos:** puedes usar dispositivos Snowball Edge para la migración de datos cuando se requiera la migración sin conexión. También se pueden usar para la computación periférica cuando se requiera un dispositivo seguro y robusto.

---

# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos en la tabla que aparece a continuación.

|Enlace del recurso|Descripción|
|---|---|
|[Las tres fases de la migración](https://docs.aws.amazon.com/prescriptive-guidance/latest/strategy-migration/overview.html)|Al hacer una migración a gran escala, normalmente hay tres fases: evaluación, traslado y, en la última fase, migración y modernización.|
|[AWS Cloud Adoption Framework](https://aws.amazon.com/cloud-adoption-framework/)|AWS CAF es un marco de trabajo que aporta la experiencia y las prácticas recomendadas de AWS a las empresas que se preparan para migrar a la nube de AWS. El marco de trabajo proporciona herramientas para ayudar a acelerar el proceso de migración, organizar los recursos y alinear la administración durante la transición.|
|[Siete estrategias de migración (7 R)](https://docs.aws.amazon.com/prescriptive-guidance/latest/large-migration-guide/migration-strategies.html)|Al migrar a la nube, hay siete estrategias de migración comunes que se pueden utilizar. Con reubicar, realojar, redefinir la plataforma, refactorizar, recomprar, retener y retirar|
|[Evaluador de la migración](https://aws.amazon.com/migration-evaluator/)|Evaluador de la migración es un servicio de evaluación de migración que te ayuda a crear un caso empresarial para la planificación y la migración a la nube de AWS. Lo hace mediante un enfoque basado en datos que analiza el estado actual y el estado objetivo, y desarrolla un plan de preparación para la migración con los costes proyectados de la nube.|
|[AWS Application Discovery Service](https://aws.amazon.com/application-discovery/)|Application Discovery Service descubre el inventario y las conexiones de los servidores locales. Reúne los detalles de configuración, rendimiento y conexión de los servidores y las bases de datos para crear un plan de migración detallado.|
|[AWS Application Migration Service](https://aws.amazon.com/application-migration-service/)|Application Migration Service es una herramienta para migrar y mejorar tus aplicaciones locales y basadas en la nube. Ayuda a simplificar, acelerar y reducir el coste de la migración y modernización de las aplicaciones.|
|[AWS Migration Hub](https://aws.amazon.com/migration-hub/)|Migration Hub es un centro único que te guía desde el descubrimiento hasta la evaluación, la planificación y la implementación de la migración. Proporciona herramientas, orientación y recomendaciones automatizadas para colaborar con tu equipo y hacer un seguimiento de la migración.|
|[AWS Database Migration Service (AWS DMS)](https://aws.amazon.com/dms/?nc=sn&loc=1)|AWS DMS permite migrar las bases de datos de forma rápida y segura a la nube de AWS. Proporciona una forma de planificar, evaluar, convertir y migrar bases de datos, incluso con almacenes de datos, en una herramienta central.|
|[Herramienta de conversión de esquemas de AWS (AWS SCT)](https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Welcome.html)|AWS SCT es un servicio que permite convertir esquemas de bases de datos y objetos de código (como procedimientos, vistas y funciones almacenados) de un motor de base de datos a otro.|
|[AWS DataSync](https://aws.amazon.com/datasync/)|AWS DataSync se ha diseñado específicamente para automatizar y acelerar las migraciones de datos seguras. DataSync administra las cargas de trabajo de movimiento de datos con limitación del ancho de banda, programación de la migración, filtrado de tareas e informes de tareas. También proporciona una rápida replicación de los datos.|
|[AWS Transfer Family](https://aws.amazon.com/aws-transfer-family/)|Transfer Family permite administrar y compartir datos sin problemas mediante transferencias de archivos sencillas, seguras y escalables. Este servicio proporciona un soporte completamente administrado para transferencias seguras de archivos a través de SFTP, FTPS, FTP y otros. Te ayuda a transferir archivos directamente hacia y desde los servicios de almacenamiento de AWS, como Amazon S3 y Amazon EFS.|
|[AWS Direct Connect](https://aws.amazon.com/directconnect/)|Direct Connect es un servicio de nube que puedes usar para establecer una conexión de red privada y exclusiva entre la red local y AWS.|
|[AWS Snow Family](https://docs.aws.amazon.com/snowball/latest/developer-guide/device-differences.html)|Los dispositivos AWS Snowball Edge Storage Optimized son una excelente solución para la migración de datos sin conexión cuando la conexión a internet puede no ser una opción. Los dispositivos Snowball Edge Storage Optimized ofrecen almacenamiento de alto rendimiento y permiten simplificar las migraciones de datos de varios petabytes desde ubicaciones locales a AWS.|