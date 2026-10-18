```table-of-contents
```
---
# Introducción al almacenamiento

AWS ofrece muchas soluciones para almacenar, acceder, administrar y hacer copias de seguridad de los datos en la nube. Estos sistemas de almacenamiento virtual eliminan la necesidad de hardware físico en el centro de datos y, al mismo tiempo, ofrecen la flexibilidad de escalar a medida que cambian tus necesidades. AWS ofrece tres tipos distintos de almacenamiento en la nube para cumplir diferentes requisitos y necesidades de aplicaciones: almacenamiento en bloques, almacenamiento de objetos y almacenamiento de archivos.

## Almacenamiento en bloques

El almacenamiento en bloques proporciona volúmenes de almacenamiento persistentes y de baja latencia a nivel de bloque que se conectan a instancias de EC2, como discos duros físicos. 

Los volúmenes de almacenamiento en bloques se pueden cifrar, hacer copias de seguridad mediante instantáneas y modificar mientras están en uso sin interrumpir la instancia. 

AWS ofrece dos servicios principales de almacenamiento en bloques:
- _Almacén de instancias de Amazon EC2_  
    Un almacenamiento en bloques no administrado, no persistente y de alto rendimiento que se adjunta directamente a las instancias de EC2 para los datos temporales.
- _Amazon Elastic Block Store (EBS)_  
    Un servicio administrado que proporciona volúmenes de almacenamiento en bloques persistentes para instancias de EC2 y ofrece varios tipos para diferentes cargas de trabajo

## Almacenamiento de objetos

El almacenamiento de objetos es una arquitectura de almacenamiento de datos que administra los datos como objetos en un espacio de direcciones plano. 

Ofrece escalabilidad ilimitada para que puedas almacenar grandes cantidades de datos sin estructurar y sin preocuparte por las restricciones de capacidad. El almacenamiento de objetos proporciona capacidades de metadatos mejoradas para brindar una administración, búsqueda y análisis de datos más eficientes en conjuntos de datos masivos.

Esta solución es el servicio principal de almacenamiento de objetos de AWS:
- _Amazon Simple Storage Service (S3)_  
    Un servicio de almacenamiento de objetos escalable y completamente administrado para almacenar y recuperar los datos necesarios desde cualquier lugar.

## Almacenamiento de archivos

Los servicios de almacenamiento de archivos de AWS proporcionan sistemas de archivos compartidos accesibles a través de redes, de forma que varios usuarios y aplicaciones pueden acceder a los mismos datos a la vez. 

Ofrecen escalabilidad y flexibilidad para que puedas ampliar la capacidad de almacenamiento a medida que aumentan las necesidades sin tener que administrar la infraestructura física. AWS ofrece dos servicios principales de almacenamiento de archivos:

- _Amazon Elastic File System (EFS)_  
    Un sistema de archivos NFS escalable y completamente administrado para su uso con los servicios de la nube de AWS y los recursos locales.
- _Amazon FSx_  
    Un servicio de almacenamiento de archivos completamente administrado para sistemas de archivos populares como Windows, Lustre y NetApp ONTAP.

## Servicios de almacenamiento adicionales

Estos servicios no encajan perfectamente en las categorías que hemos definido hasta ahora, pero son importantes ofertas de almacenamiento de AWS que debes conocer.
- _AWS Storage Gateway_  
    Un servicio de almacenamiento en la nube híbrida completamente administrado que proporciona acceso local a un almacenamiento en la nube prácticamente ilimitado.
- _AWS Elastic Disaster Recovery_  
    Un servicio completamente administrado que agiliza la recuperación de tus servidores físicos, virtuales y basados en la nube en AWS.

## Responsabilidad compartida en servicios de almacenamiento de AWS

El modelo de responsabilidad compartida de AWS agrupa los servicios en tres categorías en función de la propiedad de las tareas administrativas. Estas categorías se dividen en completamente administradas, administradas y no administradas.

### Servicios completamente administrados

En el caso de los servicios de almacenamiento completamente administrados, AWS se hace responsable de todo, desde el hardware y la infraestructura hasta toda la pila de almacenamiento. Esto incluye la durabilidad, la disponibilidad, el cifrado en reposo y la replicación de los datos. Las empresas solo son responsables de la administración de datos, los controles de acceso y la configuración adecuada del servicio.

### Servicios administrados

En el caso de los servicios de almacenamiento administrado, AWS administra la infraestructura de almacenamiento subyacente, la redundancia del hardware y la replicación de volúmenes. Las empresas son responsables de las estrategias de copia de seguridad de datos, la configuración del cifrado, la optimización del rendimiento del volumen y la planificación de la capacidad.

