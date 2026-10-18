
```table-of-contents
```
---

# Precios de AWS

AWS ofrece a la clientela un enfoque de pago por uso para fijar los precios de la gran mayoría de nuestros servicios en la nube. Con AWS, solo se paga por los servicios individuales que se necesitan, mientras se usen y sin necesidad de contratos a largo plazo ni licencias complejas.

- **Pago por uso:** Solo pagas por lo que utilizas, lo que evita gastar de más o quedarte corto en capacidad.
- **Ahorro con compromiso:** Si te comprometes a usar ciertos servicios durante 1 o 3 años, puedes obtener descuentos importantes (como con Savings Plans).
- **Menor coste al aumentar uso:** Algunos servicios reducen su precio por volumen, así que cuanto más los uses, menos pagas por unidad.

Si bien los precios influyen en varias categorías de servicios, los p**rincipales factores que impulsan el coste** son la computación, el almacenamiento y la transferencia de datos.
## 1. Computación

Pagas por el tiempo que las instancias están encendidas (por hora o por segundo).
Si no reservaste capacidad, pagas mientras el recurso está activo. 

## 2. Almacenamiento

Los precios dependen del tipo de almacenamiento, la capacidad usada o aprovisionada y cómo accedes a los datos.
Con Amazon S3, ten en cuenta los seis componentes de coste siguientes al almacenar y administrar los datos de clientes:
- Precios de almacenamiento
- Precios de solicitud y recuperación de datos
- Precios de transferencias y aceleración de transferencias de datos
- Precios de análisis y administración de datos
- Precios de replicación
- El precio del procesamiento de datos con Amazon S3 Object Lambda

## 3. Transferencia de datos

En la mayoría de los casos, la **transferencia de datos de entrada** o **entre los servicios de AWS** de la misma región es gratuita.

La **transferencia de datos de salida** se agrega en los servicios y, a continuación, se cobra según la tarifa de transferencia de datos de salida. Cuantos más datos transfieras, menos pagarás por gigabyte.

---

# Servicios de precios y facturación de AWS

## AWS Organizations

AWS Organizations proporciona una administración y una gobernanza centralizadas de tu entorno de AWS. Con AWS Organizations, puedes crear, agrupar y administrar cuentas. También puedes aplicar políticas de seguridad a nivel de cuenta y unificar la facturación con varias cuentas mediante una única forma de pago.

Casos prácticos:
- Unificar varias cuentas de AWS en una organización central
- Implementar políticas en toda la organización

## Panel de Administración de facturación y costes de AWS

El panel de Administración de facturación y costes de AWS centraliza la administración de costes y muestra los cargos, el uso, las previsiones y los desgloses detallados actuales. También proporciona herramientas para administrar pagos, ver facturas, establecer presupuestos y unificar la facturación.

Casos prácticos:
- Usar visualizaciones e informes de facturación útiles sobre el gasto mensual en AWS
- Configurar y administrar las formas de pago

## AWS Budgets

AWS Budgets ayuda a establecer presupuestos personalizados y envía alertas cuando los costes, el uso, o la cobertura o el uso de Savings Plans y las instancias reservadas (RI) superan los umbrales definidos.

Casos prácticos:
- Configurar alertas para cuando los costes proyectados superen los umbrales predefinidos
- Predecir los gastos futuros en función de las tendencias de uso actuales

## AWS Cost Explorer

AWS Cost Explorer ayuda a visualizar, analizar y administrar los costes y el uso de AWS con gráficos, informes, y predicciones interactivos. Proporciona información sobre los patrones de gasto, las tendencias y las recomendaciones de instancias reservadas.

Casos prácticos:
- Analizar las tendencias históricas de gasto para identificar oportunidades de ahorro de costes
- Predecir los costes futuros de AWS en función de los patrones de uso actuales para presupuestar de manera eficaz

## Calculadora de precios de AWS

Otra herramienta útil es la Calculadora de precios de AWS. La Calculadora de precios de AWS es una herramienta de planificación basada en la web que puedes utilizar para crear estimaciones. Introduces configuraciones específicas, como tipos de instancias, opciones de almacenamiento y volúmenes de transferencia de datos. Después, según las configuraciones, recibirás un desglose detallado de los costes para ayudarte a presupuestar la asignación de recursos de AWS.

