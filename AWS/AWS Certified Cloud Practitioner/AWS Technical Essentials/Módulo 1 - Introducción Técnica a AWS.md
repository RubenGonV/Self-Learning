---
tags:
  - AWS
  - CLF-C02
---
---
```table-of-contents
maxLevel:1
```
---
# ☁️ ¿Qué es AWS y la Computación en la Nube?

**La computación en la nube** es la entrega **bajo demanda** de recursos de TI (como capacidad de cómputo, almacenamiento y redes) a través de **Internet** con un modelo de precios principalmente de **pago por uso**.

- **Amazon Web Services (AWS)** es el proveedor que ofrece estos servicios de computación en la nube. AWS es propietaria de los centros de datos y mantiene el hardware, liberando a las empresas de esta tarea.

## Ventajas de la Computación en la Nube

La nube ayuda a eliminar las **"cargas pesadas no diferenciadas"** (tareas comunes como el aprovisionamiento de hardware o copias de seguridad) para que las empresas puedan centrarse en lo que es **estratégicamente único** para su negocio.

1. **Pagar por lo que usas:** Solo se paga por los recursos consumidos.
2. **Beneficios de las grandes economías de escala:** Obtener precios más bajos debido al gran volumen de AWS.
3. **Dejar de hacer conjeturas sobre la capacidad:** Escalar automáticamente hacia arriba o hacia abajo según la demanda.
4. **Aumentar la velocidad y la agilidad:** Desplegar entornos completos en minutos o segundos (a diferencia de la infraestructura **en las instalaciones**).
5. **Ahorrar costes:** Reducir la inversión inicial en hardware y el coste de mantenimiento.
6. **Adoptar un enfoque global en cuestión de minutos:** Implementar aplicaciones en regiones de todo el mundo rápidamente.
    

---

# 🚀 Modelos de Despliegue de la Computación en la Nube

Existen tres estrategias principales para desplegar recursos de TI:

## 1. En la Nube (Cloud)
Los recursos de TI son administrados y mantenidos por un proveedor de la nube (como **AWS**) y se accede a ellos a través de Internet.
- **Ventaja:** Permite replicar entornos completos rápidamente y a bajo coste.

## 2. En las Instalaciones (On-Premises)
Las empresas y organizaciones alojan y mantienen su propio hardware (servidores, almacenamiento, redes) en sus propios centros de datos.
- **Desventaja:** Caro, lento y requiere un gran departamento de infraestructura para el mantenimiento y la planificación de capacidad.

## 3. Híbrido (Hybrid)
Una manera de conectar la infraestructura y las aplicaciones entre los **recursos basados en la nube** y los **recursos existentes situados fuera de la nube** (en las instalaciones).
- Se utiliza para extender la infraestructura local de una organización a la nube.

---
# 🌎 Infraestructura Global de AWS: Regiones, Zonas de Disponibilidad y Ubicaciones Periféricas

La **Infraestructura Global de AWS** es la base física que sustenta todas las aplicaciones en la nube, compuesta por **Regiones** y **Zonas de Disponibilidad (AZ)**.

## Regiones

Las **Regiones** son **ubicaciones geográficas** separadas en distintas partes del mundo (por ejemplo, Norte de Virginia, Tokio, Oregón) donde AWS aloja sus centros de datos.

Cada región es **independiente** de las demás. Los datos **no se replican** automáticamente entre regiones sin el consentimiento explícito del cliente.

Se identifican con un **nombre geográfico** y un **código de región** (por ejemplo, `us-east-1` para Norte de Virginia).


## Factores para Seleccionar una Región

Al elegir la región para alojar cargas de trabajo, se deben considerar estos aspectos clave:

1. **Latencia:** Si la aplicación es sensible al retraso (como juegos o IoT), elige una región **cercana** a la base de usuarios para reducir el tiempo de respuesta.

2. **Precios:** Los costes de los servicios pueden variar entre regiones.

3. **Disponibilidad de los Servicios:** No todos los servicios de AWS están disponibles en todas las regiones.

4. **Conformidad de los Datos:** Cumplimiento de las regulaciones locales o sectoriales sobre dónde deben residir los datos (residencia de datos).

---

## Zonas de Disponibilidad (AZ)

Las **Zonas de Disponibilidad** son un clúster de **uno o más centros de datos** dentro de una región.

Cuentan con **alimentación, redes y conectividad redundantes** y operan en ubicaciones discretas.

Están conectadas dentro de la región mediante enlaces redundantes de **alta velocidad y baja latencia**.

Se identifican añadiendo una letra al código de la región (por ejemplo, `us-east-1a`).

**Resiliencia:** La **práctica recomendada** es desplegar las cargas de trabajo replicándolas en **múltiples Zonas de Disponibilidad (mínimo dos)**. Si ocurre un fallo en una AZ, la aplicación seguirá funcionando en la otra.

## Alcance de los Servicios de AWS

Los servicios de AWS se despliegan en diferentes niveles:

