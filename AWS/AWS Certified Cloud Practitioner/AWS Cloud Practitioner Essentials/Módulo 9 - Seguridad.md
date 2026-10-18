```table-of-contents
```
---

# Introducción a la seguridad en AWS

## Autenticación y autorización

La _autenticación_ es el proceso de verificar la identidad de un usuario o entidad mediante credenciales como una combinación de nombre de usuario y contraseña.
- **Caso práctico:** una persona de la plantilla inicia sesión en un portal para el personal.
   
La _autorización_ otorga a los usuarios ciertos derechos y permisos de acceso que determinan qué acciones pueden realizar en un sistema o una aplicación.
- **Caso práctico:** una persona de la plantilla solo puede acceder a sus propios registros del personal dentro del portal de empleados.

## Modelo de responsabilidad compartida de AWS

La seguridad en la nube es una responsabilidad compartida entre clientes y AWS. 

**Clientes: seguridad _en_ la nube**  
Al utilizar los servicios de AWS, la clientela mantiene un control total sobre su contenido. Como resultado, esta es responsable de proteger todo lo que crea y administra en la nube de AWS:

- Administrar la seguridad de los datos, los sistemas y las aplicaciones.
- Decidir qué datos y cargas de trabajo almacenar o ejecutar en AWS.
- Determinar qué servicios de AWS usar.
- Controlar quién tiene acceso a los entornos y los recursos.

**AWS: seguridad _de_ la nube**  
AWS es responsable de la seguridad _de_ la nube. AWS opera, administra y controla los componentes en todas las capas de la infraestructura. Esto incluye asegurar:

- El software básico que impulsa los servicios de AWS.
- La capa de virtualización.
- El hardware y la infraestructura global que respaldan los centros de datos desde los que operan los servicios. Esto incluye la protección de las regiones de AWS, zonas de disponibilidad y ubicaciones periféricas.

>[!info] ![[Pasted image 20251111114348.png]]

## Controles de seguridad de AWS

AWS ofrece varios mecanismos de seguridad para proteger tus recursos en la nube. Estos controles pueden ayudarte a:

- _Evitar_ los incidentes de seguridad mediante una administración adecuada de permisos y accesos.
- _Proteger_ las redes, las aplicaciones y los datos.
- _Detectar y responder_ a los incidentes de seguridad a medida que se produzcan.

---
# Prevención del acceso no autorizado

## AWS Identity and Access Management (AWS IAM)

**Administrar de forma segura las identidades y el acceso a los servicios y recursos de AWS.**

Una de las mejores maneras de evitar los incidentes de seguridad antes de que ocurran es mediante la administración adecuada de permisos y accesos. Con IAM, de forma predeterminada, se deniegan todas las acciones. Debes conceder permiso explícito a alguien antes de que pueda realizar cualquier acción en tu cuenta.

Cuando concedas permisos, debes proporcionar acceso únicamente cuando sea necesario. Este concepto se denomina principio de mínimo privilegio.

> _El_ **_principio de mínimo privilegio_** _exige que solo debes dar a las personas y los sistemas acceso a lo que necesitan y nada más._

IAM proporciona usuarios, grupos y roles para que puedas configurar el acceso en función de las necesidades operativas y de seguridad específicas de la empresa. Las políticas de IAM definen el acceso necesario para estas identidades.

![[Pasted image 20251111114849.png]]
### 1. Usuario raíz de la cuenta de AWS
Todas las cuentas de AWS reciben un usuario raíz de la cuenta de AWS. 

El usuario raíz es el propietario de la cuenta y tiene permiso para hacer cualquier cosa dentro de la cuenta de AWS. Debes asociar una contraseña segura a esta potente cuenta y activar la autenticación multifactor (MFA), que requiere al menos dos métodos de verificación para iniciar sesión. 

Para gestionar las tareas diarias, debes crear otras identidades de IAM, como los usuarios de IAM.

### 2. Usuarios de IAM
Un usuario de IAM representa a una persona o aplicación que interactúa con los servicios y recursos de AWS. 

Consta de un nombre y credenciales. 

AWS recomienda crear usuarios de IAM individuales para cada persona que necesite acceder a la cuenta de AWS, para que tengan su propio conjunto único de credenciales de seguridad.

### 3. Grupos de IAM
Un grupo de IAM es un conjunto de usuarios de IAM. 

Al asignar permisos a un grupo, todos los usuarios del grupo heredan los permisos. 

Por ejemplo, puedes asignar permisos de acceso estándar a un grupo denominado **personal** para que todo el personal reciba el mismo acceso genérico.

### 4. Roles de IAM
Un rol de IAM es una identidad que puedes adoptar para obtener acceso temporal a los permisos.

