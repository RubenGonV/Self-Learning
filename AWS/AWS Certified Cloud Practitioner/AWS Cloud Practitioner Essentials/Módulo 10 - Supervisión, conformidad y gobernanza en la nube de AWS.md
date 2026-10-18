```table-of-contents
```
---
# Introducción a la supervisión, la conformidad y la gobernanza en la nube de AWS

Para supervisar de manera eficaz tus soluciones en la nube de Amazon Web Services (AWS), necesitarás formas de proporcionar información sobre el uso de los recursos, identificar posibles problemas y facilitar la resolución proactiva de los incidentes.

> [!info] Progresión de la gobernanza y la conformidad
> La progresión que normalmente debes usar es la siguiente:
> 
> ![[Pasted image 20251112100405.png]]
> 
> 1. **Proteger**: Protege los datos, los sistemas y la infraestructura contra el acceso, el uso, la divulgación, la interrupción, la modificación o la destrucción sin autorización.
> 2. **Supervisar**: Observa y analiza continuamente la actividad del sistema, el tráfico de la red y los eventos de seguridad para detectar posibles amenazas o anomalías.
> 3. **Auditar**: Revisa y evalúa periódicamente la eficacia de los controles de seguridad y verifica que se cumplan todos los requisitos, así como las políticas y procedimientos de seguridad.
> 4. **Cumplir con la conformidad**: Ayuda a garantizar que las prácticas y los controles de seguridad de una organización cumplan con los requisitos de las normativas pertinentes, los estándares del sector y las obligaciones contractuales.

---
# Supervisión

La supervisión de los recursos de la nube es importante. Proporciona una forma de observar y analizar continuamente la actividad del sistema, el tráfico de la red y los eventos de seguridad para detectar posibles amenazas o anomalías.

![[Pasted image 20251112100901.png]]

## Amazon CloudWatch

CloudWatch supervisa los recursos de AWS y las aplicaciones que ejecutas en AWS en tiempo real.

Con CloudWatch, obtienes visibilidad de todo el sistema sobre el uso de los recursos, el rendimiento de las aplicaciones y el estado de funcionamiento. CloudWatch no solo sirve para supervisar. Tiene varias características que funcionan en conjunto:

- **Métricas**: CloudWatch recopila las métricas de todos los recursos, aplicaciones y servicios de AWS que se ejecutan en los servidores locales y en AWS.
- **Alarmas**: Con las alarmas de CloudWatch, puedes definir umbrales en las métricas de CloudWatch y enviar notificaciones o realizar cambios automáticamente en los recursos.
- **Paneles**: Los paneles son páginas de inicio que pueden personalizarse en la consola de CloudWatch y que puedes usar para supervisar los recursos en una única vista.
- **Registros**: Los registros de CloudWatch centralizan los registros de todos los sistemas, las aplicaciones y los servicios de AWS que uses.

**Beneficios:** CloudWatch te ayuda a visualizar y analizar los recursos, operar de manera eficiente con la automatización, utilizar una vista integrada, supervisar de forma proactiva y obtener información.

## AWS CloudTrail

AWS CloudTrail permite registrar, supervisar y analizar la actividad dentro de una cuenta de AWS.

Imagina a una empresa financiera con una solución en la nube híbrida que intenta averiguar qué ocurre cuando se realizan cambios en sus recursos locales y en la nube. Necesita esta información para solucionar problemas y proporcionar registros detallados para garantizar la conformidad. Ahí es donde CloudTrail entra en acción.

CloudTrail hace un seguimiento de la actividad de los usuarios y el uso de las API en la nube de AWS, en las instalaciones locales e incluso con otros proveedores de nube. 

CloudTrail proporciona un historial detallado de las llamadas a la API para que puedas hacer un seguimiento de los cambios e identificar quién los ha hecho y cuándo. Esto te ayuda a comprender qué acciones se han llevado a cabo en los recursos de AWS.

**Beneficios:** CloudTrail proporciona auditoría, supervisión de la seguridad y solución de problemas operativos. También ayuda a demostrar la conformidad y a mejorar la posición de seguridad.

- **Eventos de CloudTrail:** recopilan información sobre acciones realizadas (llamadas a API, uso de la consola, etc.). El historial de eventos guarda los últimos 90 días de actividades administrativas sin coste adicional. Por ejemplo, un evento en una instancia de EC2 puede generar una alerta enviada a un teléfono.

- **Registros de CloudTrail:** almacenan los eventos en archivos dentro de un bucket de Amazon S3, garantizando seguridad y trazabilidad. Estos registros sirven para auditorías y cumplimiento de normativas como PCI o HIPAA.

