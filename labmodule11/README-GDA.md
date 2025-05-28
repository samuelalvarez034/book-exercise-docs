# Gateway Device Application (Connected Devices)

## Lab Module 11

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo principal es integrar el GDA con servicios en la nube usando MQTT. Para ellos usare Ubidot como servicio en la nube, y realizaré las pruebas para comprobar el correcto funcionamiento.

How does your implementation work?

En primer lugar recalcar que he elegido ubidots como servicio en la nube.

Para lograr el objetivo, primero he implementado los siguientes métodos en MqttClientConnector:
  -initClientParameters(): Carga parámetros de configuración como el broker, puerto, credenciales,etc.
  -etConnectionListener(): permite a otra clase recibir eventos cuando se establece la conexión MQTT
  -connectComplete(): callback que se llama cuando se establece o reestablece conexción al broker.
  -publishMessage(): publica un mensaje 
  -subscribeToTopic(): se suscribe a un topico ç
  -unsubscribeFromTopic(): se desuscribe de un topico si estaba suscrito

Luego modifico la clase CloudClientConnector, en ella se implementan los siguientes métodos:
  -createTopicName(): Genera el nombre del topic MQTT
  -setDataMessageListener(): establece el listener que recibirá los mensajes de datos entrantes.
  -sendEdgeDataToCloud(): Publica datos de sensores hacia la nube convirtiendolos e JSON y enviandolos al topic concreto
  -ubscribeToCloudEvents(): Se suscribe a un tópico MQTT
  -unsubscribeFromCloudEvents(): se desuscribe de un tópico si esta suscrito
  -publishMessageToCloud(): implementa la lógica para enviar mensajes 

Por último se integra en DeviceDataManger para que al iniciar el manager se puedan enviar datos a la nube y recibirlos.

  
### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab11

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
- CloudClientConnectorTest.java


EOF.
