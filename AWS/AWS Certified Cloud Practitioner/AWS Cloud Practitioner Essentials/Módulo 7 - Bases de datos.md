```table-of-contents
```
---
# Introducción a las bases de datos

AWS ofrece una amplia gama de servicios de bases de datos para satisfacer diversas necesidades de almacenamiento y administración de datos. Estos servicios están diseñados para ser escalables, fiables y fáciles de usar para empresas de todos los tamaños. Los servicios de bases de datos de AWS incluyen opciones para bases de datos relacionales, bases de datos no relacionales, cachés en memoria y servicios diseñados específicamente para casos prácticos como la administración de documentos.

## Modelo de responsabilidad compartida de AWS

El modelo de responsabilidad compartida de AWS agrupa los servicios en tres categorías en función de la propiedad de las tareas administrativas. Estas categorías se dividen en completamente administradas, administradas y no administradas. Los servicios de AWS que verás en este módulo son principalmente de completamente administrados, con algunos servicios administrados, pero no hay servicios no administrados.

- **Servicios completamente administrados**: En el caso de los servicios completamente administrados, AWS gestiona casi todas las tareas operativas, como el aprovisionamiento, el escalado, la aplicación de parches, las copias de seguridad, la optimización del rendimiento y los parches de seguridad. AWS también proporciona supervisión y métricas integradas. Los servicios de bases de datos de AWS completamente administrados solo requieren que las empresas sean responsables del diseño de las estructuras de datos y la administración de los controles de acceso.

- **Servicios administrados**: Con los servicios de bases de datos administradas, AWS gestiona las tareas rutinarias, como las copias de seguridad, la aplicación de parches y el aprovisionamiento de hardware, mientras que las empresas son responsables de configurar las bases de datos, optimizar las consultas y adoptar las decisiones de ajuste del rendimiento.

- **Servicios no administrados**: Con las bases de datos no administradas, las empresas son responsables de instalar, configurar, aplicar parches, además de las tareas de mantenimiento, la seguridad de las bases de datos, las copias de seguridad, la configuración de alta disponibilidad y la optimización del rendimiento.

---

# Servicios de bases de datos relacionales

Las bases de datos relacionales almacenan los datos de una manera que los relaciona con otros datos y utilizan el lenguaje de consulta estructurada, o SQL, para administrar y consultar los datos. Este enfoque almacena los datos de una manera fácilmente comprensible, uniforme y escalable que funciona muy bien para las aplicaciones que requieren una administración de datos estructurada.

AWS ofrece soluciones de bases de datos relacionales completamente administradas que eliminan la carga de la administración de bases de datos y, al mismo tiempo, mantienen una alta disponibilidad y seguridad. Las bases de datos relacionales de AWS son compatibles con motores de bases de datos conocidos, como MySQL, PostgreSQL y Oracle, lo que facilita la migración de las bases de datos existentes a AWS.

## Amazon Relational Database Service (Amazon RDS)

Amazon RDS es un servicio gestionado de bases de datos relacionales que automatiza tareas como copias de seguridad, parches y aprovisionamiento de hardware. Permite elegir entre distintas clases de instancias optimizadas para memoria, rendimiento o E/S, y soporta motores como **Aurora, MySQL, PostgreSQL, SQL Server, MariaDB y Oracle**. Amazon RDS ofrece características de seguridad que incluyen el aislamiento de la red, el cifrado en tránsito y el cifrado en reposo.

**Características principales:**

- **Alta disponibilidad:** despliegues _Multi-AZ_ con conmutación por error automática para minimizar el tiempo de inactividad.

- **Seguridad:** aislamiento en VPC, cifrado en tránsito y en reposo, y copias de seguridad (automáticas o manuales mediante instantáneas).

- **Escalabilidad:** posibilidad de escalar vertical u horizontalmente según la demanda.

- **Monitoreo y rendimiento:** métricas en tiempo real y réplicas de lectura para aliviar la carga de la instancia principal.


**Beneficios:**

- **Optimización de costes:** modelo de pago por uso y reducción de costes operativos al automatizar tareas administrativas.

- **Fiabilidad:** replicación automática entre zonas de disponibilidad.

