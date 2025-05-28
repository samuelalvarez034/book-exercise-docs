# Constrained Device Application (Connected Devices)

## Lab Module 10

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

EL objetivo principal de la practica es implementar y controlar mensajería con edge messaging (en el borde), usando los protocolos MQTT y CoAP para comunicarse entre GDA y CDA. 

How does your implementation work?

Primero, se añade soporte para conexiones MQTT con TLS en MqttClientConnector, de esta manera tenemos mensajería segura entre el CDA y GDA.Para ello se añade una variable enableEncryption, la cual si es verdadera, se establece la conexión mediante TLS con self.mqttClient.tls_set(). 

Además se implementan callbacks para tener informacón de los procesos, en los métodos:
  -on_connect()
  -on_disconnect()
  -on_message()
  -on_publish()
  -on_subscribe()

Por otro lado, también en MqttClientConnector, se implementa una subscripción a mensajes de comandos de actuadores y los redirige a IDataMessageListenerr. Para esto se utilizan los métodos:

  -setDataMessageListener(): configura el receptor de mensajes
  -onActuatorCommandMessage(): es un callback que deserializa y delega el mensaje
  -onConnect(): se conecta al broker y se subscribe al tópico del actuador
  -publishMessage(): publica mensajes de manera asíncrona para no bloquear la recepción de mensajes.

  Por último, también se actualiza el DeviceDataManager para que manege los datos de sensores y del rendimiento del sistema para enviarlos al GDA. Para ello se implementan los métodos:

  -_handleUpstreamTransmission(): envía datos al GDA por MQTT o CoAP
  -handleSensorMessage(): Recibe datos sensores, los analiza, los convierte y los envia upstream
  -handleSystemPerformanceMessage(): tiene la misma función pero con datos de rendimiento
  -_handleSensorDataAnalysis():analiza datos para detectar evectos y activar actuadores
  
  
### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab10

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- DeviceDataManagerCallbackTest.py
- MqttClientConnectorTest.py
- DeviceDataManagerWithCommsTest.py

EOF.