- **CloudTrail Insights:** analiza patrones de uso y genera alertas cuando detecta anomalías en el volumen o tasa de errores de llamadas a la API, ayudando a identificar comportamientos inusuales o potencialmente problemáticos.

---
# Conformidad

La conformidad se refiere a que los recursos y datos en la nube cumplen con las normativas, los estándares del sector y las políticas internas pertinentes en relación con la seguridad y la protección de datos. AWS te ayuda a cumplir los objetivos y requisitos de conformidad de las siguientes maneras:

- Herencia de los controles de seguridad más recientes que AWS usa en su infraestructura
- Validación por parte de terceros para miles de requisitos globales
- Simplificación y automatización de la conformidad
- Informes de conformidad bajo demanda

## AWS Artifact

AWS Artifact es un servicio que proporciona acceso bajo demanda y gratuito a los informes de seguridad y conformidad de AWS, así como a determinados acuerdos en línea.

**Beneficios**: AWS Artifact te ayuda a administrar a escala, ahorrar tiempo con el acceso bajo demanda a los informes de conformidad y desplegar con más confianza.

### AWS Artifact Agreements
Supongamos que tu empresa necesita firmar un acuerdo con AWS en relación con el uso de determinados tipos de información en los servicios de AWS. Puedes hacerlo a través de AWS Artifact Agreements.

En AWS Artifact Agreements puedes revisar, aceptar y administrar los acuerdos de una cuenta individual y de todas tus cuentas de AWS Organizations. 

Se ofrecen diferentes tipos de acuerdos para abordar las necesidades de los clientes que están sujetos a regulaciones específicas, como la Ley de transferibilidad y responsabilidad del seguro sanitario (HIPAA).

### AWS Artifact Reports
A continuación, supongamos que un miembro del equipo de desarrollo de tu empresa está creando una aplicación y necesita más información sobre la responsabilidad de cumplir con ciertos estándares normativos. Puedes aconsejarle que acceda a esta información en AWS Artifact Reports.

AWS Artifact Reports proporciona informes de conformidad de auditores de terceros. 

Estos auditores han probado y verificado que AWS cumple una serie de estándares y regulaciones de seguridad globales, regionales, y específicas del sector. AWS Artifact Reports permanece actualizado con los últimos informes publicados. Puedes proporcionar a los auditores o reguladores dichos artefactos de auditoría de AWS como prueba de los controles de seguridad de AWS.

---
# Auditoría de los recursos de AWS para garantizar la conformidad

## AWS Config

AWS Config es un servicio que puedes utilizar para evaluar, auditar y examinar las configuraciones de tus recursos de AWS.

**Beneficios**: AWS Config ayuda a evaluar las configuraciones en función del estado deseado, administrar los cambios en la configuración de los recursos, así como simplificar la solución y rectificación de problemas.

## AWS Audit Manager

Audit Manager es un servicio que audita continuamente el uso de AWS para simplificar la evaluación de riesgos y conformidad. Ayuda a recopilar pruebas y administrar los datos de auditoría.

**Beneficios:** Audit Manager ahorra tiempo con la recopilación automatizada de pruebas, agiliza la colaboración entre los equipos y ayuda a garantizar la integridad de las auditorías con permisos de solo lectura.

## AWS Organizations

Organizations te ayuda a administrar y gobernar el entorno de forma centralizada a medida que creces y escalas los recursos de AWS. Te ayuda a administrar las políticas de los grupos de cuentas y a automatizar la creación de cuentas.

**Beneficios:** Organizaiones ofrecen varios beneficios, como escalar rápidamente el entorno mediante la creación con programación de nuevas cuentas de AWS para los recursos y los equipos. También simplifica la administración de los permisos a través de los SCP, así como la administración y optimización de los costes en tus cuentas y recursos de AWS.

### Conceptos clave de Organizations

En AWS, una **organización** agrupa varias cuentas que se gestionan de forma centralizada mediante una estructura jerárquica con una **raíz** y posibles **unidades organizativas (UO)**.

- **Cuenta de administración:** es la cuenta principal que crea la organización y gestiona el control, la gobernanza y la facturación.

- **Unidades organizativas (UO):** agrupan cuentas o incluso otras UO para aplicar políticas de forma conjunta.

- **Políticas de control de servicios (SCP):** establecen restricciones sobre qué servicios, recursos o acciones de API pueden usarse dentro de cuentas o UO específicas.

- **Cuentas de miembro fuera de una UO:** pueden existir directamente bajo la raíz si tienen necesidades particulares, manteniendo beneficios como la facturación unificada.