### Servicios no administrados

En el caso de los servicios de almacenamiento no administrados, los clientes asumen toda la responsabilidad en materia de administración de datos, copia de seguridad y recuperación, cifrado, optimización del rendimiento y durabilidad. AWS solo mantiene el hardware físico subyacente y la infraestructura de red.

---

# Almacenamiento en bloques

## Almacén de instancias de Amazon EC2

El _almacén de instancias de Amazon EC2_ es un almacenamiento en bloques temporal físicamente conectado al host donde corre la instancia. Los datos se pierden al detener o terminar la instancia, por lo que solo sirve para usos efímeros como cachés, búferes o datos temporales.

**Beneficios:**
- Almacenamiento disponible automáticamente
- Rentable: incluido en el precio de las instancias de EC2
- Alto rendimiento: almacenamiento de latencia extremadamente baja conectado directamente al servidor host de tu instancia de EC2

## Amazon Elastic Block Store (EBS)

Amazon EBS ofrece almacenamiento en bloques persistente para instancias de EC2, funcionando como un disco duro externo con rendimiento constante y baja latencia. Permite redimensionar, hacer copias de seguridad y mover volúmenes entre instancias.

Los datos se conservan incluso si la instancia EC2 se detiene o termina. Ideal para bases de datos, sistemas de archivos y cargas de trabajo críticas.

Algunos casos prácticos de Amazon EBS incluyen el alojamiento de bases de datos, el almacenamiento de copias de seguridad para aplicaciones y el despliegue rápido de entornos de desarrollo mediante instantáneas de volumen.

Beneficios:
- Migración de datos: Los volúmenes de EBS se pueden migrar fácilmente entre zonas de disponibilidad mediante instantáneas. Las **instantáneas** (snapshots) proporcionan una forma sencilla de mover datos entre regiones o crear copias.
- Cambios en el tipo de instancia: son independientes de las instancias de EC2, lo que permite actualizar o degradar instancias sin perder datos.
- Recuperación ante desastres: Las instantáneas automatizadas que se realizan con frecuencia aseguran que los datos permanezcan protegidos y se puedan recuperar rápidamente.
- Optimización de costes: Puedes cambiar entre los tipos de almacenamiento o ajustar la capacidad.
- Ajuste del rendimiento: Amazon EBS ofrece varios tipos de volúmenes para adaptarse a los diferentes requisitos de carga de trabajo y necesidades de E/S por segundo (IOPs).

### Ciclo de vida de los datos de Amazon EBS

La administración del ciclo de vida de los datos de Amazon EBS implica la creación, copia de seguridad y eliminación de volúmenes e instantáneas. Este proceso optimiza los costes de almacenamiento y ayuda a asegurar la protección de los datos.

### Instantáneas de EBS (Snapshots)

Las instantáneas de EBS son copias de seguridad puntuales del volumen de EBS. 

Se pueden usar para la recuperación ante desastres, la migración de datos, el cambio de tamaño de los volúmenes y para crear copias de seguridad uniformes de las cargas de trabajo de producción. 

Las instantáneas de EBS son progresivas, lo que significa que solo guardan los bloques del volumen que han cambiado después de la instantánea más reciente.

Las instantáneas de los volúmenes de EBS se almacenan de forma redundante en varias zonas de disponibilidad con Amazon S3.

#### Trabajo con instantáneas de EBS

De acuerdo con el **modelo de responsabilidad compartida de AWS**, como cliente, tienes la responsabilidad de programar y administrar las instantáneas regulares de EBS como parte de tu estrategia de copia de seguridad. Esto incluye la supervisión de los costes de las instantáneas y la eliminación de las instantáneas innecesarias para evitar cargos excesivos. También debes asegurarte de que los datos confidenciales de las instantáneas estén cifrados, verificar la integridad de las instantáneas y probar los procedimientos de restauración con regularidad.

#### Beneficios:
- Protección y recuperación de datos: permiten una recuperación rápida
- Flexibilidad operativa: Las instantáneas permiten realizar operaciones como la migración de datos entre regiones, el cambio de tamaño de volúmenes, la clonación de volúmenes y el intercambio de datos entre cuentas de AWS.
- Rentable: Las instantáneas utilizan tecnología de copia de seguridad progresiva, que almacena solo los bloques modificados después de la copia de seguridad inicial, lo que reduce los costes de almacenamiento y el tiempo de copia de seguridad.

### Amazon Data Lifecycle Manager

