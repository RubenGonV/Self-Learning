## ¿Qué es un modelo cliente-servidor?

Acabas de obtener más información sobre AWS y cómo casi toda la computación actual usa un modelo cliente-servidor básico. Vamos a recordar qué es un modelo cliente-servidor.

En computación, un cliente puede ser un navegador web o una aplicación de escritorio con la que una persona interactúa para efectuar solicitudes a los servidores informáticos. En el caso de un servidor, puede tratarse de servicios como Amazon Elastic Compute Cloud (Amazon EC2), un tipo de servidor virtual.

Por ejemplo, supongamos que un cliente solicita un artículo de noticias, la puntuación de un juego en línea o un vídeo divertido. El servidor evalúa los detalles de esta solicitud y responde a ella devolviendo la información al cliente.

## Modelos de despliegue de la computación en la nube

Los tres modelos de despliegue de la computación en la nube son: los basados en la nube, en las instalaciones o los híbridos.

### Despliegue basado en la nube
- Ejecuta todas las partes de la aplicación en la nube.
- Migra las aplicaciones existentes a la nube.
- Diseña y crea nuevas aplicaciones en la nube.

En un modelo de **despliegue basado en la nube**, puedes migrar aplicaciones existentes a la nube o diseñar y crear nuevas aplicaciones directamente desde allí. Puedes crear esas aplicaciones en una infraestructura de bajo nivel que requiera que su personal de TI las administre.
### Despliegue en las instalaciones
- Despliega recursos mediante herramientas de virtualización y administración de recursos.
- Aumenta la utilización de los recursos mediante el uso de tecnologías de virtualización y administración de aplicaciones.

**El** **despliegue en las instalaciones** también se conoce como despliegue de _nube privada_. En este modelo, los recursos se despliegan en las instalaciones mediante herramientas de virtualización y administración de recursos.
### Despliegue híbrido
- Conecta los recursos basados en la nube a la infraestructura en las instalaciones.
- Integra recursos basados en la nube con aplicaciones de TI heredadas.

En un **despliegue híbrido**, los recursos basados en la nube se conectan a la infraestructura en las instalaciones. Puede que desees usar esta estrategia en diversas situaciones. Por ejemplo, tienes aplicaciones heredadas que se mantienen mejor en las instalaciones o las regulaciones gubernamentales exigen que la empresa mantenga ciertos registros en las instalaciones.
## Beneficios de la computación en la nube

En resumen, los **beneficios de la computación en la nube** se agrupan en seis grandes categorías:

1. **De gasto inicial a gasto variable**: pagas solo por lo que usas.
2. **Deja de gastar dinero en mantener y operar centros de datos**: menos gestión de infraestructura, más foco en el negocio.
3. **Deja de hacer suposiciones sobre la capacidad**: ajustas recursos según la demanda real.
4. Beneficios de las grandes economías de escala**: precios más bajos gracias al uso compartido masivo.
5. **Aumento de la velocidad y la agilidad**: recursos disponibles en minutos, despliegue más rápido.
6. **Lograr un alcance global en minutos**: aplicaciones accesibles en todo el mundo con baja latencia.

---
# El modelo de responsabilidad compartida de AWS

![[Pasted image 20251013114337.png]]

El cliente es responsable de gestionar los requisitos de seguridad de sus datos, incluidos los datos que almacena en AWS y quién puede acceder a ellos. El cliente también controla cómo se concede, administra y revoca el acceso a los datos.

Según el servicio utilizado, las responsabilidades pueden cambiar entre el cliente y AWS. Los componentes como el cifrado del lado del servidor, la protección del tráfico de red, la administración de plataformas y aplicaciones y la configuración del sistema operativo, la red y el firewall varían según el servicio en cuanto a quién es responsable de estos elementos. A medida que conozcas más los distintos tipos de servicios, verás ejemplos específicos de cómo se dividen estos elementos entre el cliente y AWS.

Es responsabilidad de AWS proteger la infraestructura que ejecuta todos los servicios que se ofrecen en la nube de AWS. Esta infraestructura se compone del hardware, software, redes e instalaciones que ejecutan los servicios de la nube de AWS.