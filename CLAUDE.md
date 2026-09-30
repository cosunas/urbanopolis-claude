# Urbanopolis Realty Group — Hub operativo

Este repo es el **cerebro** del holding: contexto, estado y decisiones de cada negocio.
Los **documentos** (PDF, contratos, Excel) viven en Google Drive; aquí solo se guardan
notas en Markdown y rutas hacia Drive. El **código** vive en repos propios (ver abajo).

## Quién soy y cómo trabajo
- Carlos Osuna Sánchez, CEO & Founder de Urbanopolis Realty Group (Mexicali, B.C.).
- Operador, no desarrollador. Respuestas en español, ejecutivas: resumen primero,
  luego tablas y bullets, y cierre con acciones (impacto, dificultad, siguiente paso).
- Prioridad 80/20. Proponer automatización e IA por defecto.

## Mapa del holding
| Negocio | Carpeta aquí | Qué es |
|---|---|---|
| Casas Kali | `negocios/casas-kali/` | Correduría inmobiliaria. Incluye el programa INDIVI |
| Sevilla Mía Marina | `negocios/sevilla-mia/` | Desarrollo en comercialización |
| RE/MAX Procapital | `negocios/remax-procapital/` | Franquicia |
| DomoHome | `negocios/domohome/` | Domótica y energía inteligente |
| ATENEA IA | `negocios/atenea-ia/` | Consultoría IA (factura IARE ASESORES). Clientes en `clientes/` |
| Holding (legal, contable) | `holding/` | Entidades, contabilidad, proveedores |

## Dónde están los documentos
Raíz de Drive (personal) en la Mac:
`/Users/carlososunasanchez/Library/CloudStorage/GoogleDrive-carlos.osuna.mx@gmail.com/Mi unidad/`
- Cada `CLAUDE.md` de negocio lista sus rutas exactas en Drive.
- Lo de ATENEA IA se migra a las unidades compartidas del Workspace ateneaia.mx
  (`Clientes ATENEA` y `ATENEA Interno`). Lo demás se queda en el Drive personal.

## Repos de código (fuera de este hub)
| Repo | Ruta local | Remoto |
|---|---|---|
| atenea-demos | `~/Proyectos/atenea-demos` | github.com/ATENEA-IA/atenea-demos |
| ateneaia-web | `~/Proyectos/ateneaia-web` | github.com/ATENEA-IA/ateneaia-web |

## Reglas de trabajo
1. **Nunca borrar** documentos en Drive. Lo reemplazado se mueve a `_archivo/AAAA-MM-DD_motivo/`.
2. Nombres de archivo: `AAAA-MM-DD_Tema_vX.ext`. Sin espacios al inicio ni al final.
3. Una sola versión vigente por documento en la carpeta de trabajo; las anteriores van a `01_Versiones/` o `_archivo/`.
4. Entregables nuevos se guardan junto a su fuente en Drive, no en carpetas "Claude outputs" sueltas.
5. **Seguridad:** nunca copiar a este repo contraseñas, FIEL/CSD, constancias fiscales, identificaciones ni estados de cuenta. Solo se referencian por ruta.
6. Al terminar una sesión de trabajo en un negocio, actualizar su `ESTADO.md` y, si hubo decisiones, `DECISIONES.md`.

## Cómo arrancar una sesión
Abrir Claude Code en esta carpeta y decir, por ejemplo: "trabajemos INDIVI".
Claude lee el `CLAUDE.md` de ese negocio y su `ESTADO.md` antes de actuar.

## Estructura
- `negocios/<negocio>/CLAUDE.md` contexto fijo · `ESTADO.md` situación actual · `DECISIONES.md` bitácora
- `.claude/skills/` skills propias del holding
- `rutinas/` prompts de tareas recurrentes (reportes semanales, seguimientos)
- `_inbox/` notas rápidas por clasificar

## Otras carpetas de Drive
- `Personal/` — asuntos personales y familiares. Fuera del alcance del hub.
- `_archivo/` — carpetas vacías o retiradas, con `LOG_movimientos.md` de cada reorganización.
- `Grupo Berumen HUYNDAI BUSES/`, `Director Comercial Stelarhe/`, `Terrazas del Valle/` — proyectos por asignar a un negocio.
