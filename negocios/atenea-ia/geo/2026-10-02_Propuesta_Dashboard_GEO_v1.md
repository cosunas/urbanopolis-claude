# Propuesta — Sistema de seguimiento GEO de ATENEA IA (borrador para luz verde)

Objetivo: operar el Plan GEO de dos mercados con acciones, mediciones e histórico en un
solo tablero. Ese mismo sistema se convierte en el producto que se vende a clientes.

## Arquitectura (4 capas)
| Capa | Qué hace | Cómo |
|---|---|---|
| 1. Banco de preguntas | Unas 20 preguntas objetivo, etiquetadas por mercado (PyME/Industria), ciudad e intención | Tabla `prompts` |
| 2. Medición automática | Corre cada pregunta en ChatGPT, Gemini, Perplexity y Google AI Overview; detecta si aparece ATENEA, en qué posición, qué página cita y qué competidores salen | Rutina semanal (lunes 7 am) → DataForSEO → tabla `snapshots` |
| 3. Plan de acción | Acciones del plan con responsable, fecha, estado, impacto, dificultad y la pregunta que se busca mover | Tabla `acciones` (editable en el tablero) |
| 4. Tablero | KPIs, tendencia semanal, matriz pregunta × motor, share of voice contra competidores, avance de acciones, bitácora | Página web con base de datos compartida |

## KPIs
| KPI | Definición | Meta a 90 días |
|---|---|---|
| Visibility Score | % de pares pregunta × motor donde aparece ATENEA | PyME ≥70% · Industria ≥25% |
| Posición promedio | Lugar en la lista recomendada | Top 3 PyME · Top 5 Industria |
| Share of voice | Menciones de ATENEA / menciones totales de marcas | +10 pts |
| Citas propias | Páginas de ateneaia.mx citadas como fuente | ≥6 URLs distintas |
| Google AI Overview | Menciones en México | 0 → ≥3 |
| Negocio | Diagnósticos agendados por mercado (captura manual) | 5 industriales |
| Ejecución | % de acciones completadas a tiempo | ≥80% |

## Histórico
- Cada corrida guarda un snapshot con fecha, sin sobrescribir el anterior → curva por pregunta y por motor.
- Bitácora: cada acción completada queda marcada en la gráfica para ver la causa y el efecto ("se publicó la landing industrial → Q4 entra al #4").

## Costo operativo estimado (por validar con la primera corrida)
- 20 preguntas × 4 motores × 4 semanas ≈ 320 llamadas al mes. Se estima en decenas de USD al mes en DataForSEO; el costo exacto sale del campo `cost` de cada respuesta.

## Oportunidad de producto
"ATENEA GEO Tracker": diagnóstico inicial + tablero mensual por cliente (clínicas, inmobiliarias, Sevilla Mía, Casas Kali).
Mismo motor, banco de preguntas por cliente. Encaja como upsell recurrente de las Suites.

## Decisiones para mañana
1. Dónde vive el tablero: (a) página privada en claude.ai con base de datos compartida (más rápido), (b) subdominio `geo.ateneaia.mx` en Vercel (vendible a clientes), (c) Google Sheets + Looker.
2. Frecuencia: semanal (recomendada) o mensual.
3. Motores: ChatGPT + Google AI Overview como base; ¿sumar Gemini, Perplexity y Claude?
4. Banco de preguntas: validar las 20 preguntas (borrador mañana).
5. Responsables de las acciones: Carlos solo o equipo.

## Recomendación
Arrancar con (a) para operar desde la semana 1 y migrar a (b) cuando se venda al primer cliente.
Frecuencia semanal, 4 motores, 20 preguntas.
