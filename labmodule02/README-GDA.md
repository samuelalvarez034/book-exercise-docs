# Gateway Device Application (Connected Devices)

## Lab Module 02

Be sure to implement all the PIOT-GDA-* issues.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

Esta implementación sirve para desarrollar las tareas que forman parte de un sistema de monitoreo, cuyo propósito principal es monitorear y recolectar información sobre el rendimiento del sistema, específicamente los recursos de hardware como el uso de la CPU y la memoria del sistema.

What does your implementation do? 

En esta práctica, he creado las siguientes clases:

1. GatewayDeviceApp: esta clase se encargará de gestionar la ejecución de la aplicación GDA, es decir, la inicialización, incio y detención de la aplicación. Contiene un metodo parseArgs() que es el encargado de procesar los parámetros de la línea de comandos; initConfig() que se encargará de iniciar la configuración de la aplicación; un startApp() que se encarga de inciar la aplicación; un stopApp() que se encargará de finalizar la aplicación; y por último un main que crea una instancia de GatewayDeviceApp, llama a startApp(), espera unos segundos y llama a stopApp().

2. SystemPerformanceManager: esta clase es la encargada de gestionar el rendimiento del sistema al obtener diferentes métricas. Contiene un metodo startManager() para arrancarlo, un stopManager() para deternlo, y un handleTelemetry() que se encargará de obtener diferentes valores como el uso de CPU y memoria, y registralos con un Logger. Además, contiene la variable llamada pollRate que indica la frecuencia con la que se ejecutará handleTelemtry().

3. BaseSystemUtilTask: Esta clase sirve para las tareas de utilización del sistema, la cual será extendida por otras subclases que implementarán un comportamiento específico para recopilar diferentes tipos de datos sobre el sistema. Contiene un método getName(), que devuelve el nombre de la tarea; un getTypeID() que devuelve el ID de tipo de la tarea; y un método abstracto getTelemetryValue(), el cuál será implementado por cada subclase, devolviendo asi valores especificos.

4. SystemCpuUtilTask: Esta clase hereda de BaseSystemUtilTask, y se encargará de recopilar el porcentaje de uso de la CPU, para ello, utiliza la librería psutil. Contiene el método getTelemetryValue(), que retorna el uso.

5. SystemMemUtilTask: Esta clase hereda de BaseSystemUtilTask, y se encargará de recopilar el porcentaje de uso de la memoria, para ello, utiliza la libreria ManagementFactory, que contiene métodos específicos. Contiene el método getTelemetryValue(), que retorna el uso.
   

How does your implementation work?

En primer lugar, importamos la clase SystemPerformanceManager en la clase GatewayDeviceApp. Creamos una instancia del SystemPerformanceManager y cuando se llama al método starApp(), tambien llamamos al método startManager(), y de igual manera, cuando llamamos a stopApp(), también llamamos al metodo stopManager().

Por último, conectamos los paquetes SystemCpuUtilTask y SystemMemUtilTask con SystemPerformanceManager. Para ello, creamos una instancia del SystemCpuUtilTask y otra de SystemCpuUtilTask. Luego, en el método handleTelemtry del SystemPerformanceManager, llamamos a los métodos para obtener los datos y los registramos con un Logger. Además, en el startManager(), ahora usamos un ScheduledExecutorService que sirve para ejecutar el handleTelemetry() de manera periódica, con intervalos definidos por el pollRate.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/samuelalvarez034/java-components/tree/Lab02


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ConfigUtilTest.py
- SystemCpuUtilTaskTest.py
- SystemMemUtilTaskTest.py
  

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- GatewayDeviceAppTest.py
- SystemPerformanceManagerTest.py
- 

EOF.
