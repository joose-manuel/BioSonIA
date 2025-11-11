# BioSonIA 12

Monorepo gestionado con Nx que incluye:
- `back`: API en NestJS (endpoint base `/api`).
- `front`: frontend en Next.js (`/` con App Router).

## Requisitos
- Node.js 18+ y npm.
- No necesitas instalar Nx globalmente; ya está configurado en el repo. .

## Instalación
1. Instala dependencias:
   - `npm install`
2. (Opcional) Si ves errores de espacio (`ENOSPC`), libera disco y repite.

## Estructura
- `back/`: aplicación NestJS (entry `src/main.ts`).
- `front/`: aplicación Next.js (App Router en `src/app/`).
- `nx.json`, `tsconfig.base.json`: configuración de Nx/TypeScript.
- `.vscode/launch.json`: config de debug generada por Nx.

## Comandos
- `npm run back`: inicia la API NestJS en modo desarrollo.
- `npm run front`: inicia el frontend Next.js en modo desarrollo.
- `npm run dev`: arranca `back` y `front` al mismo tiempo usando Nx (`run-many`).

## Puertos
- Front: `http://localhost:4200` (configurado en `front/project.json`).
- Back: `http://localhost:3000/api`.
- Cambiar puerto del front: edita el target `serve` en `front/project.json` y ajusta `-p <puerto>`.
- Cambiar puerto del back: ajusta el bootstrap de Nest en `back/src/main.ts` o usa variables de entorno.

## Memoria para desarrollo (front)
- `npm run front` arranca Next con mayor memoria (`--max-old-space-size=4096`).
- Para cambiar el valor, edita `front/project.json` en el target `serve`.

## Desarrollo con Nx
- Generar librerías: `npx nx g @nx/js:lib nombre-lib`.
- Ver dependencias: `npx nx graph`.
- Ejecutar tareas en paralelo: `nx run-many --target=<tarea> --projects=front,back --parallel`.

## Producción (orientativo)
- Build front: `nx build front`.
- Build back: `nx build back`.
- E2E front: deshabilitado en este setup inicial para evitar dependencias extra.

## Troubleshooting
- `ENOSPC` (no hay espacio): libera disco y reintenta `npm install` o el comando fallido.
- Next 16: la sección `eslint` en `next.config.js` ya no es soportada. El front arranca igualmente; puedes eliminar esa clave si quieres.

## Quickstart
1. `npm install`
2. `npm run back`
3. `npm run front`
4. Abre `http://localhost:4200` y prueba `http://localhost:3000/api`.