# Constrained Device Application (Connected Devices)

## Lab Module 03

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

El objetivo de estas implementaciones es crear clases para representar y manejar datos de sensores, actuadores y del rendimiento del sistema, que heredan de una clase base BaseIotData, y así tener una estructura común y reutilizable para el tratamiento de datos en la arquitectura IoT (Internet of Things).

What does your implementation do? 

Las clases que he implementado o modificado en este lab son:

1. BaseIotData: Esta clase sirve como plantilla para todos los tipos de datos que se van a manejar. Contiene atributos como en name (nombre del dato), typeID(tipo de dato), timeStamp(marca de tiempo del dato), statusCode( estado del dato). Como métodos, contiene getter and setter para estos atributos entre otros.

2. ActuatorData: Esta clase hereda de BaseIotData, y sirve para enviar comandos a actuadores y manejar la respuesta de este. Contiene los atributos value(número del comando), command(tipo de comando), stateData( información adicional del estado), e isResponse(indica si es una respuesta). Como métodos, tiene getter y setter para value, command y stateData, y un método setAsReponse() para marcar como respuesta.

3. SensorData: Esta clase hereda de BaseIotData, y sirve para almacenar y manejar lecturas de sensores del sistema. Contiene el atributo value que es el valor leído por el sensor, y un getter y setter para value.

4. SystemPerformanceData: Esta clase hereda de BaseIotData, y sirve para monitorear el rendimiento del dispositivo, en este caso, representa datos como el uso de CPU y memoria. Contiene los atributos cpuUtil y memUtil que almacenan en porcentaje de uso de CPU y memoria respectivamente. Como métodos contiene getter y setter para los atributos.

5. BaseSensorSimTask: Esta clase simula el comportamiento de un sensor. Puede generar valores aleatorios o leer un conjunto de datos predefinidos, permitiendo que el sistema funcione como si estuviera interactuando con sensores reales. Sus atributos son dataset, que almacenaria el dataset de datos en caso de que se proporcione; el name que es nombre del sensor; el typeID, que es el tipo de sensor; y minVal y maxVal, que son los valores minimos y maximos para crear datos aleatorios. Como métodos tiene un getName() que devuelve el nombre, un getTypeID() que devuelve el typeID; un generateTelemetry() que genera valores como si fuera un sensor, permitiendo generarlos de manera aleatoria o a partir de un dataset establecido; y un método getTelemtryValue() que devuelve el valor actual del sensor, si no existe, llama a generateTelemetry() para obtenerlo.

6. HumiditySensorSimTask: Esta clase hereda de BaseSensorSimTask, y se encarga de simular el sensor de humedad.

7. PressureSensorSimTask: Esta clase hereda de BaseSensorSimTask, y se encarga de simular el sensor de presión.

8. TemperatureSensorSimTask: Esta clase hereda de BaseSensorSimTask, y se encarga de simular el sensor de Temperatura.

9. BaseActuatorSimTask: Esta clase sirve como base para subclases que simularan el comportamiento de actuadores, proporcionando los métodos necesarios para manejar la activación y desactivación de actuadores, registrar los comandos que se les envian y procesar las respuestas de estos. Contiene los atributos name, que es el nombre del actuador, typeID que es el identificador del tipo de actuador, simpleName que es un nombre sencillo del actuador, lastKnownCommand que almacena el último comando y lastKnownValue que almacena el último valor. Se han implementando los métodos _activateActuator y _deactivateActuator que activan y desactivan los actuadores, y un método updateActuator, que actualiza el estado del actuador en función de los comandos que llegan.

10. HumidifierActuatorSimTask: Esta clase hereda de BaseActuatorSimTask y simula el comportamiento del actuador de humuedad.

11. HvacActuatorSimTask: Esta clase hereda de BaseActuatorSimTask y simula el comportamiento del actuador de humuedad.

12. TemperatureActuatorSimTask: Esta clase hereda de BaseActuatorSimTask y simula el comportamiento del actuador de calefacción, ventilación y aire acondicionado.

13. SensorAdapterManager: Esta clase se encarga de administrar y coordinar los sensores simulados. Tiene un startManager() y un stopManager() para arrancar y detener el sistema de sensores; además, tiene un método _initEnvironmentalSensorTasks que se encarga de crear los simuladores y de generar datasets con valores aleatorios; un setDataMessageListener() que permite conectar la clase con otro componenente para que procese los datos; un handleTelemetry() que se encarga de generar los datos, imprimirlos y enviarlos al listener para que otro componente los procese.

14. ActuatorAdapterManager: Esta clase se encarga de gestionar y controlar los actuadores. Contiene un método _initEnvironmentalActuationTasks que se encarga de inicializar los actuadores; un sendActuatorCommand() que recibe comandos y se los envía a los actuadores correspondientes;  y un setDataMessageListener() que sirve para configurar el listener y que los actuadores puedan enviar respuestas de vuelta.


How does your implementation work?

Una vez que los sensores y actuadores están creados, se coordina todo desde el DeviceDataManager. Contiene métodos públicos como handleActuatorCommandMessage() que procesa los comandos que le llegan para los actuadores; un handleActuatorCommandResponse() que procesa las respuestas de los actuadores; un handleIncommingMessage() que recibe los mensajes del GDA; un handleSensorMessage() que recige datos del sensor y analiza si actuar o no; y un handleSystemPerformanceMessage() que recibe los datos del rendimiento del sistema. 

En resumen, coordina los mensajes y respuestas a los actuadores, en base de las lecturas de sensores.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab03

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ActuatorDataTest.py
- SensorDataTest.py
- SystemPerformanceDataTest.py
- HumiditySensorSimTaskTest.py
- PressureSensorSimTaskTest.py
- TemperatureSensorSimTaskTest.py
- HumidifierActuatorSimTaskTest.py
- HvacActuatorSimTaskTest

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- SensorAdapterManagerTest.py
- ActuatorAdapterManagerTest.py
- DeviceDataManagerNoCommsTest.py

EOF.
