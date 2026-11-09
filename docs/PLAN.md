# One More Box — Plan de diseño y desarrollo

> Estado: borrador v1. Las decisiones marcadas con **[DECISIÓN]** están pendientes de confirmar (ver sección 9).

## 1. Concepto

Un juego de escalada "rage" en el que solo haces una cosa: **subir cajas**. Empiezas siendo un punto sobre una cuerda cuántica y, caja a caja, creces a través de todas las escalas del universo hasta salir al espacio. Cada escala trae sus propias leyes físicas, que se van **sumando** a las anteriores. Si caes, vuelves al principio.

**Pilares**

1. **Una sola acción, mil interacciones.** El control no cambia casi nunca; lo que cambia es cómo se comportan las cajas y el mundo.
2. **La física real como diseñadora de niveles.** Cada mecánica sale de un fenómeno real de esa escala (efecto túnel, confinamiento, tensión superficial, microgravedad...).
3. **Difícil pero justo.** Todo peligro se anuncia antes de ocurrir. El jugador siempre debe poder decir "ha sido culpa mía".
4. **Caer duele, pero enseña.** No hay checkpoints. La caída es física y continua: atraviesas los mundos hacia abajo y puedes intentar salvarte agarrándote a algo.

## 2. Reglas base

| Regla | Propuesta |
|---|---|
| Objetivo | Llegar a la última caja, en lo más alto del universo |
| Caída | Física y continua. Si aterrizas en una caja más abajo, sigues desde ahí. Si no, acabas en la cuerda cuántica |
| Muerte | No hay barra de vida. Los enemigos no te matan: te **empujan, agarran o estorban** para tirarte. Morir es caer |
| Progreso guardado | Solo la posición actual (para poder cerrar el juego), el récord de altura y el tiempo. Nunca un checkpoint |
| Objetos | Se consiguen al llegar a ciertos mundos y **no se pierden al caer** (si no, repetir sería tedioso en vez de tenso) **[DECISIÓN]** |
| Estructura | Un único mundo vertical continuo, sin pantallas de carga. Las transiciones entre escalas ocurren mientras subes (y mientras caes) |

## 3. Control del personaje

**[DECISIÓN]** Es lo que define el "feel" del juego, hay que prototipar antes de comprometerse. Propuesta inicial:

- Moverse izquierda/derecha (y en profundidad cuando el mundo es 3D).
- **Salto con carga**: mantener para cargar, soltar para saltar. Más carga, más altura.
- **Casi sin control en el aire**: una vez saltas, estás comprometido. Esto es lo que genera la tensión.
- Sin doble salto ni agarre a bordes de serie; eso llega con los objetos.

Alternativa a probar en el prototipo: salto normal con control aéreo completo (más accesible, menos "rage").

## 4. Mundos

Cada mundo define: escala, paleta, comportamiento de las cajas, peligros, objeto que se consigue y transición al siguiente.

