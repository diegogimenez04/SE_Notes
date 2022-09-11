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
* Construccion y evolucion: La división provista por la arquitectura servirá para guiar el desarrollo del sistema. Cuáles partes son necesarias construir primero, cuáles partes ya están construidas. Ayuda a asignar equipos de trabajo: las distintas partes pueden construirse por distintos grupos. Durante la evolución del SW, la arquitectura ayuda a decidir cuáles partes necesitan cambiarse para incorporar nuevas características o cambios, y a decidir cuál es el impacto de tales cambios en las otras componentes.
* Analisis: Es deseable que propiedades de confiabilidad y desempeño puedan determinarse en el diseño; esto permite considerar distintas alternativas de diseño hasta encontrar los niveles de satisfacción deseados.

# Tipos de vistas
La mayoria pertenecen a estos 3 tipos:
	Modulo
	Componentes y Conectores
	Asignacion de recursos

Estan corelacionadas y representan al mismo sistema

* Vista de modulos: Un sistema es una colección de unidades de código, su relacion esta basada en el codigo
* Vista de componentes y conectores: Los elementos son entidades de ejecución denominados componentes
* Vista de asignación de recursos: Se enfoca en cómo las unidades de SW se asignan a recursos como hw, sistemas de archivos, gente, etc.


# Vista C&C
Describe los componentes y su interaccion en tiempo de ejecucion
* Componentes: son elementos computacionales o de almacenamiento de datos.
* Conectores: son mecanismos de interacción entre las componentes.

Los estilos arquitectónicos para la vista de C&C son:

## Tubos y Filtros (Pipe and Filter)
Un sistema que usa este estilo utiliza una red de transformadores para realizar el resultado deseado.

Tiene un solo componente: Filtro. Y un solo conector: Tubo.
Un filtro realiza transformaciones y le pasa los datos a otro filtro a través de un tubo.

## Estilo de datos compartidos
Dos tipos de componente: repositorio de datos y usuario de datos.
Repositorio de datos: provee almacenamiento permanente confiable.
Usuarios de datos: acceden a los datos en el repositorio, realizan calculos, y ponen resultados otra vez en el repositorio.

La comunicacion es **SOLO** a travez del repositorio

En este estilo solo hay un tipo de conector: lectura/escritura, no implica que no pueda ser complejo lo que se lee/escribe

Tiene 2 variantes
### Estilo pizarra
Cuando se agregan/modifican datos en el repositorio, se informa a todos los usuarios

### Estilo repositorio
El repositorio es pasivo

## Estilo cliente-servidor
Dos tipos de componentes: clientes y servidores

Los clientes solo se comunican con el servidor pero no con otros clientes

Siempre la comunicacion la inicia el cliente y espera respuesta del servidor

Solo un tipo de conector: solicitud/respuesta (request/reply) (asimetrico)

Tiene una estructura multinivel por lo general

Ej:
* Nivel del cliente: contiene a los clientes
* Nivel intermedio: contiene las reglas del servicio
* Nivel de base de datos: reside la informacion

## Otros estilos
Estilo publicar-subscribir (publish-subscribe):
* Dos tipos de componentes: las que publican eventos y las que se suscriben a eventos
* Cada vez que un evento es publicado se invocan las componentes suscriptas a dicho evento

Estilo peer-to-peer:
* Un unico tipo de componente
* Cada componente le puede pedir servicios a otra
$\approx$ modelo de computacion orientado a objetos

Estilo de procesos que se comunican:
* Procesos que se comunican a traves de pasaje de mensajes

# Metodo de analisis ATAM (Architecture Tradeoff Analisis Method)
Analiza las propiedades y las concesiones entre arquitecturas. (sirve para compararlas)

Pasos principales:
1. Recolectar escenarios:
	1. Los escenarios describen las interacciones del sistema.
	2. Elegir los escenarios de interes para el analisis
	3. Incluir escenarios excepcionales solo si son importantes

2. Recolectar requerimientos y/o restricciones:
	1. Definir lo que se espera del sistema en tales escenarios
	2. Deben especificar los niveles deseados para los atributos de interes

3. Describir las vistas arquitectonicas:
	1. Las vistas del sistema que seran evaluadas son recolectadas
	2. Distintas vistas pueden ser necesarias para distintos analisis

4. Analisis especificos a cada atributo:
	1. Se analizan las vistas bajo distintos escenarios separadamente para cada atributo de interes distinto
	2. Esto determina los niveles que la arquitectura puede proveer en cada atributo
	3. Se comparan con los requeridos
	4. Esto forma la base para la eleccion entre una arquitectura u otra o la modificacion de la arquitectura propuesta
	5. Puede utilizarse en cualquier tecnica o modelado

