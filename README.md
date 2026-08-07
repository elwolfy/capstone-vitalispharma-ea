# Capstone TOGAF 10 — VitalisPharma Internacional

Repositorio del **modelo de Arquitectura Empresarial** del proyecto Capstone del curso
**CD-01 · Arquitectura Empresarial con TOGAF® 10** (Programa Integral de Arquitectura Empresarial · **CPS Tech**).

El modelo se construye en **[Archi](https://www.archimatetool.com/)** y se colabora sobre este repositorio Git
mediante el plugin **coArchi**. Aquí practicaremos las tres operaciones del trabajo colaborativo:
**Sincronizar**, **Commit** (Publicar) y **Actualizar** (Refresh).

---

## 1. Requisitos previos

| Herramienta | Para qué |
|---|---|
| Archi | Modelado ArchiMate — https://www.archimatetool.com/download |
| coArchi | Colaboración Git de modelos (se instala dentro de Archi) |
| Cuenta GitHub | Alojar el repositorio — https://github.com |
| Personal Access Token (PAT) | Autenticación al hacer push/pull (ver §5) |

### Instalar coArchi en Archi
1. Abra Archi -> menu **Help > Manage Plug-ins... > Install New**.
2. Seleccione el archivo `.archiplugin` de coArchi (descarguelo desde su pagina de releases) e instale.
3. Reinicie Archi. Active la vista **Collaboration** (Window > Perspective).

---

## 2. Obtener el modelo por primera vez (clonar)

1. En Archi, abra el panel **Collaboration**.
2. Boton **"Add a Model from Online Repository"**.
3. Pegue la URL del repositorio (la comparte el instructor), por ejemplo:
   `https://github.com/<usuario>/capstone-vitalispharma-ea.git`
4. Ingrese su **usuario de GitHub** y, como contrasena, su **Personal Access Token** (ver §5).
5. Elija una carpeta local. Archi descargara el modelo y lo abrira.

> El modelo inicial contiene la **Vista de Motivacion (Fase A)** de VitalisPharma.

---

## 3. Las tres operaciones que practicaremos

| Operacion | Boton en coArchi | Que hace | Cuando usarla |
|---|---|---|---|
| **Actualizar (Refresh)** | Refresh | Trae los cambios del remoto y los combina con su copia local | **Al empezar**, antes de editar |
| **Commit** | Commit | Guarda una "foto" de sus cambios en el historial local (con un mensaje) | Cada cambio significativo |
| **Sincronizar (Publish)** | Publish / Sync | Envia sus commits al remoto y trae los de los demas (commit + push + pull) | **Al terminar** un bloque de trabajo |

**Flujo recomendado en clase**
1. **Actualizar (Refresh)** -> parto de la ultima version.
2. Editar el modelo en Archi.
3. **Commit** -> describo mi cambio (p. ej. *"Agrego meta de trazabilidad"*).
4. **Sincronizar (Publish)** -> comparto con el equipo.

> Regla de oro: **Actualizar antes de editar** y **Sincronizar al terminar**. Asi se evitan conflictos.

---

## 4. Resolucion de conflictos
- Si dos personas editan lo mismo, coArchi avisa y permite elegir "mio" / "de ellos" o combinar.
- Para practicar sin riesgo: cada estudiante trabaja en una **vista propia** dentro del modelo.

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
|- README.md                         <- esta guia (estudiantes)
|- GUIA_INSTRUCTOR.md                <- preparacion del repo y publicacion inicial
|- .gitignore
|- scripts/
|   \- Capstone_VitalisPharma_Vista_Motivacion.ajs   <- genera el modelo inicial (jArchi)
\- model/                            <- lo crea coArchi al publicar el modelo
```

---
*CPS Tech · www.cps-tech.com · capacitaciones@cps-tech.com*
