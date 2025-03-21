# Constrained Device Application (Connected Devices)

## Lab Module 05

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

En esta práctica, se ha realizado la integración y gestión de datos mediante la conversión a formato JSON. Se implementa un un sistema para serializar y deserializar datos de sensores y actuadores, permitiendo la comunicación eficientes entre aplicaciones.

How does your implementation work?

Las clases que se han implementado son:

  1. DataUtil: Esta clase se encargará de convertir los objetos de datos (ActuatorData, SensorData o SystemPerformanceData) a formato JSON, y viceversa. Esta clase contiene métodos para convertir cada tipo de dato a json, como por ejemplo actuatorDataToJson(), y para convertir datos Json a otros objetos, por ejemplo jsonToActuatorData(). Además, contiene métodos privados como _generateJsonData(), que convierte un objeto a Json string; _formatDataAndLoadDictionary() que convierte un JSON string a un diccionario; o _updateIotData() que mapea datos del diccionario a las propiedades del objeto.

De esta forma, garantizamos que la comunicación entre diferentes dispositivos, facilitamos el desarrollo de la aplicación, y la interoperabilidad con otros servicios.

Además, usa el tipo de objeto SystemPerformanceData para empaquetar los datos del sistema, en este caso, el uso de la memoria y de la CPU. Contiene el método handleTelemetry() que recopila los datos del sistema y si hay algún listener, se los envía. Para definir el listener, la clase tiene el método setDataMessageListener(), que registra al listener que recibirá los datos.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab05


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- 
- 
- 

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- SystemPerformanceManagerTest.py
- DataUtilTest.py
- DataIntegrationTest.py

EOF.