Casos prácticos:
- Estimar los costes potenciales antes del despliegue
- Comparar los costes de los diferentes servicios y configuraciones de AWS

---
# AWS Support

>[!info] Tipos de AWS Support
>![[Pasted image 20251119121651.png]]

AWS ofrece una gama de planes de soporte diseñados para satisfacer las necesidades de los diferentes clientes, desde los que acaban de empezar hasta las grandes empresas con requisitos complejos. 

Cada plan se basa en el anterior y agrega herramientas más avanzadas, soporte personalizado y tiempos de respuesta más rápidos para ayudarte a aprovechar al máximo tu experiencia con AWS. 

Para obtener más información sobre qué plan es el adecuado para ti, consulta [Compare AWS Support Plans](https://aws.amazon.com/premiumsupport/plans/). (Comparar los planes de AWS Support)

Para revisar las diferencias entre los planes, consulta la siguiente tabla.

|Basic Support|Developer Support|Business Support|Enterprise On-Ramp Support|Enterprise Support|
|---|---|---|---|---|
|Incluido para todos los clientes de AWS|Recomendado para experimentar o hacer pruebas en AWS|Nivel mínimo recomendado para las cargas de trabajo de producción en AWS|Recomendado para cargas de trabajo críticas empresariales y de producción en AWS|Recomendado para cargas de trabajo críticas para la empresa y la misión en AWS|
|Acceso a documentación, documentos técnicos y AWS re:Post incluido|Tiempos de respuesta:  <br>• Menos de 24 horas para orientación general• Menos de 12 horas cuando los sistemas están dañados|Tiempos de respuesta:  <br>• _Tiempos de respuesta del plan anterior incluidos_  <br>• Menos de 4 horas cuando el sistema de producción está dañado  <br>• Menos de 1 hora cuando el sistema de producción está inactivo|Tiempos de respuesta:  <br>• _Tiempos de respuesta del plan anterior incluidos_  <br>• Menos de 30 minutos cuando un sistema crítico para la empresa está inactivo|Tiempos de respuesta:  <br>• _Tiempos de respuesta del plan anterior incluidos_  <br>• Menos de 15 minutos cuando un sistema empresarial o crítico está inactivo|
|Comprobaciones principales de AWS Trusted Advisor|Comprobaciones principales de AWS Trusted Advisor|Conjunto completo de comprobaciones de AWS Trusted Advisor|Conjunto completo de comprobaciones de AWS Trusted Advisor|Conjunto completo de comprobaciones de AWS Trusted Advisor y recomendaciones priorizadas por parte del equipo de cuentas de AWS|
|Administración técnica de cuentas no incluida|Administración técnica de cuentas no incluida|Administración técnica de cuentas no incluida|Grupo de administradores técnicos de cuenta (TAM) para la orientación proactiva|TAM designado para la orientación de consultas sobre arquitectura y operación|

## Recursos adicionales para el traspaso a la nube

AWS ofrece varios recursos para facilitar la migración a la nube:

- **AWS re:Post:** Comunidad de preguntas y respuestas, más el Knowledge Center con guías y soluciones comunes.    
- **Centro de confianza y seguridad:** Información para reportar abuso o problemas relacionados con seguridad.
- **Arquitectos de soluciones:** Disponible con planes Business y Enterprise para asesoría técnica y de diseño.
- **AWS Professional Services:** Consultoría especializada para proyectos complejos, migraciones y optimización.
- **Autoasistencia:** Documentación extensa con guías, blogs, ejemplos y material técnico para aprender por tu cuenta.

---
# AWS Marketplace y socios de AWS

## AWS Marketplace

AWS Marketplace es un catálogo digital que incluye miles de ofertas de software de proveedores de software independientes. 

Puedes utilizar AWS Marketplace para buscar, probar y comprar software que se ejecute en AWS. 

En cada oferta de AWS Marketplace, puedes acceder a información detallada sobre opciones de precios y opiniones de otros clientes de AWS. 

Entre las soluciones y los servicios que se ofrecen en AWS Marketplace se incluyen:

- **Software como servicio (SaaS):**
    - Aplicaciones empresariales, como herramientas de administración de proyectos
    - Herramientas de marketing, como las plataformas de interacción con clientes
    - Herramientas de colaboración, como los servicios de intercambio de archivos.

- **Machine learning (ML) e IA:**    
    - Modelos prediseñados para el reconocimiento de imágenes, el procesamiento del lenguaje natural y más.        
    - Algoritmos de ML para entrenar modelos personalizados.

- **Datos y análisis:**
    - Plataformas de inteligencia empresarial para visualización e informes
    - Herramientas de integración de datos

## Red de socios de AWS

La **Red de socios de AWS (APN)** es una comunidad global que colabora con AWS para crear soluciones y servicios innovadores.

- **Colaboración con socios:** Las empresas pueden asociarse para soluciones especializadas, como mejorar la personalización de clientes con machine learning.

- **Convertirse en socio:** Ofrece beneficios como:
    - **Financiación:** Apoyo para crear, comercializar y vender soluciones con AWS.
    - **Eventos:** Webinars, talleres y networking con otros socios y expertos de AWS.
    - **Formación y certificación:** Capacitación exclusiva para mejorar habilidades en la nube y obtener certificaciones.

---
# Optimización de costes

## Amazon EC2

- **Redimensionamiento:** Ajustar instancias al tamaño adecuado según la carga de trabajo. Herramientas como **AWS Compute Optimizer** ayudan a identificar instancias sobreaprovisionadas.

- **Instancias de Spot:** Usar la capacidad sobrante de EC2 con descuentos de hasta el 90 % para cargas flexibles y no críticas.

- **Escalado automático:** **AWS Auto Scaling** elimina exceso de capacidad cuando baja la demanda; el **balanceo de carga** distribuye tráfico entre instancias para eficiencia.

- **Limpieza de recursos:** Revisar volúmenes EBS, snapshots y otros recursos sin uso para evitar gastos innecesarios.

## Amazon RDS

- **Redimensionamiento:** Ajustar instancias a la demanda real para evitar sobreaprovisionamiento o insuficiencia de recursos.

- **Escalado automático de almacenamiento:** RDS ajusta el almacenamiento según necesidad, evitando aprovisionamiento excesivo.

- **Réplicas de lectura:** Escalan horizontalmente la capacidad de lectura sin aumentar la instancia principal.

- **Almacenamiento en caché (ElastiCache):** Reduce la carga sobre la instancia principal y mejora el rendimiento.

## Amazon S3

- **Clases de almacenamiento:**
    - **S3 Glacier Deep Archive:** Bajo coste para datos accedidos raramente (1–2 veces al año).
    - **S3 Intelligent-Tiering:** Optimiza costes para patrones de acceso desconocidos o variables.

- **Compresión y políticas de ciclo de vida:** Comprimir objetos automáticamente (Lambda) y eliminar versiones antiguas para reducir costes.

- **Puntos de enlace de VPC:** Acceso privado a S3 sin pasar por Internet público, reduciendo costes de transferencia de datos, especialmente fuera de la región.

## Consideraciones generales

- Minimizar tráfico entre zonas de disponibilidad y hacia Internet reduce costes de transferencia de datos.

- Optimizar la arquitectura en conjunto (EC2 + RDS + S3) genera ahorros significativos y mejora **rendimiento y fiabilidad**.

- La optimización se basa en el equilibrio entre **coste, rendimiento y eficiencia operativa**.

---
# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

|Enlace del recurso|Descripción|
|---|---|
|[Precios de Amazon S3](https://aws.amazon.com/s3/pricing/?nc=sn&loc=4)|En la página de precios de Amazon S3 se detallan los costes de almacenamiento, solicitudes, transferencia de datos y funciones adicionales, junto con información sobre el nivel gratuito de AWS para nuevos clientes.|
|[Precios bajo demanda de Amazon EC2](https://aws.amazon.com/ec2/pricing/on-demand/)|En la página de precios bajo demanda de Amazon EC2 se detallan los costes de las instancias de EC2, incluidos los precios de los tipos de instancias, la transferencia de datos y las funciones adicionales sin compromisos a largo plazo.|
|[¿Qué es AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)|En la guía del usuario de AWS Organizations se explica cómo administrar de forma centralizada varias cuentas de AWS, automatizar la creación de cuentas, aplicar políticas de gobernanza y simplificar la facturación y el intercambio de recursos.|
|[Consola de facturación de AWS](https://aws.amazon.com/aws-cost-management/aws-billing/)|La Consola de facturación de AWS proporciona una plataforma centralizada para administrar y comprender los cargos de AWS, además de ofrecer herramientas para ver y descargar las facturas, supervisar los descuentos y los créditos, y analizar las tendencias de gastos en varias cuentas.|
|[AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/)|AWS Budgets proporciona herramientas para crear presupuestos personalizados para el seguimiento y la administración de los costes y el uso de AWS, así como el uso de instancias reservadas o Savings Plans. También ayuda a evitar gastos excesivos al ofrecer alertas y acciones automatizadas.|
|[AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)|AWS Cost Explorer proporciona herramientas para visualizar, analizar y administrar los costes y el uso de AWS mediante informes personalizables y previsiones de costes para optimizar el gasto en la nube.|
|[Documentación de Calculadora de precios de AWS](https://docs.aws.amazon.com/pricing-calculator/)|La Calculadora de precios de AWS es una herramienta gratuita basada en la web que ayuda a crear estimaciones detalladas de los costes de los servicios de AWS, de modo que pueda planificar y administrar sus gastos en la nube de manera eficaz.|
|[AWS re:Post](https://repost.aws/)|AWS re:Post es una plataforma de preguntas y respuestas impulsada por la comunidad en la que los usuarios pueden buscar ayuda, compartir conocimientos y encontrar soluciones relacionadas con los servicios y las tecnologías de AWS.|
|[Centro de confianza y seguridad de AWS](https://repost.aws/aws-trust-and-safety)|El Centro de confianza y seguridad de AWS ofrece orientación sobre cómo denunciar el abuso, proteger las aplicaciones y seguir las prácticas recomendadas para la mensajería digital en AWS.|
|[AWS Professional Services](https://aws.amazon.com/professional-services/)|En la página de AWS Professional Services se destaca cómo los expertos de AWS ayudan a las organizaciones a acelerar la adopción de la nube con una orientación personalizada para todos los sectores y tecnologías.|
|[Bienvenido a la documentación de AWS](https://docs.aws.amazon.com/index.html)|En la página de documentación de AWS se proporcionan recursos técnicos completos, que incluyen guías, referencias de API, tutoriales y prácticas recomendadas para todos los servicios de AWS.|
|[AWS Marketplace](https://aws.amazon.com/marketplace)|AWS Marketplace es un catálogo digital en el que la clientela puede descubrir, comprar y administrar software, datos y servicios de terceros con opciones de precios flexibles.|
|[Interactúa con socios de AWS](https://partners.amazonaws.com/)|En la página de socios de AWS encontrarás información para descubrir cómo los socios de AWS pueden ayudarte a agilizar el traspaso a la nube.|
|[Beneficios de financiación para los socios de AWS](https://aws.amazon.com/partners/funding/)|En la página de financiación de socios de AWS se describen los beneficios de financiación, incluidos créditos y descuentos, para ayudar a los socios de AWS a desarrollar, comercializar y vender soluciones basadas en AWS.|
|[Eventos para socios de AWS](https://aws.amazon.com/events/aws-partner-events/?events-master-all.sort-by=item.additionalFields.startDateTime&events-master-all.sort-order=asc&awsf.events-master-type=*all&awsf.events-master-tech-category=*all&awsf.events-master-location=*all)|En la página de eventos para socios de AWS se muestran los próximos webinars, talleres y eventos presenciales para profesionales de las TI, desarrolladores y líderes empresariales, con opciones para filtrar por fecha, ubicación y tema.|
|[Capacitación y certificación para socios de AWS](https://aws.amazon.com/partners/training/?nc2=sb_pt_pto)|En la página de formación para socios de AWS se ofrecen cursos, certificaciones y recursos para ayudar a los socios de AWS a desarrollar habilidades sobre la nube en diversas funciones y mejorar su experiencia.|
