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
Lo primero que vamos a hacer es utilizar las Sorting Layers. <!-- canva -->
¿Qué son las Sorting Layers en Unity?
Las Sorting Layers se usan principalmente para determinar el orden de renderizado de los objetos en 2D (como sprites, UI, partículas, etc.). Sirven para controlar qué se dibuja encima o debajo de otros objetos, sin necesidad de moverlos en el eje Z.

Selecciona un GameObject con un SpriteRenderer.
En el Inspector, verás estas dos propiedades:
Sorting Layer: El nombre de la capa (por ejemplo, "Background", "Player", "UI").
Order in Layer: Un número entero que define la prioridad dentro de la capa (mayor número = se dibuja encima).
VAmos a crear nuevas Sorting Layers desde:
Edit > Project Settings > Tags and Layers > Sorting Layers
<!-- Desafío: pseudocódigo sembrar adelante del personaje y en la dirección que está mirando-->

<!-- Solución e implementación -->

<!-- PreFAbplanta -->

<!-- Modificar código para reciclarlo -->

<!-- Agregar valores al inspector -->

<!-- Menú siembra -->

<!-- Guardar juego -->

<!-- recoger semillas -->