- **Rendimiento mejorado:** gestión inteligente de recursos y análisis continuo del rendimiento.

- **Seguridad reforzada:** múltiples capas de protección para garantizar la integridad y disponibilidad de los datos.


**Casos de uso:** aplicaciones web, sistemas empresariales y catálogos de productos en plataformas de e-commerce.


### Amazon Aurora

Amazon Aurora es una base de datos relacional administrada y compatible con MySQL y PostgreSQL, diseñada para ofrecer alto rendimiento, disponibilidad y escalabilidad automática. Reduce las operaciones de E/S innecesarias y replica los datos en múltiples zonas de disponibilidad, garantizando durabilidad y tolerancia a fallos. Además, incorpora copias de seguridad automáticas, cifrado en reposo y supervisión continua.

**Casos de uso:**  
Aplicaciones de juegos, gestión de contenido y medios, y análisis en tiempo real.

**Beneficios clave:**

- **Rendimiento y disponibilidad superiores:** hasta 5× más rápido que MySQL y 3× más que PostgreSQL, con almacenamiento distribuido en varios nodos.

- **Gestión automatizada:** el almacenamiento se amplía automáticamente de 10 GB hasta 128 TB y las copias de seguridad continuas se almacenan en Amazon S3.

- **Alta tolerancia a fallos:** seis copias de datos distribuidas en tres zonas de disponibilidad, con 99,99 % de disponibilidad y conmutación automática ante fallos.

---
# Servicios de bases de datos NoSQL

Las bases de datos NoSQL a veces se denominan _bases de datos no relacionales_ porque sus estructuras son diferentes a las de las bases de datos relacionales como Amazon RDS. En lugar de relaciones de fila y columna, las bases de datos NoSQL desarrollan una estructura para los datos que contienen utilizando _pares clave-valor_. Con los pares clave-valor, los datos se organizan en elementos que se identifican mediante claves únicas.

Cada clave tiene uno o más atributos o valores asociados que representan varias características de los datos. Puedes pensar en una clave como una entrada de palabra en un diccionario y en el valor como su definición asociada. No todos los elementos de la tabla tienen que tener los mismos atributos, y puedes añadir o eliminar atributos en cualquier momento.

## Amazon DynamoDB

DynamoDB es un servicio de base de datos NoSQL completamente administrado que proporciona un rendimiento rápido y predecible para las estructuras de datos de valores clave y documentos. Es una opción de base de datos potente e increíblemente rápida para casos prácticos que requieren un esquema flexible, y es ideal para aplicaciones que requieren un alto rendimiento y un escalado perfecto.

DynamoDB escala sin problemas junto con tus datos sin afectar al rendimiento, lo que significa que solo pagas por los recursos que utilizas. También incluye características de seguridad integradas para mejorar la protección y distribuye automáticamente los datos en varios servidores para gestionar la carga de trabajo.

### Casos prácticos

**Casos de uso:**  
Plataformas de videojuegos, servicios financieros y aplicaciones móviles con usuarios globales.

**Beneficios clave:**

- **Escalabilidad automática:** ajusta la capacidad de lectura y escritura según la carga real, sin límites prácticos de tamaño o datos almacenados.

- **Rendimiento constante:** ofrece tiempos de respuesta de milisegundos de un solo dígito incluso a gran escala, distribuyendo los datos automáticamente entre varios servidores y SSD.

- **Alta disponibilidad y durabilidad:** replica los datos en tres instalaciones por región y en múltiples regiones de AWS, logrando una disponibilidad del 99,999 %.

- **Seguridad avanzada:** cifrado automático en reposo y en tránsito, con opciones de gestión de claves para mayor control.

# Servicios de almacenamiento en caché en memoria

Una caché en memoria es una capa de almacenamiento de alta velocidad que guarda temporalmente datos de acceso frecuente en la RAM, permitiendo una recuperación cientos o miles de veces más rápida que desde discos tradicionales.

Antes de consultar la base de datos, las aplicaciones verifican la caché, lo que reduce la carga en el sistema principal y mejora los tiempos de respuesta.

