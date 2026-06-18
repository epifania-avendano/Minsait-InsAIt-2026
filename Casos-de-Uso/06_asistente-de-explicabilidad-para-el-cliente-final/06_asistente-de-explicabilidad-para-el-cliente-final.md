# Asistente de Explicabilidad para el Cliente Final

**AI Transformation Challenge 2026 · insAIt**  
**Código del caso:** `INSAIT-2026-06`  
**Modalidad:** A — Caso del catálogo

> Un espacio para conectar, conocer y compartir el conocimiento con soluciones tecnológicas potenciadas por la Inteligencia Artificial.

---

## Ficha del catálogo

| Campo | Detalle |
|---|---|
| Capacidad principal de IA | Explicabilidad de IA (XAI) |
| Área de negocio | Banca / Seguros — Experiencia + Compliance |
| Tiempo estimado | 15–20 horas |
| Tipo de caso | Caso Completo |

**Reto:** Desarrollar una interfaz que traduzca las decisiones tomadas por algoritmos de ML (rechazo de crédito, ajuste de prima) en explicaciones claras y accionables para el cliente final. Combina SHAP/LIME con LLM para narrativa amable.

---

## 1. Identificación del caso

- **Nombre del caso:** Asistente de Explicabilidad para el Cliente Final
- **Código asignado:** `INSAIT-2026-06`
- **Equipo participante:** _(completar — integrantes y rol de cada uno)_
  - Perfiles clave sugeridos para este reto: Frontend Developer · AI Engineer · Diseñador UX
- **Mentor técnico asignado:** _(completar)_
- **Mentor de negocio asignado:** _(completar)_
- **Fecha de inicio:** _(completar)_
- **Modalidad:** A — Caso del catálogo

## 2. Categoría y sector

- **Tipo de caso:** Caso Completo
- **Sector objetivo:** Banca / Seguros
- **Capacidad principal de IA:** XAI (SHAP/LIME) + GenAI para narrativa
- **Categoría predominante:** Técnico-funcional

## 3. Resumen ejecutivo

Cuando un modelo rechaza un crédito o ajusta una prima, el cliente recibe una notificación opaca que no le dice qué hacer para mejorar. Este caso propone un asistente que combina técnicas de explicabilidad (SHAP/LIME) con un LLM que traduce los factores técnicos en una narrativa amable y accionable. El prototipo simula el portal del cliente mostrando una 'Carta de Rechazo Dinámica' con factores que el cliente entiende y puede accionar.

## 4. Problema u oportunidad de negocio

Las decisiones automatizadas sin explicación generan frustración, quejas y riesgo regulatorio (derecho del cliente a entender por qué). El cliente no sabe qué variable pesó ni cómo revertir el resultado, lo que erosiona la confianza y aumenta la carga de los canales de atención con reclamos.

## 5. Objetivos del caso

- Objetivo general: traducir decisiones de ML en explicaciones claras y accionables para el cliente final.
- Generar para cada decisión los principales factores con su contribución (SHAP/LIME).
- Producir una narrativa comprensible y empática para un cliente no técnico.
- Incluir recomendaciones accionables que el cliente pueda seguir.

## 6. Alcance funcional

**Sí se cubre:**

- Modelo de decisión simulado (rechazo/ajuste)
- Cálculo de explicabilidad (SHAP/LIME)
- Generación de narrativa con LLM
- Interfaz tipo portal del cliente
- Carta de Rechazo Dinámica con factores accionables

**No se cubre:**

- Modelo de riesgo de producción
- Envío real de comunicaciones
- Datos reales de clientes
- Integración con el portal real

## 7. Descripción de la solución

Sobre un modelo de decisión simulado, se calculan las contribuciones de cada variable con SHAP/LIME. Esos factores técnicos se pasan a un LLM que redacta una explicación en lenguaje claro, empático y accionable, evitando jerga. La interfaz presenta la decisión, los 3–5 factores principales y recomendaciones concretas ('reduce tu nivel de endeudamiento', 'demuestra ingresos adicionales'). El resultado es una carta dinámica adaptada a cada cliente.

## 8. Flujo funcional de la solución

1. El cliente consulta el resultado de su solicitud en el portal.
2. El sistema recupera la decisión del modelo simulado.
3. Se calculan los factores con SHAP/LIME.
4. El LLM convierte los factores en narrativa clara.
5. Se generan recomendaciones accionables.
6. La interfaz muestra la Carta de Rechazo Dinámica.
7. El cliente entiende los motivos y los siguientes pasos.

## 9. Datos requeridos

Dataset sintético de decisiones (variables del cliente + resultado) y un modelo entrenado sobre él. Volumetría: 100–500 casos. Tratamiento: data ficticia. Campos clave: features del cliente, decisión, valores SHAP, narrativa.

## 10. Stack tecnológico propuesto

| Capa | Tecnología propuesta | Justificación |
|---|---|---|
| Modelo | scikit-learn | Decisión simulada explicable |
| Explicabilidad | SHAP / LIME | Contribución por variable |
| Narrativa | Modelo GenAI (OpenAI) | Texto claro y empático |
| Frontend | React / Streamlit | Portal del cliente |
| Backend | FastAPI | Orquesta modelo + XAI + LLM |

## 11. Arquitectura de la solución

Flujo: Modelo (decisión) → módulo XAI (SHAP/LIME → factores) → LLM (factores → narrativa) → Frontend (carta dinámica). El backend coordina las tres etapas. Punto de control: verificar que la narrativa refleje fielmente los factores calculados (consistencia XAI-texto).

## 12. Métricas de éxito e indicadores

| Métrica | Línea base | Objetivo del prototipo | Forma de medición | Tipo |
|---|---|---|---|---|
| Claridad percibida | comunicación opaca | alta (evaluación) | Encuesta/jurado | Negocio |
| Factores correctos en la carta | n/a | coinciden con SHAP | Verificación | Técnica |
| Acciones accionables incluidas | 0 | ≥ 3 por carta | Inspección | Negocio |
| Tiempo de generación | n/a | segundos | Cronometría | Técnica |

## 13. Riesgos, supuestos y dependencias

| Riesgo / supuesto | Mitigación prevista |
|---|---|
| Narrativa que contradiga al modelo | Anclar el texto a los valores SHAP; validar consistencia |
| Tono inadecuado o no empático | Diseñar prompts y revisar con UX |
| Sobre-simplificación que pierda precisión | Equilibrar claridad y exactitud |
| Riesgo regulatorio en redacción | Revisión funcional de compliance |

---

## Criterios de evaluación (rúbrica · 100 puntos)

| # | Criterio | Peso | Qué se evalúa |
|---|---|---|---|
| 1 | Impacto de Negocio | 10 | ¿Cuánto valor aporta? ¿Resuelve un pain actual? |
| 2 | Diseño Funcional | 25 | Qué lógicas de negocio sigue el diseño |
| 3 | Diseño Técnico | 15 | Seguridad, arquitectura, esquema de datos |
| 4 | Desarrollo de la solución | 25 | Backend / Frontend |
| 5 | Presentación y Storytelling | 25 | Claridad, narrativa y defensa ante el jurado |

**Hito de validación:** Simulación del portal del cliente donde se muestre una Carta de Rechazo Dinámica con factores accionables que el cliente entiende.
