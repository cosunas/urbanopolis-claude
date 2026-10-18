# Radar competitivo (servicio recurrente a clientes)

**Qué es:** cada lunes, un brief con lo que movió la competencia del cliente (precios, ofertas,
planes y anuncios nuevos) y qué hacer al respecto.
**Skill:** `atenea-radar-competitivo` (repo `ATENEA-IA/atenea-skills`, fusionado el 2026-10-18).
Un archivo por cliente en `clientes/<slug>.yaml`; sirve para cualquier vertical.

## Cadena
| Paso | Herramienta | Salida |
|---|---|---|
| 1. Alta del cliente | Skill, Modo A | `clientes/<slug>.yaml` + línea base |
| 2. Sitios | Firecrawl (`changeTracking`), semanal | Cambios de precio, plan y oferta |
| 3. Anuncios | Meta Ad Library | Anuncios nuevos (7 días) y anunciantes nuevos |
| 4. Reseñas / marketplaces | Apify (opcional) | Rating y precio de mercado |
| 5. Brief | Skill, formato fijo | 1 página con alerta, cambios y 3 acciones |

## Clientes activos
| Cliente | Desde | Cadencia | Costo Firecrawl |
|---|---|---|---|
| Grupo Fortaleza (Asset) | 2026-10-18 | Lunes 7:54 (tarea programada) | ~30 créditos/mes |

## Cómo se vende
- Incluido en cuentas con iguala (como Grupo Fortaleza).
- Suelto: Radar (~$4,000 MXN/mes) y Radar Pro (~$8,000 MXN/mes). Precios hipotéticos, a validar con los primeros 3 clientes.
- Gancho comercial: correr la línea base gratis dentro del diagnóstico y mostrar un hallazgo que el cliente no conocía.
