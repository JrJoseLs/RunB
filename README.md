# La noche del Mímico

Juego 3D de terror ligero para el navegador, hecho con [Three.js](https://threejs.org/). En la plaza de un pueblo con niebla hay cinco vecinos con farol, y uno de ellos es **el Mímico**: una criatura que puede convertirse en cualquier objeto de la plaza o copiar la cara de otro vecino para acercarse sin levantar sospechas.

Todo el juego está en un solo archivo, `index.html`. No hay que instalar ni compilar nada.

## Cómo jugar

Abre `index.html` en un navegador moderno (Chrome, Edge, Firefox o Safari), o entra en la página de GitHub Pages de este repositorio. Necesitas conexión a internet, porque Three.js y las fuentes se cargan desde CDN.

En el menú eliges tu rol y la computadora controla a los otros cuatro personajes.

### Superviviente

- **Objetivo:** encender los 5 braseros de la plaza antes de que acabe la noche (4 minutos).
- **Destello del farol:** aturde al Mímico y le quita el disfraz si le apuntas de cerca.
- **Capullo:** si el Mímico te atrapa, quedas en un capullo durante 45 s y un compañero puede liberarte. Si te atrapa por segunda vez, te devora.

### El Mímico

- **Objetivo:** atrapar a los cuatro supervivientes, o aguantar hasta que se acabe el tiempo.
- **Disfraces:** puedes copiar el objeto más cercano (barril, cajón, calabaza, roca, lápida, farol…) o el rostro de un vecino.
- **Ataques:** una embestida con zarpazo y un salto largo para cerrar distancia.
- **Sabotaje:** puedes apagar braseros ya encendidos.

Durante los primeros 12 segundos nadie sabe quién es el Mímico: todos parecen vecinos normales.

## Controles

| Tecla | Acción |
|---|---|
| `W` `A` `S` `D` + ratón | Moverse y mirar |
| `Shift` | Correr (gasta aliento) |
| `Espacio` | Saltar: permite pasar por encima de barriles, cajones y bancos |
| `C` | Rodar: esquiva el zarpazo (superviviente) |
| `E` (mantener) | Encender brasero · liberar a un compañero · apagar brasero (Mímico) |
| `Clic` / `F` | Destello del farol (superviviente) · zarpazo (Mímico) |
| `Q` | Mímico: copiar el objeto más cercano |
| `1` – `4` | Mímico: copiar el rostro de un vecino |
| `R` | Mímico: volver a la forma real |
| `M` | Silenciar |
| `P` | Mostrar FPS y nivel de calidad |

En pantallas táctiles aparecen un joystick y botones. Para mirar, arrastra el dedo sobre la escena.

## Cómo descubrir al Mímico

- Los objetos imitados **respiran** y de vez en cuando se les ve un brillo magenta.
- El Mímico no sabe copiar la luz: **su farol no ilumina el suelo**.
- El minimapa solo muestra a los vecinos reales. Si ves a dos personas iguales, una sobra.
- Si juegas de superviviente, oyes un **latido** que se acelera cuando el Mímico está cerca.

## Gráficos y rendimiento

En el menú puedes elegir la calidad: **Auto**, Baja, Media, Alta o Ultra. En modo Auto el juego empieza en Media y sube o baja según los FPS que consiga tu equipo. La elección se guarda en el navegador.

Si el juego va lento:

1. Pulsa `P` durante la partida para ver los FPS.
2. Elige la calidad **Baja** en el menú.
3. Comprueba que el navegador tenga activada la aceleración por hardware. En Chrome o Edge está en Configuración → Sistema → «Usar aceleración por hardware». Si está desactivada, el menú muestra un aviso.

## Tecnología

- **Three.js r147.** Postprocesado con bloom y corrección gamma.
- **Modelos procedurales:** personajes, criatura, casas, árboles y objetos se construyen por código, sin archivos externos.
- **Optimización:** la geometría estática se fusiona por material y por zona para reducir las llamadas de dibujo. Las colisiones usan una cuadrícula espacial. La calidad es adaptativa y las sombras siguen al jugador.
- **Sonido:** se genera con la Web Audio API (ambiente, latido, pasos, rugidos, destellos).
- **Inteligencia artificial:**
  - Los supervivientes se reparten los braseros, sospechan de objetos que se mueven y de caras duplicadas, huyen, usan el destello y ruedan para esquivar.
  - El Mímico alterna entre perseguir, hacerse pasar por un vecino, emboscar disfrazado de objeto y apagar braseros.

## Estructura

```
index.html   El juego completo: HTML, CSS y JavaScript
README.md    Este archivo
```

## Publicar en GitHub Pages

1. Sube `index.html` a la raíz del repositorio.
2. En el repositorio, ve a **Settings → Pages**.
3. En *Source*, elige la rama principal y la carpeta `/ (root)`.
4. En unos minutos el juego estará disponible en `https://<tu-usuario>.github.io/<tu-repositorio>/`.
