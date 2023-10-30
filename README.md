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

**Se ejecuta el mpirun con valores predeterminados**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/mpirun%20-np%208%20heat_mpi.png)

**Se ejecuta el mpirun para la ecuación de calor dando pasos de tiempo de 1000**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/mpirun%20-np%208%20heat_mpi%20bottle.dat.png)

**Finalmente se ejecuta mpirun con dimensiones y espacios de tiempo de 800 800 1000**
![](https://github.com/Sntgo22/Procesamiento-Memoria-Distribuida/blob/main/imgs/mpirun%20-np%204%20heat_mpi%20800%20800%201000.png)
