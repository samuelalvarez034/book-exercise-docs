# Constrained Device Application (Connected Devices)

## Lab Module 01

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 
En esta parte, no se ha implementado nada en de codigo, si no que se ha dedicado a la creación y configuración del entorno para que el proyecto funcione correctamente.

En mi caso, he optado por instalar una WSL (Windows Subsystem Linux), en concreto Ubuntu 24. En él, he creado la carpeta programmingtheiot, la cual he clonado los repositorios de python-components(CDA) y el de java-components(GDA). Además, he creado un entorno virtual para trabajar en el proyecto, en el cual he instalado lo siguiente:
  -Python 3.12
  -Java 21.0
  -Los requirements del archivo basic_imports.txt del repositorio de python
  -Apache Maven 3.8

Como editor de código, estoy desarrollando el proyecto el Visual Studio Code. Para poder conectarlo a la WSL tuve que instalar el plugin de WSL en VSCode, y asi poder trabajar con el enviroment que habia creado. Además, también instalé el pluggin de Maver for java para poder correr los test de java en el editor de código.

En el CDA, lo único que he cambiado fue el archivo ConfigConst.py, exactamente el el valor de DEFAULT_CONFIG_FILE_NAME, ya que para que funcionara, había que indicarle la ruta completa de PiotConfig.props, donde se encuentran todas las configuraciones del proyecto.

Uno de los principales problemas que encontre en la configuración del entorno, fue declarar el PYTHONPATH, ya que al querer ejecutar código, visual no encontraba los paquetes. Para solucionarlo, incluí el PYTHONPATH en el .bashrc para que siempre lo encuentre correctamente. Otro de los principales problemas fue conectar VSCode a Ubuntu, ya que tuve que instalar un pluggin de WSL para que funcionara, el cual crea un servidor externo para conectarlos.

Por último, la poca familiarización con github también me dificultó el entender como se trabajaría con las ramas, o como conectarse desde VSCode.

How does your implementation work?

  1. Entrar en Ubuntu
  2. Moverse a la carpeta programmingtheiot
  3. Arrancar el entorno virutal con (. .venv/bin/activate)
  4. Usar "code ." para abrir VSCode 

### Code Repository and Branch

NOTE: Be sure to include the branch 

URL:

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ConfigUtilTest.py
- 
- 

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- ConstrainedDeviceAppTest.py
- 
- 

EOF.
