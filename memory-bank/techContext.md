# Tech Context — TrackFlow

> Basado exclusivamente en la información de `CONTEXT.md`. Fecha: 2026-10-17.

---

## Stack tecnológico base

### Estado actual (arquitectura heredada)

| Componente                  | Descripción                                                                                            |
| --------------------------- | ------------------------------------------------------------------------------------------------------ |
| **WMS (SGA) — Los Ángeles** | Software comercial de gestión de almacenes                                                             |
| **WMS (SGA) — Zaragoza**    | Hoja de cálculo avanzada                                                                               |
| **ERP corporativo**         | Sistema de principios de la década de 2010                                                             |
| **Integraciones**           | Scripts de Python punto a punto, sin documentar                                                        |
| **Bases de datos**          | En dos proveedores cloud distintos                                                                     |
| **Telemetría**              | No existe centralizada. Cuando algo falla en Los Ángeles, el equipo en Zaragoza se entera por WhatsApp |
| **Despliegue**              | Una nueva funcionalidad tarda entre una y dos semanas en desplegarse                                   |

### Stack objetivo (lo que necesita la compañía)

El mandato de TrackFlow Tech incluye construir:

- **API de inventario unificada** — stock en tiempo real de cualquier SKU en cualquiera de los dos almacenes.
- **Pipeline de ingesta de pedidos** — parseo automático de emails con formatos de cliente variables.
- **Motor de selección de transportista** — recomendación óptima según destino, peso y urgencia.
- **Endpoint unificado de tracking** — agregación de estado desde 8 APIs de transportistas distintas.
- **Portal de seguimiento público** — para destinatarios de paquetes.
- **Motor de aprobación automática de devoluciones** — con reglas configurables por cliente.
- **Sistema de inspección asistido por IA** — clasificación por imagen del estado del producto devuelto.
- **Agente CX de primera línea** — resolución automática de consultas de tracking y devoluciones.
- **Base de conocimiento semántica** — indexada para RAG, soporte multiidioma (español + inglés).
- **Sistema de tickets unificado** — para atención al cliente.
- **CRM con perfiles unificados de cliente** — informes PDF automáticos y dashboard de salud.
- **Telemetría y logging centralizados** — ambos países.
- **Pipeline de datos** — alimentando todos los dashboards de la empresa.
- **Monitorización en tiempo real** — alertas automáticas.
- **Dashboard ejecutivo global** — KPIs en tiempo real, comparativas por país, informe semanal automático.
- **Asistente de IA en lenguaje natural** — para el CEO.
- **Agente de documentación técnica** — para el equipo de tecnología.
- **Automatización de tareas de operaciones** — backups, health checks, notificaciones de incidencias.

## Decisiones arquitectónicas (implícitas en el contexto)

1. **Monorepo** — El repositorio actual es un monorepo con carpetas por capa (`uis/`, `services/`, `agents/`, `data/`, `workflows/`, etc.).
2. **API centralizada (FastAPI)** — Según `README.md`, se recomienda un único backend FastAPI como punto de entrada.
3. **Agentes de IA** — Los agentes se alojan en `agents/` con habilidades reutilizables en `skills/` y servidores MCP en `mcps/`.
4. **Flujos de automatización** — n8n para orquestación cross-system (`workflows/`).
5. **Tipos compartidos** — `packages/shared/` con `@repo/shared-types` para interfaces comunes.
6. **Docker Compose** — Descrito en `README.md` como orquestación local desde la raíz del repositorio, pero el archivo `docker-compose.yml` aún no existe (pendiente de crear).

## Restricciones

- **Dos países, dos idiomas** — Los sistemas deben funcionar en EE. UU. e España, con soporte opcional pero recomendado de español e inglés.
- **8 carriers distintos** — Cada uno con su propia API y formato de tracking (UPS, FedEx, DHL, MRW, SEUR, etc.).
- **Legacy sin documentar** — El ERP, los scripts Python y las bases de datos existentes carecen de documentación.
- **Sin telemetría centralizada** — No hay visibilidad del estado de los sistemas en tiempo real.
- **Equipo reducido** — El equipo de tecnología son 7 personas en Zaragoza.
- **Sistemas 24/7** — Los clientes esperan sus paquetes sin interrupción; el CX agent, tracking portal y dashboards deben estar siempre disponibles.
- **Volumen de devoluciones 18–25%** — La logística inversa representa una fracción significativa del volumen total.

## Equipo de tecnología

| Rol                   | Detalle                                                |
| --------------------- | ------------------------------------------------------ |
| **CTO**               | Andrés Kim, desde Zaragoza                             |
| **Tamaño del equipo** | 7 personas (desarrolladores, data engineers, sistemas) |
| **Ubicación**         | Zaragoza, España (oficina de tecnología)               |

---

_Fuente: [CONTEXT.md](../CONTEXT.md), [README.md](../README.md) — Documento interno de 4Geeks Academy · AI Engineering Track._
