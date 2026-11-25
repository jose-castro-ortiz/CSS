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


# Tienda Online – Catálogo de Productos

Página de catálogo de una tienda en línea. Durante las subactividades se centralizaron colores, tipografía y espaciados en variables (`:root`), se agregó interactividad con pseudoclases y pseudoelementos, y se modularizó el CSS con la nomenclatura BEM.

## Vista previa

![Vista del catálogo de la Tienda Online](captura.png)

## Estructura

```
├── index.html
├── styles.css            (maestro: @import, :root, body, header, catálogo y footer)
├── images.jpg
├── captura.png
└── componentes/
    ├── botones.css
    ├── menu.lateral.css
    └── tarjetas.css
```

## Hallazgos: Centralización de Identidad Visual y Espaciado

### 1. Variables declaradas en `:root`

**Colores**
- `--color-texto`, `--color-titulo`, `--color-descripcion`, `--color-precio`
- `--color-menu`, `--color-menu-hover`, `--color-categorias`
- `--color-fondo-main`, `--color-fondo-aside`, `--color-fondo-footer`
- `--color-footer-enlace`, `--color-boton`, `--color-boton-destacado`, `--color-secundario`

**Tipografía**
- `--fuente-principal`: Lora (Google Fonts)

**Espaciados y tamaños**
- `--espaciado-pequeno` (8px), `--espaciado-medio` (16px)
- `--margen-tarjeta` (3%), `--padding-tarjeta`
- `--radio-pequeno` (4px), `--radio-medio` (6px), `--radio-insignia` (10px)

### 2. Ventaja de reutilizar medidas de margen y relleno

Si cada selector lleva su propio número, la página termina con espacios distintos que no combinan. Con las variables uso siempre las mismas medidas, todo se ve ordenado, y para cambiar un espacio en toda la página edito un solo valor en `:root`.

### 3. Cómo `:root` previene colisiones visuales

Con los valores definidos una sola vez, ningún selector puede quedar con un tono o una medida ligeramente diferente. Todos leen de la misma variable con `var()`, así que aunque la hoja crezca el diseño se mantiene coherente.

## Hallazgos: Pseudoclases y Pseudoelementos

### 1. Diferencia entre pseudoclase y pseudoelemento

Una pseudoclase (`:hover`, `:active`, `:focus`) describe un estado y se activa cuando el usuario hace algo, como pasar el cursor, hacer clic o llegar con Tab. Un pseudoelemento (`::before`, `::after`) crea contenido nuevo dentro del elemento, como el punto de cada categoría o la insignia "¡Nuevo!", sin que esté escrito en el HTML.

### 2. Importancia de `:focus` para la accesibilidad

Algunas personas no usan mouse y se mueven con la tecla Tab. Si el enlace activo no se distingue, no saben dónde están. Con `:focus` y un `outline` visible, cada categoría del menú se marca claramente y la página se puede usar solo con el teclado.

### 3. Por qué inyectar elementos decorativos desde CSS

Los adornos son parte del diseño, no del contenido. Ponerlos en el HTML obliga a repetir etiquetas vacías en cada tarjeta y ensucia la estructura. Con `::before` y `::after` el HTML queda limpio, y para cambiar o quitar un adorno edito solo el CSS.

## Hallazgos: Arquitectura BEM y Modularidad

### 1. Qué significa BEM y cómo se escribe

BEM significa Bloque, Elemento y Modificador. El bloque es el componente completo (`.card`), el elemento es una parte que solo existe dentro del bloque y se escribe con doble guion bajo (`.card__title`), y el modificador es una variación y se escribe con doble guion medio (`.card--destacada`, `.btn--secundario`). Visualmente: `bloque__elemento--modificador`.

### 2. Por qué dividir el CSS en varios archivos facilita el trabajo colaborativo

Cuando todo el CSS está en un solo archivo, dos personas editan las mismas líneas y aparecen conflictos al unir el trabajo en Git. Con un archivo por componente (`tarjetas.css`, `botones.css`, `menu.lateral.css`), cada persona trabaja en el suyo, es fácil encontrar dónde está cada regla y se puede cambiar o eliminar un componente sin tocar los demás.

### 3. Cómo BEM evita la guerra de especificidad

Antes usaba selectores anidados como `article h2` o `aside ul li a`, que pesan más que una sola clase, y para pisarlos había que escribir selectores todavía más pesados. Con BEM cada regla usa una sola clase (peso 10), así que todas pesan igual y gana la que está después en el archivo. Ninguna regla pisa a otra por accidente y el resultado es predecible. Los modificadores se escriben después del bloque para sobrescribirlo de forma controlada.

### Auditoría

Se revisaron todos los selectores de `styles.css` y de `componentes/`: cada regla depende de una sola clase. Los estados (`:hover`, `:focus`, `:active`) suman una pseudoclase y pesan 20, y los pseudoelementos (`::before`, `::after`) pesan 11. La única regla por etiqueta es `body`. Los tres módulos se cargan con `@import` en las primeras líneas de `styles.css`.

## Control de versiones