Puedes automatizar la creación, retención y eliminación de instantáneas de EBS con Amazon Data Lifecycle Manager. Amazon Data Lifecycle Manager puede programar instantáneas fuera de las horas de mayor actividad para minimizar el impacto en el rendimiento; además, puede eliminar automáticamente las copias de seguridad obsoletas para controlar los costes de almacenamiento. Es especialmente útil para los despliegues a gran escala en los que la administración manual de instantáneas requeriría mucho tiempo y sería propensa a errores.

#### Flujo de trabajo de Amazon Data Lifecycle Manager
1. Crear una política de instantáneas de EBS.
2. Elige un volumen de EBS o una instancia de EC2 como objetivo de la instantánea.
3. Excluir volúmenes: Puedes reducir los datos que se van a incluir en la instantánea.
4. Establecer horarios personalizados: Puedes automatizar la creación, retención y eliminación.
5. Implementar acciones adicionales: como las etiquetas, el archivado de instantáneas, la restauración rápida de instantáneas de Amazon EBS, la copia entre regiones y el uso compartido entre cuentas.

---
# Almacenamiento de objetos

Amazon S3 es un servicio de almacenamiento de objetos que puede almacenar cantidades ilimitadas de datos en la nube de AWS. El almacenamiento de objetos es especialmente adecuado para gestionar grandes cantidades de datos no estructurados, como documentos, imágenes y vídeos.
## Amazon Simple Storage Service (Amazon S3)

Amazon S3 es un servicio de almacenamiento de objetos de alta disponibilidad y completamente administrado para almacenar y recuperar los datos necesarios como objetos. Ofrece una durabilidad del 99,999999999 por ciento, lo que significa que tus datos tienen una protección elevada frente a pérdidas, y ofrece características como el control de versiones, la administración del ciclo de vida y varias clases de almacenamiento para optimizar los costes.

Amazon S3 almacena los archivos como objetos en contenedores conocidos como buckets, y el tamaño de cada objeto puede oscilar entre unos pocos bytes y varios terabytes.

### Objetos de S3

Un objeto en Amazon S3 es la unidad fundamental de almacenamiento de datos. 

Por lo general, cada objeto incluye los _datos_ en sí, _los metadatos_ y un identificador o _clave_ únicos. Los objetos pueden ser de cualquier tipo de archivo, como imágenes, vídeos, documentos o datos de aplicaciones.

Cada objeto de Amazon S3 se identifica de forma exclusiva en un bucket mediante su clave, que es básicamente su nombre de archivo. Los objetos también tienen propiedades como el identificador de versión, la información de control de acceso y los metadatos definidos por el usuario.

### Buckets de S3

Un bucket de Amazon S3 es un contenedor para almacenar objetos en Amazon S3. Los buckets tienen un nombre único a nivel mundial en todo AWS, lo que ayuda a identificar y organizar los datos almacenados.

Los buckets sirven como unidad básica para el control de acceso y pueden contener una cantidad prácticamente ilimitada de objetos. Tienen un rol crucial en la administración de datos, ya que permiten agrupar objetos relacionados y aplicar políticas a los buckets.

Al crear un bucket, debes especificar su nombre y la región en la que se alojará. Se pueden configurar con varios ajustes, entre los que se incluyen el control de versiones, el registro y los permisos de acceso.

### Beneficios:
- Almacenamiento prácticamente ilimitado
- Administración del ciclo de vida de los objetos
- Amplio abanico de casos prácticos: Amazon S3 se utiliza habitualmente para la _distribución de contenido_, el _alojamiento de sitios web estáticos_ y la entrega de _archivos multimedia_.

### Administración de seguridad y privacidad

Todo lo que almacena en Amazon S3 es _privado de forma predeterminada_. Debes conceder permisos de forma explícita para acceder a estos recursos.

#### Políticas
- **Políticas de buckets**: Una política de bucket de S3 especifica qué acciones están permitidas o prohibidas en el bucket, además de cada objeto de ese bucket.
- **Políticas basadas en la identidad**: Controlan las acciones que los usuarios, los grupos o los roles pueden realizar.
- La **configuración de bloqueo de acceso público** de S3 anula las políticas de bucket e impide el acceso público incluso cuando las políticas lo permiten.
#### Cifrado
- **Cifrado en reposo** : protege los datos almacenados en buckets de S3, lo que evita el acceso no autorizado a los objetos almacenados.
- **Cifrado en tránsito** : protege los datos que se transfieren hacia y desde Amazon S3, lo que mantiene una comunicación segura entre el cliente y el servicio.

### Clases de almacenamiento de Amazon S3

Amazon S3 ofrece varias clases de almacenamiento para adaptarse a una variedad de cargas de trabajo, con requisitos específicos en materia de rendimiento, acceso, resiliencia y coste.

