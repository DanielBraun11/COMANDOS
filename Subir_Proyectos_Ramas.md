# 🚀 Cómo subir varios proyectos a un mismo repositorio usando **ramas**

## 🧭 Introducción

En este documento aprenderás a subir varios proyectos (por ejemplo, prácticas o ejercicios) dentro de un **mismo repositorio de GitHub**, utilizando **ramas independientes**.  
Cada rama contendrá un proyecto diferente, manteniendo el código separado y ordenado, sin afectar el contenido de las otras ramas ni del `main`.

---

## 🗂️ Estructura inicial

Supongamos que tienes una carpeta principal que contiene varios proyectos:
```
Practicas_BACKEND/
├── Practica1_Backend/
├── Practica2_backend/
└── Practica3_backend/
```

Cada subcarpeta representa un proyecto distinto que quieres subir a su propia rama del repositorio **Practicas_BACKEND** en GitHub.

---

## ⚙️ 1️⃣ Preparación inicial

Antes de empezar, asegúrate de estar en la carpeta raíz del repositorio:

```bash
cd ~/Documentos/Practicas_BACKEND
```
Comprueba que Git esté inicializado:
```
git status
```
Si Git aún no está configurado, puedes inicializarlo así:
```
git init
git remote add origin https://github.com/TU_USUARIO/Practicas_BACKEND.git
```
## 🌿 2️⃣ Crear una nueva rama para un proyecto

Cada proyecto tendrá su propia rama.
**IMPORTANTE**: Asegurate que estas en la ubicación de la carpeta donde tienes todos los proyectos y que esta vinculada al repo (Ej. Practicas_BACKEND)
Por ejemplo, para subir la práctica 1:
```
git checkout -b practica1_backend
```
El parámetro `-b` crea y cambia automáticamente a la nueva rama.
Puedes comprobar en qué rama estás con:
```
git branch
```
El asterisco `*` indica la rama activa.
## 💾 3️⃣ Añadir los archivos del proyecto
Asegúrate de añadir **solo la carpeta del proyecto que corresponda** a la rama actual.
Por ejemplo, si estás subiendo la práctica 1:
```
git add Practica1_Backend/
```
Haz el commit con un mensaje descriptivo:
```
git commit -m "Subida práctica 1 completa (carpeta Practica1_Backend)"
```
## 🚀 4️⃣ Subir la rama a GitHub
Sube la rama al repositorio remoto:
```
git push origin practica1_backend
```
Esto crea la rama en GitHub sin tocar la rama `main`.

Puedes verificarlo entrando en tu repositorio en GitHub
→ desplegando el selector de ramas en la parte superior izquierda
→ deberías ver `main` y `practica1_backend`.

## 🧑‍💻 5️⃣ Repetir para los demás proyectos
Cada vez que tengas un nuevo proyecto, repite el proceso:
```
git checkout -b practica2_backend
git add Practica2_backend/
git commit -m "Subida práctica 2 completa (carpeta Practica2_backend)"
git push origin practica2_backend
```
Y así sucesivamente con `practica3_backend`, `practica4_backend`, etc.

## 🔄 6️⃣ Fusionar las ramas con `main`
Cuando quieras que el contenido de una práctica aparezca directamente en la rama principal:

1. Entra en tu repositorio en GitHub.
2. Cambia a la rama correspondiente (`practica1_backend`, por ejemplo).
3. Pulsa **"Compare & pull request"**.
4. Revisa los cambios.
5. Pulsa **"Merge pull request"** → **"Confirm merge"**.

Esto integrará los archivos de esa práctica en la rama `main`, sin borrar la rama original.

## 🧹 7️⃣ (Opcional) Eliminar ramas antiguas
Una vez fusionadas, puedes borrar ramas locales y remotas si ya no las necesitas:
```
git branch -d practica1_backend        # borra rama local
git push origin --delete practica1_backend   # borra rama remota
```