Por ejemplo, es posible que una persona tenga que trabajar como barista por la mañana y como cajero por la tarde. 

Cuando alguien adopta un rol de IAM, abandona todos los permisos anteriores que tenía bajo un rol anterior y adopta los permisos del nuevo rol.

### 5. Políticas de IAM
Una política de IAM es un documento JSON que permite o deniega el acceso a los servicios y recursos de AWS. 

Las políticas de IAM también pueden definir el nivel de acceso a los recursos. Por ejemplo, puedes permitir que el personal acceda a todos los buckets de Amazon S3 de tu cuenta de AWS o solo a uno específico.

## AWS IAM Identity Center

IAM Identity Center centraliza la administración de identidades y accesos en las cuentas y aplicaciones de AWS. 

IAM Identity Center también se puede conectar a un origen de identidad existente y proporcionar al personal un acceso de inicio de sesión único a todos los servicios y cuentas de AWS conectados. Esto se denomina administración de identidad federada.

> La ***administración de identidad federada*** es un sistema que permite a los usuarios acceder a varias aplicaciones, servicios o dominios mediante un único conjunto de credenciales.


## AWS Secrets Manager

Secrets Manager proporciona una forma segura de administrar, rotar y recuperar las credenciales de la base de datos, las claves de API y otros secretos a lo largo de su ciclo de vida. Esto ayuda a mantener seguras tus aplicaciones, servicios y recursos de las TI.

> Los ***secretos*** son información confidencial o privada destinada a que solo personas o grupos específicos la conozcan. Los ejemplos incluyen contraseñas, credenciales de bases de datos y claves de API.


## AWS Systems Manager

Systems Manager proporciona una vista centralizada de los nodos de las cuentas y regiones de tu organización y de los entornos híbridos y multinube. 

Con este servicio, puedes acceder rápidamente a la información de los nodos, como el ID y los detalles del sistema operativo, y automatizar las ediciones del registro, la administración de usuarios y la aplicación de parches de seguridad.

> Los ***nodos*** son puntos de conexión en una red, un sistema o una estructura.

---

# Protección de redes y aplicaciones

La protección de redes y aplicaciones es otro componente vital de un entorno seguro en AWS.

> [!point] Ataques a redes y aplicaciones
> - **Ataques DoS**: En un ataque de denegación de servicio, un atacante inunda una aplicación web con un tráfico de red excesivo. Las solicitudes legítimas de los clientes se rechazan si la aplicación web se sobrecarga y ya no puede responder.
> - **Ataques de DDoS**: En un ataque de denegación de servicio distribuida (DDoS), quien ataca puede usar varios equipos infectados (denominados bots zombis) para enviar tráfico excesivo a una aplicación web sin saberlo.

## Protección de AWS a través de la infraestructura

AWS protege automáticamente contra los ataques de fuerza bruta de bajo nivel, como los DDoS, mediante su infraestructura y arquitectura de red integradas. La infraestructura de AWS se extiende por todo el mundo e incluye varias regiones, zonas de disponibilidad y ubicaciones periféricas. Está diseñado para dificultar que los atacantes saturen el sistema.

- **Grupos de seguridad**: Los grupos de seguridad solo permiten el tráfico de solicitudes adecuado. Operan a nivel de red de AWS, por lo que pueden hacer frente a ataques masivos utilizando toda la capacidad de la región de AWS.
- **Elastic Load Balancing (ELB)**: ELB gestiona el tráfico primero antes de transferirlo, de modo que tu servidor de frontend no se sature. Al igual que los grupos de seguridad, funciona a nivel regional.
- **Regiones de AWS**: La enorme capacidad de las regiones hace que sea extremadamente difícil saturarlas. Conseguirlo sería muy caro.

## Protección de AWS a través de servicios

AWS también ofrece estos servicios para ayudar a proteger la red y tus aplicaciones.

### AWS Shield

- **_AWS Shield Estándar_** está diseñado para proteger automáticamente a clientes de AWS de los tipos de ataques DDoS más comunes y frecuentes sin coste alguno. Utiliza una variedad de técnicas de análisis para detectar y mitigar el tráfico de red malintencionado de entrada en tiempo real.
- **_AWS Shield Avanzado_** es un servicio de pago que proporciona diagnósticos de ataques detallados y ofrece la capacidad de detectar y mitigar ataques DDoS sofisticados. También se integra con otros servicios, como Amazon CloudFront, Amazon Route 53 y ELB. 
 
Además, puedes integrar AWS Shield con AWS WAF a través de reglas personalizadas para mitigar ataques DDoS complejos.

### AWS WAF

