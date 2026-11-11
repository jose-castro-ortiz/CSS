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

### Tienda Online – Catálogo de Productos

Esta actividad consistió en darle vida al catálogo con CSS, haciendo que la página reaccione cuando el usuario interactúa con ella. Trabajé en la rama feature/interactividad-css.

Lo que hice
Menú lateral: al pasar el cursor por una categoría cambia el fondo y el texto. Con CSS le puse un "•" antes de cada una y, si se navega con Tab, aparece un contorno naranja para saber dónde se está.
Tarjetas: al pasar el cursor la tarjeta sube un poquito. Junto a cada título puse una insignia que dice "¡Nuevo!", y en el producto destacado dice "¡Oferta!".
Botón Comprar: cambia de fondo al pasar el cursor y, al hacer clic, se hunde y cambia de color, como si de verdad lo estuviera presionando.
Hallazgos: Pseudoclases y Pseudoelementos

1. Qué diferencia hay entre una y otra. Una pseudoclase (:hover, :active, :focus) cambia cómo se ve algo que ya existe cuando el usuario hace algo con él, como pasar el cursor o hacer clic. Un pseudoelemento (::before, ::after) en cambio crea algo nuevo que no está escrito en el HTML, como el "•" del menú o las insignias. Para mí, la pseudoclase reacciona y el pseudoelemento agrega.

2. Por qué importa :focus. Hay personas que no usan el mouse y se mueven por la página con la tecla Tab. Si no se les muestra en qué enlace están, se pierden. El :focus les da esa señal visual, y por eso es clave para que la página sea accesible para todos.

3. Por qué decorar desde CSS. Si las insignias o los iconos se escribieran en el HTML, tendría que llenarlo de etiquetas que solo sirven de adorno. Con ::before y ::after el HTML se queda limpio, con solo el contenido real, y si quiero cambiar el diseño lo hago en un solo lugar sin tocar cada tarjeta.

Cómo lo comprobé

Abrí las herramientas de desarrollador, inspeccioné un enlace del menú y un botón, y con la opción :hov activé :hover, :active y :focus para ver cómo cambiaban. También vi que los ::before y ::after aparecen en el árbol de elementos aunque no estén en mi HTML.
