# IA para el día a día · Gestión de proyectos

Material del taller del **Perú Business Fest 2026** (Martín Velasco · TamiBot).

Una plantilla para que la IA haga el **seguimiento** de tus proyectos: capturar lo que llega,
ordenarlo en un tablero, recordar lo que vence y armar el reporte de la semana. Tú decides.

## Las cuatro piezas

| Pieza | Qué es | Para qué la usas | Costo |
|---|---|---|---|
| **VS Code + Claude Code** | El editor donde trabajas y la IA que lee y escribe tus archivos | Ordenar, actualizar el tablero, crear agentes | Claude Pro, US$ 20/mes |
| **VPS** | Una computadora alquilada en la nube, prendida 24/7 | Que los agentes trabajen aunque cierres tu laptop | Desde US$ 5/mes |
| **n8n** | El reloj y los cables: conecta apps y dispara tareas a una hora | «Todos los días a las 8:00, arma el resumen» | Gratis en tu VPS |
| **WAHA** | Tu WhatsApp conectado al sistema (escaneas un QR, como WhatsApp Web) | Leer grupos y mandar recordatorios | Gratis |

## Empieza en 10 minutos (sin servidor)

1. Instala [VS Code](https://code.visualstudio.com) y la extensión **Claude Code** (de Anthropic).
2. Descarga este repositorio (botón verde **Code → Download ZIP**) y abre la carpeta `proyecto-ejemplo` en VS Code.
3. Abre Claude Code y escribe: *«Lee CLAUDE.md y procesa la bandeja»*.
4. Revisa los cambios que propone en `tablero.md` y acéptalos.

Compara con [`proyecto-ejemplo/resultado-esperado/tablero.md`](proyecto-ejemplo/resultado-esperado/tablero.md).

Luego cambia `CLAUDE.md` por los datos de tu proyecto y usa los prompts de [`prompts.md`](prompts.md).

## La carpeta del proyecto

```
proyecto-ejemplo/
├── CLAUDE.md          la memoria: equipo, reglas y formato
├── tablero.md         todas las tareas: qué, quién, cuándo, estado
├── bandeja/           lo que llega sin ordenar (chats, audios, correos)
├── reuniones/         una acta por reunión
├── reportes/          un reporte por semana
└── .claude/agents/    tus agentes, uno por archivo
```

## Los seis agentes

| Agente | Qué hace | Cuándo |
|---|---|---|
| `actas` | Reunión → tareas con dueño y fecha | Al terminar cada reunión |
| `bandeja` | Ordena lo que llega: tarea, decisión, información o ruido | Cada hora |
| `recordatorios` | Avisa a cada dueño lo que vence mañana | 10:00 |
| `alertas` | Si algo se atrasa, avisa con opciones | Cuando cambia una fecha |
| `reporte` | Borrador del reporte semanal | Viernes 17:00 |
| `resumen` | Qué toca hoy, en 5 líneas | 8:00 |

En Claude Code los llamas con `@nombre` o los creas con `/agents`.

## Que corra solo: el servidor

Cuando ya lo uses todos los días, mira [`servidor/README.md`](servidor/README.md):
un VPS de US$ 5 con n8n (el reloj) y WAHA (WhatsApp). Puedes pedirle a Claude Code
que lo instale contigo.

## Reglas

- **La IA prepara, tú decides.** Lo que sale hacia clientes pasa por tu OK.
- **Si falta un dato, se marca `[POR DEFINIR]`.** No se inventa.
- **WAHA no es la API oficial de Meta.** Usa un número dedicado y nada de envíos masivos.
