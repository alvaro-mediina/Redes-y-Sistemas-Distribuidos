# 📘🔍 Introducción
*Cuando la carga ofrecida a cualquier red es mayor que la que puede manejar, se genera una congestión.*
La **capa de red** detecta la congestión cuando las colas crecen demasiado en los enrutadores y trata de lidiar con este problema, aunque lo único que haga sea descartar paquetes


# 📚 Definiciones
- *Ventana de congestión*: su tamaño es el número de *bytes* que puede tener el emisor en la red en cualquier momento dado.


# 🧠 Lo que TCP hace para evitar problemas con duplicados retrasados:

1. **Numera cada byte**, no cada segmento.
2. Usa un campo de **32 bits para secuencias** (actualmente), lo que permite $2^{32}$ bytes únicos antes de reiniciar.
3. Se asegura de que **los números de secuencia no se repitan dentro del MSL**.
4. Usa ventanas de recepción para **desechar duplicados**. 
5. El wrap-around está **permitido**, pero TCP debe evitar que datos viejos sean aceptados como nuevos.