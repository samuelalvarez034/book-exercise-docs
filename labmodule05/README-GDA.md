# Gateway Device Application (Connected Devices)

## Lab Module 05

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 
En esta practica he modificado las clases:

1. BaseIotData: Esta clase es la base de todas las demas clases de datos.
  
2. ActuatorData: Esta clase hereda de BaseIotData y reprensenta los datos de un actuador. Contiene atributos como command, que es el número del comando del actuador; value que es el valor asignado al actuador, como la temperatura; isResponse que indica si es una respuesta; y stateData, que es información adicional como texto.

3. SensorData: Esta clase hereda de BaseIotData y representa los datos de un sensor.

4. SystemPerformanceData: Esta clase hereda de BaseIotData y representa los datos del rendimiento del sistema. Contiene atributos como cpuUtil, que es el uso de CPU, memUtil que es el uso de memoria, o diskUtil que es el uso del disco. Además, implementa getter y setter para estos atributos.

5. DataUtil: Esta clase se usa para convertir objetos de datos (ActuatorData, SensorData y SystemPerformanceData) a un objeto JSON, o viceversa. La clase cuenta con métodos públicos como actuatorDataToJson(), para convertir datos de tipo ActuatorData a JSON, o jsonToActuatorData() para pasar de datos de tipo JSON a ActuatorData.

A mayores, se ha modificado la clase SystemPerformanceManager para la almacenar los datos de rendimiento en SystemPerformanceData, y enviar la información al IDataMessageListener, para que otros dispositivos puedan trabajar con ellos.

Tambien se a modificado la clase DeviceDataManager, que se encargaba de coordinar la comunicación entre diversos componentes. Ahora se le permite conectarse a diferentes servicios como la nube, un servidor MQTT, manejando todas las solucitudes de datos.

Por último, integramos en GatewayDeviceApp la clase DeviceDataManager. Dentro de los métodos startApp() y stopApp() de GatewayDeviceApp, integramos los métodos startManager() y stopManager() de DeviceDataManager. De esta forma, trasladamos el manejo de SystemPerformanceManager a DeviceDataManager, por lo que se eliminan las referencias a SystemPerformanceManager dentro del GatewayDeviceApp. Para terminar,el DeviceDataManager se registra como un IDataMessageListener en SystemPerformanceManager, utilizando el método setDataMessageListener(this). Esto establece que DeviceDataManager recibirá los mensajes del SystemPerformanceManager.

How does your implementation work?


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab05


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ActuatorDataTest.py
- SensorDataTest.py
- SystemPerformanceDataTest.py
- DataUtilTest.py
  
 

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- SystemPerformanceManagerTest.py
- DataIntegrationTest.py
- DeviceDataManagerNoCommsTest.py
- GatewayDeviceAppTest.py

EOF.
