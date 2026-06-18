# Copilot de Cumplimiento Regulatorio (CNBV/CONDUSEF)

**AI Transformation Challenge 2026 · insAIt**  
**Código del caso:** `INSAIT-2026-02`  
**Modalidad:** A — Caso del catálogo

> Un espacio para conectar, conocer y compartir el conocimiento con soluciones tecnológicas potenciadas por la Inteligencia Artificial.

---

## Ficha del catálogo

| Campo | Detalle |
|---|---|
| Capacidad principal de IA | RAG (Retrieval-Augmented Generation) |
| Área de negocio | Banca — Compliance y auditoría |
| Tiempo estimado | 20–25 horas |
| Tipo de caso | Caso Completo |

**Reto:** Crear un asistente experto para el equipo de auditoría interna. Al subir una nueva normativa, el asistente extrae los requisitos clave, los mapea contra las políticas internas vigentes, identifica gaps y propone acciones de remediación con trazabilidad documental.

---

## 1. Identificación del caso

- **Nombre del caso:** Copilot de Cumplimiento Regulatorio (CNBV/CONDUSEF)
- **Código asignado:** `INSAIT-2026-02`
- **Equipo participante:** _(completar — integrantes y rol de cada uno)_
  - Perfiles clave sugeridos para este reto: Agentic AI Engineer (RAG + memoria) · Especialista en regulatoria
- **Mentor técnico asignado:** _(completar)_
- **Mentor de negocio asignado:** _(completar)_
- **Fecha de inicio:** _(completar)_
- **Modalidad:** A — Caso del catálogo

## 2. Categoría y sector

- **Tipo de caso:** Caso Completo
- **Sector objetivo:** Banca
- **Capacidad principal de IA:** RAG (Retrieval-Augmented Generation)
- **Categoría predominante:** Técnica

## 3. Resumen ejecutivo

Cada nueva circular de la CNBV o disposición de CONDUSEF obliga al equipo de auditoría a leer decenas de páginas, contrastarlas contra las políticas internas y detectar dónde la institución incumple. Hoy es un proceso manual, lento y propenso a omisiones. Este caso propone un copilot basado en RAG que, al ingerir una normativa, extrae los requisitos clave, los mapea contra el cuerpo de políticas internas, identifica gaps y propone acciones de remediación, siempre con cita a la fuente. El prototipo se valida con un interrogatorio en vivo sobre un PDF de políticas simulado.

## 4. Problema u oportunidad de negocio

El análisis regulatorio en banca es intensivo en lectura experta. Una nueva normativa puede tardar semanas en analizarse e implementarse. El riesgo de omitir un requisito es alto y costoso: sanciones, observaciones de auditoría y reprocesos. Además, la trazabilidad entre 'lo que pide la norma' y 'lo que dice nuestra política' suele vivir en hojas de cálculo dispersas, lo que dificulta demostrar cumplimiento ante un regulador.

## 5. Objetivos del caso

- Objetivo general: acelerar y dar trazabilidad al análisis de cumplimiento mediante un asistente RAG sobre normativa y políticas internas.
- Reducir el tiempo de análisis inicial de una normativa de días a horas.
- Lograr ≥ 90% de respuestas con cita verificable a la fuente en el PoC.
- Detectar automáticamente gaps entre requisitos normativos y políticas internas sobre un conjunto de prueba.

## 6. Alcance funcional

**Sí se cubre:**

- Ingesta y chunking de documentos (normativa + políticas)
- Indexación vectorial y recuperación semántica
- Respuesta con cita a la fuente (documento, sección)
- Mapeo requisito-política y detección de gaps
- Propuesta de acciones de remediación

**No se cubre:**

- Conexión a repositorios documentales reales del banco
- Interpretación legal vinculante
- Actualización automática de las políticas internas
- Datos confidenciales reales

## 7. Descripción de la solución