5. Identificar los puntos sensitivos y de compromisos:
	1. Analisis de sensibilidad: cual es el impacto que tiene un elemento sobre un atributo de calidad.
	   Los elementos de mayor impacto son los puntos de sensibilidad
	2. Analisis de compromiso:
	   Los puntos de compromiso son los elementos que son puntos de sensibilidad para varios atributos


# Diseño
Empieza cuando los requerimientos estan definidos, pero se hace antes de la implementacion, funciona como lenguaje intermedio entre requerimientos y codigos. Es el desplazamiento del dominio del problema al dominio de la solucion

Los niveles en el proceso de diseño
* Diseño arquitectónico: Identifica las componentes necesarias del sistema, su comportamiento y relaciones
* Diseño de alto nivel: Es la vista de modulos del sistema
  Es decir: cuales son los modulos del sistema, que deben hacer, y como se organizan/interconectan.
* Diseño detallado o diseño logico: Establece como se implementan las componentes de los modulos de manera que satisfagan sus especificaciones
  Incluye detalles del procesamiento logico (i.e algoritmos) y de las estructuras de datos
  Muy cercano al codigo

## Criterios de diseño
* **Correccion**
* **Eficiencia
* **Simplicidad

Correccion: ¿el diseño implementa los requerimientos? ¿es factible el diseño dada las restricciones?

Eficiencia: Le compete el uso apropiado de los recursos del sistema, el desempeño es adecuado

Simplicidad: Un diseño simple facilita la comprensión del sistema lo cual hace al software mantenible. Ademas facilita el testing, el descubrimiento y correccion de bugs, y la modificacion de codigo

## Principios de diseño
Los fundamentales son:
* **Particion y jerarquia
* **Abstraccion
* **Modularidad

### Particion y jerarquia
Principio basico: "dividir y conquistar"

Dividir el problema en pequeñas partes que sean manejables:

* Cada una debe poder solucionarse separadamente
* Cada parte debe poder modificarse separadamente


Pero no son totalmente independientes entre si: deben comunicarse/cooperar para solucionar el problema mayor. 

Pero la comunicacion agrega complejidad, entonces a medida que la cantidad de componentes aumenta, el costo del particionado tambien aumenta. La mejor opcion es deterner el particionado cuando el costo supera al beneficio

Tratar de mantener la mayor independencia posible entre las distintas
partes logra simplificar el diseño y facilita el mantenimiento

### Abstraccion
La abstracción de una componente describe el comportamiento externo sin dar detalles internos de cómo se produce dicho comportamiento.

Abstracción de componentes existentes:
* Representa las componentes como cajas negras
* Oculta detalle, provee comportamiento externo
* Util para comprender sistemas existentes, por lo tanto tiene un rol importante en el mantenimiento
* Util para determinar el diseño del sistema existente

Abstraccion durante el proceso de diseño:
* Las componentes no existen
* Para decidir como interactuan las componentes solo el comportamiento externo es relevante
* Permite concentrarse en una componente a la vez
* Permite considerar una componente sin preocuparse de las otras
* Permite que el diseñador controle la complejidad
* Permite una transicion gradual de lo mas abstracto a lo mas concreto
* Necesaria para solucionar las partes separadamente

Dos mecanismos comunes de la abstraccion:
* Abstraccion funcional
* Abstraccion de datos

Abstraccion funcional:
* Especifica el comportamiento funcional de un modulo
* Los modulos se tratan como funciones de entrada/salida
* La mayoria de los lenguajes proveen caracteristicas para soportarla
* Un modulo funcional puede especificarse usando pre y post condiciones
* Forma la base de las metodologias orientadas a funciones

Abstraccion de datos:
* Una entidad del mundo real provee servicios al entorno
* Es el mismo caso para las entidades de datos: se esperan ciertas operaciones de un objeto de dato
* Detalles internos no son relevantes
* La abstraccion de datos provee esta vision
  Los datos se tratan como objetos junto a sus operaciones.
  Las operaciones definidas para un objeto sólo pueden realizarse sobre este objeto.
  Desde fuera, los detalles internos del objetos permanecen ocultos y sólo sus operaciones son visibles.
* Muchos lenguajes soportan abstraccion de datos
* Forman la base de la metodologia orientada a objetos

### Modularidad
Un sistema se dice modular si consiste de componentes discretas tal que puedan implementarse separadamente y un cambio a una de ellas tenga mínimo impacto sobre las otras.

