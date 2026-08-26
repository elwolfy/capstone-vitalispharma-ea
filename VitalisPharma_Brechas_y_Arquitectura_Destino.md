# VitalisPharma Internacional — Análisis de Brechas y Arquitectura Destino

**Programa Integral de Arquitectura Empresarial · TOGAF® 10 (Fases B, C, D → E) · Capstone** **Reto 6 — Retos actuales (assessments): brechas por dominio, arquitectura objetivo y matriz de brechas TOGAF** **Caso base:** VitalisPharma Internacional (farmacéutica multinacional, sede Lima; 8 países LATAM \+ exportación US/EU; 2 plantas, 5 CEDIS, \~400 SKUs, \~US$480M).

---

## 1\. Contexto y motivación (resumen del caso)

VitalisPharma ejecuta un **programa de transformación digital a 3 años** para lograr «medicamentos seguros, trazables y disponibles, con cumplimiento regulatorio», estableciendo una **capacidad de arquitectura**, un **modelo de datos maestros único** y una **hoja de ruta gobernada**.

**Drivers estratégicos:** cumplimiento regulatorio sostenido · crecimiento internacional y rentabilidad · reducción de riesgo regulatorio y reputacional · trazabilidad serializada extremo a extremo.

**Metas / KPIs objetivo:**

| Meta (outcome) | Objetivo |
| :---- | :---- |
| Mermas por cadena de frío | −30 % |
| Trazabilidad de lotes exportados | 100 % |
| Quiebres de stock | −25 % |
| Tiempo de liberación de producto | −40 % |
| Tiempo de recall (retiro) | \< 24 h |
| Cobertura geográfica | \+3 países |

**Marco regulatorio aplicable:** GMP/GDP (FDA 21 CFR 210/211, EU EudraLex Vol. 4), serialización (DSCSA, EU FMD 2016/161), cadena de frío (WHO TRS), integridad de datos (ALCOA+, 21 CFR Part 11, EU GMP Annex 11), farmacovigilancia (ICH E2E, GVP).

**Alcance del capstone (value stream):** *«del lote fabricado al producto entregado y trazado»* — Investigar y registrar → Planificar y abastecer → Fabricar → Controlar calidad y liberar → Serializar → Almacenar y distribuir (cadena de frío) → Comercializar y facturar → Farmacovigilancia.

---

## 2\. Estado actual (Baseline / AS-IS) y dolores

**Sistemas actuales:** ERP (SAP) *fragmentado por país* · MES *por planta* · LIMS · QMS · WMS/TMS (con 3PL) · Plataforma de serialización *por implementar/consolidar* · IoT cadena de frío *por implementar* · RIM · CRM · BI/Analytics *con datos fragmentados*.

**Problema núcleo:** ausencia de **datos maestros únicos** (producto, lote, cliente, ubicación) e **integraciones punto a punto frágiles** entre MES, WMS y ERP.

**Dolores (retos actuales):** sistemas heredados y fragmentados entre países · mermas y quiebres por fallas en la cadena de frío y planificación aislada · presión por plazos de serialización · tiempos de liberación largos por controles manuales · recall lento por visibilidad de lote incompleta.

---

## 3\. Análisis de brechas por dominio de arquitectura

> Convención: cada brecha tiene un **ID** (dominio \+ número), su **estado actual**, el **estado objetivo (TO-BE)** y el **tipo TOGAF** — **Nueva** (elemento inexistente a crear), **Mejorar** (elemento existente a evolucionar) o **Eliminar** (elemento a retirar/reemplazar).

### 3.1 Arquitectura de Negocio (Fase B)

| ID | Estado actual (AS-IS) | Estado objetivo (TO-BE) | Tipo |
| :---- | :---- | :---- | :---- |
| **B1** | Planificación de demanda/abastecimiento **aislada por país** | Capacidad de **Planificación integrada (S\&OP)** multi-país | Nueva |
| **B2** | Liberación de calidad **manual**, tiempos largos | **Liberación por excepción** (review-by-exception) automatizada | Mejorar |
| **B3** | Gestión de cadena de frío **reactiva** | **Cadena de frío proactiva** (monitoreo y alertas) | Mejorar |
| **B4** | Serialización **parcial / no consolidada** | Capacidad de **Serialización y trazabilidad E2E** (track & trace) | Nueva |
| **B5** | Recall **lento** por visibilidad de lote incompleta | Capacidad de **Recall rápido \< 24 h** con genealogía de lote | Mejorar |
| **B6** | **Sin gobierno** de datos maestros | Capacidad de **Gobierno de Datos Maestros** (producto, lote, cliente, ubicación) | Nueva |
| **B7** | Farmacovigilancia operativa pero **desconectada** | **Farmacovigilancia integrada** al ciclo de calidad y trazabilidad | Mejorar |

