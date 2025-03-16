# Constrained Device Application (Connected Devices)

## Lab Module 02

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

Esta implementación sirve para desarrollar las tareas que forman parte de un sistema de monitoreo, cuyo propósito principal es monitorear y recolectar información sobre el rendimiento del sistema, específicamente los recursos de hardware como el uso de la CPU y la memoria del sistema.

What does your implementation do? 

Las clases que he implementado son:

  1. ConstrainedDeviceApp.py: Es la clase principal, y su función es inicializar, arrancar y detener la aplicación. Es una clase sencilla con un método startApp() y stopApp(), fque sirven para ejecutar lo necesario para que la aplicación empiece a funcionar, y para detener los procesos, respectivamente. Además de un main() que crea una instancia de la clase y ejecuta sus   métodos.

  2. SystemPerformanceManager.py: Es la clase encargada de gestiionar el rendimiento del dispositivo. Consta de un método startManager() y stopManager() para arrancar y detenerlo. Además, tiene los atributos pollRate que es la frecuencia de muestreo; locationID, que es la ID de la ubicación del dispositivo. Además, también se implementa la función handleTelemtry(), que servirá para obtener valores del sistema y registralos.
  
  3. BaseSystemUtilTask.py: Es una clase que sirve para monitorear el sistema, que contiene métodos que les servirán a las clases que la hereden. Los métodos implementados en esta práctica son getName() que devuelve el nombre de la tarea, getTypeID() que devuleve el tipo de tarea, y getTelemetryValue(), que es un método abstracto por lo que no tiene una implementación concreta, y sirve para que sus subclases definan como  obtener diferentes tipos de datos.

  4. SystemCpuUtilTask.py: Hereda de la clase BaseSystemUtilTask.py, he implementa el método getTelemetryValue() para obtener el porcentaje actual de uso de la CPU.

  5. SystemMemUtilTask.py: Hereda de la clase BaseSystemUtilTask.py, he implementa el método getTelemetryValue() para obtener el porcentaje actual de uso de la memoria.

  6. SystemCpuUtilTask.py: Hereda de la clase BaseSystemUtilTask.py, he implementa el método getTelemetryValue() para obtener el porcentaje actual de uso de la CPU.

How does your implementation work?

  Importamos el SystemPerformanceManager en ConstrainedDeviceApp. Primero creamos una instancia del SystemPerformanceManager y cuando la aplicación se arranque, se llama al método startManager(), y cuando se detenga, a stopManager().

  Además, necesitamos conectar las clases SystemCpuUtilTask y SystemMemUtilTask con la clase SystemPerformanceManager, que es la encargada de gestionar el rendimiento del dispositivo. Para ello, el método handleTelemetry() de SystemPerfomanceManager(), obtinene los valores de uso de la CPU  y de memoria utilizando instancias de SystemCpuUtilTask y SystemMemUtilTask, para luego resgistrarlas con un Logger. A mayores, importa ScheduledExecutorService y Executors, que sirven para ejecutar periodecamente tareas. Cuando se llama al método startManager(), se inicializa un  ScheduledExecutorService para ejecutar la tarea de handleTelemetry() cada "pollRate" segundos.
  
### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/python-components/tree/Lab02

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ConfigUtilTest.py
- SystemCpuUtilTaskTest.py
-  SystemMemUtilTaskTest.py

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- ConstrainedDeviceAppTest.py
- SystemPerformanceManagerTest.py
- 

EOF.