AWS WAF es un **firewall** de aplicaciones web que supervisa las solicitudes de red que llegan a tus aplicaciones web. Cuando llega una solicitud a AWS WAF, comprueba la dirección IP con una lista de control de acceso web (ACL web). Si la solicitud proviene de una dirección IP bloqueada en la ACL web, AWS WAF deniega el acceso. Se permite el acceso a las solicitudes legítimas.


---
# Protección de datos

> [!point] Cifrado de datos
> El cifrado de datos funciona como un mecanismo de candado y llave. Si tienes la llave correcta, puedes acceder a los datos cifrados. Si no, no podrás acceder.
> ![[Pasted image 20251111121955.png]]
> **Tipos de cifrado de datos**
> El cifrado de datos se presenta de estas dos formas:
> - **Cifrado de datos en reposo:** los datos están inactivos y no se mueven, como cuando se almacenan en una base de datos.
> - **Cifrado de datos en tránsito:** los datos se mueven entre ubicaciones, como cuando se transfieren de una base de datos a una aplicación. Los certificados SSL/TLS se utilizan para establecer conexiones de red cifradas de un sistema a otro.
> 
> ![[Pasted image 20251111122111.png]]


AWS cuenta con una variedad de métodos para proteger los datos. Entre ellos se incluye la protección de datos integrada para opciones de almacenamiento y servicios diseñados específicamente para mejorar la protección de los datos.

## Protección de datos integrada de AWS

- **Amazon S3**: De forma predeterminada, todos los buckets de S3 nuevos tienen el cifrado configurado y todos los objetos cargados se cifran en reposo.
- **Amazon EBS**: Los volúmenes e instantáneas de Amazon EBS se pueden cifrar en reposo, incluidos los volúmenes de arranque y de datos de una instancia de Amazon EC2.
- **Amazon DynamoDB**: El cifrado en reposo del lado del servidor está habilitado en todos los datos de las tablas de DynamoDB mediante las claves de cifrado almacenadas en AWS Key Management Service (AWS KMS).

## Servicios de protección de datos de AWS

### AWS Key Management Service (AWS KMS)

Puedes usar AWS KMS para crear y administrar claves criptográficas. Luego, estas claves se pueden usar para cifrar y descifrar tus datos. 

También puedes controlar el uso de claves en una amplia gama de servicios y aplicaciones. Por ejemplo, puedes especificar qué usuarios y roles de IAM pueden administrar las claves. Tus claves nunca salen de AWS KMS y puedes desactivarlas temporalmente para que ya no se puedan usar.

> _Una_ **_clave criptográfica_** _es una cadena aleatoria de dígitos utilizada para bloquear (cifrar) y desbloquear (descifrar) datos._

### Amazon Macie

Con Amazon Macie, puedes supervisar los datos confidenciales en reposo para asegurarte de que están seguros. 

Macie utiliza el machine learning (ML) y la automatización para descubrir datos confidenciales almacenados en Amazon S3. Puedes usar Macie para evaluar tu posición de seguridad, algo especialmente útil para cumplir con los requisitos de conformidad.

### AWS Certificate Manager (ACM)

ACM centraliza la administración de tus certificados SSL/TLS que proporcionan cifrado de datos en tránsito. Se puede usar para proteger varios servicios de AWS y los recursos locales conectados.

> **_Certificados SSL/TLS_** _SSL/TLS se utilizan para establecer conexiones de red cifradas de un sistema a otro._

---
# Detección y respuesta ante incidentes de seguridad

AWS ofrece una variedad de servicios que puedes utilizar para detectar y responder ante los incidentes de seguridad.

## Amazon Inspector

Amazon Inspector ayuda a mejorar la seguridad y la conformidad de las aplicaciones mediante la ejecución de **evaluaciones de seguridad automatizadas** para las instancias, los contenedores y las funciones de Lambda de Amazon EC2. 

Comprueba las vulnerabilidades de seguridad y las desviaciones de las prácticas recomendadas de seguridad de las aplicaciones, como el acceso abierto a instancias de EC2 y las instalaciones de versiones de software vulnerables.

Puedes ver las evaluaciones finalizadas en la consola de Amazon Inspector. Estas evaluaciones incluyen una lista de resultados de seguridad priorizados por nivel de gravedad. Cada incidencia de seguridad identificada incluye una descripción detallada y una recomendación sobre cómo solucionarla. También puedes recuperar estos resultados a través de una API.

## Amazon GuardDuty

Amazon GuardDuty ofrece una detección inteligente de amenazas en toda tu infraestructura y recursos. 

