# 🛠️ Taller 4: Mapa de Infraestructura y Diagnóstico Técnico

## 🎯 Objetivo

Construir el mapa lógico y/o físico de la infraestructura tecnológica del sistema base y realizar un diagnóstico de debilidades, cuellos de botella y oportunidades de mejora.

---

## ✅ Entrega desarrollada

La entrega desarrolla exclusivamente el caso **RedExpress** descrito en este repositorio, con trazabilidad entre el mapa, los riesgos y las oportunidades de mejora:

- [Notas y diagnóstico del caso base RedExpress](clase/notas.md)
- [Mapa borrador editable de RedExpress](clase/mapa-borrador.drawio)
- [Mapa final editable de RedExpress, con estado diagnosticado y propuesta de mejora](entrega/mapa-final.drawio)
- [Informe técnico y vista previa del mapa](entrega/informe.md)
- [Investigación y referencias técnicas](entrega/referencias.md)

El informe, los mapas y las referencias usan únicamente información contenida en este repositorio. La propuesta final se limita a corregir los tres riesgos que identifica la guía del taller.

---

## 📘 Guía paso a paso

Antes de empezar a modelar, revise la [**Guía Paso a Paso: Mapa de Infraestructura y Diagnóstico Técnico**](clase/guia_paso_a_paso_infraestructura.md). Incluye la leyenda de notación, la metodología de 5 pasos (mapa + diagnóstico) que se usa en el taller, un ejemplo completo construido paso a paso sobre el caso de RedExpress con una tabla de diagnóstico priorizado, y una comparación de errores comunes.

### 🖼️ Versión visual: Mapa de Infraestructura y Riesgo

