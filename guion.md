<!-- Guión para la sesión 13 de Motores de Videojuegos -->

<!-- Comentario -->
<!-- Bienvenida y objetivo de la sesión -->
# Bienvenida

==título==

Buenos días, hoy es nuestra sesión 13. Hoy vamos a trabajar en varios temas importantes que nos ayudarán a construir una experiencia de juego mucho más rica y completa en Unity 2D.

# Objetivo General

El objetivo general de esta sesión continuar desarrollando un pequeño proyecto de simulación de granja, utilizando mecánicas básicas, buenas prácticas de programación y el control de versiones para gestionar nuestros avances.

Vamos a empezar con GitHub. Aprenderemos cómo funciona esta plataforma para poder versionar correctamente nuestros proyectos. Subiremos nuestros archivos, haremos nuestros primeros commits y entenderemos la lógica detrás de trabajar en la nube con código. Esto es fundamental para cualquier desarrollo profesional.

Después, vamos a ver cómo controlar la visibilidad de los objetos en nuestra escena usando las Sorting Layers. Esto nos permitirá decidir qué aparece delante y qué queda detrás, lo cual es súper útil en un juego en 2D donde hay árboles, personajes, animales, y objetos interactivos.

A continuación, enfrentaremos un desafío interesante: escribir el pseudocódigo para una mecánica que nos permita sembrar justo delante del personaje, tomando en cuenta la dirección hacia la que está mirando. Lo pensaremos primero en lógica simple y luego lo convertiremos en código funcional dentro de Unity.

Una vez que tengamos esta base, hablaremos sobre los ScriptableObjects, que nos permiten definir datos reutilizables sin necesidad de escribir mucho código adicional. Vamos a crear Scriptable Assets para nuestras plantas y semillas, lo que nos va a ahorrar tiempo y nos dará mayor organización.

Con estos elementos listos, pasaremos a modificar dos scripts importantes: el que permite sembrar una planta y el que controla su florecimiento. Esto nos ayudará a ver cómo nuestras configuraciones en los ScriptableObjects se conectan con el comportamiento del juego.

Después implementaremos un menú de siembra para que el jugador pueda elegir qué plantar. Además, mostraremos en pantalla la cantidad de semillas disponibles, para que el jugador pueda tomar decisiones basadas en los recursos que tiene.

También hablaremos de cómo guardar el estado del juego: cuántas semillas tienes, qué has sembrado, qué has recogido, etc. Aprenderemos a guardar y recuperar esta información para que el progreso del jugador no se pierda al cerrar el juego.

Luego implementaremos la opción de recoger semillas, así como un sistema de monedas para que el jugador pueda comprar objetos o herramientas dentro del juego.

Y ya que hablamos de economía, construiremos un pequeño mercadillo donde el jugador podrá, por ejemplo, comprar un hacha. Con esa hacha, podrá talar árboles dentro del juego, lo cual abrirá nuevas posibilidades para futuras mecánicas.

Pasaremos después al sistema de animales. Vamos a trabajar con un Prefab de gallina que se mueva de forma autónoma. Estas gallinas pondrán huevos, que eventualmente se convertirán en pollitos, y con el tiempo, en nuevas gallinas. Esto nos permitirá explorar conceptos de IA básica y ciclos de vida dentro del juego.

Finalmente, veremos cómo exportar el juego para que pueda ser jugado fuera de Unity. Una vez que tengan su juego listo, les pediré que suban sus evidencias al repositorio de GitHub y hagan la entrega final.

Con esto vamos a cerrar el proyecto, integrando todo lo aprendido en clase: lógica, organización, programación orientada a objetos, arte, economía del juego y publicación.
<!-- Recursos del juego -->
# Recursos para la sesión
Vamos a necesitar el archivo de la sesión pasada, y los UI de SproutLands, dejo el enlace en la plataforma, una cuenta de GitHub.

<!-- Git hub -->
# Paso 1: GitHub
Como pudieron notar en el video anterior, y también en este momento, los gráficos de la computadora que estoy usando no son óptimos. Por esa razón, voy a cambiar de equipo. Pensando en que alguno de ustedes podría encontrarse en una situación similar, les mostraré cómo hacer este cambio utilizando GitHub para mantener nuestro proyecto actualizado y accesible desde cualquier computadora.

Abre la terminal en la carpeta raíz del proyecto
Ahí donde están las carpetas Assets, ProjectSettings, Packages, etc.
Inicializa el repositorio Git
Crea un archivo `.gitignore`
Añade estas líneas. Las pondré en la plataforma.
```
[Ll]ibrary/
[Tt]emp/
[Oo]bj/
[Bb]uild/
[Bb]uilds/
[Ll]ogs/
[Mm]emoryCaptures/
sysinfo.txt
```


<!-- Crear repositorio -->
Ahora vamos a GitHub para crear un nuevo repositorio.
Este repositorio será el espacio donde guardaremos y actualizaremos nuestro proyecto.
<!-- Abirir en Unity -->
Abre el Unity Hub y haz clic en el botón que dice "Add". Después, busca la carpeta donde guardaste tu proyecto y selecciona "Open". Una vez que el proyecto aparece en la lista, ya está listo para usarse. Ábrelo... y comencemos.
<!-- Sorting Layers y distancia de siembra -->
# Ubicación de la siembra

==canva==

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

`Edit > Project Settings > Tags and Layers > Sorting Layers`

