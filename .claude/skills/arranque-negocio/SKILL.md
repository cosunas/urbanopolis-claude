---
name: arranque-negocio
description: Arranca una sesión de trabajo sobre un negocio o cliente del holding. Úsala cuando Carlos diga "trabajemos <negocio>", "abramos INDIVI", "vamos con Aceite Imperial", "¿cómo va <negocio>?" o similar.
---

# Arranque de sesión por negocio

1. Identifica la carpeta en `negocios/` (o `negocios/atenea-ia/clientes/`) que corresponde. Si es ambiguo, pregunta con las opciones del mapa del `CLAUDE.md` raíz.
2. Lee, en este orden: su `CLAUDE.md`, `ESTADO.md` y `DECISIONES.md`. Si `ESTADO.md` no existe, créalo con la plantilla de abajo al cerrar la sesión (no antes).
3. Si estás en la nube, consulta Drive con el conector usando los IDs del `CLAUDE.md` raíz. En la Mac, usa las rutas locales.
4. Responde con un brief de máximo 10 líneas:
   - Frentes abiertos (tabla: frente · situación · siguiente paso)
   - Lo que está vencido o en riesgo (fechas)
   - 1 pregunta concreta: "¿en qué frente nos enfocamos hoy?"

No leas, copies ni resumas carpetas con FIEL, CSD, contraseñas o constancias fiscales.

## Plantilla ESTADO.md
```markdown
# Estado <Negocio> — actualizado AAAA-MM-DD

## Frentes abiertos
| Frente | Situación | Siguiente paso |
|---|---|---|

## Pendientes de orden
-
```
