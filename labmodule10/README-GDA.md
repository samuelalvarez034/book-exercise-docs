# Gateway Device Application (Connected Devices)

## Lab Module 10

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

EL objetivo principal de la practica es implementar y controlar mensajería con edge messaging (en el borde), usando los protocolos MQTT y CoAP para comunicarse entre GDA y CDA. 

How does your implementation work?

Primero actualizamos MqttClientConnector para soportar conexiones TLS. Para ello se implementan los métodos. 

  -initCredentialConnectionParameters(): carga las credenciales y parametros necesarios
  -initSecureConnectionParameters(): configura la conexión tls, cargando el certificado PEM y lo aplica al cliente MQTT.
  -initClientParameters(): contiene todas las inicializaciones de los parámetros de los cliente, incluyendo el host, puerto, cifrado, etc.

  Además, se incluye el uso de clientes asíncronos de MQTT, evitando asi bloqueos que pueden ocurrir al publicar y recibir mensajes simultaneamente. 

  Por último, se añaden funcionalidades en el DeviceDataManager para gestionar mensajes CDA entrantes, especificamente de tres tipos:
  -SensorData
  -SystemPerformanceData
  -ActuatorData
Para esto, se implementan los siguientes métodos:
  - handleSensorMessage(): valida y procesa un mensaje de un sensor que entra
  - handleIncomingDataAnalysis(): Decide como analiza el dato basándose en su tipo
  - handleHumiditySensorAnalysis(): Analiza el valor de humedad recibido
  - sendActuatorCommandtoCda(): Envía un comando ActuatorData al CDA vía MQTT o CoAP.
  - getDateTimeFromData(): Extrae la fecha y hora del dato 

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab10



### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.
 


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- MqttClientConnectorTest.java
- DeviceDataManagerSimpleCdaActuationTest.java

EOF.
