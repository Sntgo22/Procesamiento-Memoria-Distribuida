# Procesamiento-Memoria-Distribuida

**Arquitectura de la máquina:**

- Procesador: 11th Gen Intel(R) Core(TM) i5-11300H @ 3.10GHz   3.11 GHz
- 16GB RAM
- Tarjeta gráfica: 3050 Nvidia

Para comenzar a hacer nuestro análisis y ver la diferencia entre los distintos métodos de optimización, lo primero que haremos será partir con unos valores de ejecución base, los cuáles se obtuvieron por medio del código suministrado para el ejercicio sin aplicar modificaciones previas.

**Archvios previos a hacer "make"**
![](imgs/Archivos.png)

**Archivos luego de hacer "make"**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/Archivos%20post%20make.png)

**Se ejecuta mpirun -np 4 heat_mpi**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/1.png)

**Se ejecuta mpirun -np 4 heat_mpi bottle.dat**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/2.png)

**Se ejecuta mpirun -np 4 heat_mpi bottle.dat 1000 (pasos de tiempo)**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/3.png)

**Se ejecuta mpirun -np 4 heat_mpi 800 800 1000 (dimensiones y pasos de tiempo)**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/4.png)


La solución propuesta en el curso nos presenta un documento de datos el cual usa el algoritmo para ejecutar las etapas de la transferencia de calor, el código setup.c existe una funcion llamada inicializate en donde parte de las tareas de esta, es verificar si hay un checkponit de los datos sobre los cuales se ha ejecutado el algoritmo y continua a partir de estos, por esto cada que se ejecuta el  heat_mpi se generan imágenes nuevas con un notorio cambio de temperatura en el mapa de calor. El algoritmo de core. C es una extensión de setup pero este se centra en las estructuras principales para resolver la ecuación de calor 

