---
name: cierre-sesion
description: Cierra una sesión de trabajo de un negocio actualizando ESTADO.md y DECISIONES.md y dejando el cambio en git. Úsala cuando Carlos diga "cerramos", "ya quedó", "actualiza el estado", "guarda avances" o al terminar una sesión con avances reales.
---

# Cierre de sesión

1. Actualiza `negocios/<negocio>/ESTADO.md`:
   - Fecha de actualización = hoy.
   - Cada frente: situación real y siguiente paso con responsable y fecha si se conocen.
   - Quita frentes cerrados (pásalos a DECISIONES si hubo decisión).
2. Si hubo decisiones, agrega filas a `DECISIONES.md` (fecha · decisión · quién). Nunca reescribas filas anteriores.
3. Revisa que no se haya copiado nada sensible (RFC, contraseñas, FIEL/CSD, cuentas bancarias, identificaciones). Solo rutas.
4. Git:
   - En la Mac: commit en `main` con mensaje `<Negocio>: <resumen corto>` y `git push`.
   - En la nube: commit y push en la rama `claude/...` de la sesión; avisa a Carlos que queda pendiente pasarlo a `main`.
5. Responde con 3 líneas: qué cambió, qué quedó pendiente, próxima fecha crítica.