### 3.2 Arquitectura de Datos (Fase C — Datos)

| ID | Estado actual (AS-IS) | Estado objetivo (TO-BE) | Tipo |
| :---- | :---- | :---- | :---- |
| **D1** | **Sin datos maestros únicos**; entidades duplicadas por país | **Modelo de Datos Maestros (MDM)**: producto, lote, cliente, ubicación | Nueva |
| **D2** | Trazabilidad de lote **incompleta**, sin genealogía | Entidad **Lote/Serie** trazable E2E con **genealogía** (padre-hijo) | Nueva |
| **D3** | Telemetría de temperatura **no persistida/integrada** | **Datos de cadena de frío** (IoT) integrados y consultables | Nueva |
| **D4** | Integridad de datos **no asegurada** de extremo a extremo | **Integridad ALCOA+ / 21 CFR Part 11** (registros y firmas electrónicas) | Mejorar |
| **D5** | BI con **fuentes de datos fragmentadas** | **Repositorio analítico unificado** (data warehouse/lakehouse) | Nueva |
| **D6** | **Sin gobierno** ni linaje de datos | **Gobierno de datos y linaje** (data governance / lineage) | Nueva |

### 3.3 Arquitectura de Aplicaciones (Fase C — Aplicaciones)

| ID | Estado actual (AS-IS) | Estado objetivo (TO-BE) | Tipo |
| :---- | :---- | :---- | :---- |
| **A1** | Plataforma de serialización **inexistente/dispersa** | **Plataforma de Serialización** consolidada (aggregation, reporte DSCSA/FMD) | Nueva |
| **A2** | Sin solución de monitoreo de frío | **Solución IoT de cadena de frío** (monitoreo y alertas) | Nueva |
| **A3** | Datos maestros dispersos en cada sistema | **Aplicación MDM** (gestión y distribución de maestros) | Nueva |
| **A4** | Integraciones **punto a punto frágiles** MES–WMS–ERP | **Capa de integración API-led / microservicios** (iPaaS/ESB) | Mejorar |
| **A5** | **ERP (SAP) fragmentado** por país | **ERP armonizado** (template único multi-país) | Mejorar |
| **A6** | **BI/Analytics fragmentado** | **BI/Analytics unificado** sobre datos consolidados | Mejorar |
| **A7** | Sin repositorio de trazabilidad | **Track & Trace** (repositorio de eventos de trazabilidad) | Nueva |

### 3.4 Arquitectura de Tecnología (Fase D)

| ID | Estado actual (AS-IS) | Estado objetivo (TO-BE) | Tipo |
| :---- | :---- | :---- | :---- |
| **T1** | Sin plataforma de integración; conexiones directas | **iPaaS / API Gateway** y mensajería gobernada | Nueva |
| **T2** | Sin infraestructura IoT | **Plataforma IoT** (gateways, conectividad, ingesta de telemetría) | Nueva |
| **T3** | Infraestructura **heredada por país**, poco escalable | **Nube híbrida** escalable multi-país | Mejorar |
| **T4** | Sin plataforma de datos | **Plataforma de datos** (lakehouse) y servicios de MDM | Nueva |
| **T5** | Seguridad/cumplimiento **inconsistente** | **Seguridad transversal**: IAM, cifrado, Part 11 / Annex 11 | Mejorar |
| **T6** | Observabilidad y continuidad **limitadas** | **Observabilidad y DR** de servicios críticos (frío, serialización) | Nueva |

---

## 4\. Blueprint de la Arquitectura Destino (TO-BE)

La arquitectura objetivo cierra las brechas anteriores con una plataforma **integrada, gobernada y trazable de extremo a extremo**, organizada en cuatro capas coherentes con TOGAF y trazables a los KPIs.

**Capa de Motivación.** Los *drivers* (cumplimiento, crecimiento, reducción de mermas/quiebres) y las metas (KPIs) originan **requerimientos por capa**, que se realizan mediante los elementos de negocio, aplicación y tecnología.

**Capa de Negocio.** El value stream *«del lote al producto entregado y trazado»* se soporta en las **capacidades objetivo**: Planificación integrada (S\&OP), Liberación por excepción, Cadena de frío proactiva, Serialización y trazabilidad E2E, Recall rápido, Gobierno de Datos Maestros y Farmacovigilancia integrada.

