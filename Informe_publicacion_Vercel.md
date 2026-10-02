# U3-T1 — Publicación en Internet con Vercel

**Proyecto:** Influencia360  
**Repositorio:** <https://github.com/SamCCDev/influencia360-u3-t1>  
**Servicio:** Vercel

## Reportes

- `/dashboard_datos.html`: exploración de perfiles, relaciones, publicaciones e interacciones.
- `/dashboard_resultados.html`: ranking probabilístico, red bayesiana, escenarios y evaluación.

El repositorio define `outputDirectory: "docs"` en `vercel.json`; por eso Vercel sirve los HTML generados directamente desde la raíz del sitio y no necesita ejecutar R en producción.

## Características básicas de la publicación

Vercel conecta el repositorio de GitHub, crea un despliegue en cada `push` a `main`, entrega los archivos estáticos por CDN y asigna HTTPS. La publicación es reproducible: los HTML ya versionados en `docs/` son el artefacto que se distribuye.

| Necesidad | Solución en Vercel |
|---|---|
| Dirección cualquiera | Vercel asigna automáticamente una URL `*.vercel.app`; es la opción por defecto para compartir los reportes. |
| Dirección de empresa | Se agrega un dominio propio, por ejemplo `bi.empresa.com`, y se configura su DNS para validarlo en Vercel. |
| Mucho volumen | Es apropiado para contenido estático servido por CDN. Datos de gran tamaño o dinámicos deben alojarse en almacenamiento/base de datos externa y consumirse por API, no incluirse todos dentro del HTML publicado. |
| Usuarios específicos | Se pueden proteger despliegues mediante Vercel Authentication/Deployment Protection; para una aplicación se integra autenticación propia o un proveedor externo. |

## Dos características avanzadas de pago y uso propuesto

1. **Vercel Authentication / Deployment Protection:** restringir los tableros internos de una empresa a usuarios autorizados de su equipo, manteniendo públicos sólo los reportes de clase.
2. **Web Analytics:** medir visitas, páginas más consultadas y rendimiento de los dos dashboards para conocer cómo se usan y priorizar mejoras.

Otra capacidad útil en planes superiores es el control de concurrencia y observabilidad de despliegues para varios equipos que actualizan reportes continuamente.

## Publicación

Al importar el repositorio en Vercel se selecciona el framework **Other**, sin *Build Command*, y la configuración versionada fija el directorio de salida `docs`. Las URLs finales son:

`https://<proyecto>.vercel.app/dashboard_datos.html`  
`https://<proyecto>.vercel.app/dashboard_resultados.html`

## Fuentes

- [Configuración de proyecto y outputDirectory](https://vercel.com/docs/project-configuration)
- [Vercel Drop para sitios estáticos](https://vercel.com/changelog/vercel-drop)
