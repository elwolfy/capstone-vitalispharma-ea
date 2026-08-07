# Capstone TOGAF 10 — VitalisPharma Internacional

Repositorio del **modelo de Arquitectura Empresarial** del proyecto Capstone del curso
**CD-01 · Arquitectura Empresarial con TOGAF® 10** (Programa Integral de Arquitectura Empresarial · **CPS Tech**).

El modelo se construye en **[Archi](https://www.archimatetool.com/)** y se colabora sobre este repositorio Git
mediante el plugin **coArchi**. Aquí practicaremos las tres operaciones del trabajo colaborativo:
**Sincronizar**, **Commit** (Publicar) y **Actualizar** (Refresh).

---

## Caso de estudio

El caso completo del proyecto —**contexto de la empresa, modelo de negocio, interesados, normas y
regulaciones aplicables, panorama de sistemas, retos y objetivos**— está en:

**➡ [CASO_VitalisPharma_Internacional.md](CASO_VitalisPharma_Internacional.md)**

Ese documento incluye además una **serie de ejercicios** para que cada estudiante **genere sus propios
scripts ArchiMate** (con una chuleta de la API jArchi). Sigue una **plantilla reutilizable**: la misma
estructura se usa para el caso **Banco Digital Aurora** del curso **CD-02 · Arquitectura de Negocio con BIZBOK**.

**Resumen del caso:** VitalisPharma Internacional es un laboratorio farmacéutico multinacional (sede en Lima;
operación en 8 países; exporta a EE. UU. y Europa) que integra investigación/registro, **manufactura**
(sólidos orales y biológicos refrigerados) y **distribución internacional**. Enfrenta exigencias de
cumplimiento (GMP/GDP, serialización DSCSA/FMD, cadena de frío, integridad de datos) y ejecuta un programa
de transformación digital a 3 años. El alcance del Capstone es el segmento *"del lote fabricado al producto
entregado y trazado"*.

---

## 1. Requisitos previos

| Herramienta | Para qué |
|---|---|
| Archi | Modelado ArchiMate — https://www.archimatetool.com/download |
| jArchi | Ejecutar los scripts `.ajs` (se instala dentro de Archi) |
| coArchi | Colaboración Git de modelos (se instala dentro de Archi) |
| Cuenta GitHub | Alojar el repositorio — https://github.com |
| Personal Access Token (PAT) | Autenticación al hacer push/pull (ver §5) |

### Instalar coArchi / jArchi en Archi
1. Abra Archi -> menu **Help > Manage Plug-ins... > Install New**.
2. Seleccione el archivo `.archiplugin` del plugin e instale.
3. Reinicie Archi. Active la vista **Collaboration** (coArchi) y el menu **Scripts** (jArchi).

---

## 2. Obtener el modelo por primera vez (clonar)

1. En Archi, abra el panel **Collaboration**.
2. Boton **"Add a Model from Online Repository"**.
3. Pegue la URL del repositorio (la comparte el instructor), por ejemplo:
   `https://github.com/<usuario>/capstone-vitalispharma-ea.git`
4. Ingrese su **usuario de GitHub** y, como contrasena, su **Personal Access Token** (ver §5).
5. Elija una carpeta local. Archi descargara el modelo y lo abrira.

> El modelo inicial contiene las vistas de **Motivacion**, **Capacidades (L1/L2)** y **Estrategica**.

---

## 3. Las tres operaciones que practicaremos

| Operacion | Boton en coArchi | Que hace | Cuando usarla |
|---|---|---|---|
| **Actualizar (Refresh)** | Refresh | Trae los cambios del remoto y los combina con su copia local | **Al empezar**, antes de editar |
| **Commit** | Commit | Guarda una "foto" de sus cambios en el historial local (con un mensaje) | Cada cambio significativo |
| **Sincronizar (Publish)** | Publish / Sync | Envia sus commits al remoto y trae los de los demas (commit + push + pull) | **Al terminar** un bloque de trabajo |

**Flujo recomendado en clase**
1. **Actualizar (Refresh)** -> parto de la ultima version.
2. Editar el modelo en Archi (o ejecutar un script jArchi).
3. **Commit** -> describo mi cambio.
4. **Sincronizar (Publish)** -> comparto con el equipo.

> Regla de oro: **Actualizar antes de editar** y **Sincronizar al terminar**. Asi se evitan conflictos.

---

## 4. Scripts jArchi incluidos (carpeta scripts/)

| Script | Vista que genera |
|---|---|
| `Capstone_VitalisPharma_Vista_Motivacion.ajs` | Vista de Motivacion (Fase A) por columnas |
| `Capstone_VitalisPharma_Vista_Capacidades.ajs` | Mapa de Capacidades Nivel 1 y Nivel 2 (Fase B) |
| `Capstone_VitalisPharma_Vista_Estrategica.ajs` | Vista Estrategica: Iniciativas > Capacidades > Resultados > Metas |

Ejecucion: menu **Scripts** en Archi, con el modelo Capstone seleccionado en el arbol.

---

## 5. Crear un Personal Access Token (PAT) en GitHub
GitHub ya no acepta contrasena para git por HTTPS; se usa un token.
1. GitHub -> **Settings > Developer settings > Personal access tokens > Tokens (classic)**.
2. **Generate new token** -> marque el alcance **`repo`**.
3. Copie el token (empieza con `ghp_...`) y uselo como **contrasena** en Archi/coArchi.

---

## Estructura del repositorio
```
capstone-vitalispharma-ea/
|- README.md                              <- esta guia (estudiantes)
|- CASO_VitalisPharma_Internacional.md    <- dossier del caso + ejercicios + chuleta jArchi
|- GUIA_INSTRUCTOR.md                     <- preparacion del repo y publicacion inicial
|- .gitignore
|- scripts/                               <- scripts jArchi de referencia
\- model/                                 <- lo crea coArchi al publicar el modelo
```

---
*CPS Tech · www.cps-tech.com · capacitaciones@cps-tech.com*
