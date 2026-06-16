# Gestor Documental Inteligente

**AI Transformation Challenge 2026 · insAIt**  
**Código del caso:** `INSAIT-2026-07`  
**Modalidad:** A — Caso del catálogo

> Un espacio para conectar, conocer y compartir el conocimiento con soluciones tecnológicas potenciadas por la Inteligencia Artificial.

---

## Ficha del catálogo

| Campo | Detalle |
|---|---|
| Capacidad principal de IA | NLP + Document AI + Rule Engine |
| Tipo de perfil | Técnico avanzado |
| Área de negocio | Banca / Seguros — Onboarding y operación |
| Perfiles clave sugeridos | AI Engineer · NLP Specialist · Data Governance Consultant |
| Tiempo estimado | 25–30 horas |
| Tipo de caso | Caso Completo |

**Reto:** Desarrollar una plataforma capaz de ingerir expedientes documentales de clientes (IDs, comprobantes, contratos), extraer información estructurada, validar cumplimiento KYC/AML y enrutar al flujo correspondiente con observabilidad y trazabilidad completa.

---

## 1. Identificación del caso

- **Nombre del caso:** Gestor Documental Inteligente
- **Código asignado:** `INSAIT-2026-07`
- **Equipo participante:** _(completar — integrantes y rol de cada uno)_
  - Perfiles clave sugeridos para este reto: AI Engineer · NLP Specialist · Data Governance Consultant
- **Mentor técnico asignado:** _(completar)_
- **Mentor de negocio asignado:** _(completar)_
- **Fecha de inicio:** _(completar)_
- **Modalidad:** A — Caso del catálogo

## 2. Categoría y sector

- **Tipo de caso:** Caso Completo
- **Sector objetivo:** Banca / Seguros
- **Capacidad principal de IA:** Document AI + NLP + motor de reglas
- **Categoría predominante:** Técnica

## 3. Resumen ejecutivo

El onboarding de clientes implica recibir y revisar manualmente expedientes (identificaciones, comprobantes, contratos), una tarea lenta y propensa a errores. Este caso propone una plataforma que ingiere los documentos, extrae información estructurada con Document AI, valida cumplimiento KYC/AML mediante un motor de reglas y enruta cada expediente al flujo correspondiente, con trazabilidad y observabilidad completas. El prototipo procesa expedientes simulados, detecta inconsistencias, completa campos faltantes y genera alertas.

## 4. Problema u oportunidad de negocio

La captura manual de datos de documentos es costosa, lenta y genera errores que se propagan a todo el ciclo de vida del cliente. Las validaciones KYC/AML dependen de revisión humana, lo que alarga el onboarding (días) y aumenta el riesgo de incumplimiento. Además, no existe trazabilidad de qué se validó y por qué.

## 5. Objetivos del caso

- Objetivo general: automatizar la extracción, validación KYC/AML y enrutamiento de expedientes documentales con trazabilidad completa.
- Extraer automáticamente los campos clave de cada documento del expediente.
- Validar reglas KYC/AML y marcar inconsistencias en el set de prueba.
- Enrutar el expediente y generar alertas, con registro auditable de cada decisión.

## 6. Alcance funcional

**Sí se cubre:**

- Ingesta de documentos (IDs, comprobantes, contratos)
- Extracción de campos estructurados (Document AI/OCR)
- Validación KYC/AML por motor de reglas
- Detección de inconsistencias y campos faltantes
- Enrutamiento y alertas con trazabilidad

**No se cubre:**

- Conexión a sistemas core/onboarding reales
- Verificación biométrica
- Documentos con PII real
- Decisión final de alta del cliente

## 7. Descripción de la solución

La plataforma recibe el expediente y aplica Document AI/OCR para extraer texto y campos. Un módulo de NLP estructura la información (nombre, identificación, domicilio, montos). El motor de reglas valida cumplimiento KYC/AML (coincidencias, listas, completitud) y detecta inconsistencias entre documentos. Según el resultado, enruta el expediente (aprobado, revisión, rechazo) y dispara alertas. Cada paso queda registrado para auditoría.

## 8. Flujo funcional de la solución

1. Se cargan los documentos del expediente.
2. Document AI/OCR extrae texto y campos.
3. El módulo NLP estructura la información clave.
4. El motor de reglas valida KYC/AML y completitud.
5. Se detectan inconsistencias y campos faltantes.
6. La plataforma enruta el expediente y genera alertas.
7. Todo el proceso queda registrado para trazabilidad.

## 9. Datos requeridos

Expedientes simulados: imágenes/PDF de IDs ficticios, comprobantes y contratos, más listas de control sintéticas. Volumetría: 10–30 expedientes. Tratamiento: data ficticia, sin PII real. Campos clave: tipo_documento, campos_extraidos, flags_kyc, inconsistencias, ruta.

## 10. Stack tecnológico propuesto

| Capa | Tecnología propuesta | Justificación |
|---|---|---|
| Document AI/OCR | Tesseract / parser de documentos | Extracción de texto y campos |
| NLP/estructuración | spaCy / LLM | Normalización de campos |
| Motor de reglas | Python/JSON rules | Validación KYC/AML |
| Backend | FastAPI | Orquestación y enrutamiento |
| Observabilidad | Logging + tablero | Trazabilidad de cada decisión |
| Frontend | Streamlit | Visualización de expedientes y alertas |

## 11. Arquitectura de la solución

Pipeline de Document AI: Ingesta → OCR/extracción → estructuración NLP → motor de reglas KYC/AML → enrutador → alertas, con un log transversal de trazabilidad que alimenta un tablero de observabilidad. Punto de control: cada documento y cada validación quedan registrados con resultado y motivo.

## 12. Métricas de éxito e indicadores

| Métrica | Línea base | Objetivo del prototipo | Forma de medición | Tipo |
|---|---|---|---|---|
| Tiempo de procesamiento del expediente | días | minutos | Cronometría | Negocio |
| Exactitud de extracción de campos | manual | alta vs. ground truth | Comparación | Técnica |
| Inconsistencias detectadas | manual | cobertura del set | Pruebas | Técnica |
| Trazabilidad de decisiones | parcial | 100% registrada | Auditoría del log | Negocio |

## 13. Riesgos, supuestos y dependencias

| Riesgo / supuesto | Mitigación prevista |
|---|---|
| OCR de baja calidad en documentos | Preprocesar imágenes; validar muestras |
| Reglas KYC/AML incompletas | Co-diseñar con mentor de negocio |
| Variabilidad de formatos documentales | Acotar tipos en el PoC |
| Falsos positivos en alertas | Calibrar umbrales |

---

## Criterios de evaluación (rúbrica · 100 puntos)

| # | Criterio | Peso | Qué se evalúa |
|---|---|---|---|
| 1 | Impacto de Negocio | 10 | ¿Cuánto valor aporta? ¿Resuelve un pain actual? |
| 2 | Diseño Funcional | 25 | Qué lógicas de negocio sigue el diseño |
| 3 | Diseño Técnico | 15 | Seguridad, arquitectura, esquema de datos |
| 4 | Desarrollo de la solución | 25 | Backend / Frontend |
| 5 | Presentación y Storytelling | 25 | Claridad, narrativa y defensa ante el jurado |

**Hito de validación:** Procesamiento automático de expedientes simulados donde la plataforma identifique inconsistencias, complete campos faltantes y derive alertas.
