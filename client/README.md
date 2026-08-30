# Landing de reformas

Landing estática creada con React, Vite y Tailwind CSS.

## Requisitos

- [Node.js](https://nodejs.org/) 20.19 o superior.
- npm, incluido con Node.js.

## Ejecutar desde cero

1. Abre una terminal en la carpeta del proyecto:

   ```bash
   cd "C:/dev/Pruebas landing/landing-vite"
   ```

2. Instala las dependencias:

   ```bash
   npm install
   ```

3. Arranca el entorno de desarrollo:

   ```bash
   npm run dev
   ```

4. Abre en el navegador la dirección que muestra Vite, normalmente:

   ```text
   http://localhost:5173
   ```

## Crear la versión de producción

Genera los archivos estáticos optimizados:

```bash
npm run build
```

El resultado se genera en `dist/`.

## Previsualizar la compilación de producción

Tras ejecutar el build:

```bash
npm run preview
```

Vite mostrará la URL local para revisar la versión generada.

## Scripts disponibles

| Comando | Descripción |
| --- | --- |
| `npm run dev` | Inicia el servidor de desarrollo. |
| `npm run build` | Genera la versión estática para producción en `dist/`. |
| `npm run preview` | Sirve localmente la compilación de producción. |
| `npm run lint` | Ejecuta la comprobación estática configurada. |

## Tecnologías

- React
- Vite
- Tailwind CSS
- HTML semántico
