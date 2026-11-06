# Mil y una noches en Vercel

Esta carpeta está lista para publicarse como un proyecto independiente de Vercel. Es una entrada mediante proxy: el visitante ve tu nueva dirección de Vercel durante la navegación. Conserva la página, el panel, las cuentas, los audios y las imágenes del servicio actual.

## Publicar desde GitHub

1. Descomprime el paquete. Crea un repositorio nuevo y sube **el contenido de esta carpeta**: `vercel.json`, `package.json`, `check.mjs`, `public/` y este archivo.
2. En Vercel, selecciona **Add New → Project** e importa ese repositorio.
3. Usa **Framework Preset: Other**. La configuración ya establece `npm run build` y el directorio `public`; no elijas Next.js.
4. Elige el nombre disponible que prefieras y publica. Vercel asignará una dirección terminada en `.vercel.app`. No necesitas comprar un dominio para usarla.
5. Abre la nueva dirección y prueba **Panel del equipo** con tu correo y contraseña actuales. Las sesiones son independientes en cada dominio; inicia sesión de nuevo.
6. Desde la nueva dirección, abre **Equipo** e imprime la carátula: la liga se adapta a la dirección que estés utilizando. Genera también desde esa dirección los textos para redes.

Si usas el repositorio completo del blog en lugar de este paquete, selecciona `deploy/vercel` como **Root Directory**. No publiques la raíz del proyecto Vinext como si fuera una aplicación Next.js de Vercel.

## Qué se conserva y qué depende del servicio original

- **Firebase Authentication** sigue validando el correo y la contraseña. Este flujo se resuelve en el servidor mediante la API de Firebase; no usa ventanas de Google, redirecciones OAuth ni exige configurar un proveedor nuevo.
- Las fichas, permisos, fechas y evidencias siguen en la base de datos del alojamiento actual. Los archivos permanecen en su archivo de objetos. Firebase no está guardando esos contenidos.
- Los cambios del panel se ven al cargar o actualizar el blog en cualquiera de las direcciones. Los cambios del código de la página requieren publicar una versión del servicio original; este paquete los refleja después, sin copiar sus archivos.
- La carátula y los enlaces generados para redes toman el dominio de la ventana actual. Las ligas o documentos que ya hayas entregado no cambian por sí solos.
- **Mantén activo y público el sitio original.** Este paquete depende de él y no realiza una migración independiente del servidor ni de la base de datos. Si se elimina o deja de estar disponible, esta entrada tampoco funcionará.
- No se incluyen contraseñas, claves de administrador ni datos privados en el paquete. No requiere Firebase Storage, Blaze, Vercel Blob ni una tarjeta añadida por este proyecto. Usa el plan y los límites de tus cuentas actuales; no se promete capacidad ilimitada.

## Accesos, archivos y comprobación

El tráfico usa rutas del CDN de Vercel, sin una función intermedia que reciba los audios. Las solicitudes de escritura solo se reenvían cuando el navegador indica `Sec-Fetch-Site: same-origin`; después se adapta `Origin` al destino. Las solicitudes de otros sitios o sin esa comprobación se rechazan. Se conservan la validación de sesión, permisos, fecha, turno, tamaño, cuota y guion en el servidor original. No se desactiva la protección de origen ni se comparte una clave administrativa con Vercel.

Comprueba en tu publicación:

- El blog, las pestañas, el modo noche y la búsqueda.
- El inicio y cierre de sesión del panel.
- La vista de lectura, las tres ilustraciones y el audio.
- Una subida normal desde Archivos y una grabación, dentro de los límites del panel.
- La liga impresa de la carátula y los textos para compartir.

La configuración fue revisada localmente. La comprobación real de estas rutas externas y las subidas en Vercel requiere publicar en tu cuenta. Si el panel devuelve «Origen no permitido», conserva `vercel.json` completo y revisa que el navegador sea reciente; no elimines las verificaciones para resolverlo.

## Referencias

- https://vercel.com/docs/routing/rewrites
- https://vercel.com/docs/project-configuration/vercel-json#routes
- https://vercel.com/docs/project-configuration/vercel-json#transform-object-definition
- https://vercel.com/docs/limits#proxied-request-timeout