**Capa de Aplicaciones.** Un núcleo de aplicaciones especializadas —**MDM**, **Plataforma de Serialización**, **IoT Cold Chain**, **Track & Trace**, **ERP armonizado (SAP)**, **MES**, **LIMS**, **QMS**, **WMS/TMS** y **BI unificado**— se comunica a través de una **capa de integración API-led / microservicios** (fin de las conexiones punto a punto). Los **objetos de datos** clave (Producto, Lote/Serie, Cliente, Ubicación, Telemetría) se gestionan como maestros compartidos.

**Capa de Tecnología.** Todo se ejecuta sobre una **nube híbrida escalable**, con **iPaaS / API Gateway**, **Plataforma IoT**, **Plataforma de Datos (lakehouse)**, **Seguridad transversal (IAM, cifrado, Part 11/Annex 11\)** y **Observabilidad y DR**.

> Las dos vistas ArchiMate que acompañan este documento representan (a) la **vista de brechas — requerimientos por capa** y (b) el **blueprint de la arquitectura destino**.

---

## 5\. Matriz de Brechas según TOGAF (Gap Analysis Matrix)

TOGAF propone construir la matriz de brechas cruzando los **bloques de arquitectura del estado actual (Baseline)** en las **filas** con los del **estado objetivo (Target)** en las **columnas**. Se añaden:

- una **columna "Eliminado"** para los bloques baseline que se retiran o reemplazan intencionalmente, y  
- una **fila "Nuevo"** para los bloques target que no tienen contraparte en el baseline (brechas a llenar).

Una celda de **intersección (match)** \= bloque **retenido/evolucionado**; un cruce con la fila **Nuevo** \= **brecha (elemento nuevo)**; un cruce con la columna **Eliminado** \= elemento **retirado**. Las omisiones no intencionales (celdas vacías que deberían tener match) son también brechas.

### 5.1 Matriz TOGAF consolidada (nivel de bloques de arquitectura)

Leyenda de celdas: **R** \= Retenido · **M** \= Mejorado/evolucionado · **N** \= Nuevo (brecha) · **X** \= Eliminado/reemplazado.

| Baseline ↓ \\ Target → | ERP armon. | MDM | Serialización | IoT Frío | Track & Trace | Integración API | BI unificado | Data Platform | Seguridad Part 11 | Eliminado |
| :---- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **ERP (SAP) fragmentado** | M |  |  |  |  |  |  |  |  |  |
| **MES por planta** |  |  |  |  |  | R |  |  |  |  |
| **LIMS / QMS** |  |  |  |  |  | R |  |  |  |  |
| **WMS/TMS (+3PL)** |  |  | R |  |  | R |  |  |  |  |
| **BI/Analytics fragmentado** |  |  |  |  |  |  | M |  |  |  |
| **Integraciones punto a punto** |  |  |  |  |  |  |  |  |  | **X** |
| **(sin serialización)** |  |  | N |  |  |  |  |  |  |  |
| **(sin IoT frío)** |  |  |  | N |  |  |  |  |  |  |
| **(sin datos maestros)** |  | N |  |  |  |  |  |  |  |  |
| **(sin trazabilidad E2E)** |  |  |  |  | N |  |  |  |  |  |
| **(sin plataforma de datos)** |  |  |  |  |  |  |  | N |  |  |
| **(seguridad inconsistente)** |  |  |  |  |  |  |  |  | N/M |  |
| **Fila NUEVO (target sin baseline)** |  | ✔ | ✔ | ✔ | ✔ | ✔ |  | ✔ | ✔ |  |

**Lectura de la matriz:**

- **Retenidos/Mejorados (R/M):** ERP (armonizar), MES, LIMS/QMS y WMS/TMS se conservan y se **integran** vía la nueva capa API; BI se **unifica**.  
- **Eliminado (X):** las **integraciones punto a punto** MES–WMS–ERP se **reemplazan** por la capa de integración gobernada.  
- **Nuevos (N):** MDM, Plataforma de Serialización, IoT de cadena de frío, Track & Trace, Plataforma de Datos y Seguridad Part 11 — **no existen en el baseline** y constituyen las brechas principales a cubrir.

### 5.2 Registro de brechas accionable (trazable a KPIs y fases del ADM)