#### S3 Standard
Se considera un tipo de almacenamiento de uso general para las aplicaciones en la nube, los sitios web dinámicos, la distribución de contenido, las aplicaciones móviles y de juegos, y el análisis de big data. Cuando cargas un objeto en Amazon S3 sin especificar una clase de almacenamiento, el objeto se añade a S3 Standard de forma predeterminada.

#### S3 Intelligent-Tiering
Esta capa resulta útil si los datos tienen patrones de acceso desconocidos o cambiantes. S3 Intelligent-Tiering almacena los objetos en tres capas: una capa de acceso frecuente, una capa de acceso poco frecuente y una capa de acceso instantáneo al archivo.

#### S3 Standard-Infrequent Access (Standard-IA)
Sirve para los datos a los que se accede con menor frecuencia, pero que requieren un acceso rápido cuando es necesario. Ofrece la alta durabilidad, el alto rendimiento y la baja latencia de S3 Standard, con un precio de almacenamiento por GiB y una tarifa de recuperación por GiB bajos.

#### S3 One Zone-Infrequent Access (One Zone-IA)
Almacena los datos en una única zona de disponibilidad, lo que reduce los costes en comparación con S3 Standard-IA, que emplea tres zonas. Es una opción ideal para almacenar copias de seguridad secundarias o datos que se pueden recrear con facilidad.

#### S3 Express One Zone
S3 Express One Zone almacena los datos en una única zona de disponibilidad. S3 Express One Zone ofrece una velocidad de acceso a los datos hasta 10 veces más rápida y costes de solicitud hasta un 80 % más bajos que los de S3 Standard. Ideal para las aplicaciones sensibles a la latencia y a los datos a los que se accede con mayor frecuencia.

#### S3 Glacier Instant Retrieval
Usa S3 Glacier Instant Retrieval para archivar datos a los que rara vez se accede y requieren una recuperación de milisegundos. Almacenar datos en esta clase de almacenamiento permite ahorrar hasta un 68 por ciento en comparación con la clase de almacenamiento S3 Standard-IA, y con la misma latencia y rendimiento.

#### S3 Glacier Flexible Retrieval
S3 Glacier Flexible Retrieval ofrece almacenamiento barato para datos archivados a los que se accede de una a dos veces al año. Con S3 Glacier Flexible Retrieval, puedes acceder a los datos en entre uno a cinco minutos mediante la recuperación rápida. También puedes solicitar recuperaciones en bloque en un plazo de entre 5 a 12 horas sin coste adicional.

#### S3 Glacier Deep Archive
S3 Glacier Deep Archive es la clase de almacenamiento de Amazon S3 más económica. Permite la retención a largo plazo y la preservación digital de datos a los que se accede de una a dos veces al año. Los datos almacenados en la clase de almacenamiento S3 Glacier Deep Archive tienen un periodo de recuperación predeterminado de 12 horas.

#### S3 Outposts
Amazon S3 Outposts ofrece almacenamiento de objetos a tu entorno local de AWS Outposts con las funciones y las API de Amazon S3, además, sirve cargas de trabajo con requisitos de residencia de datos locales. También ayuda a mantener un rendimiento óptimo cuando los datos deben permanecer cerca de las aplicaciones locales.

### S3 Lifecycle

Para evitar la administración manual de las configuraciones de los niveles de almacenamiento de objetos, puedes usar las configuraciones de S3 Lifecycle para automatizar el proceso. Al definir una configuración de ciclo de vida para un objeto o grupo de objetos, puedes elegir automatizar dos tipos de acciones de la siguiente manera:

- _Acciones de transición:_ definen cuándo los objetos deben pasar a otra clase de almacenamiento.
- _Acciones de vencimiento:_ definen cuándo los objetos vencen y deberían eliminarse de forma definitiva.

Por ejemplo, podrías traspasar objetos a la clase de almacenamiento S3 Standard-IA 30 días después de crearlos. O podrías archivar objetos en la clase de almacenamiento S3 Glacier Deep Archive 1 año después de crearlos.

---
# Almacenamiento de archivos

## Amazon Elastic File System (Amazon EFS)

Amazon EFS es un servicio de almacenamiento de archivos escalable y completamente administrado que se utiliza con los servicios de la nube de AWS y los recursos locales.

Funciona mediante el _protocolo Linux Network File System (NFS)_ y _escala automáticamente_ a petabytes a medida que añade o eliminas archivos sin interrumpir las aplicaciones. 

EFS está diseñado para admitir una gran variedad de cargas de trabajo y pueden acceder a él _varias instancias de EC2_ a la vez.

