# Caso de Estudio — VitalisPharma Internacional

**Curso:** CD-01 · Arquitectura Empresarial con TOGAF® 10 · Proyecto Capstone
**Uso:** material base para que el estudiante construya, por sí mismo, las vistas del modelo ArchiMate (con scripts jArchi).

> Este dossier sigue una **plantilla de caso reutilizable**. La misma estructura (contexto → modelo de negocio → interesados → normas y regulaciones → panorama de sistemas → retos → objetivos → ejercicios) se emplea para el caso **Banco Digital Aurora** del curso **CD-02 · Arquitectura de Negocio con BIZBOK**. Cambia el dominio y las regulaciones; el método de trabajo es el mismo.

> **Nota:** VitalisPharma Internacional es una empresa **ficticia** creada con fines formativos. Las normas y regulaciones mencionadas son **reales**; el estudiante debe verificar siempre su versión vigente antes de usarlas en un contexto profesional.

---

## 1. Contexto de la empresa

VitalisPharma Internacional es un laboratorio farmacéutico multinacional con sede corporativa en Lima (Perú), operación comercial en 8 países de Latinoamérica y exportación a Estados Unidos y la Unión Europea. Bajo una misma empresa integra tres cadenas de valor:

- **Investigación, desarrollo y registro** de medicamentos.
- **Manufactura**, con dos plantas: una de **sólidos orales** (tabletas y cápsulas) y otra de **productos biológicos** que requieren **cadena de frío** (2–8 °C).
- **Distribución internacional**, a través de centros de distribución (CEDIS) propios y operadores logísticos terceros (3PL).

**Indicadores de referencia (ficticios, para dimensionar el caso):** ~3.200 colaboradores; 2 plantas y 5 CEDIS; ~400 SKU comercializados; presencia en 8 países; ~US$ 480 M de ingresos anuales.

**Contexto estratégico.** El directorio aprobó un **programa de transformación digital a 3 años**. La empresa no cuenta con una arquitectura empresarial formal previa y busca establecer la capacidad de arquitectura, un modelo de datos maestros único y una hoja de ruta gobernada.

---

## 2. Modelo de negocio y cadena de valor

**Propuesta de valor:** medicamentos seguros, trazables y disponibles, con cumplimiento regulatorio en cada mercado.

**Segmentos de cliente:** hospitales y clínicas, cadenas de farmacias, distribuidores mayoristas, compras públicas (Estado) y, en algunos mercados, pacientes vía canales autorizados.

**Cadena de valor (extremo a extremo):**

Investigar y registrar → Planificar y abastecer → **Fabricar** → **Controlar calidad y liberar** → **Serializar** → **Almacenar y distribuir (cadena de frío)** → Comercializar y facturar → **Farmacovigilancia y postventa**.

El **alcance del Capstone** se acota al segmento *"del lote fabricado al producto entregado y trazado"*, que cubre manufactura, calidad, serialización, cadena de frío y distribución internacional.

---

## 3. Interesados (stakeholders) y sus preocupaciones

| Interesado | Principales preocupaciones (concerns) |
|---|---|
| Directorio / CEO | Crecimiento internacional, rentabilidad, riesgo regulatorio y reputacional |
| Dirección de Operaciones / Manufactura | Eficiencia productiva, cumplimiento GMP, mermas |
| Asuntos Regulatorios / Calidad (QA/QC) | Registros vigentes, cumplimiento GMP/GDP, integridad de datos, auditorías |
| Cadena de Suministro / Logística | Continuidad de suministro, cadena de frío, quiebres de stock |
| Dirección de TI / Arquitectura | Integración de sistemas, datos maestros, seguridad de la información |
| Comercial / Clientes y Distribuidores | Disponibilidad, tiempos de entrega, trazabilidad del producto |
| Entes reguladores | Seguridad, eficacia, trazabilidad y farmacovigilancia del producto |

---

## 4. Normas y regulaciones aplicables

Este es el marco normativo que el estudiante debe reflejar en las vistas de **Motivación** (como *drivers*, *assessments*, *requirements*, *constraints*) y de **Negocio/Aplicación** (como capacidades y servicios de cumplimiento).