| ID | Dominio | Brecha (resumen) | Tipo | Requerimiento objetivo | KPI impactado | Fase ADM |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| B1 | Negocio | Planificación aislada por país | Nueva | S\&OP integrado | Quiebres −25 % | B |
| B2 | Negocio | Liberación manual y lenta | Mejorar | Liberación por excepción | Liberación −40 % | B |
| B3 | Negocio | Cadena de frío reactiva | Mejorar | Cadena de frío proactiva | Mermas −30 % | B |
| B4 | Negocio | Serialización no consolidada | Nueva | Serialización/trazabilidad E2E | Trazabilidad 100 % | B |
| B5 | Negocio | Recall lento | Mejorar | Recall \< 24 h | Recall \< 24 h | B |
| B6 | Negocio | Sin gobierno de maestros | Nueva | Gobierno de Datos Maestros | Trazabilidad 100 % | B |
| D1 | Datos | Sin datos maestros únicos | Nueva | MDM (producto, lote, cliente, ubicación) | Trazabilidad 100 % | C |
| D2 | Datos | Trazabilidad de lote incompleta | Nueva | Genealogía de Lote/Serie | Recall \< 24 h | C |
| D3 | Datos | Telemetría no integrada | Nueva | Datos de cadena de frío | Mermas −30 % | C |
| D4 | Datos | Integridad no asegurada | Mejorar | ALCOA+ / Part 11 | Trazabilidad 100 % | C |
| D5 | Datos | BI fragmentado | Nueva | Repositorio analítico unificado | (todos) | C |
| A1 | Aplic. | Sin plataforma de serialización | Nueva | Plataforma de Serialización | Trazabilidad 100 % | C |
| A2 | Aplic. | Sin monitoreo de frío | Nueva | Solución IoT Cold Chain | Mermas −30 % | C |
| A3 | Aplic. | Maestros dispersos | Nueva | Aplicación MDM | Trazabilidad 100 % | C |
| A4 | Aplic. | Integraciones punto a punto | Mejorar/Eliminar | Capa de integración API-led | Liberación −40 % | C |
| A5 | Aplic. | ERP fragmentado | Mejorar | ERP armonizado multi-país | Quiebres −25 % | C |
| A6 | Aplic. | BI/Analytics fragmentado | Mejorar | BI unificado | (todos) | C |
| A7 | Aplic. | Sin repositorio de trazabilidad | Nueva | Track & Trace | Trazabilidad 100 % | C |
| T1 | Tecnol. | Sin plataforma de integración | Nueva | iPaaS / API Gateway | Liberación −40 % | D |
| T2 | Tecnol. | Sin infraestructura IoT | Nueva | Plataforma IoT | Mermas −30 % | D |
| T3 | Tecnol. | Infraestructura heredada | Mejorar | Nube híbrida escalable | \+3 países | D |
| T4 | Tecnol. | Sin plataforma de datos | Nueva | Data platform (lakehouse) | (todos) | D |
| T5 | Tecnol. | Seguridad inconsistente | Mejorar | IAM, cifrado, Part 11/Annex 11 | Trazabilidad 100 % | D |
| T6 | Tecnol. | Observabilidad/continuidad limitada | Nueva | Observabilidad y DR | Recall \< 24 h | D |

---

## 6\. Conclusión y siguiente paso (Fase E)

El análisis muestra que el mayor peso de las brechas es **estructural**: la ausencia de **datos maestros** y de una **capa de integración gobernada** es la causa raíz de los dolores de trazabilidad, liberación y cadena de frío. La arquitectura destino resuelve esto con un **núcleo MDM \+ integración API-led**, sobre el que se apoyan las capacidades nuevas de **serialización, IoT de frío y track & trace**.

En la **Fase E (Oportunidades y Soluciones)** estas brechas se agrupan en **work packages** y **arquitecturas de transición** (p. ej. *Plateau 1: MDM \+ integración*; *Plateau 2: serialización y track & trace*; *Plateau 3: IoT de cadena de frío*), priorizados por valor de negocio en la **Fase F**.

---

## Anexo metodológico — Cómo se identificaron las brechas

*Respuesta a la pregunta: «¿cómo se identifican las brechas, qué técnicas se aplican y cómo se elaboraron los cuadros 3.1, 3.2, 3.3 y 3.4?».*

### A.1 El principio: análisis de brechas (gap analysis) de TOGAF

El *gap analysis* es una **técnica formal del ADM** que se aplica una vez por dominio en las **Fases B, C y D** y se consolida en la **Fase E**. Su lógica es una resta: **estado objetivo (Target / TO-BE) menos estado actual (Baseline / AS-IS)**. Cada diferencia es una **brecha**, y cada brecha se convierte después en un componente del *roadmap* (work package de la Fase E). Ninguna brecha se "inventa": todas se derivan de esa comparación, dominio por dominio.