# Desafío 

<!-- Desafío: pseudocódigo sembrar adelante del personaje y en la dirección que está mirando. -->

==EN CANVA==


Ahora viene el desafío.
La idea es que el personaje siembre algo frente a él, en la dirección en la que está mirando, no justo debajo de sus pies. Tienes 5 min.


<!-- Solución e implementación -->
==Canva==

Esta es la solución que a mí se me ocurrió, pero eso no significa que sea la única forma de hacerlo.
En programación, muchas veces hay varias maneras válidas de resolver un mismo problema. Lo importante es que la lógica tenga sentido y que funcione correctamente.

Para que el prefab del trigo se siembre delante del personaje —según la última dirección en la que estaba mirando—, vamos a usar dos valores que ya estamos guardando en el Animator: ultimaDirX y ultimaDirY.

Con esos dos valores podemos construir una dirección, y usarla para calcular una posición adelantada, justo al frente del personaje. Esa será la posición donde se va a sembrar el prefab.

Ahora, vamos a modificar el método Sembrar.
En lugar del contenido que tiene actualmente, vamos a escribir lo siguiente:

==sublime==
```
public void Sembrar(InputAction.CallbackContext contexto){
    if(contexto.started){
        Debug.Log("Presionaste C");

        // Obtener la última dirección en la que se movió el jugador
        float dirX = animator.GetFloat("ultimaDirX");
        float dirY = animator.GetFloat("ultimaDirY");

        // Normalizar para que la distancia sea constante
        Vector2 direccion = new Vector2(dirX, dirY).normalized;

        // Posición final un poco delante del jugador
        Vector2 posicionFinal = (Vector2)transform.position + direccion * 1f; // Puedes cambiar la distancia

        Instantiate(trigo, posicionFinal, Quaternion.identity);
    }
}
```

Con esto, el trigo se sembrará un paso adelante, en la dirección en la que el personaje estaba mirando la última vez que se movió.
La línea donde multiplicamos por 1f nos permite ajustar qué tan lejos se siembra. Puedes aumentar o reducir ese número si quieres que esté más cerca o más lejos.

==Canva==

Hasta ahora, hemos estado creando prefabs y scripts que controlan el comportamiento de las plantas. Pero, ¿qué pasa si queremos tener muchas plantas distintas, con diferentes tiempos de crecimiento, sprites, precios, etc.? Si metemos toda esa información directamente en los scripts, va a ser difícil de mantener y modificar.

Aquí es donde entra ScriptableObject.

Un ScriptableObject es una clase especial en Unity que nos permite guardar datos como si fueran "archivitos" independientes. No necesitan estar en una escena para existir, y lo mejor de todo: se pueden editar desde el inspector como si fueran assets normales. Son súper útiles para definir configuraciones que se repiten.

¿Qué vamos a hacer?
Vamos a crear un ScriptableObject llamado `DatosSemillas`. Esta clase va a contener los datos que definen una semilla:

Nombre de la planta (por ejemplo: Trigo)

Tiempo de crecimiento

Sprite que se mostrará cuando esté plantada

Prefab que se instanciará al crecer

Precio de la semilla

Así, cada semilla será un archivo independiente que podemos arrastrar fácilmente a menús, scripts, tiendas o lo que necesitemos.

==sublime==
```
using UnityEngine;

[CreateAssetMenu(fileName = "NuevaSemilla", menuName = "Granja/Semilla")]
public class DatosSemillas : ScriptableObject
{
    public string nombre;
    public Sprite icono;
    public GameObject prefabPlantaCrecida;
    public float tiempoCrecimiento;
    public int precio;
}
```
Una vez que tengamos este script, podemos ir a Unity, hacer clic derecho en la carpeta donde lo guardamos y seleccionar:

Create > Granja > Semilla

¡Y listo! Unity creará un nuevo asset con ese formato y lo llamamos ==trigo== . Lo abrimos y llenamos los campos: 
`nombre = trigo;` , sprite, prefab, precio, etc.

Esto nos va a permitir reutilizar esta configuración cuantas veces queramos, con la ventaja de que podemos modificarla sin tocar el código. Y cuando en el juego seleccionemos qué semilla sembrar, solo tendremos que referenciar uno de estos assets y ya tendremos todos sus datos listos para usar.

== cambio de scripts (11) ==

Cambiamos el script de `Siembra Productos.cs` la linea de `private float tiempoEspera = 8f;` por

```
public DatosPlanta datos;
private float tiempo;

void Start()
{
    tiempo = datos.tiempoEntreAnimaciones;
    // usar tiempo para tus animaciones
}
```
Y en el prefab "trigo", arrastras el asset Trigo.asset al campo datos.

Modifica el script `MovimientoJugador`

```
public DatosPlanta semillaSeleccionada; // contiene el prefab

Instantiate(semillaSeleccionada.prefabCrecido, posicion, Quaternion.identity);

```
# Paso ?: Creamos otra semilla

## Prefab

Creamos un Prefab con las animaciones del Tomate.

## ScriptableObject

Creamos un nuevo ScriptableObject y lo llamamos tomate, llenamos los datos en el Inspector.

## Probarlo

En tu jugador (MovimientoJugador), en el campo semillaSeleccionada, cambia el asset Trigo por Tomate y juega la escena.
Al presionar C, deberías sembrar una planta de tomate en lugar de trigo.

# Paso ? : Creacion de menú de siembra