El copilot indexa dos corpus: la normativa y las políticas internas. Ante una pregunta o al cargar una nueva norma, recupera los fragmentos más relevantes y genera una respuesta fundamentada que cita explícitamente la fuente. Un módulo de mapeo compara los requisitos extraídos de la norma contra las políticas y marca: cubierto, parcial o gap. Para cada gap, el asistente propone una acción de remediación. La clave del valor es la trazabilidad: toda afirmación está respaldada por una cita.

## 8. Flujo funcional de la solución

1. Se cargan los documentos (normativa y/o políticas) al asistente.
2. El sistema fragmenta e indexa el contenido en una base vectorial.
3. El auditor pregunta o solicita el análisis de una nueva norma.
4. El asistente recupera los fragmentos relevantes (retrieval).
5. El LLM genera la respuesta citando documento y sección.
6. El módulo de mapeo contrasta requisitos vs. políticas y marca gaps.
7. El asistente entrega hallazgos + citas + acciones de remediación.

## 9. Datos requeridos

PDFs simulados de normativa (estilo circular CNBV) y un manual de políticas internas ficticio. Volumetría: 2–5 documentos, decenas de páginas. Tratamiento: los textos son ficticios, sin datos reales. Campos/estructura clave: id_documento, sección, texto, embedding, tipo (norma/política).

## 10. Stack tecnológico propuesto

| Capa | Tecnología propuesta | Justificación |
|---|---|---|
| Vector store | FAISS / Chroma | Recuperación semántica local y reproducible |
| Embeddings | Modelo de embeddings vía API | Calidad de recuperación |
| LLM | Modelo GenAI (OpenAI) | Generación con citas |
| Ingesta | PyPDF / Unstructured | Extracción y chunking de PDFs |
| Backend | FastAPI | Orquesta retrieval + generación |
| Frontend | Streamlit/React (chat) | Interrogatorio en vivo |

## 11. Arquitectura de la solución

Pipeline RAG: Ingesta (PDF → chunks) → Embeddings → Vector store. En consulta: pregunta → retrieval top-k → prompt aumentado → LLM → respuesta con citas. Un módulo de mapeo cruza requisitos extraídos contra políticas. Punto de control clave: cada respuesta debe adjuntar las referencias recuperadas para auditar la fidelidad.

## 12. Métricas de éxito e indicadores

| Métrica | Línea base | Objetivo del prototipo | Forma de medición | Tipo |
|---|---|---|---|---|
| Tiempo de análisis de una norma | días | horas | Cronometría del PoC | Negocio |
| Respuestas con cita verificable | baja | ≥ 90% | Revisión manual de muestra | Técnica |
| Precisión de gaps detectados | n/a | alta vs. ground truth | Comparación con set anotado | Técnica |
| Cobertura de requisitos mapeados | manual | completa en el set | Conteo | Negocio |

## 13. Riesgos, supuestos y dependencias

| Riesgo / supuesto | Mitigación prevista |
|---|---|
| Alucinación / cita inventada | Forzar respuesta solo desde contexto recuperado; mostrar las fuentes |
| Chunking pobre que pierde contexto | Probar tamaños de chunk y solapamiento |
| Ambigüedad regulatoria | Mantener al especialista en regulatoria como validador (human-in-the-loop) |
| Documentos mal extraídos (escaneos) | Usar OCR/parser robusto y validar muestras |

---

## Criterios de evaluación (rúbrica · 100 puntos)

| # | Criterio | Peso | Qué se evalúa |
|---|---|---|---|
| 1 | Impacto de Negocio | 10 | ¿Cuánto valor aporta? ¿Resuelve un pain actual? |
| 2 | Diseño Funcional | 25 | Qué lógicas de negocio sigue el diseño |
| 3 | Diseño Técnico | 15 | Seguridad, arquitectura, esquema de datos |
| 4 | Desarrollo de la solución | 25 | Backend / Frontend |
| 5 | Presentación y Storytelling | 25 | Claridad, narrativa y defensa ante el jurado |

**Hito de validación:** Interrogatorio en tiempo real al asistente usando un PDF simulado de Políticas — el jurado evalúa precisión, citas y trazabilidad.