Usos comunes: almacenar datos de sesión, respuestas de API, resultados de consultas y cualquier información repetidamente solicitada por las aplicaciones.

## Amazon ElastiCache

Amazon ElastiCache es un servicio completamente administrado de almacenamiento en caché en memoria compatible con Redis, Valkey y Memcached, diseñado para ofrecer alto rendimiento, baja latencia y alta disponibilidad. Automatiza tareas como el aprovisionamiento, la aplicación de parches, la supervisión y la sustitución de nodos fallidos.

Casos de uso:  
Gestión de datos de sesión, aceleración de consultas a bases de datos y tablas de clasificación en videojuegos.

Beneficios técnicos clave:

- **Alto rendimiento y escalabilidad:** despliegue optimizado de Redis, Valkey o Memcached con capacidad para añadir o eliminar nodos dinámicamente según la demanda.

- **Alta disponibilidad:** supervisión continua de nodos y promoción automática de réplicas ante fallos, reduciendo el tiempo de inactividad a minutos.

- **Replicación Multi-AZ:** distribución de nodos principales y réplicas en múltiples zonas de disponibilidad para tolerancia a fallos e integridad de datos.

- **Seguridad completa:** cifrado en reposo y en tránsito (TLS) para proteger los datos tanto almacenados como transmitidos.

---
# Servicios de bases de datos adicionales

Además de los servicios que has visto hasta ahora, hay algunos servicios especializados en bases de datos de AWS y sus tecnologías de soporte que deberías conocer. En esta lección, examinarás los casos prácticos y los beneficios de Amazon DocumentDB, AWS Backup y Neptune.

## Amazon DocumentDB 

Amazon DocumentDB es una base de datos completamente administrada diseñada para manejar datos semiestructurados mediante documentos JSON con esquemas dinámicos. Es compatible con MongoDB, lo que permite usar sus API, controladores y herramientas existentes sin cambios significativos en el código. 

Permite almacenar, consultar e indexar datos JSON, con escalado automático, copias de seguridad continuas y seguridad de nivel empresarial.

**Casos de uso:** sistemas de gestión de contenido, catálogos e inventarios, y perfiles o personalización de usuarios.

**Beneficios técnicos:**

- **Compatibilidad con MongoDB:** permite migrar aplicaciones existentes con cambios mínimos.

- **Rendimiento y escalabilidad:** almacenamiento que escala automáticamente hasta 64 TB, gestionando millones de solicitudes por segundo.

- **Réplica de lectura:** hasta 15 réplicas para mejorar el rendimiento de lectura en aplicaciones de alto volumen.


---

## AWS Backup  
AWS Backup centraliza y automatiza la protección de datos en múltiples servicios de AWS y entornos locales. Proporciona un panel único para administrar copias de seguridad de EBS, EFS, bases de datos y otros recursos, con cifrado, programación flexible y replicación entre regiones.

**Casos de uso**: recuperación ante desastres, cumplimiento normativo y gestión centralizada de respaldos.

**Beneficios técnicos:**

- **Administración centralizada:** supervisión y programación automatizada de copias de seguridad en todas las cuentas y servicios de AWS.

- **Redundancia entre regiones:** replicación automática de copias de seguridad en regiones secundarias para garantizar recuperación ante desastres.

- **Conformidad y auditoría:** mantiene registros detallados y aplica políticas corporativas de respaldo con trazabilidad completa.
    

---

## Amazon Neptune  
Amazon Neptune es una base de datos de grafos completamente administrada, optimizada para manejar conjuntos de datos altamente conectados y consultas complejas de relaciones. Soporta los modelos de grafos de propiedades y RDF (Resource Description Framework).

**Casos de uso:** redes sociales, detección de fraudes, y sistemas de recomendación o búsqueda.

**Beneficios técnicos:**

- **Diseño especializado para relaciones complejas:** permite consultas avanzadas sobre grafos y análisis de patrones entre nodos.

- **Alto rendimiento y escalabilidad:** maneja miles de millones de relaciones con baja latencia, escalando el almacenamiento automáticamente hasta 64 TB y ofreciendo alta disponibilidad mediante copias de seguridad y conmutación por error automáticas.

---

# Resumen del módulo

