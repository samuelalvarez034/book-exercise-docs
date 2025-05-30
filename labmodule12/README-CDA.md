# Constrained Device Application (Connected Devices)

## Lab Module 12 - Semester Project - CDA Components

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

El objetivo principal de esta practica es añadir un sensor y un actuador en el sistema, en este caso, un sensor que mida la calidad del aire (CO2), y un acutador que será un purificador del aire.

How does your implementation work?

La implementación ha sido muy simple. Para ello se han creado los archivos para la simulación y emulación de los sensores y actuadores:
  -AirQualitySensorSimTask: Es la clase que simula el sensor de calidad del aire. Contiene los métodos que hereda de BaseSensorSimTask(), y los valores minimos y maximos normales que genera son 600 ppm y 1000 ppm. 
  -AirPurifierActuatorSimTask: Es la clase que simula el actuador de purificar el aire. Contiene todos los métodos que hereda de BaseActuatorSimTask().
  -AirQualitySensorSimTask: Es la clase que implementa la emulación del hardwware del sensor. Hereda los métodos de la clase BaseSensorSimTask(),y emula datos con SenseHAT en vez de simularlos.
  -AirPurifierEmulatorTask: Es la clase que implementa la emulación del hardware del actuador con SenseHAT. Hereda de la clase BaseActuatorSimTask(), implementando los métodos para activar, desactivar o actualizar el actuador

Además, se actualizan las clases:
  -SensorAdapterManager: Se incluye el sensor, tanto si se usa la simulación como la emulación del mismo, de esta forma se implenta en la logica del trabajo en DeviceDataManager.
  -ActuatorAdapterManager: Se incluye el actuador, tanto si se usa la simulación como la emulación del mismo, de esta forma se implenta en la logica del trabajo en DeviceDataManager.

Por último, al tratarse de un dato tipo SensorData, su integración con el GDA y la comunicación con diferentes protocolos está implementada como se implementa para el resto de sensores y actuadores que usan SensorData.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: 


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)


EOF.
