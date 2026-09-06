# Referencias e investigación técnica — Taller 4

## Taller

Taller 4 — Mapa de Infraestructura y Diagnóstico Técnico aplicado a EcoRecicla (SIAR).

Fecha de consulta de las fuentes web: 6 de septiembre de 2026.

## Pregunta de investigación

¿Qué prácticas de infraestructura permiten que un sistema transaccional de pesajes, trazabilidad de materiales y reportes regulatorios evolucione desde un prototipo de interfaz hacia una operación disponible, escalable y observable?

## Síntesis

La primera decisión es separar la entrega estática de la interfaz de los servicios transaccionales. La interfaz puede distribuirse desde almacenamiento de objetos y CDN, mientras las operaciones de pesaje, recicladores, rutas, balance de masas, PQR y generación SUI pasan por una API sin estado. Este desacoplamiento permite replicar el cómputo detrás de un balanceador y escalarlo según demanda. AWS Well-Architected recomienda recuperación automática, pruebas de recuperación y escalamiento horizontal para reducir puntos únicos de falla [1]; Kubernetes documenta que el Horizontal Pod Autoscaler ajusta el número de réplicas usando métricas de recursos o métricas personalizadas [2]. En EcoRecicla estas prácticas se traducen en dos o más instancias de API, al menos dos zonas de disponibilidad y trabajos pesados enviados a una cola.

La persistencia exige un tratamiento distinto al cómputo sin estado. PostgreSQL señala que un servidor secundario puede asumir rápidamente si falla el primario y que las decisiones entre replicación síncrona y asíncrona implican compromisos entre consistencia, pérdida potencial y latencia [3]. Por eso el mapa propone una base administrada con primario y standby en zonas diferentes, copias cifradas y recuperación a un punto en el tiempo. El RPO y RTO incluidos en el informe son objetivos iniciales para validar, no garantías actuales.

Finalmente, alta disponibilidad sin observabilidad deja fallas invisibles. OpenTelemetry describe métricas, logs y trazas como señales complementarias, y recomienda indicadores medidos desde la perspectiva del usuario [4]. La propuesta centraliza las tres señales y alerta sobre errores, latencia, saturación, profundidad de cola y fallos de replicación. Estas medidas conectan los controles técnicos con operaciones del negocio como registrar un pesaje o generar un reporte SUI.

## Aplicación de las fuentes al diseño

| Fuente | Práctica extraída | Aplicación en EcoRecicla |
|---|---|---|
| [1] AWS Well-Architected | Recuperación automática, pruebas de recuperación, escalamiento horizontal y automatización de cambios. | API replicada en dos zonas, balanceador administrado, infraestructura automatizable y simulacros de restauración. |
| [2] Kubernetes HPA | Ajuste automático de réplicas con métricas de CPU, memoria o negocio. | Escalar API y workers con demanda, usando solicitudes por segundo y profundidad de cola además de CPU. |
| [3] PostgreSQL HA | Standby, failover y selección consciente entre replicación síncrona/asíncrona. | Primario + standby, failover probado, PITR y revisión de latencia de escritura. |
| [4] OpenTelemetry | Instrumentación con métricas, logs y trazas; SLI desde el punto de vista del usuario. | Trazar `registrar pesaje` y `generar SUI`; medir éxito y latencia extremo a extremo. |

## Referencias

1. Amazon Web Services. *AWS Well-Architected Framework — Reliability Pillar: Design principles*. <https://docs.aws.amazon.com/wellarchitected/2024-06-27/framework/rel-dp.html>.
2. Kubernetes Authors. *Horizontal Pod Autoscaling*. <https://kubernetes.io/docs/concepts/workloads/autoscaling/horizontal-pod-autoscale/>.
3. PostgreSQL Global Development Group. *High Availability, Load Balancing, and Replication*. <https://www.postgresql.org/docs/current/high-availability.html>.
4. OpenTelemetry Authors. *Observability primer*. <https://opentelemetry.io/docs/concepts/observability-primer/>.

## Criterios de calidad de las fuentes

Se priorizaron documentos oficiales y vigentes de los proyectos o proveedores responsables. No se usaron blogs comerciales secundarios ni Wikipedia. Las fuentes sustentan patrones; no certifican que la infraestructura propuesta ya esté desplegada ni sustituyen la validación de costos, capacidad, seguridad y continuidad con el cliente.

---

Este archivo forma parte de la entrega académica del curso AREM — Universidad de La Sabana.