### Beneficios de Amazon EFS
- **Redundancia multi-AZ**
- **Acceso compartido**: Amazon EFS admite **miles** de conexiones NFS simultáneas
- **Almacenamiento elástico**: Amazon EFS puede aumentar y reducir automáticamente

### Clases de almacenamiento de Amazon EFS

Con Amazon EFS puedes crear y configurar sistemas de archivos rápidamente sin coste mínimo ni de configuración. Solo pagas por el almacenamiento que utilizas.

#### Clases de almacenamiento Standard
Las clases de almacenamiento _EFS Standard_ y _EFS Standard-Infrequent Access (Standard-IA)_ ofrecen resiliencia multi-AZ y los mayores niveles de durabilidad y disponibilidad. Tienen un coste más alto debido a su mayor disponibilidad y durabilidad.

#### Clases de almacenamiento One Zone
_EFS One Zone_ y _EFS One Zone-Infrequent Access (EFS One Zone-IA)_ proporcionan ahorros adicionales al guardar los datos en una única zona de disponibilidad. Al usar solo una zona de disponibilidad, puedes reducir los costes de almacenamiento en comparación con las clases de almacenamiento Standard EFS.

#### Clase de almacenamiento Archive
La clase de almacenamiento _EFS Archive_ tiene un coste optimizado para los datos a los que se accede solo unas pocas veces al año o menos y que no necesitan las latencias inferiores a un milisegundo de EFS Standard. EFS Archive ofrece un precio de almacenamiento hasta un 50 % inferior al de EFS Infrequent Access, lo que permite una solución más rentable para datos inactivos con accesos poco frecuentes.

### Ciclo de vida de los datos de Amazon EFS
Puedes optimizar aún más los costes de almacenamiento de Amazon EFS al transferir automáticamente los datos entre las clases de almacenamiento en función de los patrones de uso.

#### Transición al acceso poco frecuente
Esta política indica a la administración del ciclo de vida cuándo tiene que mover los archivos al almacenamiento poco frecuente, que tiene un coste optimizado para los datos a los que se accede solo unas pocas veces cada trimestre. De forma predeterminada, los archivos a los que no se accede en el almacenamiento Standard durante 30 días se transfieren al almacenamiento poco frecuente.

#### Transición a Archive
Esta política indica a la administración del ciclo de vida cuándo tiene que mover los archivos a la clase de almacenamiento Archive, que tiene un coste optimizado para los datos a los que se accede solo unas pocas veces al año o menos. De forma predeterminada, los archivos a los que no se accede en el almacenamiento Standard durante 90 días se transfieren al almacenamiento Archive.

#### Transición a Standard
Esta política indica a la administración del ciclo de vida si se deben transferir los archivos de almacenamiento poco frecuente o Archive y volver al almacenamiento Standard cuando se accede a los archivos en el almacenamiento poco frecuente o Archive. De forma predeterminada, los archivos no se devuelven al almacenamiento Standard y permanecen en la clase de almacenamiento poco frecuente o Archive aunque se acceda a ellos.


## Amazon FSx

Amazon FSx permite iniciar, ejecutar y escalar sistemas de archivos de alto rendimiento y con gran cantidad de características en la nube de forma práctica y rentable.

Admite una amplia gama de cargas de trabajo gracias a su fiabilidad, seguridad, escalabilidad y gran cantidad de capacidades. 

En comparación con Amazon EFS, que se centra en la compatibilidad del sistema de archivos de red (NFS), Amazon FSx admite varios protocolos de sistemas de archivos, incluidos Windows File Server, Lustre, OpenZFS y NetApp ONTAP.

#### Beneficios de Amazon FSx
- **Integración de sistemas de archivos**
- **Infraestructura administrada**
- **Almacenamiento escalable**
- **Rentable**

#### Amazon FSx para Windows File Server
Amazon FSx para Windows File Server proporciona almacenamiento compartido completamente administrado basado en Windows Server.

Entre los casos prácticos, se incluyen los siguientes:
- Migrar los servidores de archivos de Windows a AWS.
- Agilizar las cargas de trabajo híbridas.
- Reducir el coste de despliegue de SQL Server.
- Optimizar los escritorios virtuales y el streaming.

#### Amazon FSx para NetApp ONTAP
Amazon FSx para NetApp ONTAP proporciona almacenamiento compartido completamente administrado en la nube de AWS con las reconocidas capacidades de acceso a datos y de administración de ONTAP.

Entre los casos prácticos, se incluyen los siguientes:
- Migrar cargas de trabajo a AWS sin problemas.
- Desarrollar aplicaciones modernas.
- Modernizar la administración de datos.
- Optimizar la continuidad del negocio.

