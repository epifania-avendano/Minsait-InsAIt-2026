# Dashboard Ejecutivo de IA en Producción

**AI Transformation Challenge 2026 · insAIt**  
**Código del caso:** `INSAIT-2026-12`  
**Modalidad:** A — Caso del catálogo

> Un espacio para conectar, conocer y compartir el conocimiento con soluciones tecnológicas potenciadas por la Inteligencia Artificial.

---

## Ficha del catálogo

| Campo | Detalle |
|---|---|
| Capacidad principal de IA | AI Observability & BI |
| Tipo de perfil | Funcional |
| Área de negocio | Transversal — Reporting al CDO |
| Perfiles clave sugeridos | BI Specialist · Data Analyst · Consultor de Gobierno |
| Tiempo estimado | 15–20 horas |
| Tipo de caso | Caso Completo |

**Reto:** Diseñar un dashboard ejecutivo (Power BI / Looker) que monitorea: número de modelos en producción, drift, costo de inferencia, valor de negocio generado, casos de uso por área. Incluir alertas y narrativa automática para el CDO mensual.

---

## 1. Identificación del caso

- **Nombre del caso:** Dashboard Ejecutivo de IA en Producción
- **Código asignado:** `INSAIT-2026-12`
- **Equipo participante:** _(completar — integrantes y rol de cada uno)_
  - Perfiles clave sugeridos para este reto: BI Specialist · Data Analyst · Consultor de Gobierno
- **Mentor técnico asignado:** _(completar)_
- **Mentor de negocio asignado:** _(completar)_
- **Fecha de inicio:** _(completar)_
- **Modalidad:** A — Caso del catálogo

## 2. Categoría y sector

- **Tipo de caso:** Caso Completo
- **Sector objetivo:** Transversal (Banca y Seguros)
- **Capacidad principal de IA:** AI Observability + BI
- **Categoría predominante:** Funcional

## 3. Resumen ejecutivo

El CDO necesita una vista única del estado de la IA en la organización, pero la información vive dispersa. Este caso diseña un dashboard ejecutivo que monitorea modelos en producción, drift, costo de inferencia, valor de negocio generado y casos de uso por área, con alertas y una narrativa automática para el reporte mensual del CDO. El prototipo se demuestra con un caso simulado de modelo en drift y su narrativa generada automáticamente.

## 4. Problema u oportunidad de negocio

Sin observabilidad ejecutiva, la dirección no sabe cuántos modelos hay en producción, si están degradándose (drift), cuánto cuestan ni qué valor generan. La información se arma manualmente cada mes, llega tarde y sin alertas. Esto impide gestionar el portafolio de IA con criterio y reaccionar a tiempo ante problemas.

## 5. Objetivos del caso

- Objetivo general: dar al CDO visibilidad ejecutiva y oportuna del portafolio de IA en producción.
- Visualizar modelos en producción, drift, costo y valor por área.
- Configurar alertas ante condiciones críticas (p. ej. drift).
- Generar automáticamente la narrativa mensual para el CDO.

## 6. Alcance funcional

**Sí se cubre:**

- Dashboard ejecutivo con KPIs de IA
- Monitoreo de drift y costo de inferencia
- Valor de negocio y casos de uso por área
- Alertas configurables
- Narrativa automática para el CDO

**No se cubre:**

- Conexión a la infraestructura real de modelos
- Telemetría en tiempo real productiva
- Datos reales de la organización
- Reentrenamiento de modelos

## 7. Descripción de la solución

Se modela un conjunto de métricas de portafolio (número de modelos, drift, costo de inferencia, valor de negocio, casos por área) alimentado por datos simulados. El dashboard presenta estas métricas con vistas ejecutivas y filtros por área. Un módulo de alertas marca condiciones críticas (p. ej. drift por encima de umbral) y un componente GenAI redacta automáticamente la narrativa mensual que interpreta los números para el CDO.

## 8. Flujo funcional de la solución

1. Se cargan los datos simulados de los modelos en producción.
2. El dashboard calcula y muestra los KPIs.
3. Se monitorean drift, costo y valor por área.
4. Se evalúan las condiciones de alerta.
5. Se dispara una alerta en el caso de drift simulado.
6. El módulo GenAI redacta la narrativa mensual.
7. El CDO recorre el dashboard y recibe la narrativa.

## 9. Datos requeridos

Datos simulados de telemetría de modelos: id_modelo, área, métricas de drift, costo de inferencia, valor estimado, estado. Volumetría: 10–30 modelos simulados, varios periodos. Tratamiento: data ficticia. Campos clave: modelo, area, drift, costo, valor, alerta.

## 10. Stack tecnológico propuesto

| Capa | Tecnología propuesta | Justificación |
|---|---|---|
| BI | Power BI / Looker / Streamlit | Dashboard ejecutivo |
| Datos | CSV/SQLite simulado | Telemetría de modelos |
| Alertas | Reglas sobre umbrales | Detección de condiciones críticas |
| Narrativa | Modelo GenAI (OpenAI) | Redacción automática para el CDO |
| Backend | Python | Cálculo de KPIs |

## 11. Arquitectura de la solución

Flujo BI: Fuente de telemetría (simulada) → cálculo de KPIs → dashboard + motor de alertas → módulo de narrativa GenAI. Vistas por área y por modelo. Punto de control: las alertas y la narrativa se derivan de los mismos KPIs mostrados (consistencia).

## 12. Métricas de éxito e indicadores

| Métrica | Línea base | Objetivo del prototipo | Forma de medición | Tipo |
|---|---|---|---|---|
| KPIs cubiertos | 0 | modelos/drift/costo/valor/área | Revisión del dashboard | Negocio |
| Alertas funcionando | n/a | dispara en drift | Prueba con caso simulado | Técnica |
| Narrativa automática | manual | generada | Demostración | Negocio |
| Tiempo de reporte mensual | manual/días | automático | Comparación | Negocio |

## 13. Riesgos, supuestos y dependencias

| Riesgo / supuesto | Mitigación prevista |
|---|---|
| Métricas mal definidas | Acordar definiciones con gobierno |
| Narrativa inconsistente con datos | Anclar el texto a los KPIs calculados |
| Sobrecarga visual del dashboard | Priorizar KPIs ejecutivos |
| Datos simulados poco realistas | Diseñar telemetría plausible |

---

## Criterios de evaluación (rúbrica · 100 puntos)

| # | Criterio | Peso | Qué se evalúa |
|---|---|---|---|
| 1 | Impacto de Negocio | 10 | ¿Cuánto valor aporta? ¿Resuelve un pain actual? |
| 2 | Diseño Funcional | 25 | Qué lógicas de negocio sigue el diseño |
| 3 | Diseño Técnico | 15 | Seguridad, arquitectura, esquema de datos |
| 4 | Desarrollo de la solución | 25 | Backend / Frontend |
| 5 | Presentación y Storytelling | 25 | Claridad, narrativa y defensa ante el jurado |

**Hito de validación:** Recorrido del dashboard con un caso simulado de modelo en drift — narrativa generada automáticamente para el CDO.
