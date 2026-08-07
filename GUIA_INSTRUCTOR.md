# Guia del Instructor — Preparar el repositorio y publicar el modelo inicial

Objetivo: dejar en GitHub un repositorio con el modelo inicial (Vista de Motivacion de VitalisPharma),
listo para que los estudiantes practiquen **Actualizar (Refresh)**, **Commit** y **Sincronizar (Publish)**.

## Paso 1 — Crear el repositorio en GitHub
1. GitHub -> **New repository**.
2. Nombre sugerido: `capstone-vitalispharma-ea`.
3. Visibilidad: **Public** (mas simple para clase) o Private.
4. Marque **Add a README file** (opcional; luego se reemplaza por el de esta carpeta).
5. **Create repository**.

## Paso 2 — Subir estos archivos base
Opcion A (web): en el repo -> **Add file > Upload files** -> arrastre `README.md`, `GUIA_INSTRUCTOR.md`,
`.gitignore` y la carpeta `scripts/` -> **Commit changes**.

Opcion B (terminal):
```
cd capstone-vitalispharma-ea
git init
git add .
git commit -m "Proyecto inicial del Capstone (guias y script jArchi)"
git branch -M main
git remote add origin https://github.com/<usuario>/capstone-vitalispharma-ea.git
git push -u origin main
```
(Use su usuario de GitHub y un Personal Access Token como contrasena.)

## Paso 3 — Generar el modelo en Archi
1. Abra Archi con el plugin **jArchi** instalado (Help > Manage Plug-ins).
2. Menu **Scripts** -> abra `scripts/Capstone_VitalisPharma_Vista_Motivacion.ajs` y ejecutelo.
3. Se crea el modelo "Capstone - VitalisPharma Internacional" con la vista **A - Motivacion**.

## Paso 4 — Publicar el modelo al repositorio con coArchi
1. Instale **coArchi** (Help > Manage Plug-ins > Install New).
2. Panel **Collaboration** -> con el modelo seleccionado, use **"Add Model to Workspace"** y luego **Publish**
   (o **"Add a Model from Online Repository"** primero si prefiere clonar y luego mover el modelo).
3. Indique la URL `https://github.com/<usuario>/capstone-vitalispharma-ea.git` y autentiquese con usuario + PAT.
4. coArchi crea la carpeta `model/` (e `images/`) dentro del repo y publica (push) el modelo.

> A partir de aqui, el repo ya contiene el modelo. Los estudiantes lo clonan siguiendo el `README.md`.

## Paso 5 — Dar acceso a los estudiantes
- **Solo lectura / practicar en vistas propias:** repositorio Public; clonan y publican en un fork, o
- **Escritura directa (recomendado para la clase):** **Settings > Collaborators** -> invite a cada estudiante,
  asi podran hacer push (Publish) al mismo repositorio.

## Guion sugerido para la demostracion en clase
1. Todos ejecutan **Actualizar (Refresh)**.
2. El instructor edita un elemento y hace **Commit** + **Sincronizar (Publish)**.
3. Los estudiantes hacen **Actualizar (Refresh)** y ven el cambio aparecer.
4. Cada estudiante agrega un elemento en su vista, hace **Commit** y **Sincronizar**.
5. Se provoca un conflicto a proposito (dos editan el mismo elemento) para mostrar la resolucion.

---
*CPS Tech · www.cps-tech.com · capacitaciones@cps-tech.com*