#### Amazon FSx para OpenZFS
Amazon FSx para OpenZFS proporciona un almacenamiento de archivos compartido completamente administrado, integrado en el sistema de archivos OpenZFS y accesible mediante el protocolo NFS (v3, v4, v4.1 y v4.2).

Entre los casos prácticos, se incluyen los siguientes:
- Migrar cargas de trabajo a AWS sin problemas.
- Proporcionar información más rápidamente para cargas de trabajo de análisis de datos.
- Agilizar la administración de contenidos.
- Aumentar la velocidad de desarrollo/pruebas.

#### Amazon FSx para Lustre
Amazon FSx para Lustre proporciona un almacenamiento compartido completamente administrado con la escalabilidad y el rendimiento del popular sistema de archivos Lustre.

Entre los casos prácticos, se incluyen los siguientes:
- Agilizar el machine learning (ML).
- Activar la computación de alto rendimiento (HPC).
- Desbloquear el análisis de big data.
- Aumentar la agilidad de la carga de trabajo multimedia.

---
# Servicios de almacenamiento adicionales

## AWS Storage Gateway
Storage Gateway es un servicio de almacenamiento en la nube híbrida que permite integrar sin problemas los entornos locales con el almacenamiento en la nube de AWS. Puedes usarlo para extender el almacenamiento local a la nube y, al mismo tiempo, mantener un acceso de baja latencia a los datos de uso frecuente.

### Beneficios
- **Integración sin problemas**: conectividad fluida entre aplicaciones locales y AWS
- **Administración de datos mejorada**: administración centralizada
- **Almacenamiento en caché local**:  Guarda en local los datos a los que se accede con frecuencia.
- **Optimización de costes**

### Tipos de puerta de enlace

#### Amazon S3 File Gateway
Amazon S3 File Gateway une tu entorno local con Amazon S3. Proporciona a las aplicaciones locales acceso a un almacenamiento en la nube prácticamente ilimitado con protocolos de archivos conocidos. 

Cuando despliegas un S3 File Gateway, tus sistemas locales lo ven como un servidor de archivos estándar. Los archivos escritos en este servidor se cargan automáticamente en Amazon S3 y, al mismo tiempo, se mantiene el acceso local a los datos utilizados recientemente mediante el almacenamiento en caché inteligente. Esto significa que tus aplicaciones pueden seguir trabajando con los archivos como siempre lo han hecho mientras los datos reales se almacenan de forma segura en la nube de AWS.

#### Volume Gateway
Con Volume Gateway, puedes crear volúmenes de almacenamiento virtual y, al mismo tiempo, mantener el acceso local a los datos. Básicamente, funciona como un puente entre la infraestructura local y el almacenamiento en la nube de AWS al presentar los datos en la nube como volúmenes iSCSI que tus aplicaciones actuales pueden montar.

>[!info]- iSCSI 
> iSCSI es un protocolo de red que permite transferir comandos de almacenamiento SCSI a través de redes TCP/IP. Permite que un servidor o dispositivo acceda al almacenamiento en un dispositivo de red, como un NAS o un servidor de almacenamiento, como si fuera un disco duro local conectado directamente.

Volume Gateway funciona en dos configuraciones principales:

- El _modo de volumen en caché_ almacena los datos principales en la nube, mientras que los datos a los que se accede con frecuencia se almacenan en caché de forma local para ofrecer un acceso de baja latencia.
- El _modo de volumen almacenado_ conserva de forma local el conjunto de datos completo mientras realizar copias de seguridad de forma asíncrona en la nube como instantáneas de EBS.

#### Tape Gateway
Tape Gateway permite reemplazar la infraestructura física de cintas por capacidades de cinta virtual y, al mismo tiempo, aprovechar la durabilidad y la escalabilidad del almacenamiento en la nube de AWS. Tape Gateway proporciona una interfaz que funciona con el software de copia de seguridad de cinta existente, lo que hace que la transición de las cintas físicas al almacenamiento en la nube se lleve a cabo sin problemas.

Cuando despliegas un Tape Gateway, se presenta a tus aplicaciones de copia de seguridad como hardware de cinta estándar. Tu software de copia de seguridad escribe los datos en estas cintas virtuales del mismo modo que lo haría en las cintas físicas y se almacenan en Amazon S3.

También puedes configurar Tape Gateway para que transfiera automáticamente los datos a los que se accede con menos frecuencia a una clase de almacenamiento más rentable para una retención a largo plazo.

## AWS Elastic Disaster Recovery

