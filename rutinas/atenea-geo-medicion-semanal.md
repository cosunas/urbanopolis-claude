# Rutina: Medición semanal GEO — ATENEA IA

Corre cada lunes 7:00 am (Mexicali). Alimenta el tablero **ATENEA GEO Tracker**:
https://claude.ai/artifact/GSyxzJ7vx5wEuYDgicHKdU

## Pasos
1. Leer las preguntas activas del tablero: `ArtifactData` → `list`, collection `prompts` (campos: mercado, ciudad, q, activo). Usar solo `activo: true`.
2. Correr cada pregunta en 4 motores con DataForSEO (`mcp__DataForSEO__api_request`, POST, una tarea por llamada, hasta ~10 en paralelo). Enviar `q` tal cual como `user_prompt`; `tag` = id de la pregunta.
   | engine | path | model_name | geolocalización |
   |---|---|---|---|
   | chatgpt | /v3/ai_optimization/chat_gpt/llm_responses/live | gpt-5.5 | web_search true, web_search_country_iso_code "MX", web_search_city = ciudad |
   | gemini | /v3/ai_optimization/gemini/llm_responses/live | gemini-3.5-flash | web_search true + la geolocalización que acepte el endpoint (MX) |
   | perplexity | /v3/ai_optimization/perplexity/llm_responses/live | sonar-pro | web_search_country_iso_code "MX" (sin ciudad) |
   | claude | /v3/ai_optimization/claude/llm_responses/live | claude-sonnet-5 | web_search true + la geolocalización que acepte el endpoint (MX) |
   `max_output_tokens` 2048. Si una llamada falla, reintentar una vez; si vuelve a fallar, registrar `error`.
3. Por respuesta extraer: `appears` (texto menciona "ATENEA" o alguna cita apunta a ateneaia.mx), `position` (lugar de ATENEA entre las marcas recomendadas, por orden de primera mención; null si no aparece), `brands` (lista ordenada de empresas recomendadas, máx. 12, sin herramientas genéricas), `atenea_urls` (URLs de ateneaia.mx citadas, sin parámetros), `n_citations`, `cost`.
4. Google AI Overview: POST /v3/ai_optimization/llm_mentions/search/live con `target:[{"domain":"ateneaia.mx","include_subdomains":true}]`, `location_name:"Mexico"`, `language_code:"es"`, `platform:"google"` → `aio_mentions` = total_count.
5. Guardar UNA corrida: `ArtifactData` → `set`, collection `runs`, doc_id `AAAA-MM-DD` (fecha de hoy), data:
   `{date, label:"Semanal", engines:{chatgpt:"gpt-5.5",...}, results:[{id,engine,model,appears,position,brands,atenea_urls,n_citations,cost,error}], aio_mentions, cost_usd (suma de costos conocidos o null), notes}`.
   Nunca sobrescribir corridas anteriores.
6. Agregar a `bitacora` un documento nuevo (doc_id `r-AAAA-MM-DD`): `{fecha, texto:"Medición semanal: PyME X%, Industria Y%, AIO Z. Cambios: ...", ts}` con los cambios relevantes vs. la corrida anterior (preguntas que entraron o salieron).
7. Si la visibilidad de un mercado cae más de 10 puntos o ATENEA sale de una pregunta donde estaba en top 3, decirlo al inicio del resumen final.

## Reglas
- No modificar `prompts` ni `acciones` (los gestiona Carlos desde el tablero).
- No publicar ni cambiar la página del tablero; solo escribir en `runs` y `bitacora`.