---
# Gobernanza

A medida que una organización escala verticalmente, puede tener dificultades para administrar los servicios y las cuentas, incluidas las nuevas cuentas de AWS, los servicios de AWS que eligen e incluso las licencias de software.

En esta lección, revisaremos los tres servicios de AWS que pueden ayudar a administrar y aplicar los servicios y las cuentas para cumplir con los requisitos de tu empresa:

- AWS Control Tower
- AWS Service Catalog
- AWS License Manager

## AWS Control Tower

AWS Control Tower es un servicio que puedes usar para aplicar y administrar las reglas de gobernanza para la seguridad, las operaciones y la conformidad a escala en todas tus organizaciones y cuentas en la nube de AWS.

**Beneficios**: acelera la configuración de entornos multi-cuenta con controles predefinidos, automatización y soporte para herramientas de terceros.

- **Panel:** ofrece supervisión continua y detección de recursos no conformes.
- **Account Factory:** permite crear cuentas nuevas de forma estandarizada mediante plantillas configurables.
- **Controles (barreras de protección):** definen reglas de gobernanza que garantizan el cumplimiento y la seguridad.
- **Zona de aterrizaje:** entorno multi-cuenta estructurado según buenas prácticas (Well-Architected), que agrupa todas las UO, cuentas y recursos bajo un marco común de conformidad.

## AWS Service Catalog

Con Service Catalog, puedes crear, compartir y organizar a partir de un catálogo seleccionado de recursos de AWS. Puedes desplegar herramientas de seguridad y recursos de red básicos para las nuevas cuentas de AWS y así gobernar de manera coherente.

**Beneficios**: Service Catalog ahorra tiempo al facilitar la búsqueda y el despliegue de recursos de autoservicio aprobados en la nube. También ayuda a mantenerse ágil a medida que se mejora la gobernanza de los recursos en varias cuentas.

**Casos prácticos:** úsalo para aprovisionar recursos en las cuentas de AWS, aplicar controles de acceso y agilizar el aprovisionamiento de canalizaciones (CI/CD) de integración continua y entrega continua.

### AWS License Manager

License Manager es un servicio que te ayuda a administrar las licencias de software y ajustar los costes de licencias.

**Beneficios:** License Manager ayuda con la visibilidad y el control, el seguimiento y la administración de las licencias, y la disminución del riesgo de incumplimiento de las licencias.

**Casos prácticos:** úsalo para agilizar la administración de licencias y simplificar la experiencia de Movilidad de licencias mediante Software Assurance. También puedes usarlo para automatizar la distribución y la activación de los derechos de software en las cuentas de AWS para los usuarios finales.

---
# AWS Health

AWS Health es el origen de datos de referencia para los eventos y cambios que afectan al estado de tus recursos en la nube de AWS. Te avisa sobre los eventos de servicio, los cambios planificados y las notificaciones de la cuenta para ayudarte a administrar y tomar medidas.

### Panel de AWS Health

Con el panel de AWS Health, puedes ver la información de estado específica de la cuenta y obtener actualizaciones sobre los eventos de AWS Health. También puedes usar AWS Health mediante programación con la API de AWS Health, que está disponible con AWS Premium Support.

**Beneficios:** el panel de AWS Health proporciona información valiosa como un origen de datos para eventos y cambios. Te aporta orientación oportuna y práctica para solucionar los problemas. También ayuda a administrar el estado de los servicios y está integrado y automatizado para su uso a escala.

**Casos prácticos:** usa el panel de AWS Health para ver la información de estado específica de la cuenta. También puedes usarlo para planificar eventos del ciclo de vida o solucionar un incidente.

---

# AWS Trusted Advisor

Es muy importante optimizar los despliegues de nube a gran escala y no es una tarea que se haga una sola vez. Debes buscar maneras de optimizar los costes, el rendimiento, la seguridad y la resiliencia. 

Con AWS Trusted Advisor, puedes evaluar de forma continua el entorno de AWS mediante comprobaciones de las prácticas recomendadas en varias categorías. 

Todos los planes de AWS Support incluyen acceso a docenas de comprobaciones de Trusted Advisor. Con Business Support y otros planes avanzados, puedes beneficiarte de cientos de comprobaciones.

**Beneficios:** Trusted Advisor te ayuda a alinearte con las prácticas recomendadas de AWS, priorizar las recomendaciones y optimizar tus recursos de AWS a escala.

**Casos prácticos:** se puede usar para optimizar el coste, la eficiencia, la seguridad, mejorar el rendimiento y hacer un seguimiento de los límites de servicio.

