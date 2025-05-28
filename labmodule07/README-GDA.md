# Gateway Device Application (Connected Devices)

## Lab Module 07

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo es incorporar la capacidad de comunicación de datos usando MQTT dentro del GDA. De esta forma, permitiremos que el GDA se conecte y desconecte a un broker mqtt, publique mensajes en él y se subscriba a topics especificos para recibir mensajes de otros sistemas.

How does your implementation work?

Para lograr el objetivo, se implementa la clase MqttClientConnector que implementa las interfaces IPubSubClient y MqttCallbackExtended. Primero se instancian los atributos necesarios para la conexión: host, puerto, protocolo y keepalive, clientID. 

Para implementar la interación con el broker, los métodos que se han implementado son:
  -connectClient(): Conecta un client al broker
  -disconnectClient(): Desconecta el client del broker si está conectado
  -publishMessage(): Publica un mensage en un tema concreto, con un QoS válido
  -subscribeToTopic(): Se subscribe a un tema concreto con un QoS adecuado
  -unsubscribeToTopic(): Se desubscribe de un tema si esta relación existía
  -isConnected(): Devuelve true si el cliente esta conectado al broker 
  
También se implementan callbacks para informar de direntes sucesos. Estos son:
  -connectComplete(): informa si se ha conectado al broker
  -connectionLost(): informa si se pierde la conexión
  -deliveryComplete(): informa si un mensaje fue entregado con éxito
  -messageArrived(): informa que se ha recibido un mensage de un tema

Por último, se integra con DeviceDataManager. Primero se instancia un mqttclient si tenemos la opcion enableMqttClient en true. Luego se conecta el cliente al arrancar el manager y se desconecta cuando se para el manager.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab07


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
  
EOF.