| # | Mundo | Escala | Dimensión | Mecánica nueva de las cajas | Peligros | Objeto |
|---|---|---|---|---|---|---|
| 0 | Cuerda cuántica | 10⁻³⁵ m | 2D | Efecto túnel; colapso al pisarlas | — | — |
| 1 | Quarks | 10⁻¹⁸ m | 2D → 3D | Fuerza fuerte, débil y electromagnética | Aniquilación con antimateria | Cambio de carga |
| 2 | Átomo | 10⁻¹⁰ m | 3D | Orbitales: cajas en capas, salto entre niveles de energía | Fotones que te excitan o te tiran | — |
| 3 | Molecular / célula | 10⁻⁹ – 10⁻⁶ m | 3D | Enlaces elásticos, movimiento browniano | Virus, bacterias | — |
| 4 | Hierba | 10⁻³ m | 3D | Agua: resbalar, tensión superficial | Hormigas, arañas, viento | Gancho de seda |
| 5 | Jardín y casa | 1 m | 3D | Cajas de cartón reales: se aplastan, se mojan, se vuelcan | Gato, aspiradora, niños | Ventosas |
| 6 | Ciudad | 10² m | 3D | Contenedores, grúas, andamios en movimiento | Palomas, lluvia, rayos | Gancho mejorado |
| 7 | Montaña y cielo | 10⁴ m | 3D | Hielo, cajas colgadas de globos, nubes | Viento fuerte, aves, aire fino | Planeador |
| 8 | Órbita | 10⁵ – 10⁷ m | 3D | Microgravedad, inercia, basura espacial | Micrometeoritos, satélites | Propulsor de gas |
| 9 | Sistema solar | 10¹² m | 3D | Pozos de gravedad, tirachinas gravitatorio | Viento solar, cinturón de asteroides | Ancla gravitatoria |
| 10 | Interestelar | 10¹⁶ – 10²¹ m | 3D | Relatividad: dilatación del tiempo, lente gravitatoria | Agujeros negros (fuerzas de marea) | — |
| 11 | Red cósmica | 10²⁶ m | 3D → 2D | Todas las anteriores, mezcladas | Expansión: las cajas se alejan solas | — |

### Mundo 0 — Cuerda cuántica (2D)

- **Estética:** fondo negro, trazo blanco fino, ruido y parpadeo. La "cuerda" es una línea que vibra en la base; personaje y cajas son contornos 2D.
- **Efecto túnel:** las cajas se teletransportan cada cierto tiempo a otra posición posible. Antes de saltar muestran su "nube de probabilidad" (fantasmas tenues en los destinos posibles) para que sea justo.
- **Colapso:** mientras estás encima de una caja, queda fija. Variante avanzada: también se fija la caja que estás **mirando**, lo que permite planificar el siguiente salto.
- **Enseña:** saltar, cargar, leer el aviso antes de un cambio.

### Mundo 1 — Quarks (transición a 3D)

- **Transición:** la cámara ortográfica pasa a perspectiva y gira; los contornos planos se extruyen y ganan volumen; aparece el color (rojo, verde, azul: la carga de color de los quarks).
- **Fuerza fuerte (confinamiento):** las cajas van en tríos unidos por "gomas" de gluones. Cuanto más separas una, más fuerte tira hacia atrás. Si la goma se rompe, aparece un par nuevo de cajas.
- **Fuerza débil (desintegración):** algunas cajas tienen cuenta atrás visible y se transforman en otro tipo (cambian de tamaño, peso o carga).
- **Electromagnetismo:** cajas con carga + o −. Tú también tienes carga: te atraen o te repelen en el salto. **Objeto:** poder invertir tu carga en el aire.
- El efecto túnel sigue activo, pero menos frecuente.

### Mundo 2 — Átomo (propuesto, opcional)

- Cajas distribuidas en capas alrededor de un núcleo. Solo puedes subir de capa con el salto justo (ni más ni menos energía: cuantización).
- Fotones que pasan: si te golpean te "excitan" y te lanzan una capa arriba o abajo.
- Sirve de puente entre lo cuántico y lo molecular. Se puede fusionar con el mundo 1 si el alcance se dispara.

### Mundo 3 — Molecular y célula

- Los efectos cuánticos se apagan poco a poco (decoherencia): menos túnel, cajas más estables.
- **Enlaces:** cajas unidas por muelles que vibran con la temperatura. Zonas calientes = más movimiento.
- **Movimiento browniano:** todo tiembla y deriva lentamente.
- **Virus:** se adhieren a una caja, la "infectan" y al cabo de unos segundos revienta en copias. También se te pegan y te añaden peso.
- **Bacterias:** te persiguen nadando con el flagelo y embisten. Se las puede esquivar o usar como plataforma móvil.
- **Aliados posibles:** anticuerpos que neutralizan virus si los llevas hasta ellos.

### Mundo 4 — Hierba