|**Alcance del Servicio**|**Descripción**|**Recomendación**|
|---|---|---|
|**Regional**|El servicio está disponible en toda la región. AWS gestiona automáticamente la **durabilidad y disponibilidad** de los datos (por ejemplo, S3). Solo necesitas seleccionar la región.|Usar estos servicios administrados para aumentar la disponibilidad y resiliencia.|
|**Por Zona de Disponibilidad**|Requiere que el usuario especifique una AZ individual. El usuario a menudo debe encargarse de replicar los recursos para lograr la **alta disponibilidad** (por ejemplo, una instancia EC2).|Replicar la carga de trabajo en múltiples AZ para resiliencia.|
|**Global**|El servicio opera a nivel mundial (por ejemplo, IAM, CloudFront).|N/A|

---
## Ubicaciones Periféricas (Edge Locations)

Son **ubicaciones globales** utilizadas para almacenar contenido en **caché** y están dispersas por todo el mundo (más de 400).

- **Propósito:** Mejorar la **velocidad de entrega** del contenido y reducir la latencia para los usuarios finales.

- **Servicio Asociado:** **Amazon CloudFront** utiliza esta red de ubicaciones periféricas para dirigir al usuario a la ubicación con la menor latencia, distribuyendo el contenido con el mejor rendimiento posible.
  
---
# 💻 Interacción con AWS: Llamadas a la API

Cualquier acción que se realiza en AWS es esencialmente una **llamada a la API** (Interfaz de Programación de Aplicaciones) que debe ser **autenticada y autorizada**.

Existen tres formas principales de realizar estas llamadas a la API para administrar los servicios y recursos de AWS:

---
## 1. Consola de Administración de AWS (AWS Management Console)

La Consola de Administración de AWS es una **interfaz gráfica (basada en la web)** con la que puedes iniciar sesión y administrar tus recursos en la nube.

- **Uso:** Es la forma más sencilla de empezar a crear y administrar recursos, especialmente para principiantes o para tareas manuales.

- **Funcionalidades Clave:**
    - Puedes seleccionar **Servicios** (agrupados por categorías como Cómputo, Almacenamiento, etc.).  
    - Incluye un **selector de regiones** en la esquina superior derecha; al cambiarlo, todas las solicitudes se dirigen a la región elegida.

---
## 2. Interfaz de Línea de Comandos de AWS (AWS CLI)

**AWS CLI** es una **herramienta unificada de código abierto** que puedes descargar y configurar para administrar los servicios de AWS directamente desde la **línea de comandos** de tu sistema operativo (Windows, Linux, macOS).

- **Uso:** Ideal para tareas **programáticas y de automatización** (por ejemplo, ejecutar informes diarios, extraer datos de muchos servidores o crear scripts).

- **Mecanismo:** Utilizas comandos con la sintaxis `aws <servicio> <acción>`.

> [!example] Ejemplo:
> 
> ```bash
> aws s3api list-buckets
> ```
> 
> Esta llamada a la API utiliza la AWS CLI para enumerar todos los _buckets_ (contenedores de almacenamiento) en tu cuenta de Amazon S3.

---
## 3. Kits de Desarrollo de Software de AWS (AWS SDK)

Los **SDK de AWS** son kits de herramientas de **código abierto** mantenidos por AWS que permiten a los desarrolladores realizar llamadas a la API de AWS directamente desde el código fuente de sus aplicaciones, utilizando lenguajes de programación populares (como Python, Java, JavaScript, C++, etc.).

- **Uso:** Se utilizan para **integrar el código de una aplicación** con los servicios de AWS. Permite a las aplicaciones interactuar directamente con la infraestructura en la nube.

- **Mecanismo:** El desarrollador importa el SDK del lenguaje deseado y luego llama a los clientes de servicio de AWS dentro del código.    

> [!example] Ejemplo (Python - Boto3):
> 
> ```python
> import boto3
> ec2 = boto3.client('ec2')
> response = ec2.describe_instances()
> print(response)
> ```
> 
> Este código utiliza el SDK de AWS para Python (**Boto3**) para realizar una llamada a la API al servicio EC2 y obtener información sobre las instancias de cómputo en ejecución.

---
# 🔒 Seguridad y Modelo de Responsabilidad Compartida de AWS

El **Modelo de Responsabilidad Compartida** de AWS define que la **seguridad y la conformidad** son una responsabilidad dividida entre **AWS** y el **cliente**. Este modelo se suele dividir conceptualmente en:

- **Seguridad _de_ la Nube** (Responsabilidad de AWS).

- **Seguridad _en_ la Nube** (Responsabilidad del Cliente).

![[Pasted image 20251201121717.png]]

---
## Responsabilidad de AWS: Seguridad **DE** la Nube

AWS es responsable de proteger la **infraestructura** que ejecuta los servicios en la Nube de AWS.

Esto incluye:

1. **Seguridad Física:** Proteger y asegurar las **Regiones, Zonas de Disponibilidad y Centros de Datos** (incluida la seguridad física de los edificios).

