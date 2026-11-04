# CSS
# 1. La diferencia práctica entre Margin y Padding
- **Padding (Relleno interno):** Es el espacio que se genera **dentro** del elemento, ubicado entre su contenido (texto o enlaces) y su borde[cite: 1]. Permite que los elementos internos no queden pegados a las paredes de la caja[cite: 1, 3].
- **Margin (Margen exterior):** Es el espacio de separación que se aplica **fuera** de los límites de la caja[cite: 3]. Sirve para empujar a los elementos vecinos y evitar colisiones visuales entre ellos en la pantalla

# 2. Por qué es obligatorio usar box-sizing: border-box
Por defecto, los navegadores calculan el tamaño de las cajas sumando el ancho, el relleno (`padding`) y los bordes (`border`), lo que suele desconfigurar el diseño[cite: 2]. Al declarar `box-sizing: border-box;` en el selector universal (`*`), le indicamos al navegador que el relleno y los bordes se incluyan dentro del ancho y alto total definido, manteniendo la estructura organizada y sin romper el contenedor padre

# 3. Cómo se ven afectados los elementos hermanos cuando se aplica un margen grande a uno de ellos
Cuando se le aplica un margen grande a un elemento, este genera un "campo de fuerza" o espacio de separación que empuja y desplaza de manera visual a sus elementos hermanos adyacentes a lo largo del flujo del documento, obligándolos a mantener una distancia mayor para evitar superposiciones


# 1. Variables declaradas

En `:root` declaré estas variables:

Colores
- `--color-primario`: #d9534f (header)
- `--color-secundario`: #a94442 (categorías)
- `--color-fondo-main`: #dff0d8 (fondo de productos)
- `--color-fondo-tarjeta`: #ffffff (tarjetas)
- `--color-borde`: #ddd (borde de las tarjetas)
- `--color-texto`: #333333 (texto general)
- `--color-texto-claro`: #ffffff (enlaces)

Espaciados
- `--espaciado-pequeno`: 8px
- `--espaciado-medio`: 16px
- `--espaciado-grande`: 24px

También declaré --fuente-principal con la fuente Lora de Google Fonts.

# 2. Ventaja de reutilizar medidas de margen y relleno

Antes escribía un número distinto en cada selector 20px en uno, 15px en otro, y eso hacía que
la página se viera desordenada. Con las variables de espaciado uso siempre las mismas tres
medidas, así que todas las tarjetas y secciones tienen el mismo espacio. Además, si quiero
cambiar el espacio de toda la página, solo modifico un valor en :root y no tengo que buscar
línea por línea.

### 3. Cómo :root previene colisiones visuales

Si el mismo color o medida está escrito a mano en muchos lugares, es fácil equivocarse en uno
por ejemplo, #d9534f en un sitio y #d9534e en otro y la página queda con diferencias que casi
no se notan pero se ven mal. Con :root cada valor se define una sola vez y todos los selectores
lo leen con var(), así que no pueden contradecirse. Cuando la hoja de estilos crece y se
agregan más selectores, todos siguen usando los mismos valores y el diseño se mantiene igual
en toda la página.