# Hermes Best Skills

Una curaduría de las mejores **skills** para [Hermes Agent](https://hermes-agent.nousresearch.com) — el asistente AI autónomo.

Este repo te ayuda a arrancar rápido: cada skill resuelve un problema real, y todas están probadas.

---

## Tabla de Contenidos

- [¿Qué es una skill?](#qué-es-una-skill)
- [Cómo instalar una skill](#cómo-instalar-una-skill)
- [Skills por categoría](#skills-por-categoría)
  - [Coding & Software Development](#coding--software-development)
  - [Autonomous AI Agents](#autonomous-ai-agents)
  - [Creative & Design](#creative--design)
  - [DevOps & Automation](#devops--automation)
  - [Email & Communication](#email--communication)
  - [GitHub & Open Source](#github--open-source)
  - [MLOps & AI/ML](#mlops--aiml)
  - [Productivity](#productivity)
  - [Research & Data](#research--data)
  - [Social Media](#social-media)
  - [Red Teaming](#red-teaming)
- [Skills esenciales para empezar](#skills-esenciales-para-empezar)
- [Cómo crear tu propia skill](#cómo-crear-tu-propia-skill)
- [Contribuir](#contribuir)

---

## ¿Qué es una skill?

Una **skill** en Hermes es un documento markdown (SKILL.md) que le enseña al agente cómo hacer algo específico. Piensa en ello como un "plug-and-play" para capacidades:

- Le decís a Hermes _"cargá la skill `plan`"_ y automáticamente sabe estructurar planes de acción.
- Le decís _"cargá `test-driven-development`"_ y aplica TDD sin que le expliques el ciclo RED-GREEN-REFACTOR.

Skills viven en `~/.hermes/skills/` y se cargan con `skill_view("nombre-de-la-skill")`.

---

## Cómo instalar una skill

```bash
# 1. Clonar este repo
git clone https://github.com/josezuma/hermes-best-skills.git
cd hermes-best-skills

# 2. Copiar las skills que quieras a tu perfil de Hermes
cp skills/plan/SKILL.md ~/.hermes/skills/plan/

# 3. O instalar desde el skill store integrado de Hermes
#    (si la skill está publicada)
hermes skills install plan
```

Para cargar una skill en una sesión:

```python
skill_view("plan")                    # ver contenido
skill_view("plan", file_path="references/api.md")  # ver archivo auxiliar
```

---

## Skills por categoría

### Coding & Software Development

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [test-driven-development](skills/tdd) | Ciclo RED-GREEN-REFACTOR forzado. Escribe tests antes del código. | Elimina falsos positivos. El agente no puede declarar "funciona" sin tests verdes. |
| [plan](skills/plan) | Escribe planes accionables en markdown. Tasks pequeñas, paths exactos, código completo. | Evita que el agente codee sin dirección. Úsala ANTES de escribir código. |
| [systematic-debugging](skills/systematic-debugging) | Debug de 4 fases: reproducir, aislar, entender, fix. | El agente no adivina. Sigue un proceso forense real. |
| [spike](skills/spike) | Experimentos descartables para validar una idea antes de construir. | Ahorra horas construyendo la dirección equivocada. |
| [requesting-code-review](skills/requesting-code-review) | Pre-commit review automático: security scan, quality gates, auto-fix. | Atrapa bugs, secretos, y code smells antes del push. |
| [simplify-code](skills/simplify-code) | 3 agentes en paralelo limpian código reciente. | Refactoring sin riesgo. Cada agente revisa el trabajo de los otros. |
| [node-inspect-debugger](skills/node-inspect-debugger) | Debug Node.js via `--inspect` + Chrome DevTools Protocol. | Cuando el stack trace no alcanza — inspeccionás variables en vivo. |
| [python-debugpy](skills/python-debugpy) | Debug Python con pdb REPL + debugpy remoto (DAP). | Lo mismo pero para Python. Breakpoints remotos. |
| [codebase-inspection](skills/codebase-inspection) | Escanea codebases con pygount: LOC, lenguajes, proporciones. | Saber cuánto realmente hay antes de prometer fechas. |
| [hermes-agent-skill-authoring](skills/hermes-agent-skill-authoring) | Autoría de SKILL.md: frontmatter, validador, estructura, principios de calidad. | Para escribir tus PROPIAS skills bien desde el vamos. |

### Autonomous AI Agents

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [claude-code](skills/claude-code) | Delega coding a Claude Code CLI (features, PRs). | Cuando necesitás un segundo agente codeando en paralelo. |
| [codex](skills/codex) | Delega coding a OpenAI Codex CLI (features, PRs). | Lo mismo con Codex de OpenAI. |
| [opencode](skills/opencode) | Delega coding a OpenCode CLI (features, PR review). | Alternativa open-source para delegar. |
| [hermes-agent](skills/hermes-agent) | Configurar, extender, o contribuir a Hermes Agent. | La skill sobre Hermes mismo — configuración, CLI, plugins, providers. |
| [kanban-orchestrator](skills/kanban-orchestrator) | Descomposición de tareas + reglas anti-tentación para el rol de orquestador. | Orquestar trabajo sin hacerlo vos mismo. |
| [kanban-worker](skills/kanban-worker) | Pitfalls, ejemplos, edge cases para workers Kanban. | Cuando ejecutás tareas dentro de un flujo Kanban. |

### Creative & Design

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [sketch](skills/sketch) | Mockups HTML descartables: 2-3 variantes de diseño para comparar. | Validar diseño visual en 5 minutos, no 2 horas. |
| [claude-design](skills/claude-design) | Diseñar artifacts HTML únicos (landing, deck, prototype). | Una sola página con diseño premium, sin framework. |
| [architecture-diagram](skills/architecture-diagram) | Diagramas SVG dark-mode de arquitectura/infra como HTML. | Documentación técnica que se ve bien en docs. |
| [excalidraw](skills/excalidraw) | Diagramas hand-drawn en JSON (arquitectura, flujo, secuencia). | Para compartir en PRs o docs informales. |
| [popular-web-designs](skills/popular-web-designs) | 54 sistemas de diseño reales (Stripe, Linear, Vercel) como HTML/CSS. | Inspiración directa de los mejores. |
| [p5js](skills/p5js) | Sketches p5.js: gen art, shaders, interactive, 3D. | Visualizaciones creativas y demos interactivas. |
| [ascii-art](skills/ascii-art) | Arte ASCII: pyfiglet, cowsay, boxes, image-to-ascii. | Banners, headers para CLI, decoración en terminal. |
| [ascii-video](skills/ascii-video) | Video/audio a ASCII animado en colores (MP4/GIF). | Demos retro en terminal. |
| [manim-video](skills/manim-video) | Animaciones Manim CE: videos estilo 3Blue1Brown. | Explicaciones matemáticas/algorítmicas de alto impacto. |
| [comfyui](skills/comfyui) | Generar imágenes, video, audio con ComfyUI. | Pipelines visuales de Stable Diffusion, controlnet, etc. |
| [touchdesigner-mcp](skills/touchdesigner-mcp) | Controlar TouchDesigner via MCP — 36 herramientas nativas. | Visuales en tiempo real desde el agente. |
| [songwriting-and-ai-music](skills/songwriting-and-ai-music) | Composición musical + prompts para Suno AI. | Generar canciones desde letra + tags. |
| [heartmula](skills/heartmula) | HeartMuLa: generación de canciones estilo Suno. | Alternativa a Suno desde CLI. |
| [pretext](skills/pretext) | Layout de texto sin DOM para ASCII art, typography games, gen art. | Demos creativas con @chenglou/pretext. |

### DevOps & Automation

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [watchers](skills/watchers) | Polling de RSS, JSON APIs, y GitHub con watermark dedup. | Monitorear cambios sin infraestructura externa. |
| [kanban-orchestrator](skills/kanban-orchestrator) | Descomposición de tareas con workflow Kanban. | Gestión de proyecto dentro del agente. |
| [kanban-worker](skills/kanban-worker) | Ejecución de tareas Kanban con pitfalls documentados. | Para workers que ejecutan tareas asignadas. |

### Email & Communication

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [agentmail](skills/agentmail) | Dale al agente su propia bandeja de entrada email (agent@agentmail.to). | El agente puede recibir y responder emails autónomamente. |
| [himalaya](skills/himalaya) | Cliente IMAP/SMTP desde terminal. | Para cuentas de email tradicionales (Gmail, Migadu, etc.). |
| [one-three-one-rule](skills/one-three-one-rule) | Framework de decisión estructurado: 1 problema → 3 opciones → 1 recomendación. | Cuando hay que elegir entre caminos técnicos. |

### GitHub & Open Source

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [github-auth](skills/github-auth) | Setup de auth: HTTPS tokens, SSH keys, gh CLI login. | Lo primero que necesitás para cualquier operación GitHub. |
| [github-pr-workflow](skills/github-pr-workflow) | Ciclo de vida completo: branch, commit, open PR, CI, merge. | Sin esta skill el agente no sabe el orden correcto. |
| [github-code-review](skills/github-code-review) | Review PRs: diffs, inline comments via gh o REST API. | Para revisar código sin salir de la terminal. |
| [github-issues](skills/github-issues) | Crear, triage, etiquetar, asignar issues. | Gestión de issues desde el agente. |
| [github-repo-management](skills/github-repo-management) | Clonar, crear, fork repos; manage remotes, releases. | Operaciones de repo que no son PRs ni issues. |

### MLOps & AI/ML

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [llama-cpp](skills/llama-cpp) | Inferencia local GGUF + descubrimiento de modelos en HF Hub. | Correr LLMs localmente sin GPU. |
| [serving-llms-vllm](skills/serving-llms-vllm) | Serving de LLMs con vLLM: alta throughput, API OpenAI, cuantización. | Para producción: sirve modelos con API compatible con OpenAI. |
| [huggingface-hub](skills/huggingface-hub) | CLI de HuggingFace: buscar, descargar, subir modelos y datasets. | Acceso al ecosistema HF completo. |
| [evaluating-llms-harness](skills/evaluating-llms-harness) | Benchmarking con lm-eval-harness (MMLU, GSM8K, etc.). | Medir performance real de modelos. |
| [weights-and-biases](skills/weights-and-biases) | Logging de experimentos, sweeps, model registry, dashboards. | Seguimiento de experimentos de ML. |
| [obliteratus](skills/obliteratus) | Abliteración de LLMs: remover refusal patterns (diff-in-means). | Para fine-tuning de modelos sin restricciones artificiales. |
| [audiocraft-audio-generation](skills/audiocraft-audio-generation) | MusicGen text-to-music, AudioGen text-to-sound. | Generación de audio desde texto. |
| [segment-anything-model](skills/segment-anything-model) | SAM: segmentación de imágenes zero-shot por puntos, boxes, masks. | Segmentación de imágenes sin entrenamiento. |

### Productivity

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [obsidian](skills/obsidian) | Leer, buscar, crear, editar notas en el vault de Obsidian. | El agente puede leer/escribir tu base de conocimiento personal. |
| [notion](skills/notion) | API de Notion + CLI ntn: pages, databases, markdown, Workers. | Integración directa con Notion. |
| [airtable](skills/airtable) | API REST de Airtable via curl: CRUD, filters, upserts. | Gestionar bases de datos visuales desde el agente. |
| [google-workspace](skills/google-workspace) | Gmail, Calendar, Drive, Docs, Sheets via CLI. | Acceso completo a Google Workspace. |
| [powerpoint](skills/powerpoint) | Crear, leer, editar presentaciones .pptx. | Generar decks automáticamente. |
| [nano-pdf](skills/nano-pdf) | Editar texto/typos/títulos en PDFs via CLI (lenguaje natural). | Correcciones rápidas en PDFs sin herramientas pesadas. |
| [ocr-and-documents](skills/ocr-and-documents) | Extraer texto de PDFs/scans con pymupdf, marker-pdf. | Digitalizar documentos escaneados. |
| [maps](skills/maps) | Geocoding, POIs, rutas, timezones via OpenStreetMap/OSRM. | Información geográfica sin API key. |
| [petdex](skills/petdex) | Instalar y seleccionar mascotas animadas para Hermes. | Personalización visual del agente. |
| [teams-meeting-pipeline](skills/teams-meeting-pipeline) | Pipeline de resúmenes de reuniones de Teams via CLI. | Resumir reuniones automáticamente. |

### Research & Data

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [arxiv](skills/arxiv) | Buscar papers por keyword, autor, categoría, o ID. | Acceso directo a literatura académica. |
| [blogwatcher](skills/blogwatcher) | Monitorear blogs y feeds RSS/Atom via CLI. | Seguimiento de contenido sin redes sociales. |
| [llm-wiki](skills/llm-wiki) | Base de conocimiento interlinked markdown estilo wiki. | Construir y consultar wikis de conocimiento. |
| [polymarket](skills/polymarket) | Consultar Polymarket: markets, prices, orderbooks, history. | Información de mercados de predicción. |
| [scrapling](skills/scrapling) | Web scraping: HTTP, browser stealth, Cloudflare bypass, crawling. | Extraer datos de sitios web con protección. |
| [research-paper-writing](skills/research-paper-writing) | Escribir papers ML para NeurIPS/ICML/ICLR. | Publicación académica desde el agente. |
| [jupyter-live-kernel](skills/jupyter-live-kernel) | Python interactivo via kernel Jupyter en vivo (hamelnb). | Exploración de datos iterativa. |
| [youtube-content](skills/youtube-content) | Transcripts de YouTube a resúmenes, threads, blogs. | Convertir videos en contenido escrito. |

### Social Media

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [xurl](skills/xurl) | X/Twitter via CLI: post, search, DM, media, API v2. | Gestionar Twitter/X desde terminal. |
| [gif-search](skills/gif-search) | Buscar/descargar GIFs desde Tenor via curl + jq. | Para respuestas visuales rápidas. |

### Red Teaming

| Skill | Qué hace | Por qué usarla |
|-------|----------|----------------|
| [godmode](skills/godmode) | Técnicas de jailbreak: Parseltongue, GODMODE, ULTRAPLINIAN. | Para testing de seguridad de LLMs. |

---

## Skills esenciales para empezar

Si sos nuevo en Hermes, instalá estas 5 primero:

```
# 1. Planificar antes de codear
hermes skills install plan

# 2. No codear sin tests
hermes skills install test-driven-development

# 3. Debuggear sistemáticamente
hermes skills install systematic-debugging

# 4. GitHub sin errores de proceso
hermes skills install github-pr-workflow

# 5. Decisiones estructuradas
hermes skills install one-three-one-rule
```

Con estas 5 skills cubrís el 80% de los problemas diarios: planificar, codificar con calidad, debuggear, publicar, y decidir.

---

## Cómo crear tu propia skill

Usá la skill `hermes-agent-skill-authoring` que te guía con:

1. **Frontmatter** obligatorio: `name`, `description`, `category`
2. **Estructura**: trigger conditions, numbered steps, verification
3. **Pitfalls**: errores comunes que ya conocemos
4. **Dual mode**: instrucciones para CLI + para agentes autónomos

```bash
# Crear una skill nueva
skill_manage(action='create', name='mi-skill', content=...) 

# Ver el validador
skill_view('hermes-agent-skill-authoring')
```

Reglas de oro:
- Mínimo 2000 caracteres de contenido útil
- Cada paso debe ser ejecutable, no descriptivo
- Incluir sección de verificación (¿cómo sé que funcionó?)
- Documentar pitfalls para que otros no pierdan tiempo

---

## Contribuir

1. Forkeá el repo
2. Agregá tu skill en `skills/<nombre>/SKILL.md`
3. Actualizá el README con la entry en la tabla correspondiente
4. Abrí un PR

**Criterios de aceptación:**
- SKILL.md con frontmatter válido
- Mínimo 2000 caracteres de contenido
- Trigger conditions claras
- Pasos numbered ejecutables
- Sección de verificación
- Pitfalls documentados si aplican

---

## Licencia

MIT — hacé lo que quieras con esto.

---

_Creado por [José Zuma](https://github.com/josezuma) para la comunidad de Hermes Agent._