Elastic Disaster Recovery replica las cargas de trabajo críticas en AWS con un tiempo de inactividad mínimo. Los datos en los bloques de tus servidores se replican de forma continua en AWS, lo que los convierte en una opción ideal para casos prácticos que requieren soluciones sólidas de recuperación ante desastres. 

Es compatible con servidores físicos y virtuales, lo que permite una recuperación rápida ante interrupciones, algo especialmente valioso en sectores como el sanitario, donde la disponibilidad del sistema es vital.

Puedes usar Elastic Disaster Recovery para reducir los tiempos de inactividad, la pérdida de datos y, al mismo tiempo, eliminar los costes asociados al mantenimiento de los centros de datos secundarios.

### Beneficios
- **Resiliencia empresarial**
- **Recuperación ante desastres optimizada**
- **Optimización de costes**

---
# Comparación de los servicios de almacenamiento


- **Amazon S3**: Servicio de **almacenamiento de objetos**. Ideal para **sitios web estáticos**, **activos web**, **copias de seguridad** y **almacenamiento escalable**.
    - Escala automáticamente sin gestión manual.
    - Se paga solo por lo que se usa.
    - No es adecuado para operaciones rápidas y continuas de lectura/escritura (no transaccional).

- **Amazon EBS (Elastic Block Store)**: Proporciona **almacenamiento en bloques persistente** para instancias de **EC2**, usado comúnmente por **bases de datos** y sistemas que requieren **baja latencia** y **alto rendimiento**.
    - Ofrece distintos tipos de volúmenes (SSD, aprovisionados por IOPS, etc.) para optimizar el rendimiento.
    - Diseñado para operaciones transaccionales y acceso a nivel de bloque.
        
- **Amazon EFS (Elastic File System)**: Servicio de **almacenamiento compartido y escalable** a nivel de **sistema de archivos**.
    - Permite acceso simultáneo desde múltiples instancias y ubicaciones.
    - Escala automáticamente a petabytes.
    - Ideal para **procesamiento multimedia**, **colaboración en tiempo real** y **acceso concurrente a archivos**.

**Resumen :**
- **S3 →** almacenamiento de objetos, escalable y económico.
- **EBS →** almacenamiento en bloques, persistente y de alto rendimiento.
- **EFS →** sistema de archivos compartido, escalable y accesible en tiempo real.

---

# Resumen del módulo

En este módulo, has aprendido acerca de las diversas opciones de almacenamiento disponibles en AWS, empezando por los servicios de almacenamiento en bloques como el almacén de instancias de Amazon EC2 y Amazon EBS. Has visto cómo Amazon EBS proporciona volúmenes de almacenamiento en bloques persistentes para las instancias de EC2, mientras que el almacén de instancias de EC2 ofrece almacenamiento temporal en bloques. También has aprendido a usar las instantáneas de EBS y AWS Data Lifecycle Manager para administrar de forma automatizada las copias de seguridad y la protección de datos.

A continuación, has examinado Amazon S3, un servicio de almacenamiento de objetos con mucha escalabilidad que sirve de base para muchas necesidades de almacenamiento en la nube. Has profundizado en las soluciones de almacenamiento de archivos, como Amazon Elastic File System (Amazon EFS) para cargas de trabajo basadas en Linux y Amazon FSx para sistemas de archivos Windows, Lustre, OpenZFS y NetApp ONTAP. Por último, has visto AWS Storage Gateway, un servicio que conecta entornos locales con el almacenamiento de AWS y facilita arquitecturas de almacenamiento en la nube híbrida.

## Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| **Enlace del recurso**                                                                                                                                             | **Descripción**                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Guía del usuario del almacén de instancias de Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) | Opción de almacenamiento temporal que se conecta directamente al equipo host de una instancia de EC2 y que proporciona un almacenamiento de alto rendimiento, pero no persistente.                                                      |
| [Amazon Elastic Block Store (Amazon EBS)](https://aws.amazon.com/ebs/)                                                               | Un servicio de almacenamiento en bloque escalable que proporciona volúmenes persistentes y de alto rendimiento que puedes adjuntar a tus instancias de EC2 para almacenar datos y aplicaciones.                                         |
| [Preguntas frecuentes sobre Amazon Elastic Block Store (Amazon EBS)](https://aws.amazon.com/ebs/faqs/)                               | Preguntas frecuentes sobre Amazon EBS.                                                                                                                                                                                                  |
| [Guía del usuario de las instantáneas de Amazon EBS](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-snapshots.html)            | Las instantáneas de EBS son copias de seguridad puntuales de tus volúmenes de almacenamiento en la nube, que permiten proteger los datos y restaurarlos cuando sea necesario.                                                           |
| [Guía del usuario de Amazon Data Lifecycle Manager](https://docs.aws.amazon.com/ebs/latest/userguide/snapshot-lifecycle.html)        | Un servicio que agiliza la creación, retención y eliminación de instantáneas de Amazon EBS.                                                                                                                                             |
| [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/)                                                              | Un servicio de almacenamiento en la nube escalable que puede almacenar y recuperar los datos necesarios desde cualquier lugar de la web.                                                                                                |
| [Preguntas frecuentes sobre Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/faqs/)                              | Preguntas frecuentes sobre Amazon S3.                                                                                                                                                                                                   |
| [Clases de almacenamiento de Amazon S3](https://aws.amazon.com/s3/storage-classes/)                                                  | Amazon S3 ofrece varias clases de almacenamiento, desde un acceso frecuente de alto rendimiento hasta opciones de archivado rentables, adaptadas a las diferentes necesidades de recuperación de datos y restricciones presupuestarias. |
| [Guía del usuario del control de versiones de Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)      | El control de versiones de Amazon S3 conserva varias variantes de objetos, lo que posibilita la recuperación de eliminaciones o modificaciones no deseadas al conservar todas las actualizaciones de los archivos.                      |
| [Guía del usuario de Amazon S3 Buckets](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-buckets-s3.html)              | Los buckets de S3 son contenedores de almacenamiento en la nube que almacenan de forma segura varios tipos de datos, lo que permite un acceso y una administración cómodos a través de la infraestructura en línea de AWS.              |
| [Amazon Elastic File System (Amazon EFS)](https://aws.amazon.com/efs/)                                                               | Un servicio de almacenamiento de archivos escalable y completamente administrado que permite que varios recursos de AWS accedan a los datos compartidos de forma simultánea sin necesidad de planificar la capacidad.                   |
| [Preguntas frecuentes sobre Amazon Elastic File System (Amazon EFS)](https://aws.amazon.com/efs/faq/)                                | Preguntas frecuentes sobre Amazon EFS.                                                                                                                                                                                                  |
| [Amazon FSx](https://aws.amazon.com/fsx/)                                                                                            | Un servicio de almacenamiento de archivos completamente administrado que te permite iniciar y ejecutar sistemas de archivos como Windows File Server, Lustre, NetApp ONTAP y OpenZFS en la nube de AWS.                                 |
| [Amazon FSx para Windows File Server](https://aws.amazon.com/fsx/windows/)                                                           | Una opción de Amazon FSx que proporciona un almacenamiento de archivos fiable y de alto rendimiento compatible con las aplicaciones de Windows en la nube de AWS.                                                                       |
| [Amazon FSx para NetApp ONTAP](https://aws.amazon.com/fsx/netapp-ontap/)                                                             | Una opción de Amazon FSx que proporciona almacenamiento de archivos con capacidades avanzadas de administración de datos y compatibilidad con cargas de trabajo de Windows y Linux en AWS.                                              |
| [Amazon FSx para OpenZFS](https://aws.amazon.com/fsx/openzfs/)                                                                       | Una opción de Amazon FSx que proporciona almacenamiento escalable y de alto rendimiento mediante el popular sistema de archivos ZFS de código abierto.                                                                                  |
| [Amazon FSx para Lustre](https://aws.amazon.com/fsx/lustre/)                                                                         | Una opción de Amazon FSx diseñada para agilizar las cargas de trabajo al proporcionar un acceso rápido a los datos para aplicaciones con uso intensivo de recursos de computación en AWS.                                               |
| [AWS Storage Gateway](https://aws.amazon.com/storagegateway)                                                                         | Un servicio de almacenamiento en la nube híbrida que proporciona una integración perfecta y segura entre el entorno local y los servicios de almacenamiento en la nube de AWS.                                                          |
| [Amazon S3 File Gateway](https://aws.amazon.com/storagegateway/file/s3/)                                                             | Una configuración de Storage Gateway que proporciona acceso local a los archivos de los objetos de S3 y, al mismo tiempo, almacena en caché localmente los datos a los que se accede con frecuencia para una recuperación más rápida.   |
| [Tape Gateway](https://aws.amazon.com/storagegateway/vtl/)                                                                           | Una configuración de Storage Gateway que se utiliza para realizar copias de seguridad de los datos en Amazon S3 y, al mismo tiempo, mantener la compatibilidad con las aplicaciones de copia de seguridad basadas en cinta existentes.  |
| [Volume Gateway](https://aws.amazon.com/storagegateway/volume/)                                                                      | Una configuración de Storage Gateway que proporciona volúmenes de almacenamiento en bloque iSCSI a las aplicaciones locales y ofrece modos almacenados y en caché.                                                                      |