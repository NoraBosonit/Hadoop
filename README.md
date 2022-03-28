# Hadoop
Tradicionalmente se trabajaba en máquinas individuales. Sin embargo, a medida que el tiempo pasa la cantidad de datos va siendo cada vez mayor por lo que se crean cuellos de botella en las máquinas. DE ahí surje una una nueva forma de trabajar con Big Data; Hadoop. 

## Deficición
Hadoop es un framework de código abierto para almacenar datos y ejecutar aplicaciones en clusters.

## Introducción
### Historia
Inspirado en los documentos de Google para MapReduce y GFS (Google File System) y actualmente es un proyecto de alto nivel de Apache.
Las principales distribuciones de Apache Hadoop son:
- Cloudera
- Hortonworks
- MapR

### Características 
1. En Hadoop se distribuyen los datos nada más llegan al Cluster y los nodos se deben comunicar entre sí lo menos posible. Además, los datos se replican (normalmente factor 3) para obtener **disponibilidad, fiabilidad y tolerancia a fallos**. 

3. Cada ejecución de MapReduce se denomida job y estos deben de ejecutarse de manera independiente en en cluster. Es decir, la salida de un job no debe condicionar la salida de otro job a no ser que sea estrictamente necesario. El rendimiento de un job se puede ver afectar potr la ejecución de otro job ya que la potencia del Cluster es finita, pero eso ya se tiene en cuenta. 

5. Tipos de datos soportados en Hadoop:
- Estructurados
- Semi-estructurados 
- No estructurados

6. Tiempo de procesado:
- Originalmente procesado por lotes (programa que no necesita iteracción del usuario)
- Near Real Time: los datos se procesan con una diferencia de a tiempo real
- Real Time: los datos se procesan a tiempo real con latencia mínima

7. Tipo de procesado:
- Ejecución en paralelo
- Sobre datos distribuidos (**HDFS**)

### Nociones bácicas
Un Cluster se compone de un conjunto de servidores (nodos) que trabajan juntos para conseguir un objetivo común. Hay 2 tipo de nodos:
- Maestros --> gobiernan el cluster
- Escalvos --> procesan y almacenan la información

Cada nodo tiene sus Demonios corriendo. *Siendo un demonio un programa que se encarga de procesos del sistema en segundo plano y al que no puede acceder el usuario directamente*

### Componentes de Hadoop
- HDFS
  - Almacena los datos en el cluster
- MapReduce
  - Procesa los datos en el cluster
- Ecosistema de herramientas
  - Conjunto de herramientas que hacen más fácil trabajar con Hadoop

## HDFS 
### Definición
Es un sistema de archivos nativo de Google escrito en Java el cual está desplegado sobre el sistema de archivos nativo de cada servidor. 

### Características 
Su característica más importante es que **provee de almacenamiento redundante de grandes volúmenes de datos transparente al usuario** --> El usuario no tiene que indicar que quiere replicar la información almacenada

### Funcionamiento 
Está pensado para escribir una sola vez, pero leer muchas. Es preferible borrar el archivo y copiarlo de nuevo antes que modificarlo. Además, es óptimo cuando trabaja con cantidad moderada de datos ya que funciona mejor con millones de datos antes que con billones. 

HDFS está pensado para leer óptimamente archivos de gran tamaño no para lecturas aleatorias --> **DUDA**

#### Funcionamiento 1
Cada archivo se divide en bloques entre los nodos del cluster en un tiempo igual al tiempo de escritura replicandóse cada nodo un total de 3 (por defecto aunque modificable) veces. 