```bash
git checkout -b feature/arquitectura-bem
git add .
git commit -m "refactor(styles): modularizar codigo en archivos css independientes"
git add index.html
git commit -m "refactor(html): aplicar nomenclatura BEM en los componentes del catalogo"



Arquitectura Web Modular: Flexbox, BEM y Custom Properties

Este proyecto implementa una interfaz de comercio electrónico (vitrina de productos) construida bajo una arquitectura CSS modular, escalable y totalmente elástica. Se integran principios de diseño moderno como el Modelo de Caja, la metodología BEM (Block, Element, Modifier), variables nativas de CSS (Custom Properties) y un sistema de maquetación basado en Flexbox desde la macro-estructura hasta los micro-componentes.

📁 Estructura del Proyecto

La hoja de estilos está dividida en módulos independientes para facilitar el mantenimiento y la escalabilidad:

├── index.html
└── css/
    ├── base.css        # Variables globales (Custom Properties), reset y macro-layout (.app-layout, .main-wrapper)
    ├── header.css      # Estilos de cabecera y barra de navegación (.header, .nav__list)
    ├── aside.css       # Panel lateral de filtros y categorías (.aside)
    ├── tarjeta.css     # Componente de tarjeta de producto y micro-layouts (.card)
    └── footer.css      # Pie de página y distribución de enlaces (.footer)


🛠️ Implementación de la Arquitectura

Macro-Arquitectura (.app-layout & .main-wrapper): Contenedor principal flexible en columna que garantiza el aprovechamiento total del viewport, acompañando de un contenedor central que distribuye horizontalmente la barra lateral (<aside>) y la vitrina principal (<main>).

Cabecera y Navegación (.header): Distribución espacial extrema (space-between) entre la identidad de marca y el menú, utilizando listas flexibles con espaciado uniforme.

Panel Lateral (.aside): Organización vertical estructurada para controles de filtrado y categorías.

Tarjeta de Producto (.card): Componente simétrico de altura uniforme con distribución interna elástica y alineación tipográfica en la sección de precios.

Pie de Página (.footer): Reparto equitativo de información legal, derechos de autor y redes sociales.

Hallazgos: Arquitectura Total con Flexbox

Durante la construcción y auditoría de esta interfaz, se consolidaron tres aprendizajes fundamentales sobre el comportamiento del layout moderno en CSS:

1. Control del Pie de Página con min-height: 100vh y flex-direction: column

Uno de los problemas más comunes en el desarrollo web ocurre cuando una página tiene poco contenido y el pie de página (<footer>) queda flotando a mitad de la pantalla, dejando un espacio vacío debajo. Al configurar el contenedor global (.app-layout) con display: flex y flex-direction: column, transformamos el flujo natural de la página en una columna flexible. Al añadir min-height: 100vh, obligamos a que este contenedor mida como mínimo el 100% de la altura visible del navegador. Finalmente, al darle flex: 1 al contenedor central (.main-wrapper), este actúa como una esponja que absorbe todo el espacio vertical sobrante, empujando inevitablemente al <footer> hacia el borde inferior de la pantalla sin importar qué tan corto sea el contenido.

2. Reemplazo de márgenes laterales mediante la propiedad gap

Tradicionalmente, para separar los elementos de un menú de navegación (.nav__list) o los bloques de un panel lateral (.aside), era necesario aplicar márgenes externos (margin-right o margin-bottom) a cada ítem y luego usar pseudo-clases como :last-child para eliminar el margen sobrante del último elemento y evitar desalineaciones. Con la propiedad gap dentro de un contenedor Flexbox, este problema desaparece por completo. El espaciado se gestiona desde el elemento padre —apoyado en nuestras Custom Properties como var(--espaciado-medio)—, aplicando separación únicamente entre elementos adyacentes. Esto resulta en un código más limpio, predecible y libre de efectos secundarios en los bordes del contenedor.

3. Resiliencia en tarjetas de producto: La sinergia de BEM, Custom Properties y Flexbox

En una tienda real, los títulos y descripciones de los productos nunca tienen la misma cantidad de palabras, lo que suele romper la simetría visual de las cuadrículas. Al combinar estas tres tecnologías logramos un componente indestructible:

BEM nos dio una estructura semántica clara (.card, .card__body, .card__price-wrapper, .card__button) sin conflictos de especificidad.

Custom Properties aseguraron que los espaciados internos y tipografías mantuvieran una proporción matemática coherente en toda la interfaz.

Flexbox resolvió la asimetría del contenido: al aplicar display: flex; flex-direction: column; height: 100%; a la .card y otorgarle flex-grow: 1 al contenedor de la descripción (.card__body), creamos un "resorte invisible". Si un producto tiene poco texto, su descripción crece para ocupar el espacio vacío; si tiene mucho texto, se expande naturalmente. En ambos casos, el botón de compra (.card__button) queda siempre anclado milimétricamente en la misma línea inferior, mientras que el micro-flexbox de precios (align-items: baseline) garantiza que el precio de oferta y el precio original tachado compartan exactamente la misma línea base de lectura.