- Todo es gigante: briznas como torres, cajas apoyadas en hojas que se doblan con tu peso.
- **Agua:** superficies mojadas que resbalan; gotas de rocío en las que te quedas atrapado por tensión superficial o que usas como trampolín; gotas que caen y te arrastran.
- **Bichos:** hormigas que se llevan cajas, arañas con telarañas pegajosas, mariquitas como plataforma, pulgones.
- **Objeto: gancho de seda.** Se dispara a una caja y te columpias. Difícil a propósito: alcance corto, hay que apuntar y soltar en el momento justo.

### Mundos 5 a 7 — Escala humana

- **Jardín y casa:** cajas de cartón de verdad (se aplastan si llevan peso, se ablandan mojadas), juguetes, estanterías. El gato tira cosas de las mesas. **Ventosas:** agarre breve a superficies lisas.
- **Ciudad:** obra con grúas que mueven contenedores, andamios, fachadas. Lluvia (vuelve el resbalón), viento racheado entre edificios, rayos atraídos por las cajas metálicas (vuelve el electromagnetismo).
- **Montaña y cielo:** hielo, aludes, cajas colgadas de globos meteorológicos que suben y bajan, nubes que ocultan el camino. **Planeador:** convierte altura en distancia, sin ganar altura.

### Mundos 8 a 11 — Espacio

- **Órbita:** microgravedad. No hay "abajo": caer es alejarte a la deriva. Inercia pura; cada salto es una trayectoria. **Propulsor:** unas pocas ráfagas de gas que se recargan al tocar una caja.
- **Sistema solar:** cada cuerpo tiene su pozo de gravedad. Saltas entre asteroides-caja usando tirachinas gravitatorios. **Ancla gravitatoria:** te fija temporalmente a la órbita de un cuerpo.
- **Interestelar:** cerca de objetos masivos el tiempo va más lento (las cajas lejanas se mueven más rápido vistas desde ahí); la luz se curva y la posición aparente de las cajas no es la real.
- **Red cósmica:** los filamentos de galaxias se parecen a... una cuerda. La expansión aleja las cajas. Reaparecen todas las mecánicas anteriores.

### Final (propuesta)

En lo más alto hay una última caja. Al subirte, la cámara se aleja: todo el universo estaba **dentro de una caja**, apoyada sobre otra cuerda que vibra. Siempre hay una caja más. Desbloquea una partida nueva con variaciones.

## 5. Sistemas transversales

- **Comportamientos de caja como componentes.** Cada caja es una base física más una lista de comportamientos combinables: `Tunneling`, `Collapsible`, `Charged`, `Bonded`, `Decaying`, `Slippery`, `Crushable`, `Orbiting`... Un mundo nuevo es sobre todo una mezcla nueva de componentes.
- **Aviso previo obligatorio.** Todo comportamiento que mueve o quita una caja debe tener una señal visual y sonora antes.
- **Aleatoriedad con semilla.** Los niveles están diseñados a mano; lo aleatorio (destinos del túnel, rachas de viento) usa un generador con semilla para que sea reproducible y se pueda aprender.
- **Cámara.** 2D lateral en el mundo 0. En 3D, cámara en tercera persona con seguimiento suave y recorrido guiado en espiral alrededor de la columna de cajas, para que el salto siempre se lea bien **[DECISIÓN]**.
- **Escala.** El personaje no crece de verdad en unidades del motor: en cada transición se re-escala el mundo (evita problemas de precisión numérica).
- **Narración.** Una voz o textos breves que comentan tus caídas con datos de física y algo de sorna. Opcional, fase tardía.
- **Audio.** Cada escala con su textura: de ruido y tonos puros en lo cuántico a silencio y graves en el espacio.

## 6. Tecnología

**Propuesta: web con TypeScript + Vite + Three.js + Rapier.**

