# CREAR PROYECTOS EN VS CODE PARA TYPESCRIPT
## 1) Comprobar/instalar Node (recomendado: usar `nvm`)
Primero comprueba si ya tienes `node` y `npm`:
```bash
node -v
npm -v
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































