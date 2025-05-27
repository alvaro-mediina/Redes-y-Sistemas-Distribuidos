# Ejercicio H
*a.* Se elige el camino más corto de 1d a 3a, este camino pasa por 1a y 1c . Por lo tanto hay que usar $I_1$. Se agrega la tabla de reenvio entonces $(x, I_1)$
*b.* Ahora suponiendo que hay un enlace físico entre $AS4$ y $AS2$
Bajo estas condiciones  $I$ ahora es $I_2$ puesto que el camino es más corto.
	*1d* tiene dos caminos:
		- 3a, $AS3$, $AS4,x$ 
		- 2a, $AS2$, $AS4$, $x$
	Por lo tanto hay que usar *hot potato routing*. El camino más corto interno a 3a es 1d, 1a, 1c, 3a que tiene costo 3. El camino más corto interno es 2a: 1d, 1b, 2a. Este último es el que tiene la menor distancia. Por lo tanto se lo escoge. Esto quiere decir que la línea de salida es a 1b. Por lo tanto se usa la interfaz $I_2$. Entonces se agrega a la tabla de reenvío ($I_2$, $x$)
*c.* Tenemos dos rutas: 3a, AS3, AS4, x y a otra ruta es: 2a, AS2, AS5, AS4, x. Como la primera tiene menos sistemas autónomos se la elige. Para ir a 3a el camino más corto es por $I_1$. Luego se agrega a la tabla $(I_1, x)$
