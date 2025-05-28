# Constrained Device Application (Connected Devices)

## Lab Module 06

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo es incorporar la capacidad de comunicación de datos usando MQTT dentro del CDA. De esta forma, permitiremos que el CDA publique mensajes en un broker y se subscriba a topics especificos para recibir mensajes de otros sistemas.

How does your implementation work?

Para lograr el objetivo, modificamos e implementamos la clase MqttClientConnector que implementa la interfaz IPubSubClient. Primero se inicializan las propiedades necesarias para conectarse: host, port, keepalive y clientID. Los métodos que se implementan son:

  -connectClient(): Permite que el client se conecte al MQTT.
  -disconnectClient(): Desconecta el client del broker.
  -publishMessage(): Publica en un tema específico, comprobando el topic y los niveles QoS
  -subscribeToTopic(): Se subscribe a un topic especifico validando también el topic y QoS
  -unsubscribeToTopic(): Cancela la subscripción de un tema si esta existe.

Por último, se integra con DeviceDataManager para que se conecte al iniciar la aplicación y se desconecte al cerrarla. En caso de que querramos conectarnos al MQTT.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab06


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- MqttClientConnectorTest.py

EOF.
