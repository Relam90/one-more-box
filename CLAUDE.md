# One More Box

Juego "rage" de escalada: solo subes cajas, desde una cuerda cuántica hasta el espacio. Cada escala añade leyes físicas nuevas a las anteriores. Si caes, vuelves al principio.

Diseño completo en `docs/PLAN.md`. **No lo leas entero salvo que haga falta**: lee solo la sección del mundo o sistema en el que trabajes.

## Trabajo con el usuario

- Responder en español. Código, nombres y commits en inglés.
- Repo: `github.com/Relam90/one-more-box`. `gh` no está instalado; usar `git` (credenciales ya guardadas).
- Trabajar en ramas; commit y push solo cuando el usuario lo pida.
- Shell: Windows PowerShell 5.1 (sin `&&`).

## Estado

- Hecho: repo, `docs/PLAN.md` (borrador v1, rama `docs/game-plan`).
- Sin código todavía. Siguiente: confirmar decisiones pendientes, luego M0.

## Decisiones (propuestas, sin confirmar por el usuario)

1. Control: salto con carga (mantener/soltar), casi sin control aéreo.
2. Caída: física y continua a través de los mundos; puedes salvarte aterrizando. Sin checkpoints.
3. Sin barra de vida: los enemigos empujan o se pegan; morir es caer.
4. Los objetos se conservan al caer.
5. Cámara 3D guiada en espiral alrededor de la columna de cajas.
6. Stack: TypeScript + Vite + Three.js + Rapier (WASM) + Vitest; deploy en GitHub Pages con Actions.
7. Mundo 2 (Átomo) es opcional; se puede fusionar con Quarks.

Al confirmarse o cambiar alguna, actualizar esta lista y `docs/PLAN.md` §9.

## Mundos (resumen)

| # | Mundo | Cajas | Peligros | Objeto |
|---|---|---|---|---|
| 0 | Cuerda cuántica, 2D, negro con trazo blanco | Túnel cuántico; fijas al pisarlas (colapso) | — | — |
| 1 | Quarks, transición 2D→3D | + fuerza fuerte (tríos con goma), débil (desintegración), EM (cargas) | Antimateria | Invertir carga |
| 2 | Átomo (opcional) | Capas de energía, salto exacto | Fotones | — |
| 3 | Molecular/célula | Enlaces-muelle, browniano; lo cuántico se apaga | Virus, bacterias | — |
| 4 | Hierba | Agua: resbalar, tensión superficial | Hormigas, arañas, viento | Gancho de seda |
| 5 | Jardín y casa | Cartón: se aplasta, se moja | Gato, aspiradora | Ventosas |
| 6 | Ciudad | Contenedores, grúas | Lluvia, rayos, palomas | Gancho mejorado |
| 7 | Montaña y cielo | Hielo, globos | Viento, aves | Planeador |
| 8 | Órbita | Microgravedad, inercia | Basura espacial | Propulsor |
| 9 | Sistema solar | Pozos de gravedad, tirachinas | Viento solar, asteroides | Ancla gravitatoria |
| 10 | Interestelar | Dilatación temporal, lente gravitatoria | Agujeros negros | — |
| 11 | Red cósmica | Todo mezclado; expansión | — | — |

Final: el universo estaba dentro de una caja sobre otra cuerda.

## Reglas de diseño que el código debe respetar

- **Aviso previo obligatorio**: todo lo que mueva o quite una caja se anuncia antes (visual y sonido). P. ej. el túnel muestra fantasmas en los destinos posibles.
- **Cajas = base física + comportamientos combinables** (`Tunneling`, `Collapsible`, `Charged`, `Bonded`, `Decaying`, `Slippery`, `Crushable`, `Orbiting`...). Un mundo nuevo es una mezcla nueva.
- **Niveles a mano, azar con semilla** (RNG propio, nunca `Math.random()` en lógica de juego).
- **Paso de física fijo**, separado del render.
- **Escala**: el personaje no crece en unidades del motor; se re-escala el mundo en cada transición.
- Mundo vertical continuo, sin pantallas de carga; solo se simulan los mundos cercanos al jugador.

## Estructura prevista

```
src/core      bucle, entrada, cámara, RNG
src/physics   envoltorio de Rapier
src/player    control, estados, objetos
src/boxes     caja base + comportamientos
src/worlds    una carpeta por mundo
src/enemies  src/fx  src/ui
```

## Hitos

- **M0** Base: Vite+TS+Three+Rapier, bucle, deploy. Hecho cuando hay URL pública con un cubo cayendo sobre otro.
- **M1** El salto: personaje, salto, cajas grises 2D, caída, medidor de altura. Hecho cuando subir 20 cajas es divertido.
- **M2** Mundo 0: túnel con aviso, colapso, estética cuántica, sonido básico.
- **M3** Transición 2D→3D y Quarks. Después, revisar el plan.
- **M4** Molecular (sistema de enemigos). **M5** Hierba (agua, gancho). **M6+** un mundo por hito.

Mantener "Estado" y "Decisiones" al día al cerrar cada hito.
