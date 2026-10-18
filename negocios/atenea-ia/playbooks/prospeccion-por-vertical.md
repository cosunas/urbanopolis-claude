# Prospección por vertical (motor comercial de ATENEA → servicio a clientes)

**Qué es:** el sistema con el que ATENEA convierte "vertical + plaza" en prospectos calificados,
con su dolor, el canal correcto y el mensaje listo; después les da seguimiento hasta la cita.
**Skill:** `atenea-prospector` (repo `ATENEA-IA/atenea-skills`). Solo lo opera Carlos.
**Revisado:** 2026-10-18.

## Modos del prospector
| Modo | Volumen | Cuándo | Salida |
|---|---|---|---|
| Precisión | 10–20 empresas | Vertical nueva, cuentas grandes | CSV con score, dolores y mensaje |
| Volumen | 200–2,000+ | Barrer una plaza completa por código postal | CSV de volumen + top 10–20 % a profundidad |
| Social | 20–500 | Negocios que viven en Facebook/Instagram y no en su web o GBP | Workbook con score de madurez digital 0–100 y segmento |

Clínicas: en cualquier modo corre el detector de software de agenda (AgendaPro, Fresha, Doctoralia…) y asigna el pitch de Clinic Suite.

## Cadena y stack por fase
| Fase | Qué hace | Herramienta principal | Respaldo |
|---|---|---|---|
| 0. Intake | Vertical, plaza, oferta, modo | Claude | — |
| 1. Filtro de vertical | ¿Invierte en digital, ticket suficiente, proceso automatizable? | Claude | — |
| 2. Descubrir | Negocios de la plaza | **Apify** (Google Maps, Facebook, Instagram) | Nimble (`local-places`) |
| 2B. Enriquecer | Tamaño real y tomador de decisión | **Vibe Prospecting** (solo con dominio propio) | — |
| 3. Diagnosticar | Dolor en reseñas, web, redes, anuncios | **ATENEA Web Intel** (DeepSeek → Nimble) + Meta Ad Library | Firecrawl |
| 3B–3E. Señales extra | Sitio viejo (Sitio Espejo), ranking Maps/orgánico, software de clínicas | DataForSEO, Local Falcon (opcional), detector propio | — |
| 4. Mensaje | Outreach por empresa y canal | Claude | — |
| 5. Entregable | Tabla + CSV / workbook | Scripts del skill | — |
| 6. Diagnóstico | El demo que se manda: lo único que sale antes de la cita y su meta es abrirla | **Demo Factory** (`diagnostico.ateneaia.mx`), logo del prospecto con Firecrawl | — |
| 7. Seguimiento | Toques hasta agendar la cita | **Pipeline** (en construcción con Manuel, oct-2026) | — |
| 8. Cita | Presentación de cita con la marca y colores del prospecto | `atenea-cita` (`/cita/<token>/`) | — |
| 9. Presentación final / propuesta | Solo después de la cita | `atenea-propuesta-alto-calibre`, `biz-proposal-pro` | — |

**Regla:** no se arma la presentación final sin cita. Antes de la cita solo se manda el diagnóstico.

Costo de referencia: piloto Social de lotes de autos seminuevos en Mexicali, 31 negocios por $0.31 USD.

## Dónde entra Firecrawl
- **Logo del prospecto en el diagnóstico:** botón *Logo del prospecto (Firecrawl)* en `atenea-demos` (PR #189): toma el logo del sitio propio y deja un PR para revisarlo.
- **Colores en la presentación de la cita:** `armar-cita.mjs` ya los saca del logo y, sin logo, de Firecrawl.
- **Radar competitivo**: el mismo prospecto puede recibir como gancho un brief de su competencia (ver `radar-competitivo.md`).

## Seguimiento
Manuel está juntando el pipeline (oct-2026). Hasta entonces, el prospector termina en un CSV y el panel de Demo Factory registra aperturas del diagnóstico.

Referencia de diseño (para cuando se integre):
- **Tablero de pipeline** como página con base de datos (igual que la Mesa de aprobación de contenido): una fila por prospecto, que Claude puede leer y actualizar.
- Columnas: empresa · vertical · plaza · score · canal · etapa · último contacto · siguiente toque · resultado · notas.
- Etapas: nuevo → contactado → respondió → cita → propuesta → ganado / perdido.
- Cadencia: día 0 (llamada o WhatsApp), día 3, día 7, día 14; después pasa a "frío" y vuelve al siguiente lote.
- Rutina semanal (`rutinas/atenea-prospeccion-seguimiento-semanal.md`) que lista los toques vencidos.

## Reglas de envío
- Email frío nunca desde ateneaia.mx: dominio secundario, correos verificados y rebote < 1 %.
- WhatsApp: sin envíos masivos en frío desde el número de Bird de ATENEA.
- Datos personales: validar con `legal-mx-pro` (LFPDPPP) antes de escalar; siempre una forma de darse de baja.
- Una vertical, una plaza y una oferta por campaña.

## Métricas del embudo (por campaña)
Prospectos barridos → calificados (score) → contactados → respuestas → citas → propuestas → cierres.
Costo por prospecto calificado y costo por cita.

## Cómo se vende a clientes
- **Diagnóstico de presencia digital** (producto derivado del modo Social): gancho de entrada.
- **Prospección como servicio** para clientes B2B (lista calificada + mensajes + seguimiento), con precio a definir con `atenea-pricing-suites`.
