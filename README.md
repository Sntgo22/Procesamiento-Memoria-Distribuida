# Procesamiento-Memoria-Distribuida

**Arquitectura de la máquina:**

- Procesador: 11th Gen Intel(R) Core(TM) i5-11300H @ 3.10GHz   3.11 GHz
- 16GB RAM
- Tarjeta gráfica: 3050 Nvidia

Para comenzar a hacer nuestro análisis y ver la diferencia entre los distintos métodos de optimización, lo primero que haremos será partir con unos valores de ejecución base, los cuáles se obtuvieron por medio del código suministrado para el ejercicio sin aplicar modificaciones previas.

- **Archvios previos a hacer "make"**
![](imgs/Archivos.png)

- **Archivos luego de hacer "make"**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/Archivos%20post%20make.png)

- **Se ejecuta mpirun -np 4 heat_mpi**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/1.png)

- **Se ejecuta mpirun -np 4 heat_mpi bottle.dat**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/2.png)

- **Se ejecuta mpirun -np 4 heat_mpi bottle.dat 1000 (pasos de tiempo)**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/3.png)

- **Se ejecuta mpirun -np 4 heat_mpi 800 800 1000 (dimensiones y pasos de tiempo)**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/4.png)

# Análisis de los archivos más importantes
La solución propuesta en el curso nos presenta un documento de datos el cual usa el algoritmo para ejecutar las etapas de la transferencia de calor, el código setup.c existe una funcion llamada inicializate en donde parte de las tareas de esta, es verificar si hay un checkponit de los datos sobre los cuales se ha ejecutado el algoritmo y continua a partir de estos, por esto cada que se ejecuta el  heat_mpi se generan imágenes nuevas con un notorio cambio de temperatura en el mapa de calor. El algoritmo de core. C es una extensión de setup pero este se centra en las estructuras principales para resolver la ecuación de calor.

# Cambios realizados al main.c
Se identifica que el archivo que más influye en los tiempos de ejecución, es main.c, es por esto que se deciden hacer ciertas modificaciones de las cuáles se irá viendo su estructura y su respectiva explicación de cada parte:

1. Inclusión de Bibliotecas:
````
#include <stdio.h>
#include <stdlib.h>
#include <mpi.h>
#include "heat.h"
````
Se incluyen las bibliotecas estándar de entrada/salida, manejo de memoria dinámica, MPI para programación paralela, y un archivo de encabezado personalizado ("heat.h").
3. Declaración de Variables:
Se declaran variables para almacenar parámetros del problema, información sobre la malla y el tiempo, así como estructuras de datos para almacenar los campos de temperatura actual y anterior. También se declaran variables relacionadas con la paralelización y contadores de iteración.
4. Inicialización MPI y del Problema:
Se inicializa MPI y se lleva a cabo la inicialización del problema, configurando la distribución de trabajo entre los procesos MPI y estableciendo las condiciones iniciales.
5. Cálculos Preliminares:
Se realizan cálculos previos relacionados con la distribución del trabajo entre los procesos MPI.
6. Salida Inicial de Campo de Temperatura:
Se genera la salida inicial del campo de temperatura.
7. Cálculos para el Paso de Tiempo:
Se calculan los valores necesarios para el paso de tiempo, considerando la estabilidad numérica de la solución.
8. Evolución Temporal:
Se realiza la evolución temporal del sistema, distribuyendo el trabajo entre los procesos MPI. Se intercambian datos entre procesos para garantizar la coherencia en los bordes de las regiones locales.
9. Salida de Resultados y Checkpoints:
Se generan salidas visuales en intervalos regulares y se guardan checkpoints para permitir la reanudación de la simulación.
10. Estadísticas y Finalización:
Se imprimen estadísticas, como el tiempo total de ejecución, y se finaliza la ejecución, liberando recursos y cerrando MPI.