[`clase/visualizacion-infraestructura.html`](clase/visualizacion-infraestructura.html) es una página interactiva autocontenida: un mapa de infraestructura de RedExpress por zonas (Clientes, Borde/Global, Región Bogotá y Región Medellín) en el que los componentes marcados con ⚠️ (balanceador de carga, base de datos distribuida y API Gateway de Medellín) son clickeables y muestran su categoría de riesgo, impacto y prioridad; además incluye la leyenda de notación, la metodología de 5 pasos, la tabla de diagnóstico priorizado completa, los errores comunes a evitar y la vista ArchiMate equivalente. GitHub no la renderiza interactiva desde la vista de archivo; para verla:
- Descargue el archivo y ábralo con doble clic (funciona sin conexión, es HTML plano), o
- Pegue esta URL en [htmlpreview.github.io](https://htmlpreview.github.io/): `https://raw.githubusercontent.com/m4rtin24/AREM-Taller_4_Infraestructura/main/clase/visualizacion-infraestructura.html`

## 🚚 Caso base de referencia: RedExpress (Plataforma de Logística)

RedExpress cuenta con una infraestructura híbrida que incluye servidores regionales, servicios en la nube, centros de distribución físicos y dispositivos móviles utilizados por los mensajeros. La plataforma digital debe garantizar alta disponibilidad y rendimiento, especialmente durante campañas promocionales o temporadas de alto volumen como Navidad. El mapa de infraestructura y el diagnóstico técnico permitirán visualizar riesgos como puntos únicos de falla, cuellos de botella en bases de datos, y limitaciones en la escalabilidad horizontal de servicios críticos.

**Contexto:**
- RedExpress gestiona paquetes y rastreo de envíos mediante una app móvil y una plataforma web.
- La infraestructura actual incluye servicios desplegados en la nube, servidores regionales para procesamiento de rutas, y una base de datos centralizada.

**Elementos esperados para modelar:**

- Componentes de infraestructura:
  - Balanceadores de carga
  - Base de datos distribuida
  - API Gateway
  - Servicios de monitoreo y alertas
  - Módulos de procesamiento de rutas y estados de paquetes

- Áreas críticas a diagnosticar:
  - Latencia en rastreo en tiempo real
  - Riesgo de puntos únicos de falla
  - Escalabilidad por zonas geográficas

---

## 🧪 Parte 1: Trabajo en Clase

Durante la clase se espera que el equipo:

Siga la metodología de 5 pasos de la [guía paso a paso](clase/guia_paso_a_paso_infraestructura.md) para construir el mapa de infraestructura de RedExpress:

1. Identifique los componentes de infraestructura (servidores, servicios, bases de datos, balanceadores, etc.).
2. Agrúpelos por zona geográfica o capa.
3. Conecte los componentes según el tráfico real entre ellos.
4. Marque qué componentes críticos tienen redundancia y cuáles son instancia única.
5. Diagnostique y priorice los riesgos, y valide el mapa con la [checklist de autoevaluación](clase/guia_paso_a_paso_infraestructura.md#5-checklist-de-autoevaluación-antes-de-entregar).

- Use papel, draw.io o cualquier herramienta visual para registrar su análisis.
- Reciba retroalimentación del docente y registre avances en `clase/notas.md` (use la [plantilla de notas](plantillas/plantilla_notas.md)).

---

## 🧠 Parte 2: Aplicación al Cliente Real

Después de la clase, el equipo debe:

- Elaborar el mapa de infraestructura del sistema real del cliente, aplicando los mismos 5 pasos de la metodología.
- Identificar debilidades o cuellos de botella reales o potenciales, y clasificarlos igual que en la tabla de diagnóstico de la guía (disponibilidad, rendimiento, escalabilidad).
- Redactar el informe en `entrega/informe.md` usando la [plantilla de informe del taller](plantillas/plantilla_informe_taller.md); explicar el diagnóstico técnico y las diferencias con el caso base.
- Complementar con una pequeña investigación sobre buenas prácticas de arquitectura de infraestructura (cloud, on-premise, híbrida), y registrar las fuentes en `entrega/referencias.md` con la [plantilla de referencias](plantillas/plantilla_referencias.md).

---

## 📁 Estructura esperada del repositorio

```text
taller-04-infraestructura/
├── README.md
├── clase/
│   ├── guia_paso_a_paso_infraestructura.md   # Notación, metodología de 5 pasos y ejemplo guiado
│   ├── mapa-borrador.drawio
│   └── notas.md                              # Ver plantillas/plantilla_notas.md
├── entrega/
│   ├── mapa-final.drawio
│   ├── informe.md                            # Ver plantillas/plantilla_informe_taller.md
│   └── referencias.md                        # Ver plantillas/plantilla_referencias.md
└── plantillas/
    ├── plantilla_informe_taller.md
    ├── plantilla_notas.md
    └── plantilla_referencias.md
```

---

## ⚠️ Errores comunes

Antes de entregar, compare su mapa y diagnóstico contra los errores más frecuentes (componentes sin agrupar, redundancia sin marcar, diagnóstico desconectado del mapa) documentados en la [sección 4 de la guía paso a paso](clase/guia_paso_a_paso_infraestructura.md#4-errores-comunes-a-evitar).

## 📤 Entregables

- Mapa de infraestructura del sistema del cliente
- Informe de diagnóstico técnico
- Documento de referencias/investigación

---

## 📊 Rúbrica de Evaluación

| Criterio                            | Excelente (5)                                                             | Aceptable (3) / Insuficiente (1–2)                         |
|-------------------------------------|----------------------------------------------------------------------------|-------------------------------------------------------------|
| Mapa de infraestructura (caso base) | Representa claramente componentes, nodos y servicios críticos             | Elementos incompletos o mal estructurados                  |
| Análisis de cuellos de botella      | Se identifican y justifican problemas técnicos reales o simulados         | Diagnóstico débil o poco argumentado                       |
| Adaptación al cliente real          | El modelo refleja la infraestructura del cliente con lógica y detalle     | Adaptación superficial o desconectada                      |
| Investigación técnica               | Se apoya en buenas prácticas (cloud, escalabilidad, redundancia, etc.)    | Investigación poco clara o sin fuentes aplicadas           |

---

## ✅ Licencia

Este taller hace parte del curso de Arquitectura Empresarial - Universidad de La Sabana. Uso académico bajo licencia MIT.
