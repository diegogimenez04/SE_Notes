![[Pasted image 20220821121706.png ]]
* Especifica toda la funcionalidad que el sistema debe proveer
* Especifica que salida debe proveerse para cada entrada dada y las relaciones entre ellas
* Describe todas las operaciones que el sistema debe realizar
* Describe las entradas validas y las verificaciones de validez de entrada y salida
* Describe el comportamiento de sistema en caso de entradas invalidas, errores de calculo u otras situaciones anormales (o en el caso de situaciones normales pero con imposibilidad de operar – ej. avión fully booked)

Las otras componentes son:
* Desempeño (performance)
* Restricciones de diseño
* Interfaces externas

Ej:
* Ante una entrada invalida, el sistema debe mostrar un mensaje de error y permitir al usuario cargar de nuevo la entrada
* Al cargar los datos del usuario, solamente se permitiran numeros a la hora de cargar su DNI

![[Pasted image 20220821151930.png]]
El objetivo principal es poder lograr entender lo que quiere el cliente

![[Pasted image 20220821152042.png]]
Especificar los requisitos permite poder formalizar las ideas abstractas que provienen del analis (entendimiento) del cliente

![[Pasted image 20220821152320.png]]
* Correcta
* Completa
* No ambigua
* Consistente
* Verificable
* Rastreable (Traceable)
* Modificable
* Ordenada en aspectos de importancia y estabilidad

Si no fuera verificable, tranquilamente el cliente al mostrar el sistema con las especificaciones, podria dar un punto de vista subjetivo y habria problemas. Por ejemplo: El cliente quiere que el sistema cargue "rapido", pero "rapido" no es verificable y genera ambiguedad
Si no fuera completa, podria haber ambiguedades en el sistema y llegar a problemas del tipo "el cliente queria un color pero como nunca se especifico el color hubo problemas porque el cliente cree que se ve feo"
Si no fuera modificable, el cliente podria haberse arrepentido de una decision anterior y no podria modificarla. Ademas si no fuera modificable ademas de ser ambiguo llevaria a problemas mucho mayores

![[Pasted image 20220821152750.png]]
![[Pasted image 20220823124611.png]]
1) 
![[Pasted image 20220823124627.png]]
![[Pasted image 20220823124635.png]]
### Caso de uso 1: Retirar un libro de la biblioteca
Actor primario: Usuario
Precondicion: El usuario esta registrado en la biblioteca
Escenario exitoso principal:
1) El usuario intenta retirar un libro
2) El sistema pide al usuario primero que escanee su tarjeta de miembro
3) El usuario escanea su tarjeta
4) El sistema pide al usuario que ahora escanee los libros que desea llevarse
5) El usuario escanea sus libros y toca el boton para terminar la operacion
6) El/los libro/s se marca en el sistema como prestados y se registra el momento en el cual se saco el libro
7) El sistema informara que la tarea fue exitosa y se le dira hasta que dia y hora tiene para devolver el libro dependiendo si es estudiante o docente

Escenarios excepcionales:
1) El usuario tiene una penalizacion por haber demorado la entrega de algun libro
	1) No se desactivara el codigo antirrobo del libro
	2) El sistema avisara al usuario que tiene una penalizacion anterior y no se le permitira llevar el libro
2) El libro es exclusivo de consulta en la biblioteca
	1) No se desactivara el codigo antirrobo del libro
	2) El sistema avisara al usuario que ese libro es exclusivo de consulta en la biblioteca

### Caso de uso 2:  Darse de alta como usuario de la biblioteca
Actor primario: Usuario
Precondicion: El usuario quiere darse de alta
Escenario exitoso principal:
1) 
2) El sistema pide al usuario primero que escanee su tarjeta de miembro
3) El usuario escanea su tarjeta
4) El sistema pide al usuario que ahora escanee los libros que desea llevarse
5) El usuario escanea sus libros y toca el boton para terminar la operacion
6) El/los libro/s se marca en el sistema como prestados y se registra el momento en el cual se saco el libro
7) El sistema informara que la tarea fue exitosa y se le dira hasta que dia y hora tiene para devolver el libro dependiendo si es estudiante o docente

Escenarios excepcionales:
1) El usuario tiene una penalizacion por haber demorado la entrega de algun libro
	1) No se desactivara el codigo antirrobo del libro
	2) El sistema avisara al usuario que tiene una penalizacion anterior y no se le permitira llevar el libro
2) El libro es exclusivo de consulta en la biblioteca
	1) No se desactivara el codigo antirrobo del libro
	2) El sistema avisara al usuario que ese libro es exclusivo de consulta en la biblioteca
