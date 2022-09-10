# Codificación

## Objetivo: implementar el diseño de la mejor manera posible

* Afecta al testing y al mantenimiento
* La idea es escribir codigo que reduzca tales costos, pues el testing suele ser caro


## Principios y pautas para la Programacion
* Constructores de control: Utilizar pocos constructores estructurados
* Gotos: No usar
* Ocultamiento de la informacion: Usarla!
* Tipos definidos por el usuario: Utilizarlo para facilitar la lectura de los programas
* Tamaño de los modulos: No deberian ser muy largos para evitar la perdida de cohesion
* Interfaz del modulo: hacerla simple
* Robustez: Manipular situaciones excepcionales
* Efectos secundarios: Evitarlos, documentar (ej: vars globales)


## Proceso de Codificación
Proceso basico:
* Escribir codigo del modulo
* Realizar test de unidad
* Si error: arreglar bugs y repetir test
![[Pasted image 20220901110105.png]]

### Desarrollo dirigido por test
_Definicion_:
Falso positivo/negativo
Es cuando un test da un resultado el cual es erroneo, pej: Un test da falso positivo si el test paso pero el bug esta. Y falso negativo cuando el test no pasa pero ningun bug se encuentra.

### Programacion de a pares
Eficiencia: No se sabe
Idea: 
* El código se escribe por dos programadores en lugar de individuos:
	* Conjuntamente, ambos programadores diseñan los algoritmos, estructuras de datos, estrategias, etc.
	* Una tipea, la otra lo revisa
	* Se señalan errores y conjuntamente se buscan soluciones
	* Los roles se alternan periodicamente
* Revision continua de codigo
* Mejor diseño en general
* Mas dificil que escapen las condiciones particulares

## Refactorizacion


### Conceptos basicos

### Ejemplo
![[Pasted image 20220901110241.png]]
![[Pasted image 20220901110248.png]]
![[Pasted image 20220901110303.png]]
![[Pasted image 20220901110311.png]]

## Refactorizaciones mas comunes
* Muchas formas de mejorar el diseño de programas
* Existen catalogos que se extienden continuamente
* Para mejorar el diseño se enfocan en
	* metodos,
	* clases,
	* jerarquia de clases
* Siempre el objetivo es mejorar el acoplamiento, la cohesion, y el principio abierto cerrado

### Refactorizaciones mas comunes
#### Extraccion de metodos
* Se realiza si el metodo es demasiado largo
* Objetivo: separar en metodos cuya signatura indique lo que el metodo hace
* Partes del codigo se extraen en nuevos metodos
* Variables referenciadas en estas partes se transforman en parametros
* Variables definidas en esta parte pero utilizadas en otras partes deben definirse en el metodo original
* Tambien se realiza si un metodo retorna un valor y tambien cambia el estado del objeto

#### Mejoras de clases
##### Extraccion de clases
* Si una clase agrupa multiples conceptos, separa cada concepto en una clase distinta
* Mejora cohesion

##### Reemplazar valores de datos por objetos
* Algunas veces, una coleccion de atributos se transforma en una entidad logica
* Separarlos como una clase y definir objetos para accederlos

#### Mejoria de jerarquías
##### Reemplazar condicionales con polimorfismos

##### Subir metodos/atributos

## Verificacion
### Inspeccion de codigo
### Testing de unidad
### Metodos formales


