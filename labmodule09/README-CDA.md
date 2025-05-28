# Constrained Device Application (Connected Devices)

## Lab Module 09

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo principal es construir el cliente CoAP en el CDA, permitiendo así la comunicación entre el GDA y CDA a través de este protocolo.

How does your implementation work?

Para lograr el objetivo se implementa CoapClientConnector.py, con los métodos:
  -_initClient() y _initClientContext(): inicializan el cliente CoAP y su contexto
  -sendDiscoveryRequest(), sendGetRequest(), sendDeleteRequest(), sendPostRequest(), sendPutRequest(), startObserver(), stopObserver(): Definen las operaciones que puede realizar el cliente contra el servidor CoAP.
  -setDataMessageListener(): recibe un objeto y lo asigna a self.dataMsgListener

Por último se integra con DeviceDataManager para que funcione con la lógica del CDA. Mediante el atributo enalbeCoapClient que es un booleano, se establece o no el cliente CoAP, y, en caso de que sea verdadera, se instancia un cliente.
### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab09

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- CoapClientConnectorTest.py


EOF.