2. **Infraestructura Base:** Administrar el **hardware, software y componentes de red** que ejecutan los servicios, como los servidores físicos, los sistemas operativos _host_, las capas de virtualización y los componentes de redes de AWS.

> El nivel exacto de responsabilidad de AWS depende de si el servicio es más o menos gestionado.

---
## Responsabilidad del Cliente: Seguridad **EN** la Nube

El cliente es responsable de configurar y administrar **correctamente** los servicios de AWS que utiliza, garantizando la seguridad de sus datos y aplicaciones.

El nivel de responsabilidad del cliente también varía según el servicio de AWS utilizado (cuanto más abstracto y gestionado sea el servicio por AWS, menos responsabilidad de seguridad tendrá el cliente).

> [!example] Ejemplos Clave de Responsabilidad del Cliente
> 
> El cliente mantiene el control total de sus datos y es responsable de la seguridad relacionada con su contenido:
> 
> - **Protección de Datos:**
>     - Implementar mecanismos de protección de datos, como el **cifrado** y las **copias de seguridad** programadas.
>     - Elegir la **Región** para los recursos de AWS en conformidad con las normas de **soberanía de datos** aplicables.
> 
> - **Control de Acceso:**
>     - Usar el control de acceso (**IAM**) para limitar quién puede acceder a los datos y recursos de AWS.
> 
> - **Configuración:**
>     - Configuración correcta de _firewalls_ (Grupos de Seguridad, ACL de Red).
>     - Administración de los sistemas operativos (si aplica al servicio), el código de la aplicación y el contenido del cliente.

---
# 🔑 Protección del Usuario Raíz de AWS

El **Usuario Raíz de AWS** es la identidad de inicio de sesión inicial que se crea al configurar una cuenta de AWS. Posee **acceso total** a todos los servicios, recursos e información de facturación de la cuenta.

## Credenciales del Usuario Raíz

El usuario raíz tiene dos conjuntos de credenciales asociadas, que otorgan diferentes tipos de acceso:

1. **Consola de Administración:** La **dirección de correo electrónico** y la **contraseña** utilizadas para crear la cuenta.

2. **Acceso Programático (CLI/API):** Las **Claves de Acceso**, que constan de:
    - **ID de clave de acceso** (ejemplo: `A2lAl5EXAMPLE`)
    - **Clave de acceso secreta** (ejemplo: `wJalrFE/KbEKxE`)

## Prácticas Recomendadas para el Usuario Raíz

Dado que el usuario raíz tiene permisos ilimitados, es una **práctica recomendada de seguridad** no usarlo para tareas cotidianas. Las credenciales deben bloquearse de forma segura.

1. **Crear un Usuario IAM:** **Crear y utilizar un usuario de Identity and Access Management (IAM)** para todas las tareas administrativas o cotidianas.

2. **Contraseña Segura:** Elegir una **contraseña fuerte** y única.

3. **Habilitar MFA:** **Habilitar la autenticación multifactor (MFA)** para el usuario raíz.

4. **No Compartir:** **Nunca compartir** la contraseña o las claves de acceso del usuario raíz.

5. **Eliminar Claves de Acceso:** **Desactivar o eliminar** las claves de acceso asociadas al usuario raíz a menos que sea absolutamente necesario.


---

## 🔐 Autenticación Multifactor (MFA)

La MFA es un mecanismo de seguridad esencial que requiere **dos o más métodos de autenticación** para verificar una identidad, lo que proporciona una capa adicional de seguridad frente a contraseñas comprometidas.

La MFA utiliza información de dos o más de las siguientes categorías:

|**Categoría**|**Descripción**|**Ejemplo**|
|---|---|---|
|**Algo que sabes**|Información que solo tú conoces.|Nombre de usuario y contraseña, o un PIN.|
|**Algo que tienes**|Un objeto físico en tu poder.|Contraseña de un solo uso (OTP) de una aplicación móvil o dispositivo de hardware.|
|**Algo propio**|Una característica física inherente a ti.|Huella dactilar o tecnología de escaneo facial.|

Al habilitar la MFA para el usuario raíz de AWS, se requiere la combinación de:
- **Algo que sabes** (correo electrónico/contraseña).
- **Algo que tienes** (código numérico temporal de un dispositivo MFA).

## Dispositivos de MFA compatibles con AWS

AWS admite varios mecanismos de MFA:

|**Dispositivo**|**Descripción**|**Ejemplos de Dispositivos**|
|---|---|---|
|**MFA Virtual**|Aplicación de software en un teléfono que genera una contraseña de un solo uso (OTP) basada en tiempo (TOTP).|Google Authenticator, Microsoft Authenticator.|
|**Token TOTP de Hardware**|Dispositivo de hardware dedicado (como una clave o tarjeta) que genera códigos numéricos de un solo uso.|Clave única, tarjeta de visualización.|
|**Claves de Seguridad FIDO**|Claves de seguridad de hardware certificadas por FIDO (conectadas a un puerto USB).|Productos con certificado FIDO (ej. Yubico).|

---