## Analizador de acceso de IAM

Aunque Trusted Advisor hace comprobaciones para optimizar la seguridad, es posible que necesites ayuda para comprobar los permisos detallados de AWS Identity and Access Management (AWS IAM).

El Analizador de acceso de IAM ofrece funciones para establecer, verificar y refinar los permisos mediante el análisis del acceso externo y la validación de que las políticas coincidan con los estándares de seguridad corporativos.

**Beneficios**: el Analizador de acceso de IAM ofrece beneficios como limitar los permisos, validar las políticas de IAM, ayudarte a cumplir los objetivos de mínimo privilegio y automatizar las revisiones de las políticas de IAM.

**Casos prácticos**: se puede usar para establecer permisos detallados, verificar quién puede acceder a qué, corregir el acceso no usado, y ajustar y eliminar el acceso amplio.

---
# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| Enlace del recurso                                                                                                     | Descripción                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)                                  | CloudWatch supervisa los recursos de AWS y las aplicaciones que se ejecutan en AWS en tiempo real. Con CloudWatch, obtienes visibilidad de todo el sistema sobre el uso de los recursos, el rendimiento de las aplicaciones y el estado de funcionamiento.                                                                                 |
| [AWS CloudTrail](https://aws.amazon.com/cloudtrail/)                                     | CloudTrail permite la auditoría, la supervisión de seguridad y la solución de problemas operativos. CloudTrail registra la actividad de los usuarios y las llamadas a la API en los servicios de AWS como eventos. Los eventos de CloudTrail ayudan a responder a la pregunta “¿Quién hizo qué, dónde y cuándo?”.                          |
| [AWS Artifact](https://aws.amazon.com/artifact/)                                         | AWS Artifact es un portal de autoservicio que proporciona acceso bajo demanda a la documentación de seguridad y conformidad de AWS, incluidos informes, certificaciones y acuerdos.                                                                                                                                                        |
| [AWS Config](https://aws.amazon.com/config/)                                             | AWS Config es un servicio para evaluar, auditar y examinar las configuraciones de los recursos de AWS.                                                                                                                                                                                                                                     |
| [AWS Audit Manager](https://aws.amazon.com/audit-manager/)                               | Audit Manager es un servicio para auditar continuamente el uso de AWS con el fin de agilizar la evaluación de riesgos y conformidad.                                                                                                                                                                                                       |
| [AWS Organizations](https://aws.amazon.com/organizations/)                               | Organizations te ayuda a administrar y gobernar el entorno de forma centralizada a medida que creces y escalas los recursos de AWS. Te ayuda a administrar las políticas de los grupos de cuentas y a automatizar la creación de cuentas.                                                                                                  |
| [AWS Control Tower](https://aws.amazon.com/controltower/)                                | Con AWS Control Tower se pueden aplicar y administrar las reglas de gobernanza para la seguridad, las operaciones y la conformidad a escala en todas las organizaciones y cuentas en la nube de AWS.                                                                                                                                       |
| [AWS Service Catalog](https://aws.amazon.com/servicecatalog/)                            | Con Service Catalog se puede crear, compartir y organizar a partir de un catálogo seleccionado de recursos de AWS. Puedes desplegar herramientas de seguridad y recursos de red básicos para las nuevas cuentas de AWS para poder gestionarlas de manera sistemática.                                                                      |
| [AWS License Manager](https://aws.amazon.com/license-manager/)                           | License Manager es un servicio que te ayuda a administrar las licencias de software y ajustar los costes de licencias.                                                                                                                                                                                                                     |
| [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) | Trusted Advisor ayuda a optimizar los costes, aumentar el rendimiento, mejorar la seguridad y la resiliencia, y operar a gran escala en la nube. Evalúa continuamente el entorno de AWS mediante comprobaciones de las prácticas recomendadas en esas categorías y recomienda acciones para corregir las desviaciones de dichas prácticas. |
| [AWS Health](https://aws.amazon.com/premiumsupport/technology/aws-health/)               | AWS Health es el origen de datos para los eventos y cambios que afectan a los recursos en la nube de AWS. AWS Health avisa sobre los eventos de servicio, los cambios planificados y las notificaciones de la cuenta para ayudar a administrar y tomar medidas.                                                                            |
| [Analizador de acceso de AWS IAM](https://aws.amazon.com/iam/access-analyzer/)           | El Analizador de acceso de IAM ofrece funciones para establecer, verificar y ajustar los permisos de seguridad para lograr los estándares de seguridad con mínimo privilegio.                                                                                                                                                              |
