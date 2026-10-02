# U3-T1 — Publicación en Internet: Influencia360

**Asignatura:** Business Intelligence 2  
**Estudiante:** Samuel Castillo  
**Proyecto:** Influencia360 — análisis de redes sociales con redes bayesianas  
**Repositorio de origen:** <https://github.com/rubendcl/Influencers>  
**Commit recreado:** `a1b6d2c`  
**Servicio seleccionado:** Netlify

## Reportes publicados

El sitio se configura para publicar `docs/`, que contiene dos reportes interactivos:

1. `dashboard_datos.html`: exploración de perfiles, relaciones, publicaciones, interacciones y calidad de datos.
2. `dashboard_resultados.html`: ranking probabilístico, red bayesiana, escenarios de inferencia y evaluación.

`index.html` es la portada metodológica. Los HTML son autocontenidos; Netlify los distribuye como contenido estático sin requerir un servidor R.

## Publicación con Netlify

`netlify.toml` define `docs/` como *Publish directory*. Al conectar la rama `main` con Netlify, cada `git push` crea un despliegue atómico: la nueva versión se vuelve pública sólo cuando todos sus archivos terminaron de cargarse. Para esta entrega no hace falta comando de build porque los HTML ya están generados.

## Necesidades resueltas

| Necesidad | Solución |
|---|---|
| Dirección cualquiera | Netlify asigna por defecto `https://nombre.netlify.app`; es la solución inmediata para distribuir los reportes. |
| Dirección de empresa | Se conecta un dominio propio, como `bi.empresa.com`, mediante DNS y TLS/HTTPS. |
| Mucho volumen | Sirve contenido estático desde CDN y despliega de forma atómica. No debe usarse como base de datos o almacenamiento masivo; los datos grandes deben estar en BD/almacenamiento externo y exponerse por API. Existe un límite de 54.000 archivos por directorio publicado. |
| Usuarios específicos | Se puede usar contraseña o visibilidad privada. Para usuarios identificados, Netlify Identity admite correo/contraseña y proveedores externos, con validación desde Functions/Edge Functions. |

## Dos capacidades avanzadas de pago

1. **Visibilidad privada y colaboración Pro:** para un tablero empresarial, sólo analistas y gerencia invitados pueden acceder a los reportes y previsualizaciones.
2. **Identity Pro:** permite auditoría de eventos de identidad y personalizar plantillas/remitente de los correos de invitación, recuperación y acceso para clientes.

La capacidad adicional de *concurrent builds* es otra opción de pago útil cuando varios equipos actualizan reportes simultáneamente.

## Fuentes

- [Despliegues y límite de archivos](https://docs.netlify.com/deploy/deploy-overview/)
- [Subdominio por defecto y dominios propios](https://docs.netlify.com/manage/domains/domains-fundamentals/understand-domains/)
- [Protección de despliegues](https://docs.netlify.com/deploy/protect-deploys/)
- [Netlify Identity y opciones Pro](https://docs.netlify.com/manage/security/secure-access-to-sites/identity/plans-and-pricing/)
