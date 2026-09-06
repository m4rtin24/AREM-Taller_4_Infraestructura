# Referencias del Taller 4

## Alcance

En cumplimiento de la restricción de trabajar únicamente con el contenido del repositorio, esta entrega no utiliza fuentes externas. La investigación complementaria se construyó a partir del caso RedExpress, la guía, la visualización y las plantillas incluidas.

## Fuentes internas utilizadas

1. [`../README.md`](../README.md) — objetivo del taller, descripción de RedExpress, infraestructura híbrida, componentes esperados, áreas críticas, estructura de la entrega y rúbrica.
2. [`../clase/guia_paso_a_paso_infraestructura.md`](../clase/guia_paso_a_paso_infraestructura.md) — leyenda de notación, metodología de cinco pasos, mapa progresivo, diagnóstico priorizado, errores comunes, checklist y vista ArchiMate equivalente.
3. [`../clase/visualizacion-infraestructura.html`](../clase/visualizacion-infraestructura.html) — representación interactiva de las cuatro zonas, los flujos y los riesgos del balanceador, la base de datos y la región Medellín.
4. [`../plantillas/plantilla_informe_taller.md`](../plantillas/plantilla_informe_taller.md) — estructura del informe.
5. [`../plantillas/plantilla_notas.md`](../plantillas/plantilla_notas.md) — estructura del registro de clase.
6. [`../plantillas/plantilla_referencias.md`](../plantillas/plantilla_referencias.md) — estructura del documento de referencias.

## Relación entre fuentes y entrega

| Contenido de la entrega | Fuente interna |
|---|---|
| Descripción del sistema y temporadas de alto volumen | `README.md` |
| Zonas Clientes, Borde/Global, Bogotá y Medellín | Guía y visualización interactiva |
| Inventario de clientes, gateways, rutas, base de datos, balanceador y monitoreo | `README.md` y guía |
| R1 — punto único de falla del balanceador | Tabla de diagnóstico de la guía |
| R2 — latencia por escritura única en Bogotá | Tabla de diagnóstico de la guía |
| R3 — límite de escalabilidad de Medellín | Tabla de diagnóstico de la guía |
| Propuesta de redundancia y distribución regional | Derivación directa de R1, R2 y R3 |
| Criterios de autoevaluación | Checklist de la guía y rúbrica del `README.md` |

## Síntesis de investigación interna

El material del taller establece que un mapa de infraestructura debe mostrar componentes, agrupaciones y conexiones, pero también la redundancia de los elementos críticos. Esta última información permite diferenciar un punto único de falla de un cuello de botella y de un límite de escalabilidad.

En RedExpress, los componentes globales pueden afectar a toda la plataforma, mientras los componentes regionales explican dependencias geográficas. La escritura concentrada en Bogotá afecta el rendimiento de otras regiones; la ausencia de un módulo de rutas en Medellín limita el crecimiento regional; y un balanceador único compromete la disponibilidad completa. Por ello la propuesta final corrige cada condición en el mismo nivel donde se origina.

---

Este archivo forma parte de la entrega académica del curso AREM — Universidad de La Sabana.
