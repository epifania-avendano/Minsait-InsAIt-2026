# Asistente Conversacional para Empleados (Knowledge Base Interna)

**AI Transformation Challenge 2026 · insAIt**  
**Código del caso:** `INSAIT-2026-13`  
**Modalidad:** A — Caso del catálogo

> Un espacio para conectar, conocer y compartir el conocimiento con soluciones tecnológicas potenciadas por la Inteligencia Artificial.

---

## Ficha del catálogo

| Campo | Detalle |
|---|---|
| Capacidad principal de IA | GenAI + RAG corporativo |
| Tipo de perfil | Técnico-funcional |
| Área de negocio | Transversal — Productividad interna |
| Perfiles clave sugeridos | AI Engineer · Diseñador conversacional · Consultor sectorial |
| Tiempo estimado | 20–25 horas |
| Tipo de caso | Caso Completo |

**Reto:** Construir un asistente conversacional para empleados de banca/seguros que responda dudas sobre productos, políticas internas y procesos operativos. Integrar control de acceso por rol, citas a fuente y feedback loop.

---

## 1. Identificación del caso

- **Nombre del caso:** Asistente Conversacional para Empleados (Knowledge Base Interna)
- **Código asignado:** `INSAIT-2026-13`
- **Equipo participante:** _(completar — integrantes y rol de cada uno)_
  - Perfiles clave sugeridos para este reto: AI Engineer · Diseñador conversacional · Consultor sectorial
- **Mentor técnico asignado:** _(completar)_
- **Mentor de negocio asignado:** _(completar)_
- **Fecha de inicio:** _(completar)_
- **Modalidad:** A — Caso del catálogo

## 2. Categoría y sector

- **Tipo de caso:** Caso Completo
- **Sector objetivo:** Transversal (Banca y Seguros)
- **Capacidad principal de IA:** GenAI + RAG corporativo
- **Categoría predominante:** Técnico-funcional

## 3. Resumen ejecutivo

Los empleados pierden tiempo buscando respuestas sobre productos, políticas y procesos en documentos dispersos. Este caso construye un asistente conversacional basado en RAG corporativo que responde con citas a la fuente, respeta control de acceso por rol y aprende de un feedback loop. El prototipo se valida en una sesión en vivo con preguntas de empleados, donde el asistente debe citar fuentes y manejar correctamente los casos sensibles.

## 4. Problema u oportunidad de negocio

El conocimiento interno (productos, políticas, procesos) está fragmentado en múltiples documentos y sistemas. Los empleados consultan a colegas o adivinan, lo que genera errores operativos y pérdida de productividad. Además, no todos deben ver toda la información (control por rol), y sin citas no se puede confiar en las respuestas.

## 5. Objetivos del caso

- Objetivo general: dar a los empleados respuestas confiables, citadas y controladas por rol sobre el conocimiento interno.
- Responder consultas con cita verificable a la fuente.
- Aplicar control de acceso por rol al conocimiento.
- Incorporar un feedback loop para mejorar respuestas.

## 6. Alcance funcional

**Sí se cubre:**

- Asistente conversacional con RAG sobre KB interna
- Citas a la fuente en cada respuesta
- Control de acceso por rol
- Feedback loop (útil/no útil)
- Manejo de casos sensibles (declinar/derivar)

**No se cubre:**

- Integración con IdP y repositorios reales
- Cobertura de toda la base documental
- Datos confidenciales reales
- Acciones operativas automáticas

## 7. Descripción de la solución

El asistente indexa una base de conocimiento corporativa simulada (productos, políticas, procesos). Ante una pregunta, recupera los fragmentos relevantes filtrados por el rol del usuario y genera una respuesta que cita la fuente. Para temas sensibles o fuera de alcance, el asistente declina o deriva. Un feedback loop captura si la respuesta fue útil, alimentando la mejora continua. El control por rol asegura que cada empleado solo accede a lo que le corresponde.

## 8. Flujo funcional de la solución

1. El empleado se identifica con su rol.
2. Plantea una pregunta sobre producto/política/proceso.
3. El asistente recupera fragmentos filtrados por rol.
4. Genera la respuesta citando la fuente.
5. Para casos sensibles, declina o deriva adecuadamente.
6. El empleado marca la respuesta como útil/no útil.
7. El feedback alimenta la mejora del asistente.

## 9. Datos requeridos

Base de conocimiento simulada: documentos de productos, políticas y procesos ficticios, con etiquetas de rol. Volumetría: decenas de documentos. Tratamiento: contenido ficticio. Campos clave: documento, rol_permitido, texto, embedding, fuente.

## 10. Stack tecnológico propuesto

| Capa | Tecnología propuesta | Justificación |
|---|---|---|
| Vector store | Chroma / FAISS | Recuperación semántica |
| Embeddings | Modelo de embeddings (API) | Calidad de retrieval |
| LLM | Modelo GenAI (OpenAI) | Respuestas conversacionales |
| Control de acceso | Filtro por rol en retrieval | Seguridad por perfil |
| Feedback | Registro útil/no útil | Mejora continua |
| Frontend | Chat (Streamlit/React) | Sesión en vivo |

## 11. Arquitectura de la solución

RAG con control de acceso: pregunta + rol → retrieval filtrado por rol → prompt aumentado → LLM → respuesta con citas → feedback loop. Guardrails para temas sensibles. Punto de control: el filtro por rol se aplica antes del retrieval y cada respuesta adjunta sus fuentes.

## 12. Métricas de éxito e indicadores

| Métrica | Línea base | Objetivo del prototipo | Forma de medición | Tipo |
|---|---|---|---|---|
| Respuestas con cita | baja | alta | Revisión de muestra | Técnica |
| Cumplimiento de control por rol | n/a | 100% en pruebas | Pruebas por perfil | Técnica |
| Manejo de casos sensibles | n/a | correcto | Sesión en vivo | Negocio |
| Utilidad percibida | n/a | alta (feedback) | Feedback loop | Negocio |

## 13. Riesgos, supuestos y dependencias

| Riesgo / supuesto | Mitigación prevista |
|---|---|
| Fuga de información entre roles | Aplicar filtro por rol antes del retrieval |
| Alucinación sin cita | Responder solo desde contexto recuperado |
| Casos sensibles mal manejados | Definir políticas de declinar/derivar |
| KB desactualizada | Versionar y refrescar el índice |

---

## Criterios de evaluación (rúbrica · 100 puntos)

| # | Criterio | Peso | Qué se evalúa |
|---|---|---|---|
| 1 | Impacto de Negocio | 10 | ¿Cuánto valor aporta? ¿Resuelve un pain actual? |
| 2 | Diseño Funcional | 25 | Qué lógicas de negocio sigue el diseño |
| 3 | Diseño Técnico | 15 | Seguridad, arquitectura, esquema de datos |
| 4 | Desarrollo de la solución | 25 | Backend / Frontend |
| 5 | Presentación y Storytelling | 25 | Claridad, narrativa y defensa ante el jurado |

**Hito de validación:** Sesión en vivo con preguntas de empleados reales donde el asistente responde con citas y maneja casos sensibles correctamente.
