# Arduino_Capitulo_22
El presente proyecto es la prueba del programa demuestra el funcionamiento del codificador rotatorio KY-040 permitiendo incrementar o decrementar un valor inicial dependiendo del sentido de giro del mismo y estableciendo un limite minimo y maximo que puede asumir la variable POSICION.
Ademas de la justificacion de la ejecucion de Arduino capitulo 22 de BitwiseAr

# Justificacion
Primero tenemos que entender como funciona el incremento y decremento de la potencia. Teniendo como referencia cada pata de una resistencia donde la mas corta se tomara como A y la mas larga sera B.
Si ambos puntos de las resistencias se enuentran fueran de cotacto tanto A como B se encontraran con un valor de corriente alto, ppor ende si se encuentran en contacto con el potenciometro su nivel de potencia sera bajo.
Si la punta que conocemos con valor de A hace contacto primero con el potenciometro decimos que gira en sentido horario (CW), si B es el que entra en contacto primero, significa que gira en sentido antiorario (CCW).

# Funcionamiento codigo
Para iniciar se declaran variables con los valores de los pines asignados a las partes del modulo DT (pin 2) y CLK (pin 4) luego declaramos una variable llamada Anterior se va autilizar para que la comsola pueda escribir siempre y cuando la variable posicion sea diferente a 50. 
Declaramos el modo de los pines A y B tipo entrada, lla siguiente funcion llamada attachInterrupt servira para asignar la interrupcion a cualquier pin seleccionado con un valor bajo. Declaramos una condicion la cual su condicion sera que si las variables POSICION y ANTERIOR su valor es diferente, imprimira el valor que esta guardando posicion, despues de esto la variable ANTERIOR tendra que actualizar su valor con el dato almacenado en posicion.
Declararemos la funcion ISR que es la de mayor importancia para la ejecucion de nuestro codigo, en la funcion indicamos que si se lee un nivel de potencia alto en el pin B el contador aumentara su valor, de lo contrario disminuira.
Ahora realizaremos las condicionales correspondientes para evitar un rebote no deseado, ya que por fabricacion del pulsador existe la probabilidad de que existan pulsos continuos sin que se le hayan indicado. Ese pulso debe desestimarce ya que es producto de un rebote.