### 4.1 Manufactura y calidad
- **BPM / GMP (Buenas Prácticas de Manufactura):** OMS GMP; **FDA 21 CFR Parts 210/211** (EE. UU.); **EU GMP – EudraLex Volumen 4**; en Perú, supervisión de **DIGEMID**.
- **ICH Q7** (GMP para ingredientes farmacéuticos activos), **ICH Q9** (Gestión de Riesgos de Calidad), **ICH Q10** (Sistema de Calidad Farmacéutica).
- **ISO 9001** (gestión de calidad) como marco complementario.

### 4.2 Distribución y cadena de frío
- **BPD / GDP (Buenas Prácticas de Distribución):** **EU GDP – 2013/C 343/01**; **OMS GDP**.
- **Cadena de frío:** OMS – Technical Report Series (TRS) para almacenamiento y distribución con control de temperatura; requisitos de monitoreo continuo (2–8 °C para biológicos).

### 4.3 Serialización y trazabilidad (track & trace)
- **EE. UU.: DSCSA** (Drug Supply Chain Security Act).
- **UE: FMD** (Falsified Medicines Directive **2011/62/EU**) y su **Reglamento Delegado (UE) 2016/161** (identificador único y dispositivo antimanipulación; verificación en el **EMVS/NMVS**).
- **Estándares GS1:** **GTIN**, **SGTIN**, **GLN**, **SSCC** y **EPCIS** para el registro de eventos de trazabilidad.

### 4.4 Registro sanitario (acceso a mercados)
- **ICH CTD** (Common Technical Document) para el dossier de registro.
- Agencias por mercado: **DIGEMID** (Perú), **INVIMA** (Colombia), **ANMAT** (Argentina), **COFEPRIS** (México), **FDA** (EE. UU.), **EMA** (UE).

### 4.5 Datos, sistemas y ciberseguridad
- **Integridad de datos – ALCOA+** (Atribuible, Legible, Contemporáneo, Original, Exacto, y +).
- **FDA 21 CFR Part 11** (registros y firmas electrónicas); **EU GMP Annex 11** (sistemas computarizados).
- **Protección de datos personales:** **GDPR** (UE) y, en Perú, **Ley N.° 29733**.
- **Seguridad de la información:** **ISO/IEC 27001**.

### 4.6 Farmacovigilancia
- **ICH E2E** y **Buenas Prácticas de Farmacovigilancia (GVP)** de la UE; reporte de eventos adversos a las autoridades de cada mercado.

> **Cómo se traduce a ArchiMate:** una regulación suele modelarse como **Driver** ("Cumplimiento regulatorio") y/o **Requirement** ("Serialización GS1", "Monitoreo de cadena de frío") y, cuando limita el diseño, como **Constraint** ("Regulaciones locales por país"). Las capacidades de cumplimiento (p. ej. "Gestión de Cumplimiento GMP/GDP") se modelan en la capa de **negocio/estrategia**.

---

## 5. Panorama de sistemas (para las vistas de Aplicación y Tecnología)

| Sistema | Función | Observación |
|---|---|---|
| ERP (p. ej. SAP) | Finanzas, compras, inventario, ventas | Instancias distintas por país (fragmentado) |
| MES | Ejecución de manufactura | Por planta |
| LIMS | Gestión de laboratorio y ensayos de calidad | — |
| QMS | Desviaciones, CAPA, cambios, auditorías | — |
| WMS / TMS | Almacenes y transporte | 3PL en algunos mercados |
| Plataforma de Serialización | Números de serie, agregación, reportes DSCSA/FMD | A implementar/consolidar |
| Plataforma IoT de cadena de frío | Sensores y alertas de temperatura | A implementar |
| RIM | Gestión de información regulatoria y registros | — |
| CRM | Clientes, pedidos, distribuidores | — |
| BI / Analítica | Reportes e indicadores | Datos no unificados |

**Problema transversal:** ausencia de **datos maestros únicos** (producto, lote, cliente, ubicación) e integraciones punto a punto frágiles entre MES, WMS y ERP.

---

## 6. Retos actuales (assessments)

- Sistemas heredados y **fragmentados** entre países.
- **Mermas** y **quiebres de stock** por fallas en la cadena de frío y planificación aislada.
- Presión por cumplir **plazos de serialización** en mercados regulados.
- **Tiempos de liberación** de producto elevados (calidad manual).
- **Recall/retiro** de lote lento por trazabilidad incompleta.

---

## 7. Objetivos y resultados esperados (resumen)

Metas: trazabilidad serializada extremo a extremo; cumplimiento regulatorio sostenido; reducir mermas y quiebres; visibilidad de inventario en tiempo real; habilitar el crecimiento internacional.

