# Sistema de ventas (frontend)

Frontend Angular para la gestión del sistema de ventas. Consume la API del proyecto `Compras-Backend` bajo el prefijo `/api/local`.

## Funcionalidad

- Inicio de sesión, recuperación y cambio de contraseña.
- Cobro (POS): carrito, búsqueda por código de barras, pagos en efectivo y con tarjeta, emisión de ticket PDF y apertura y cierre de caja.
- Productos y categorías con alta, edición, baja y reactivación.
- Usuarios y roles con permisos por pantalla.
- Compras a proveedores y consulta de márgenes.
- Reportes de ventas y corte de caja con exportación a PDF y Excel.
- Historial de ventas y perfil del usuario.

## Tecnologías

- Angular 21 en modo standalone, TypeScript 5.9 y RxJS 7.
- Angular Material para los componentes de interfaz.
- Chart.js para las gráficas.
- jsPDF y jspdf-autotable para tickets y reportes en PDF.
- xlsx para la exportación a Excel.
- Vitest y jsdom para las pruebas.
- SSR habilitado y Zone.js para la detección de cambios.

## Backend

El backend es `Compras-Backend`, una API de Spring Boot. En desarrollo escucha en `http://localhost:8081/api` y esta aplicación usa `http://localhost:8081/api/local`. La URL de producción se define en `src/environments/environment-prod.ts`.

La autenticación usa JWT. El token se guarda en `localStorage` y `AuthInterceptor` lo envía en cada petición. Las rutas protegidas comprueban el permiso correspondiente antes de cargar la pantalla.

## Estructura

- `src/app/core`: servicios HTTP, interfaces, guard de permisos, interceptor, pipe de paginación y utilidades.
- `src/app/features`: pantallas de login, cobro, productos, categorías, usuarios, roles, compras, reportes, historial de ventas, perfil y vistas de elementos dados de baja.

## Rutas

La raíz `/` es el inicio de sesión. El resto de pantallas están en `/cobro`, `/perfil`, `/productos`, `/productos-desactivados`, `/categorias`, `/usuarios`, `/usuarios-desactivados`, `/roles`, `/compras`, `/reportes`, `/salehistory`, `/forgot-password` y `/reset-password`.

## Ejecutar el proyecto

Requiere Node.js y npm.

```
npm install
npm start
```

La aplicación queda disponible en `http://localhost:4200`. El backend debe estar en ejecución para que las pantallas carguen datos.

```
npm run build
npm test
```

`npm run build` genera los archivos de producción en `dist/` y `npm test` ejecuta las pruebas con Vitest.
