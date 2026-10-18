```table-of-contents
```

---
# IA/ML en AWS

La pila de IA/ML de AWS se compone de los tres niveles de soluciones siguientes:

- **Servicios de IA**: modelos prediseñados que ya están entrenados para realizar funciones específicas.
- **Servicios de ML**: un enfoque más personalizado con Amazon SageMaker AI en el que puedes crear, entrenar y desplegar tus propios modelos de machine learning con una infraestructura completamente administrada.
- **Infraestructura y marcos de trabajo de ML**: un enfoque completamente personalizado para desarrollar modelos con chips diseñados específicamente que se integran con los marcos de trabajo de machine learning más conocidos.

---
# Servicios de IA de AWS prediseñados
La capa de servicios de IA de AWS se compone de modelos prediseñados que ya están entrenados para realizar funciones específicas.

## Servicios lingüísticos
Los servicios lingüísticos de IA de AWS son ideales cuando necesitas interpretar texto o voz y transformarlo en algo significativo. 

- **Amazon Comprehend:** Servicio de procesamiento de lenguaje natural (NLP) que extrae información clave de textos, como frases, idioma y sentimientos.  
- **Amazon Polly:** Convierte texto en voz realista con soporte para múltiples idiomas, géneros y acentos.  
- **Amazon Transcribe:** Transforma voz en texto, con identificación de hablantes, vocabulario personalizado y transcripción en tiempo real.  
- **Amazon Translate:** Ofrece traducción automática de texto en tiempo real o por lotes, con soporte multilingüe.  
### Servicios de visión artificial y búsqueda
Estos servicios son ideales para responder preguntas y recopilar información de varios tipos de orígenes de contenido, como documentos, imágenes, vídeos y mucho más. 

- **Amazon Kendra:** Utiliza procesamiento de lenguaje natural para buscar respuestas en grandes volúmenes de contenido empresarial, comprendiendo el contexto de las consultas para ofrecer resultados más precisos y relevantes.  
- **Amazon Rekognition:** Servicio de análisis de vídeo e imágenes que identifica objetos, personas, textos, escenas y actividades en contenido almacenado en Amazon S3.  
- **Amazon Textract:** Detecta y extrae texto mecanografiado o manuscrito de documentos, formularios y tablas para su procesamiento automatizado.  

### Servicios de personalización e IA conversacional
Con estos servicios, los usuarios pueden interactuar con tus aplicaciones a través de conversaciones de texto y voz. También puedes mostrar a tus clientes recomendaciones de productos personalizadas exclusivas para ella.

- **Amazon Lex:** Permite añadir interfaces de conversación de voz y texto a las aplicaciones mediante comprensión del lenguaje natural (NLU) y reconocimiento automático de voz (ASR) para generar interacciones realistas.  
- **Amazon Personalize:** Utiliza datos históricos para crear aplicaciones con recomendaciones personalizadas adaptadas al comportamiento y preferencias de los usuarios.  


## Servicios de machine learning
El nivel de servicios de machine learning proporciona un enfoque más personalizado para quienes quieran tener un poco más de control sobre sus soluciones de ML sin tener que administrar la infraestructura. SageMaker AI es una oferta clave en este nivel.

### Amazon SageMaker AI
Servicio completamente gestionado para desarrollar, entrenar y desplegar modelos de *machine learning* sin preocuparse por la infraestructura. Incluye un entorno de desarrollo integrado (IDE) que permite gestionar experimentos, visualizar datos y supervisar flujos de trabajo, además de ofrecer modelos preentrenados listos para usar.  

  Principales beneficios:  
  - Selección de herramientas: Permite elegir entre un IDE para científicos de datos o una interfaz sin código para analistas.  
  - Infraestructura administrada: Proporciona una plataforma de alto rendimiento y rentable para centrarse en el desarrollo de modelos.  
  - Flujos de trabajo repetibles: Facilita la automatización y estandarización de procesos de MLOps con transparencia y capacidad de auditoría.  


## Infraestructuras y marcos de trabajo de ML

Algunas organizaciones tienen necesidades muy especializadas que requieren un control total sobre el proceso de entrenamiento de ML. Pueden utilizar la experiencia interna, los marcos de trabajo de ML y la infraestructura de AWS para desarrollar sus propias soluciones de ML.

La infraestructura de ML de AWS, como las instancias optimizadas para ML de Amazon Elastic Compute Cloud (Amazon EC2), Amazon EMR, y Amazon Elastic Container Service (Amazon ECS), pueden respaldar estas soluciones personalizadas. Estos servicios proporcionan rendimiento y flexibilidad elevados para las cargas de trabajo de ML avanzadas.

---

# IA generativa en AWS

AWS ofrece los siguientes tipos de soluciones de IA generativa:

- **Amazon SageMaker JumpStart**: un centro de ML con modelos fundacionales y soluciones de ML prediseñadas que se pueden implementar con unos pocos clics.
- **Amazon Bedrock**: un servicio completamente administrado para adaptar e implementar modelos fundacionales de Amazon y otras empresas líderes de inteligencia artificial.
- **Amazon Q**: un asistente de IA interactivo que se puede integrar con los repositorios de información de una empresa.