| Pieza | Elección | Motivo |
|---|---|---|
| Render | Three.js | 3D en navegador; el paso 2D → 3D es un cambio de cámara y de geometría dentro del mismo motor |
| Física | Rapier (3D, WASM) | Rápida, determinista con paso fijo, soporta muelles y articulaciones para enlaces y ganchos |
| Lenguaje y build | TypeScript + Vite | Recarga instantánea, tipado para los componentes de caja |
| Tests | Vitest | Probar la lógica de comportamientos sin render |
| Publicación | GitHub Pages con GitHub Actions | Cada push a `main` deja una versión jugable en una URL |

Ventaja para iterar: el juego se puede abrir y probar en el navegador en cada cambio. Alternativa descartada por ahora: Godot (motor más completo, pero iteración más lenta y sin verificación automática de lo que se ve).

**Estructura de carpetas prevista**

```
src/
  core/      bucle de juego (paso fijo), entrada, cámara, RNG con semilla
  physics/   envoltorio de Rapier
  player/    control, estados, objetos
  boxes/     caja base + comportamientos
  worlds/    una carpeta por mundo: layout, paleta, reglas, transición
  enemies/   virus, bacterias, bichos...
  fx/        shaders, partículas, postprocesado
  ui/        altura, tiempo, menús
docs/
```

## 7. Hitos

El riesgo principal es el alcance (12 mundos). Por eso primero se valida que saltar cajas es divertido en una sola pantalla, y luego se hace un "corte vertical" de los dos primeros mundos antes de planificar el resto en detalle.

| Hito | Contenido | Se da por hecho cuando... |
|---|---|---|
| **M0 — Base** | Proyecto Vite + TS + Three + Rapier, bucle con paso fijo, despliegue en Pages | Hay una URL pública con un cubo que cae sobre otro |
| **M1 — El salto** | Personaje, salto con carga, cajas estáticas en 2D, caída y vuelta al inicio, medidor de altura | Subir 20 cajas grises es divertido y frustrante a partes iguales |
| **M2 — Mundo 0** | Efecto túnel con aviso, colapso, estética cuántica (shaders), sonido básico | El mundo 0 se puede completar y apetece reintentar |
| **M3 — Transición y Quarks** | Paso 2D → 3D, cámara 3D, las tres fuerzas, inversión de carga | Se juega del mundo 0 al 1 sin cortes, y al caer se vuelve al 0 |
| **M4 — Molecular** | Sistema de enemigos, virus y bacterias, enlaces, browniano | Los enemigos tiran al jugador de forma legible y esquivable |
| **M5 — Hierba** | Agua, bichos, gancho de seda | El gancho es difícil pero dominable |
| **M6+** | Un mundo por hito, en orden. Guardado, menú, narración, final | — |

Tras M3 se revisa este plan con lo aprendido.

## 8. Riesgos

| Riesgo | Mitigación |
|---|---|
| Alcance excesivo | Corte vertical M0–M3 antes de comprometer el resto; el mundo 2 es prescindible |
| Plataformas en 3D difíciles de leer | Cámara guiada, sombra del personaje bajo los pies, cajas grandes y con contraste |
| El túnel cuántico se percibe como injusto | Nube de probabilidad visible, colapso por pisar y por mirar |
| Caer hasta el principio con 12 mundos es demasiado castigo | La caída es física y se puede frenar; los objetos se conservan; valorar "salientes" anchos entre mundos |
| Física poco reproducible | Paso fijo, RNG con semilla, tests de comportamientos |
| Rendimiento en navegador | Solo se simulan los mundos cercanos al jugador; el resto se descarga |

## 9. Decisiones pendientes

1. **Control:** salto con carga y sin control aéreo (propuesta) o salto clásico.
2. **Caída:** física y continua con posibilidad de salvarte (propuesta) o reinicio inmediato en la cuerda.
3. **Objetos:** se conservan al caer (propuesta) o se pierden.
4. **Cámara 3D:** guiada en espiral (propuesta) o libre.
5. **Tecnología:** Three.js + Rapier en web (propuesta) u otro motor.
6. **Mundo 2 (Átomo):** incluirlo o fusionarlo con Quarks.
