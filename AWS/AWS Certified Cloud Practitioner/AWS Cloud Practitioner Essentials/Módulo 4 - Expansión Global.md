```table-of-contents

```
---

# Introducción 

Expansión global con la infraestructura de AWS:
- Cómo elegir una región o un conjunto de regiones
- Ubicaciones periféricas de AWS: Las ubicaciones periféricas almacenan en caché elementos como imágenes, vídeos y otros recursos, para que los usuarios puedan acceder al contenido que necesitan con una latencia más baja.
- Infraestructura como código y CloudFormation: AWS cuenta con servicios, como CloudFormation, que puedes utilizar para automatizar el despliegue de los recursos en la nube. Estos servicios utilizan la infraestructura como código, o IaC (por sus siglas en inglés).

---

# Selección de las regiones de AWS

Cada región está aislada de las demás, en el sentido de que ningún dato entra ni sale de tu entorno en esa región si no concedes explícitamente permiso para traspasar esos datos.

Los datos de una región de AWS están sujetos a las leyes y estatutos locales del país en el que reside la región. La conformidad es la primera de las cuatro consideraciones que hay que tener al elegir una región.

El segundo factor es la proximidad. Cuán cerca estás de la base de clientes es un factor importante.

Tercero: características disponibles. A veces, puede que la región más cercana no tenga todas las características de AWS que deseas.

Por último, el cuarto factor es el precio. Incluso cuando los servicios y las características son iguales de una región a otra, operar en algunas ubicaciones es más rentable que en otras. Aspectos como los impuestos locales y los costes de energía influyen en la ecuación.

## Consideraciones clave a la hora de elegir regiones

![[Pasted image 20251013110912.png]]

- **Conformidad:** Cada región tiene sus propias leyes y normativas (por ejemplo, RGPD en la UE) que pueden exigir consentimiento, acceso y eliminación de datos personales.
    
- **Proximidad:** Cuanto más cerca esté la región de tus usuarios, menor será la latencia y mejor la experiencia.
    
- **Disponibilidad de características:** No todas las regiones ofrecen los mismos servicios; algunas tienen funciones especiales (como AWS GovCloud para agencias gubernamentales de EE. UU.).
    
- **Precios:** Los costes varían por región debido a factores operativos, fiscales y legales (incluidas leyes de soberanía de datos).

---

# Profundización en la infraestructura global de AWS

**En esta lección, aprenderás:**
- Cuáles son los beneficios clave de usar varias regiones y zonas de disponibilidad.
- Qué son las ubicaciones periféricas.
- Qué son las regiones, zonas de disponibilidad y ubicaciones periféricas, y sus diferencias.

## Diseño de arquitecturas de alta disponibilidad

 Desarrollar arquitecturas redundantes o replicar los recursos en en **varias regiones y zonas de disponibilidad** mejora la **alta disponibilidad** y la **fiabilidad** de las aplicaciones:

- La **alta disponibilidad** permite que los sistemas sigan funcionando incluso si fallan algunos componentes.    
- La **agilidad** facilita adaptarse y desplegar servicios rápidamente ante cambios del mercado o requisitos.    
- La **elasticidad** permite escalar automáticamente los recursos según la demanda, optimizando el uso y el coste.

---
## Ubicaciones periféricas

Las ubicaciones periféricas son sitios ubicados estratégicamente en todo el mundo que almacenan contenido en caché para entregar datos, vídeos y aplicaciones con una latencia más baja y velocidades de transferencia más altas. 

Las ubicaciones periféricas se consideran una parte vital de la red de entrega de contenido (CDN) de AWS y utilizan servicios como CloudFront para distribuir los datos de manera eficiente a los usuarios finales.

---
## Infraestructura y automatización

En esta lección, examinarás los métodos para automatizar estos tipos de despliegues. Las herramientas de infraestructura como código (IaC), como CloudFormation, pueden ayudarte a escalar los recursos de una ubicación a otra con un esfuerzo mínimo.

### Infraestructura como código (IaC)

Configurar recursos manualmente entre regiones es lento, propenso a errores y difícil de reproducir. La infraestructura como código (IaC) permite definir la infraestructura en archivos que actúan como esquemas.

Con IaC, puedes automatizar la creación y configuración de recursos según esas definiciones. Facilita repetir despliegues idénticos y rastrear cambios mediante control de versiones.

### CloudFormation

CloudFormation es un servicio que te ayuda a modelar y configurar los recursos de AWS. 

Con CloudFormation, puedes definir tu infraestructura como código. Puedes crear una plantilla donde se describan todos los recursos de AWS que deseas (como las instancias de Amazon Elastic Compute Cloud o Amazon EC2), y CloudFormation se encargará de aprovisionar y configurar esos recursos en tu lugar.

Ayuda a garantizar que los despliegues sean uniformes en diferentes entornos, como el desarrollo, las pruebas y la producción.

>[!tip] Recuerda
> Hay varias formas de operar en la nube de AWS. Para interactuar con los recursos de AWS, debes invocar las API de AWS. Para interactuar con estas API, puedes usar: 
>- **Acceso mediante programación (CLI y SDK):** ideal para desarrolladores; permite automatizar tareas (CLI) e integrar AWS en aplicaciones (SDK).
>- **Consola de administración:** interfaz web intuitiva para usuarios sin experiencia técnica; útil para gestión visual, facturación y servicios gráficos.
>- **Infraestructura como código (CloudFormation):** automatiza y estandariza la creación y gestión de recursos, clave para entornos **DevOps** y despliegues **CI/CD**.

---

# Resumen del módulo

En esta sección de la formación, has aprendido más sobre la infraestructura global de AWS. Ahora sabes cómo elegir una región, el valor de las ubicaciones periféricas y cómo usar servicios como CloudFormation para optimizar y automatizar el despliegue.
## Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

|Enlace del recurso|Descripción|
|---|---|
|[Infraestructura global de AWS](https://aws.amazon.com/about-aws/global-infrastructure/)|Obtén más información sobre la infraestructura global de AWS.|
|[AWS para las ubicaciones periféricas](https://aws.amazon.com/edge/?nc2=type_a)|Obtén más información sobre las ubicaciones periféricas y las redes periféricas de AWS.|
|[AWS CloudFormation](https://aws.amazon.com/cloudformation/)|Obtén más información sobre la infraestructura como servicio de código, CloudFormation.|