## Amazon SageMaker JumpStart

Centro de *machine learning* dentro de SageMaker AI que acelera la creación, entrenamiento y despliegue de modelos. Ofrece una biblioteca de soluciones y modelos preentrenados en dominios como visión artificial, NLP y datos tabulares, que pueden personalizarse y desplegarse fácilmente.  

  **Principales beneficios:**  
  - **Despliegues rápidos:** Permite implementar modelos preentrenados sin necesidad de experiencia avanzada en ML.  
  - **Soluciones personalizadas:** Facilita el ajuste de modelos preentrenados con datos específicos del dominio.  
  - **Prototipado ágil:** Permite comparar y experimentar con distintos modelos antes de adoptar una solución definitiva.  

## Amazon Bedrock

Servicio completamente gestionado diseñado para trabajar con modelos fundacionales y crear aplicaciones de IA generativa. Ofrece acceso a modelos de Amazon y de terceros (como Claude o Stable Diffusion) mediante una API unificada. Permite experimentar, ajustar modelos con datos propios e integrarlos fácilmente en aplicaciones de AWS.  

  **Principales beneficios:**  
  - **IA generativa empresarial:** Facilita el desarrollo de aplicaciones de IA generativa seguras, escalables y listas para producción.  
  - **Generación multimodal:** Permite crear aplicaciones que generen texto, imágenes y otros tipos de contenido.  
  - **IA conversacional avanzada:** Desarrolla agentes conversacionales que se conectan a datos empresariales para ofrecer respuestas precisas.  

## Amazon Q

