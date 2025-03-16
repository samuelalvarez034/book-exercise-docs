# Constrained Device Application (Connected Devices)

## Lab Module 04

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

El objetivo de las implementaciones es tener tareas que emulen sensores, simulando los comportamientos del hardware, utilizando específicamente los emuladores de Sense HAT.

What does your implementation do? 

En primer lugar, lleve a cabo la instalación y configuración del emulador Sense-Emu y la instalación de la libreria Pisense. El único problema fue que la versión de la librería Pillow, que sirve para procesar imagenes, era la última, y esta ya no tiene muchos de los métodos aplicados en el CDA, como .textsize(). Para solucionarlo, instale manualmente la versión 9.5.0.

1. BaseSensorSimTask: Esta clase se vuelve a utilizar como plantilla, de la cual deben heredad todas las tareas de emulación.

2. HumiditySensorEmulatorTask: Esta clase hereda de BaseSensorSimTask, e implementa la emulación del sensor de Humedad. Contiene un método generateTelemetry() que se usa para generar los datos cada vez que sea necesario, devolviendo un objeto de tipo SensorData, que se utiliza para almacenar los datos de cada sensor.

3. PressureSensorEmulatorTask: Esta clase hereda de BaseSensorSimTask, e implementa la emulación del sensor de presión. Contiene un método generateTelemetry() que se usa para generar los datos cada vez que sea necesario, devolviendo un objeto de tipo SensorData, que se utiliza para almacenar los datos de cada sensor.

4. TemperatureSensorEmulatorTask: Esta clase hereda de BaseSensorSimTask, e implementa la emulación del sensor de temperatura. Contiene un método generateTelemetry() que se usa para generar los datos cada vez que sea necesario, devolviendo un objeto de tipo SensorData, que se utiliza para almacenar los datos de cada sensor.

5. HumidifierEmulatorTask: Esta clase hereda de BaseActuatorSimTask, y simula un actuador de humidificador utilizando el emulador de Sense HAT. Contiene los métodos _activateActuator() y _deactivateActuator(), que activan y desactivan el actuador de humidificar.

6. HvacEmulatorTask: Esta clase hereda de BaseActuatorSimTask, y simula un actuador de un sistema HVAC(calefacción, ventilación, y aire acondicionado) utilizando el emulador de Sense HAT. Cuenta con los mismo métodos de _activateActuator() y _deactivateActuator().

7. LedDisplayEmulatorTask: Esta clase hereda de BaseActuatroSimTask, y sirve para simular un actuador de pantalla LED utilizando el emulador de Sense HAT. También tiene los métodos de _activateActuator() y _deactivateActuator().


How does your implementation work?

Modificamos la clase de SensorAdapterManager para integrar ahora la funcionalidad del emuladores de humedad, presión y temperatura utilizando las bibliotecas de emulación de Sense-Emu y Pisense.

Añadimos un atributo useEmulator en el constructor de SensorAdapterManager, que se usará para saber si deseamos o no utilizar la emulación. Si useEmulator es verdadero, entonces se cargan los emuladores de los sensores de temperatura, humedad y presión; si useEmulator es false, entonces seguimos usando el generador de datos simulado que se implemento anteriormente. En el método _initEnvironmentalSensorTasks() se comprueba el valor de useEmulator, y además, se instancian los emuladores.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab04


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

- SenseHatEmulatorQuickTest.py
- HumidityEmulatorTaskTest.py
- PressureEmulatorTaskTest.py
- TemperatureEmulatorTaskTest.py
- HumidifierEmulatorTaskTest.py
- HvacEmulatorTaskTest.py
- LedDisplayEmulatorTaskTest.py
- SensorEmulatorManagerTest.py
  

EOF.
