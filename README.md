# CSS
# 1. La diferencia práctica entre Margin y Padding
- **Padding (Relleno interno):** Es el espacio que se genera **dentro** del elemento, ubicado entre su contenido (texto o enlaces) y su borde[cite: 1]. Permite que los elementos internos no queden pegados a las paredes de la caja[cite: 1, 3].
- **Margin (Margen exterior):** Es el espacio de separación que se aplica **fuera** de los límites de la caja[cite: 3]. Sirve para empujar a los elementos vecinos y evitar colisiones visuales entre ellos en la pantalla

# 2. Por qué es obligatorio usar box-sizing: border-box
Por defecto, los navegadores calculan el tamaño de las cajas sumando el ancho, el relleno (`padding`) y los bordes (`border`), lo que suele desconfigurar el diseño[cite: 2]. Al declarar `box-sizing: border-box;` en el selector universal (`*`), le indicamos al navegador que el relleno y los bordes se incluyan dentro del ancho y alto total definido, manteniendo la estructura organizada y sin romper el contenedor padre

# 3. Cómo se ven afectados los elementos hermanos cuando se aplica un margen grande a uno de ellos
Cuando se le aplica un margen grande a un elemento, este genera un "campo de fuerza" o espacio de separación que empuja y desplaza de manera visual a sus elementos hermanos adyacentes a lo largo del flujo del documento, obligándolos a mantener una distancia mayor para evitar superposiciones