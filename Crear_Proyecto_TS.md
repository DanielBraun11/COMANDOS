# CREAR PROYECTOS EN VS CODE PARA TYPESCRIPT
## 1) Comprobar/instalar Node (recomendado: usar `nvm`)
Primero comprueba si ya tienes `node` y `npm`:
```bash
node -v  # Devuelve la version
npm -v   # Devuelve la version
```
Si te devuelve versiones, perfecto. Si no, recomiendo instalar `nvm` (manejador de versiones de Node — evita problemas con permisos):
```bash
# instala nvm (versión estable actual; copia y pega)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash

# carga nvm en la sesión actual (si usas bash)
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# instala la última LTS de Node y úsala
nvm install --lts
nvm use --lts

# verifica
node -v
npm -v
```

## 2) Crear el proyecto y abrir en VS Code
```bash
# crea la carpeta del proyecto
mkdir -p ~/laboratorioPruebas
cd ~/laboratorioPruebas

# abre la carpeta en VS Code (si tienes el comando `code` instalado)
code .
```

## 3) Inicializar npm y dependencias de desarrollo
Dentro del directorio del proyecto ejecuta:
```bash
# inicializa package.json
npm init -y

# instala TypeScript y herramientas útiles como ts-node y tipos de node (dev)
npm install --save-dev typescript ts-node @types/node

# opcional: nodemon para recarga automática durante desarrollo
npm install --save-dev nodemon
```

## 4) Crear `tsconfig.json` (configuración de TypeScript)
Crea el archivo `tsconfig.json` en la raíz del proyecto con este contenido (puedes crear y pegar en VS Code):
```bash
npx tsc --init
```
Esto crea un archivo `tsconfig.json` en tu carpeta actual con muchas opciones comentadas.
Luego puedes editarlo con VS Code para dejarlo más limpio.
Ejecuta:
```bash
code tsconfig.json
```
Y reemplaza su contenido por este (copiar/pegar en VS Code):
```bash
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "rootDir": "src",
    "outDir": "dist",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src"]
}
```
Guarda con Ctrl + S.

## 5) Estructura de carpetas y archivo de ejemplo
Crea la carpeta `src` y un archivo de ejemplo `src/index.ts`:
1. Asegúrate de estar en la carpeta del proyecto:
```bash
cd ~/laboratorioPruebas
```
2. Crea la carpeta `src` (si no la hiciste antes):
```bash
mkdir -p src
```
3. Crea el archivo `index.ts` dentro de `src`:
```bash
touch src/index.ts
```
En este arquivo ya puedes programar tus cosas y compilar sin problema. Por ejemplo este código:
```bash
// src/index.ts
const saludo = (nombre: string) => `Hola, ${nombre}!`;

console.log(saludo("laboratorioPruebas"));

function suma(a: number, b: number): number {
  return a + b;
}

console.log("2 + 3 =", suma(2, 3));
```
Puedes crear más archivos como `src/ejemplo1.ts`, `src/ejemplo2.ts` y luego importarlos desde `index.ts` o compilar por separado.

## 6) Scripts útiles en `package.json`
Abre `package.json` y añade (o sustituye) la sección `"scripts"` por algo así:
```bash
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "ts-node src/index.ts",
  "watch": "tsc -w",
  "dev:watch": "nodemon --watch 'src/**/*.ts' --exec 'ts-node' src/index.ts"
}
```
- `npm run build` → compila TypeScript a JavaScript en `dist/`.
- `npm start` → ejecuta el `dist/index.js`.
- `npm run dev` → ejecuta directamente el `.ts` con `ts-node` (rápido para pruebas).
- `npm run watch` → compila en modo vigilancia.
- `npm run dev:watch` → recarga automática con `nodemon` (si lo instalaste).

## 7) Compilar y ejecutar desde terminal (ejemplos)
Compilar todo:
```bash
npm run build
# luego
ls dist
node dist/index.js
```
Ejecutar directamente sin compilar (ideal para pequeños tests):
```bash
npm run dev
```
Compilar sólo un archivo (opcional):
```bash
npx tsc src/index.ts --outDir dist
node dist/index.js
```
Ver errores de TypeScript: `npm run build` muestra los mensajes de compilador en la terminal.

## 8) Buenas prácticas rápidas
- Añade .gitignore con:
```bash
node_modules
dist
.env
```
- Si quieres formato y lint: instala `eslint` y `prettier` más adelante.
- Para probar distintos mini-programas crea archivos `src/ejemploX.ts` y ejecútalos con `npm run dev` o importándolos en `index.ts`.





























