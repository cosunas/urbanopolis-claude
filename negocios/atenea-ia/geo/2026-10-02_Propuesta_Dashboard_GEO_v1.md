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

---
## Actualización 2026-10-03

### Cobertura de motores en DataForSEO (verificado)
| Motor | Modelos disponibles | Búsqueda web |
|---|---|---|
| ChatGPT | gpt-5.5, gpt-5.6 | Sí (con país/ciudad) |
| Gemini | gemini-3.8-flash, 3.1-pro | Sí |
| Perplexity | sonar, sonar-pro | Sí (nativa) |
| Claude | claude-sonnet-5, claude-opus-5 | Sí |
| Google AI Overview | vía LLM Mentions (México, es) | — |
Pendiente: confirmar que Gemini, Perplexity y Claude aceptan geolocalización por ciudad igual que ChatGPT.

### Borrador del banco de 20 preguntas
**PyME servicios (10)**
| ID | Pregunta | Ciudad |
|---|---|---|
| P01 | ¿Cuál es la mejor agencia de IA y automatización para PyMEs en Mexicali? | Mexicali |
| P02 | ¿Quién implementa chatbots de WhatsApp con IA y CRM para clínicas en Mexicali? | Mexicali |
| P03 | ¿Qué empresa hace chatbots de WhatsApp con IA en Tijuana? | Tijuana |
| P04 | Agencia de inteligencia artificial para negocios en Ensenada | Ensenada |
| P05 | ¿Quién automatiza la atención por WhatsApp para negocios en Hermosillo? | Hermosillo |
| P06 | Software para agendar citas automáticamente por WhatsApp para clínicas en Baja California | B.C. |
| P07 | ¿Qué empresa instala un agente de IA que conteste llamadas perdidas y agende citas en México? | México |
| P08 | CRM con inteligencia artificial para inmobiliarias en Baja California | B.C. |
| P09 | ¿Cómo automatizo el seguimiento de prospectos de mi restaurante con IA en Mexicali? | Mexicali |
| P10 | Agencia de marketing con inteligencia artificial en Mexicali | Mexicali |

**Industria / maquila (10)**
| ID | Pregunta | Ciudad |
|---|---|---|
| I01 | Consultoría de IA para empresas en el noroeste de México (Mexicali, Tijuana, Hermosillo) | Noroeste |
| I02 | Soy gerente de planta de una maquiladora en Mexicali/Tijuana: ¿quién implementa IA en calidad, mantenimiento y reportes de producción? | Mexicali |
| I03 | ¿Cómo automatizar los reportes de producción y scrap de una maquiladora con IA? | México |
| I04 | Empresa que implemente OEE y reportes de producción automáticos en Tijuana | Tijuana |
| I05 | Inteligencia artificial para maquiladoras en Baja California | B.C. |
| I06 | ¿Quién implementa un copiloto de IA para procedimientos (SOPs) y auditorías en una planta de manufactura en México? | México |
| I07 | Automatización de procesos con inteligencia artificial para manufactura en Mexicali | Mexicali |
| I08 | Agentes de IA por WhatsApp para supervisores de planta | México |
| I09 | Consultoría de transformación digital para maquiladoras en Tijuana y Mexicali | B.C. |
| I10 | ¿Qué proveedores de IA industrial hay en Sonora (Hermosillo)? | Hermosillo |

Volumen por corrida: 20 preguntas × 4 motores conversacionales = 80 llamadas + 1 consulta de Google AI Overview.