Modularidad:
* Provee la abstraccion en el software
* Es el soporte de la estructura jerarquica de los programas
* Mejora la claridad del diseño y facilita la implementacion
* Reduce los costos de testing, debugging y mantenimiento

Necesita criterios de descomposición: resulta de la conjunción de la abstracción y el particionado.

# Diseño orientado a funcion
## Acoplamiento
Dos módulos son independientes si cada uno puede funcionar completamente sin la presencia del otro.

Se desea independencia entre modulos:
* Los modulos se pueden modificar separadamente
* Se pueden implementar y testear independientemente
* El costo de programacion decrece

En un sistema no existe independencia entre todos los modulos, por lo tanto deben cooperar entre si

Cuanto más conexiones hay entre dos módulos, más dependientes son uno del otro
El acoplamiento captura la nocion de dependencia

Entonces nuestro objetivo es que los modulos sean tan debilmente acoplados como sea posible. Es un concepto inter-modular

**Factores que mas influyen:
* **Tipo de conexiones entre modulos. Ej: ¿Utilizo sólo las interfaces especificadas o también uso datos compartidos?
* **Complejidad de las interfaces. Ej: ¿Estoy pasando solo los parametros necesarios?
* **Tipo de flujo de informacion entre modulos. Ej:  ¿Estoy pasando parametros de control (pej. flags)?

El acoplamiento queda definido por la "fuerza de conexion" entre dos modulos

En general: cuando mas necesitamos conocer un modulo A para comprender un modulo B, mayor es la conexion de A a B

**La complejidad y oscuridad de las interfaces de un modulo aumenta el acoplamiento

El acoplamiento disminuye si:
* Solo las entradas definidas en un modulo son utilizadas por otros
* La informacion se pasa exclusivamente a traves de parametros

El acoplamiento se incrementa si:
* Se utilizan interfaces indirectas y oscuras
* Se usan directamente operaciones y atributos internos al modulo
* Se utilizan variables compartidas

El acoplamiento depende del tipo de flujo de informacion

Dos tipos de informacion: control o dato

Transferencia de información de control:
* Las acciones de los modulos dependen de la informacion
* Hace que los modulos sean mas dificiles de comprender

Transferencia de  informacion de datos:
* Los modulos se pueden ver simplemente como funciones de entrada/salida

Bajo acoplamiento: Las interfaces solo contienen comunicacion de datos
Alto acoplamiento: Las interfaces contienen comunicacion de informacion hibrida (datos + control)

## Cohesion
Caracteriza el vínculo intra-modular.

Con la cohesion intentamos captura cuan cercanamente estan relacionados los elementos de un modulo entre si (es decir, da la idea de si distintos elementos de un modulo tienen caracteristicas comunes)
**Buscamos: Menor acoplamiento y mayor cohesion (estan correlacionados pero no perfectamente correlacionados)

Objetivo: Alta cohesion
Para esto existen varios niveles (escala no lineal):
| Nivel          | Desde mas debil a mas fuerte                                                                                                    |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Casual         | La relación entre los elementos del módulo no tiene significado                                                                 |
| Logica         | Existe alguna relación lógica entre los elementos del módulo; los elementos realizan funciones dentro de la misma clase lógica  |
| Temporal       | Parecida a la cohesion logica pero los elementos estan relacionados en tiempo y se ejecutan juntos                              |
| Procedural     | Contiene elementos que pertenecen a una misma unidad procedural                                                                 |
| Comunicacional | Tiene elementos que estan relacionados por una referencia al mismo dato                                                         |
| Secuencial     | Estan juntos porque la salida de uno corresponde a la entrada del otro                                                          |
| Funcional      | Es la mas fuerte de todas las cohesiones: Todos los elementos del modulo estan relacionados para llevar a cabo una sola funcion |

Como determinar la cohesion de un modulo?
Describir su proposito con una oracion

Realizar el siguiente test
+ Si la oracion es compuesta entonces el modulo esta probablemente realizando mas de una funcion. Probablemente tenga cohesion secuencial o comunicacional
+ Si tiene palabras relacionadas (ej: primero, segundo) entonces probablemente tenga cohesion temporal o secuencial
+ Si no contiene un unico objeto especifico a continuacion del verbo probablemente tenga cohesion logica
+ Palabras como inicializar/limpiar/... implican cohesion temporal

Los modulos funcionalmente cohesivos siempre pueden describirse como una oracion simple

Dos aspectos de interes en la fase de diseño:
* El diseño del sistema
	* El proceso que lleva a cabo el diseño