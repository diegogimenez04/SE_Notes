# Analisis
El análisis se enfoca en la comprensión del sistema deseado y
sus requerimientos.

## Estrategia básica: Dividir y conquistar
Descomponer el problema en pequeñas partes; comprender
cada una de estas partes y las relaciones entre ellas.

Se genera grandes cantidades de informacion y la clave es organizarla

Objetivo del análisis: comprender la estructura del problema y su
dominio (componentes, entrada, salida).

# Especificacion
Se enfoca en el comportamiento externo, la salida final es la SRS.

Lo que se transporta del analisis a la especificacion es el conocimiento adquirido sobre el sistema

Debe cumplir con ser
* Correcta: Cada requerimiento representa precisamente alguna caracteristica deseada por el cliente en el sistema final

* Completa: Todas las características deseadas por el cliente están descriptas.
* No ambigua: Cada requerimiento tiene exactamente un significado
* Consistente: Ningún requerimiento contradice a otro.
* Verificable: Si es verificable, entonces algun proceso puede determinar precisamente lo que se espera
* Rastreable (Traceable): Cada parte del sistema esta enlazada a un requerimiento
* Modificable: Permite incorporar cambios preservando la completitud y consistencia
* Ordenada en aspectos de importancia y estabilidad: Los requerimientos pueden ser críticos, importantes pero no críticos, deseables pero no importantes.

# Casos de uso
Idea: especificar cada funcion provista por el sistema
Capturan el comportamiento del sistema como interacción de los usuarios con el sistema. Se enfocan solo en la especificacion de la funcionalidad 
![[Pasted image 20220909222816.png]]
**COMPLETAR**
# Metricas
Herramientas para poder estimar costos y tiempos, y planear. El proyecto se necesita
“medir” el esfuerzo que demandará.

## Punto funcion
Define el tamaño en términos de la “funcionalidad”, cada una de las cosas mencionadas son un peso segun sean simple, promedio o complejas
| Tipo de funciones            | Simp. | Prom. | Compl. |
| ---------------------------- | ----- | ----- | ------ |
| Entradas externas            |       |       |        |
| Salidas externas             |       |       |        |
| Archivos lógicos internos    |       |       |        |
| Archivos de interfaz externa |       |       |        |
| Transacciones externas       |       |       |        |

Entradas externas: Tipo de entrada (dato / control) externa a la aplicacion
Salidas externas: Tipo de salida que deja el sistema
Archivos lógicos internos: Grupo logico de dato / control de informacion generado/usado/manipulado
Archivos de interfaz externa: Archivos pasados/compartidos entre aplicaciones
Transacciones externas: Inputs/Outputs inmediatos (queries) Ej: buscador

La idea es:
Contar cada tipo de función diferenciando según sea compleja,
promedio o simple. 
Cij denota la cantidad de funciones tipo “i” con complejidad “j”.

Punto función no ajustado (UFP):
$\sum_{i=0}^{5} \sum_{j=0}^{3} w_{ij} c_{ij}$

Ajustar el UFP de acuerdo a la complejidad del entorno. Se evalúa según las siguientes características:
* Comunicacion de datos
* Procesamiento distribuido
* Objetivos de desempeño
* Carga en la configuracion de operacion
* Tasa de transaccion
... entre otros

Cada uno debe evaluarse como:
No presente = 0
Influencia insignificante = 1
Influencia moderada = 2
Influencia promedio = 3
Influencia significativa = 4
Influencia fuerte = 5

$0.65 + 0.01 \sum_{i=1}^{14} p_{i}$

Factor de ajuste de complejidad (CAF):
Puntos función = CAF * UFP

1 punto función = n lineas de codigo

# Arquitectura
La arquitectura tiene como objetivo identificar subsistemas y la forma que interactúan entre ellos.

Definición: La arquitectura de SW de un sistema es la estructura del sistema que comprende los elementos del SW, las propiedades externamente visibles de tales elementos, y la relación entre ellas. Es el diseño a mas alto nivel

* Comprension y comunicacion: Al mostrar la estructura de alto nivel del sistema ocultando la complejidad de sus partes, la descripción arquitectónica facilita la comunicación.

* Reuso: Una de las principales técnicas para incrementar la productividad. Se facilita si a un alto nivel se reusan componentes que proveen un servicio completo.
* Construccion y evolucion: 
* Analisis: 

# Vista C&C
Describe los componentes y su interaccion en tiempo de ejecucion