Asistente de IA generativa diseñado para mejorar la productividad, acelerar la toma de decisiones y optimizar procesos empresariales.  

  **Componentes principales:**  
  - **Amazon Q Business:** Responde preguntas, resuelve problemas y automatiza acciones conectándose de forma segura a los sistemas internos de la empresa.  
  - **Amazon Q Developer:** Ofrece recomendaciones y generación de código para múltiples lenguajes (C#, Java, JavaScript, Python, TypeScript), integrándose con IDEs para acelerar el desarrollo y mejorar la calidad del código.  

---
# Pipelines de datos (ETL) en AWS

## Servicios de canalización de datos de AWS  

Los servicios de AWS permiten construir canalizaciones completas para la **ingesta, almacenamiento, catalogación, procesamiento, análisis y visualización** de datos.

### Servicios de ingesta de datos  
Permiten transferir datos desde los sistemas de origen a la solución de almacenamiento, en tiempo real o por lotes.  
- **Amazon Kinesis Data Streams:** Ingesta en tiempo real de grandes volúmenes de datos de aplicaciones, transmisiones y sensores, con escalado automático sin servidor.  
- **Amazon Data Firehose:** Ingesta casi en tiempo real y entrega de datos en segundos a lagos de datos, almacenes o servicios de análisis.  

### Servicios de almacenamiento de datos  
Consolidan datos procedentes de múltiples orígenes en ubicaciones centralizadas.  
- **Amazon S3:** Almacenamiento de objetos seguro, elástico y escalable para datos estructurados o no estructurados.  
- **Amazon Redshift:** Almacén de datos completamente gestionado y escalable para análisis de grandes volúmenes de datos estructurados o semiestructurados.  

### Servicios de catalogación de datos  
Organizan y describen los datos mediante metadatos para facilitar su descubrimiento y gestión.  
- **Catálogo de datos de AWS Glue:** Repositorio centralizado y administrado de metadatos que mejora la detección y la eficiencia de las canalizaciones de datos.  

### Servicios de procesamiento de datos  
Preparan, limpian y transforman los datos para su análisis.  
- **AWS Glue:** Servicio de ETL totalmente administrado que automatiza la preparación y transformación de datos mediante scripts y metadatos del catálogo.  
- **Amazon EMR:** Plataforma escalable de procesamiento de datos masivos compatible con marcos de *big data* como Spark, Hadoop y Hive.  

### Servicios de análisis y visualización de datos  
Permiten consultar, analizar y visualizar datos para obtener información práctica.  
- **Amazon Athena:** Servicio sin servidor que ejecuta consultas SQL sobre datos en S3 u otros orígenes, pagando solo por consulta.  
- **Amazon Redshift:** Almacén de datos optimizado para consultas SQL complejas con procesamiento paralelo masivo.  
- **Amazon QuickSight:** Herramienta de BI para crear paneles e informes interactivos con consultas en lenguaje natural mediante Amazon Q.  
- **Amazon OpenSearch Service:** Servicio de búsqueda y análisis en tiempo real con visualizaciones unificadas de métricas, registros y trazas.  

![[Pasted image 20251107180710.png]]

---
# Recursos

Para obtener más información sobre los materiales que se tratan en este módulo, haz clic en los enlaces de recursos que figuran en la tabla que aparece a continuación.

| **Enlace del recurso**                                                                                                                                                     | **Descripción**                                                                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Amazon Comprehend](https://aws.amazon.com/comprehend/)                                                                                      | Utiliza el procesamiento del lenguaje natural para extraer información clave de los documentos.                                                                                             |
| [Amazon Polly](https://aws.amazon.com/polly/)                                                                                                | Convierte el texto en un discurso realista.                                                                                                                                                 |
| [Amazon Transcribe](https://aws.amazon.com/transcribe/)                                                                                      | Convierte el discurso en texto.                                                                                                                                                             |
| [Amazon Translate](https://aws.amazon.com/translate/)                                                                                        | Traduce el texto en varios idiomas.                                                                                                                                                         |
| [Amazon Kendra](https://aws.amazon.com/kendra/)                                                                                              | Utiliza el procesamiento del lenguaje natural para consultar de forma inteligente el contenido empresarial.                                                                                 |
| [Amazon Rekognition](https://aws.amazon.com/rekognition/)                                                                                    | Identifica objetos y actividades en imágenes y vídeos.                                                                                                                                      |
| [Amazon Textract](https://aws.amazon.com/textract/)                                                                                          | Puedes detectar y extraer texto mecanografiado y escrito a mano en documentos.                                                                                                              |
| [Amazon Lex](https://aws.amazon.com/lex/)                                                                                                    | Incorpora interfaces de conversación de voz y texto a las aplicaciones.                                                                                                                     |
| [Amazon Personalize](https://aws.amazon.com/personalize/)                                                                                    | Añade recomendaciones personalizadas de clientes a las aplicaciones.                                                                                                                        |
| [Amazon SageMaker AI](https://aws.amazon.com/sagemaker-ai/)                                                                                  | Crea, entrena y despliega tus propios modelos de ML sin preocuparte por la infraestructura.                                                                                                 |
| [Amazon SageMaker JumpStart](https://aws.amazon.com/sagemaker-ai/jumpstart/)                                                                 | Despliega soluciones de ML previamente entrenadas, como visión artificial, PNL y datos tabulares, con solo unos pocos clics.                                                                |
| [Amazon Bedrock](https://aws.amazon.com/bedrock/)                                                                                            | Ajusta e integra sin problemas grandes modelos fundacionales de Amazon y empresas emergentes líderes de IA en tus aplicaciones de AWS con una sola API.                                     |
| [Amazon Q Business](https://aws.amazon.com/q/business/)                                                                                      | Puedes responder preguntas y resolver problemas utilizando los datos y la experiencia que se encuentran en los repositorios de información de la empresa.                                   |
| [Amazon Q Developer](https://aws.amazon.com/q/developer/)                                                                                    | Agiliza el desarrollo con recomendaciones de código.                                                                                                                                        |
| [Amazon Kinesis Data Streams](https://aws.amazon.com/kinesis/data-streams/)                                                                  | Puedes ingerir terabytes de datos de streaming en tiempo real.                                                                                                                              |
| [Amazon Data Firehose](https://aws.amazon.com/firehose/)                                                                                     | Puedes ingerir y entregar datos en cuestión de segundos a varios consumidores, como lagos de datos y almacenes.                                                                             |
| [Amazon S3](https://aws.amazon.com/s3/)                                                                                                      | Puedes almacenar cantidades prácticamente ilimitadas de todos los tipos de datos con esta conocida opción de lago de datos.                                                                 |
| [Amazon Redshift](https://aws.amazon.com/redshift/)                                                                                          | Almacena petabytes de datos estructurados o semiestructurados en este servicio de almacenamiento de datos. Analiza grandes conjuntos de datos almacenados mediante consultas SQL complejas. |
| [Catálogo de datos de AWS Glue](https://docs.aws.amazon.com/prescriptive-guidance/latest/serverless-etl-aws-glue/aws-glue-data-catalog.html) | Proporciona metadatos a varios servicios de análisis con este repositorio centralizado.                                                                                                     |
| [AWS Glue](https://aws.amazon.com/glue/)                                                                                                     | Puedes procesar los datos utilizando el catálogo de datos de AWS Glue como referencia.                                                                                                      |
| [Amazon EMR](https://aws.amazon.com/emr/)                                                                                                    | Puedes procesar cargas de trabajo de big data con marcos de trabajo conocidos como Apache Spark.                                                                                            |
| [Amazon Athena](https://aws.amazon.com/athena/)                                                                                              | Puedes usarlo para analizar varios orígenes de datos alojados en cualquier lugar con una única consulta SQL.                                                                                |
| [Amazon QuickSight](https://aws.amazon.com/quicksight/)                                                                                      | Consulta los datos mediante la creación de paneles interactivos con o sin experiencia.                                                                                                      |
| [Amazon OpenSearch Service](https://aws.amazon.com/opensearch-service/)                                                                      | Consulta y supervisa el análisis de datos en tiempo real con búsquedas de palabras clave o NLP.                                                                                             |

