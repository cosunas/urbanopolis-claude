# Radar de Guiones Virales (piloto interno → servicio a clientes)

**Qué es:** cada semana se toman los reels o videos con más vistas de una vertical, se transcriben,
se desarma su estructura (gancho, partes, llamada a la acción, ritmo) y se adaptan como guiones propios
en Motion Studios / Media Content.
**Regla legal:** se analiza la estructura, nunca se vuelve a publicar el video ni se copia el texto tal cual.

## Cadena
| Paso | Herramienta | Salida |
|---|---|---|
| 1. Encontrar | Revisión manual de cuentas de referencia + Firecrawl / Nimble | 10 links por vertical por semana |
| 2. Bajar | Cobalt desde el navegador en cobalt.tools, sin instalar nada (piloto) → yt-dlp en su propio servidor (fase 2). En YouTube se saca el subtítulo directo | Audio o MP4 |
| 3. Transcribir | `audio_transcribe` (conector ATENEA Video/Imagen FAL) | Texto con tiempos |
| 4. Desarmar | Claude | Ficha de guion (plantilla abajo) |
| 5. Adaptar | `atenea-motion-studios` / `atenea-media-content` | 3 guiones propios + tarjeta de producción |
| 6. Revisar | `atenea-editor-qc` | Visto bueno para publicar |
| 7. Medir | Metricool | Retención a 3s, tiempo visto, guardados, compartidos, leads |

## Ficha de guion de referencia
- Fuente (link, cuenta, vistas, fecha) · Vertical · Formato y duración
- Gancho (0–3 s): texto exacto + tipo (pregunta, dato que impacta, contraste, "error común", resultado primero)
- Partes (cada 3–5 s) · Ritmo (cortes por minuto) · Texto en pantalla
- Llamada a la acción · Por qué funciona (1 línea) · Cómo adaptarlo a nuestra marca o la del cliente

## Piloto interno (ATENEA IA primero)
| Fase | Cuenta | Qué se hace |
|---|---|---|
| Semana 0 | ATENEA IA | Sacar de Metricool el promedio de los últimos 60–90 días. Si no hay historial, las 2 primeras semanas se publica normal y eso queda como punto de partida |
| Semanas 1–4 | ATENEA IA | 3 guiones por semana hechos con el Radar |
| Después | Casas Kali | Solo si ATENEA alcanzó la meta |

**Meta para venderlo:** ver `radar-baseline-atenea.md`. Retención a 3 s ≥ 20 %, tiempo visto ≥ 4 s, ≥ 50 % de reels con guardados o compartidos.
Si no se logra, no se vende.

## Cómo se vendería
- **Extra** para clientes que ya tienen manejo de redes: más retención y "contenido que se basa en lo que ya funciona".
- Va dentro del retainer como capa diferenciadora, no como servicio aparte (al inicio).
- El precio se define con `atenea-pricing-suites` cuando el piloto tenga resultados.
- Entregable para el cliente: reporte semanal de 1 página con el top 10 de su vertical + 3 guiones adaptados.
