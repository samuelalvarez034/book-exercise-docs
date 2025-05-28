# Gateway Device Application (Connected Devices)

## Lab Module 08

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo principal es construir un servidor CoAP en el GDA, que sea capaz de gestionar solicitudes GET, POST, PUT y DELETE, utilizando la librería Californium. Además, realizar pruebas de funcionamiento básicas para ver su correcto funcionamiento.

How does your implementation work?

Para lograr el objetivo, se construye la clase CoapServerGateway, que encapsulará la funcionalidad principal del servidor CoAP. En el se implementan los métodos:

  -startServer(): arranca el servidor CoAP
  -stopServer(): para el servidor CoAP

Además se crean e implementan dos clases, UpdateSystemPerformanceResourceHandler y UpdateTelemetryResourceHandler. Ambas son handlers que manejarán las solicitudes que lleguen al servidor.

Por otro lado, se implementa la clase GetActuatorCommandResourceHandler para poder enviar comandos de actuación al CDA como respuesta.

Por último se integra con DeviceDataManager, de esta forma se integra en la lógica del GDA. Cuando el DeviceDataManager llama a startManager(), se arranca el servidor CoAP si la variable  enableCoapServer es verdadera, y se apaga cuando se llama a stopManager().

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab08


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- CoapServerGatewayTest.java

EOF.