En este módulo hemos analizado las capacidades de bases de datos relacionales administradas de Amazon RDS y Amazon Aurora. Has descubierto cómo AWS DMS facilita las migraciones de bases de datos sin problemas y DynamoDB proporciona información sobre las soluciones de bases de datos NoSQL para aplicaciones escalables.

Hemos repasado las capacidades de almacenamiento en caché en memoria de ElastiCache y las características de base de datos de documentos compatibles con MongoDB de Amazon DocumentDB. Examinamos la estrategia integral de protección de datos en todos los servicios de AWS que ofrece AWS Backup. Y, por último, hemos terminado con las potentes capacidades de base de datos de grafos de Neptune enfocadas a las consultas de relaciones complejas.

## Recursos
Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| **Enlace del recurso**                                                                                        | **Descripción**                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Amazon Relational Database Service (Amazon RDS)](https://aws.amazon.com/rds/)                                | Un servicio de bases de datos relacionales que admite varios motores como MySQL, PostgreSQL y Microsoft SQL Server con mantenimiento y copias de seguridad automatizados.                                                      |
| [Seguridad en Amazon RDS](https://aws.amazon.com/rds/features/security/)                                      | Información detallada sobre las configuraciones de seguridad en Amazon RDS.                                                                                                                                                    |
| [Amazon Aurora](https://aws.amazon.com/rds/aurora/)                                                           | Una base de datos nativa en la nube que ofrece un rendimiento y una disponibilidad superiores a los de las bases de datos tradicionales, a la vez que mantiene la compatibilidad con MySQL y PostgreSQL.                       |
| [AWS Database Migration Service (AWS DMS)](https://aws.amazon.com/dms/)                                       | Un servicio que proporciona una migración fluida de bases de datos entre las bases de datos de origen y destino, a la vez que mantiene operativa la base de datos de origen.                                                   |
| [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)                                                           | Un servicio de base de datos NoSQL que proporciona un rendimiento de milisegundos de un único dígito a cualquier escala con seguridad integrada.                                                                               |
| [Amazon ElastiCache](https://aws.amazon.com/elasticache/)                                                     | Un servicio de almacenamiento en caché en memoria que admite Redis, Valkey o Memcached para mejorar el rendimiento de las aplicaciones mediante una recuperación de datos más rápida.                                          |
| [Amazon DocumentDB](https://aws.amazon.com/documentdb/)                                                       | Un servicio de base de datos de documentos compatible con MongoDB diseñado para cargas de trabajo críticas con escalado automático.                                                                                            |
| [Copia de seguridad de Amazon](https://aws.amazon.com/backup/)                                                | Un servicio centralizado para automatizar y administrar las copias de seguridad de los datos en los servicios de AWS y los recursos locales.                                                                                   |
| [Amazon Neptune](https://aws.amazon.com/neptune/)                                                             | Un servicio de base de datos de grafos optimizado para almacenar y consultar relaciones de datos altamente conectadas.                                                                                                         |
| [¿Qué es una base de datos relacional?](https://aws.amazon.com/relational-database/)                          | Una base de datos estructurada que utiliza tablas con esquemas predefinidos, que admite consultas y transacciones complejas a través de SQL para lograr relaciones de datos uniformes.                                         |
| [¿Qué es una base de datos NoSQL?](https://aws.amazon.com/nosql/)                                             | Una base de datos no relacional que ofrece esquemas flexibles y alta escalabilidad para diversos tipos de datos, optimizada para modelos y patrones de datos específicos.                                                      |
| [¿Qué es un servicio de almacenamiento en caché en memoria?](https://aws.amazon.com/caching/aws-caching/)     | Una capa de almacenamiento de datos de alta velocidad que utiliza RAM en lugar de almacenamiento en disco, lo que ofrece una latencia de microsegundos para los datos a los que se accede con frecuencia.                      |
| [Modelo de responsabilidad compartida de AWS](https://aws.amazon.com/compliance/shared-responsibility-model/) | AWS es responsable de la seguridad **de** la nube (infraestructura, hardware, redes, instalaciones), mientras que la clientela es responsable de la seguridad **en** la nube (datos, configuración, administración de acceso). |