Resultados esperados (outcomes): mermas por cadena de frío −30%; trazabilidad 100% de lotes exportados; quiebres de stock −25%; tiempo de liberación −40%; cobertura internacional +3 países; auditorías aprobadas sin observaciones; recall < 24 h.

*(Estos elementos ya están modelados en la vista de Motivación de referencia.)*

---

## 8. Ejercicios — el estudiante genera sus scripts ArchiMate

Cada ejercicio se resuelve escribiendo un **script jArchi** (menú *Scripts* en Archi) que crea o amplía una vista. Trabaje siempre sobre el modelo **Capstone - VitalisPharma** seleccionado en el árbol.

1. **Motivación (Fase A).** Tome la vista de referencia y **añada** un nuevo *driver* ("Sostenibilidad ambiental – ISO 14001") con su *goal*, *requirement* y *outcome*, enlazados correctamente.
2. **Capacidades L1/L2 (Fase B).** Agregue la capacidad L1 **"Farmacovigilancia"** con sus L2 ("Gestión de Eventos Adversos", "Reporte a Autoridades") y mencione sus objetos de negocio en la descripción.
3. **Vista Estratégica.** Añada una nueva iniciativa (curso de acción) y enlácela: *desarrolla* → capacidad, *contribuye a* → resultado, *realiza* → meta.
4. **Value Stream (Fase B).** Modele el flujo *"del lote al producto entregado y trazado"* con sus etapas (*value stream stages*) y mapéelas a las capacidades.
5. **Aplicaciones (Fase C).** Modele los componentes (ERP, MES, WMS, Serialización, IoT) y sus *application services*; relacione cada servicio con la capacidad/proceso que soporta.
6. **Tecnología (Fase D).** Modele nodos, servicios de nube, sensores IoT y la red que conecta plantas y CEDIS.

**Criterios de calidad esperados:** uso correcto de la notación ArchiMate; trazabilidad entre capas; cobertura de las regulaciones aplicables; y coherencia con el ADM.

---

## 9. Chuleta jArchi (para escribir los scripts)

```javascript
// Modelo destino: usar el modelo seleccionado en el arbol
var m = (typeof model !== "undefined" && model) ? model
        : $.model.create("Capstone - VitalisPharma Internacional");

// Crear una vista
var view = m.createArchimateView("Nombre de la vista");

// Crear un elemento (tipos en minusculas con guiones)
var e = m.createElement("driver", "Cumplimiento regulatorio");
e.documentation = "Descripcion del elemento...";

// Colocar el elemento en la vista (x, y, ancho, alto) -> objeto de diagrama
var dobj = view.add(e, 20, 40, 200, 55);

// Crear una relacion y dibujarla entre dos objetos de diagrama
var rel = m.createRelationship("influence-relationship", "", e, otroElemento);
view.add(rel, dobj, otroDobj);

// Notas (etiquetas) y grupos (franjas)
var nota  = view.createObject("note",  20, 10, 220, 40); nota.text = "TITULO";
var franja = view.createObject("group", 20, 70, 1000, 300); franja.name = "ESTRATEGICA";

// Anidar un elemento dentro de otro objeto de diagrama
var hijo = dobj.add(otroElemento, 10, 46, 200, 34);

// Mostrar en la UI (clave para que la vista/modelo aparezcan)
if (typeof view.openInUI === "function") view.openInUI();
```

**Tipos de elemento frecuentes:** `stakeholder`, `driver`, `assessment`, `goal`, `outcome`, `requirement`, `constraint`, `principle`, `capability`, `course-of-action`, `resource`, `value-stream`, `business-actor`, `business-role`, `business-process`, `business-service`, `business-object`, `application-component`, `application-service`, `data-object`, `node`, `technology-service`, `system-software`, `device`.

**Tipos de relación frecuentes:** `association-relationship`, `influence-relationship`, `realization-relationship`, `serving-relationship`, `assignment-relationship`, `aggregation-relationship`, `composition-relationship`, `access-relationship`, `flow-relationship`, `triggering-relationship`.

> **Regla práctica:** si una relación no es válida entre dos tipos, jArchi lanza *"Invalid relationship…"* y detiene el script. Ante la duda, use `association-relationship` (siempre válida) o pruebe la relación dentro de un `try { … } catch(e) { … }`.

---

*CPS Tech · www.cps-tech.com · capacitaciones@cps-tech.com*