GuardDuty identifica las amenazas mediante la **supervisión continua de los flujos de metadatos** de tu cuenta y de la actividad de red en el entorno. Utiliza direcciones IP malintencionadas conocidas, detección de anomalías y machine learning para identificar las amenazas con mayor precisión.

Puedes revisar los resultados detallados sobre cualquier amenaza detectada por GuardDuty en la consola de administración de AWS. Los resultados incluyen los pasos recomendados para poder solucionarlas. También puedes configurar las funciones de AWS Lambda para que implemente los pasos de corrección automáticamente.

## Amazon Detective

Una vez detectada una amenaza, puedes emplear Amazon Detective para investigar más a fondo la causa raíz. 

Detective te ayuda a **analizar las amenazas** con visualizaciones interactivas que se presentan en una vista unificada de la consola de administración de AWS. Estas visualizaciones incluyen las interacciones entre los recursos y los usuarios a lo largo de un cronograma configurable con los pasos recomendados para la corrección.

## AWS Security Hub

Security Hub reúne varios servicios de seguridad en un único lugar y formato. 

Con este servicio, puedes **ver rápidamente tu estado de seguridad y conformidad en una visión completa**. Security Hub incorpora automáticamente los resultados de seguridad de AWS y los servicios de los socios y los organiza en agrupaciones útiles y significativas denominadas informaciones. Puede reducir el tiempo de resolución (TTR) necesario con la corrección automatizada.

---

# Recursos de seguridad adicionales

## Documentación de seguridad de AWS

AWS ofrece una amplia documentación para gestionar la **seguridad, identidad y conformidad** de sus servicios.

- La **documentación oficial** detalla cómo proteger recursos específicos según el servicio.
- El **Knowledge Center** ayuda a resolver dudas y problemas comunes.
- La **AWS Security Documentation** organiza los contenidos por categoría de producto.
- El **AWS Security Blog** publica novedades, prácticas recomendadas y guías de expertos.

## Recursos de seguridad en AWS Marketplace

**AWS Marketplace** permite adquirir soluciones de terceros orientadas a la seguridad en la nube. Entre ellas destacan:

- **Detección y prevención de amenazas:** identifican y bloquean actividades maliciosas.
- **Administración de identidades y accesos:** gestionan permisos y autenticación de usuarios.
- **Protección de datos:** cifran y resguardan información sensible.
- **Conformidad y gobernanza:** ayudan a cumplir con regulaciones y normativas de seguridad.

---

# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| **Enlace del recurso**                                                                                     | **Descripción**                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| [AWS Identity and Access Management (AWS IAM)](https://aws.amazon.com/iam/)  | Administrar de forma segura las identidades y el acceso a los servicios y recursos de AWS.                                             |
| [AWS IAM Identity Center](https://aws.amazon.com/iam/identity-center/)       | Conecta tu origen de identidad de personal existente y administra de forma centralizada el acceso a AWS con un inicio de sesión único. |
| [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)               | Almacena y administra de forma centralizada las credenciales, las claves de API y otros secretos.                                      |
| [AWS Systems Manager](https://aws.amazon.com/systems-manager/)               | Administra nodos o puntos de conexión a escala en AWS y en entornos híbridos y de múltiples nubes.                                     |
| [AWS Shield](https://aws.amazon.com/shield/)                                 | Protege tu red y aplicaciones de los tipos de ataques DDoS más comunes y frecuentes.                                                   |
| [AWS WAF](https://aws.amazon.com/waf/)                                       | Protege tu red y aplicaciones de las direcciones IP bloqueadas definidas por una ACL web.                                              |
| [AWS Key Management Service (AWS KMS)](https://aws.amazon.com/kms/)          | Crea y administra claves criptográficas para cifrar y descifrar los datos.                                                             |
| [Amazon Macie](https://aws.amazon.com/macie/)                                | Certifica que los datos confidenciales se descubren y protegen en Amazon S3.                                                           |
| [AWS Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/) | Centraliza y administra los certificados SSL/TLS que proporcionan cifrado de datos en tránsito.                                        |
| [Amazon Inspector](https://aws.amazon.com/inspector/)                        | Compruebe las aplicaciones para detectar vulnerabilidades de seguridad y desviaciones de las prácticas recomendadas de seguridad.      |
| [Amazon GuardDuty](https://aws.amazon.com/guardduty/)                        | Supervisa continuamente el entorno de AWS con una detección inteligente de amenazas.                                                   |
| [Amazon Detective](https://aws.amazon.com/detective/)                        | Analiza las amenazas con visualizaciones interactivas contenidas en una vista unificada.                                               |
| [AWS Security Hub](https://aws.amazon.com/security-hub/)                     | Añade los resultados de seguridad y organízalos en información procesable.                                                             |
