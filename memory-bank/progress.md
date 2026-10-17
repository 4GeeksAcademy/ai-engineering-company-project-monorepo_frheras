# Progress — TrackFlow

> Basado exclusivamente en la información de `CONTEXT.md` y `README.md`. Fecha: 2026-10-17.

---

## Estado actual del desarrollo

### Organización

Daniel ha creado una unidad interna llamada **TrackFlow Tech** con un mandato claro: construir los sistemas, integraciones y automatizaciones inteligentes que permitan a TrackFlow operar como la empresa logística moderna que necesita ser.

### Estado del repositorio

> El repositorio actualmente proporciona una **estructura base de carpetas y un esqueleto de documentación únicamente**. No incluye aplicaciones ejecutables ni scripts globales.

- `CONTEXT.md` ya contiene el contexto completo de TrackFlow (reemplazando el placeholder original de la plantilla).
- No hay un `AGENTS.md` raíz todavía.
- Existe metadata de paquetes compartidos en `packages/shared/package.json` (`@repo/shared-types`), pero **no hay un workspace runner configurado en la raíz**.

### Lo que ya existe (estructura)

| Carpeta      | Propósito                               | Estado    |
| ------------ | --------------------------------------- | --------- |
| `uis/`       | Interfaces de usuario (frontends)       | Esqueleto |
| `services/`  | API centralizada FastAPI                | Esqueleto |
| `data/`      | Datos, pipelines, evaluación            | Esqueleto |
| `agents/`    | Agentes de IA (+ `_template/`)          | Esqueleto |
| `skills/`    | Capacidades reutilizables para agentes  | Esqueleto (skill `data-analysis` funcional con script pandas y métricas de referencia) |
| `mcps/`      | Servidores MCP (Model Context Protocol) | Esqueleto |
| `workflows/` | Flujos de automatización (n8n)          | Esqueleto |
| `packages/`  | Librerías compartidas                   | Esqueleto (con tipos compartidos reales en `packages/shared/`) |
| `shared/`    | Assets compartidos sueltos              | Esqueleto |
| `docs/`      | Documentación transversal               | Esqueleto |
| `infra/`     | Infraestructura y despliegue            | Esqueleto |
| `scripts/`   | Scripts de ayuda                        | Esqueleto |
| `internal/`  | Herramientas internas de desarrollo     | Esqueleto |

### Problemas actuales de la compañía (sin resolver)

1. **Sin visibilidad de inventario global** — Los dos almacenes no pueden ver el stock del otro.
2. **Pedidos entrantes manuales** — Llegan por email en distintos formatos y se transcriben a mano.
3. **Picking en papel** — Listas impresas, sin digitalización.
4. **Asignación manual de transportistas** — Sin criterio objetivo ni histórico de rendimiento.
5. **Tracking fragmentado** — Cada transportista tiene su propio portal; no hay un endpoint unificado.
6. **Devoluciones revisadas una por una** — Sin criterios automáticos de aprobación.
7. **Inspección subjetiva** — Sin asistencia de IA para clasificar el estado del producto devuelto.
8. **80% de consultas de CX resolubles automáticamente** — Pero todas las responde un humano.
9. **Sin CRM** — Los account managers usan hojas de cálculo personales e hilos de email.
10. **Informes manuales** — El CEO recibe un informe consolidado los lunes con datos de 1–2 días de antigüedad.
11. **Sin telemetría centralizada** — Cuando algo falla, el equipo se entera por WhatsApp.
12. **Despliegue lento** — 1–2 semanas para desplegar una nueva funcionalidad.
13. **Sin base de conocimiento** — Los agentes de CX consultan un documento de Word en Google Drive.

---

## Siguientes pasos

Basados en las necesidades expresadas por cada departamento en `CONTEXT.md`:

### 1. 🚚 Operaciones de Almacén

- [ ] API de inventario unificada (stock en tiempo real para cualquier SKU en ambos almacenes)
- [ ] Pipeline de ingesta de pedidos (parseo automático de emails)
- [ ] Dashboard de operaciones de almacén
- [ ] Alertas de stock bajo (notificaciones a cliente y equipo de compras)

### 2. 📦 Última Milla y Transportistas

- [ ] Motor de selección de transportista (recomendación óptima según destino, peso y urgencia)
- [ ] Endpoint unificado de tracking (agregación desde 8 carriers)
- [ ] Portal de seguimiento público para destinatarios
- [ ] Dashboard de rendimiento de transportistas

### 3. 🔄 Logística Inversa

- [ ] Motor de aprobación automática de devoluciones (reglas configurables por cliente)
- [ ] Flujo automatizado de recogida (aprobación → etiqueta → programación con transportista)
- [ ] Sistema de inspección asistido por IA (fotografía → clasificación del estado)
- [ ] Dashboard de devoluciones con análisis de patrones

### 4. 📞 Experiencia del Cliente (CX)

- [ ] Agente CX de primera línea (resolución automática de tracking y devoluciones)
- [ ] Base de conocimiento semántica indexada para RAG
- [ ] Sistema de tickets unificado
- [ ] Dashboard de CX en tiempo real
- [ ] Análisis de sentimiento (detección de clientes frustrados)
- [ ] Soporte multiidioma (español + inglés, empezando por un idioma base)

### 5. 🤝 Comercial y Clientes

- [ ] CRM con perfiles unificados de cliente
- [ ] Informes PDF automáticos para clientes (generados por agente)
- [ ] Dashboard de salud de cliente (puntuación de riesgo de renovación)
- [ ] Alertas a 90 y 30 días del vencimiento del contrato
- [ ] Agente comercial (sugerencia de servicios y precios para prospectos)

### 6. 💻 Tecnología

- [ ] Telemetría y logging centralizados (ambos países)
- [ ] Pipeline de datos (alimentando todos los dashboards)
- [ ] Monitorización en tiempo real con alertas automáticas
- [ ] Agente de documentación técnica
- [ ] Automatización de tareas de operaciones (backups, health checks, notificaciones)

### 7. 📊 Dirección Ejecutiva

- [ ] Dashboard ejecutivo global con KPIs en tiempo real
- [ ] Informe semanal generado automáticamente (lunes a las 7:00)
- [ ] Comparativas por país
- [ ] Alertas por umbrales
- [ ] Asistente de IA en lenguaje natural para el CEO

---

## Notas

- Este registro se actualizará a medida que se desarrollen los diferentes sistemas, agentes e integraciones.
- Las prioridades deben definirse con el equipo (no se especifica orden de prioridad en `CONTEXT.md`).
- Cada nuevo servicio, agente o pipeline debe documentarse en su propia subcarpeta con su `README.md`.

---

_Fuente: [CONTEXT.md](../CONTEXT.md), [README.md](../README.md) — Documento interno de 4Geeks Academy · AI Engineering Track._