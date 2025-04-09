<!-- Guión para la sesión 13 de Motores de Videojuegos -->

<!-- Comentario -->
<!-- Bienvenida y objetivo de la sesión -->
# Bienvenida
Buenos días, hoy es nuestra sesión 13, vamos a:
1. Usar Git Hub para respaldar / mover / compartir nuestro proyecto.
2. Ubicación de la siembra.
3. Evitar que nuestro player pise las siembras.
4. Reusar nuestro código con otra semilla
5. Agregar un menú
<!-- Recursos del juego -->
# Recursos para la sesión
Vamos a necesitar el archivo de la sesión pasada, y los UI de SproutLands, dejo el enlace en la plataforma, una cuenta de GitHub.

<!-- Git hub -->
Como pudieron notar en el video anterior, y también en este momento, los gráficos de la computadora que estoy usando no son óptimos. Por esa razón, voy a cambiar de equipo. Pensando en que alguno de ustedes podría encontrarse en una situación similar, les mostraré cómo hacer este cambio utilizando GitHub para mantener nuestro proyecto actualizado y accesible desde cualquier computadora.

<!-- Abirir en Unity -->
Abre el Unity Hub y haz clic en el botón que dice "Add". Después, busca la carpeta donde guardaste tu proyecto y selecciona "Open". Una vez que el proyecto aparece en la lista, ya está listo para usarse. Ábrelo... y comencemos.
<!-- Sorting Layers y distancia de siembra -->
# Ubicación de la siembra

<!-- canva -->
Lo primero que vamos a hacer hoy es trabajar con Sorting Layers.

¿Y qué son las Sorting Layers en Unity?

Son una herramienta que nos permite controlar el orden en el que se dibujan los objetos 2D en pantalla, como sprites, interfaces de usuario, partículas, entre otros. Esto es muy útil cuando queremos que ciertos elementos aparezcan encima o debajo de otros, sin tener que moverlos en el eje Z.
<!-- unity esperar 3 seg -->
Selecciona un GameObject que tenga un Sprite Renderer.
En el panel del Inspector, verás dos propiedades importantes:

Sorting Layer: Aquí eliges el nombre de la capa, como por ejemplo "Background", "Player" o "UI".

Order in Layer: Es un número entero que indica la prioridad dentro de esa capa. Mientras más alto sea el número, más al frente se dibuja el objeto.

Ahora vamos a crear nuestras propias Sorting Layers.
Para hacerlo, ve al menú:

Edit > Project Settings > Tags and Layers > Sorting Layers


<!-- Desafío: pseudocódigo sembrar adelante del personaje y en la dirección que está mirando-->

<!-- Solución e implementación -->

<!-- PreFAbplanta -->

<!-- Modificar código para reciclarlo -->

<!-- Agregar valores al inspector -->

<!-- Menú siembra -->

<!-- Guardar juego -->

<!-- recoger semillas -->