TOGAF lo formaliza en una **matriz** (sección 5.1): bloques del baseline en las filas, bloques del target en las columnas, más una **columna "Eliminado"** y una **fila "Nuevo"**. La coincidencia baseline↔target \= elemento retenido o mejorado; un objetivo sin contraparte \= fila "Nuevo" (brecha a construir); un baseline sin destino \= columna "Eliminado".

### A.2 Técnicas aplicadas para descubrir las brechas

La matriz es el *registro*; las brechas se *descubren* con técnicas complementarias, todas usadas sobre el caso VitalisPharma:

| Técnica | Qué aporta | Ejemplo en el caso |
| :---- | :---- | :---- |
| **Comparación Baseline vs Target por dominio** | Método base de las Fases B/C/D | Negocio, datos, aplicaciones y tecnología descritos AS-IS y TO-BE |
| **Análisis de *assessments* (dolores)** del modelo de motivación | Cada diagnóstico es la raíz de una brecha | «Sistemas heredados y fragmentados»; «Fallas en la cadena de frío» |
| **Descomposición Driver → Goal → Requirement** | Un requerimiento no satisfecho \= brecha | Requerimiento «Serialización y track & trace (GS1)» sin plataforma actual |
| **Evaluación de capacidades (BIZBOK / heat map)** | Madurez actual vs requerida por capacidad | Planificación aislada → S\&OP integrado; liberación manual → por excepción |
| **Brecha de KPI / outcome** | Meta cuantitativa vs desempeño actual | Liberación −40 %, mermas −30 %, recall \< 24 h |
| **Checklist de cumplimiento regulatorio** | Cada exigencia no cubierta es una brecha | 21 CFR Part 11 (integridad/firmas), serialización DSCSA/FMD, GMP/GDP |
| **Análisis de interoperabilidad** | Integraciones frágiles \= brecha estructural | Punto a punto MES–WMS–ERP → capa de integración |

En un proyecto real, el conjunto se **valida en talleres con los interesados** (Directorio, QA, Operaciones, TI) antes de cerrarlo.

### A.3 Cómo se construyó cada cuadro (3.1–3.4)

Los cuatro cuadros siguen la **estructura por dominios de arquitectura de TOGAF** (por eso hay uno de Negocio-Fase B, uno de Datos y otro de Aplicaciones-Fase C, y uno de Tecnología-Fase D) y comparten las mismas cuatro columnas — **ID · Estado actual (AS-IS) · Estado objetivo (TO-BE) · Tipo** — llenadas con estas fuentes:

- **Columna AS-IS:** del caso (sección 6 — retos), el *landscape* de sistemas actual y las vistas AS-IS existentes del modelo (aplicaciones monolíticas, objetos de datos por sistema, topología on-premise).  
- **Columna TO-BE:** de los objetivos estratégicos, los KPIs, los requerimientos de la vista de motivación (serialización, IoT, integración, inventario unificado, planificación integrada) y los principios (*datos maestros únicos*).  
- **Columna Tipo:** clasifica cada brecha con una regla explícita —  
  - **Nueva** — no existe contraparte en el baseline (MDM, serialización, IoT de frío, track & trace, plataforma de datos).  
  - **Mejorar** — existe pero fragmentado/manual/reactivo (ERP fragmentado → armonizado; liberación manual → por excepción; frío reactivo → proactivo).  
  - **Eliminar / Reemplazar** — se retira intencionalmente (integraciones punto a punto → capa de integración gobernada).

Finalmente, cada brecha se **traza a un KPI y a la fase del ADM** (registro accionable 5.2), de modo que toda brecha responde a un driver o una meta del negocio.

### A.4 Síntesis en una frase (para el aula)

> Las brechas no se "inventan": se **derivan restando** el estado objetivo (que sale de drivers, metas, requerimientos y principios) menos el estado actual (que sale del caso y de las vistas AS-IS), **dominio por dominio**, y **clasificando** cada diferencia como *nueva*, *a mejorar* o *a eliminar*. La causa raíz que emerge —ausencia de datos maestros e integración frágil— es la que ordena la arquitectura destino.

---

*Elaborado para el Capstone del Programa Integral de Arquitectura Empresarial — CPS Tech · TOGAF® 10 · notación ArchiMate®.*  
