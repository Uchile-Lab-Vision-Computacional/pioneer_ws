#  Pioneer Workspace

######  Por Eduardo Jorquera & Ignacio Dassori - Otoño 2023

Este repositorio incluye el ROS workspace utilizado para controlar el robot diferencial Pioneer P3-DX disponible en el laboratorio de Visión Computacional del Departamento de Ingeniería eléctrica de la Universidad de Chile.
 
 
## Instalación

Esta instalación está probada en Ubuntu 18.04, con ROS melodic. 

0.  Clonar este repositorio en el directorio Home 
1.  Instalar rosaria en el directorio pioneer_ws/src - http://wiki.ros.org/ROSARIA/Tutorials/How%20to%20use%20ROSARIA
Para esto clonar repositorio de git de rosaria
```
$ git clone https://github.com/amor-ros-pkg/rosaria
```

2. Instalar **ARIACODA**, porque pkg oficial ARIA está deprecado. https://github.com/reedhedges/AriaCoda

	i) 	instalar compilador de C++ (g++): ```$ sudo apt install make g++```
	ii) 	compilar con ``` $ make -j2```dentro de directorio ARIACODA (cambiar j2 a j4, j6 para mas jobs paralelos)
	iii)	instalar Aria con ``` $ sudo make install```

3) Instalar RosAria: Hacer ```catkin_make``` en pioneer_ws

## Uso de Pioneer con RosAria

Como iniciar nodo RosAria

1. Primero tener sourced el ws
```
$ cd pioneer_ws
$ . devel/setup.bash
```
Alternativamente se puede escribir este comando en el bashrc

2) Setear variable ROS_IP. Para esto usar ifconfig para ver la IP del equipo, luego ejecutar
```$ export ROS_IP="your_ip"```
example: ```$ export ROS_IP=192.168.1.124```

3) Si no se han dado, otorgar permisos al puerto ttyUSB0
```$ sudo chmod a+rw /dev/ttyUSB0```

4) En una terminal comenzar un roscore. En una segunda terminal correr: 
```$ rosrun rosaria RosAria```

### Opcional: rosaria_client

Adicionalmente se puede clonar e instalar el repo **rosaria_client**
Este contiene demos de manejar el robot mediante una interfaz gráfica
```
$ cd pioneer_ws/src
$ git clone https://github.com/pengtang/rosaria_client.git
$ cd ..
$ catkin_make
```
Teniendo roscore en una terminal y el nodo rosaria en otra, en una
tercera termina correr:
```
$ rosrun rosaria_client interface
```

La demo es autoexplicativa.
