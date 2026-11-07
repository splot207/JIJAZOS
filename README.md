# JIJAZOS 🔥 — Apuestas fuertes (stake 15%+)

Dashboard para los **JIJAZOS**, las apuestas con stake desde 15%:
- **Dashboard** con usuario y contraseña (`admin` / `admin`): subes las fotos de los tickets, se llenan solos, marcas ✅ / ❌ y ves tu capital.
- **/diario**: página pública con el resumen del día y del mes (solo porcentajes).
- **Bot de WhatsApp**: manda cada jijazo y su resultado al grupo de JIJAZOS. Es el mismo bot de JIJA$: un solo número atiende los dos grupos.

Los datos van en la misma base gratis de Upstash, separados con el prefijo `jz:`, así que no se mezclan con los de JIJA$.

## Variables en Vercel
- `SESSION_SECRET`: frase larga para la sesión
- `BOT_KEY`: llave del bot (la misma que pongas en `bot/conexion.json`)
- `UPSTASH_REDIS_REST_TOKEN`: token de la base de datos de Upstash
- `UPSTASH_REDIS_REST_URL`: opcional (por defecto se usa la de `config.json`)
- `ADMIN_USER` / `ADMIN_PASS`: opcional, para cambiar el login

## Bot (en tu PC)
En `bot/conexion.json` pon los dos dashboards:
```json
{
  "dashboards": [
    { "nombre": "JIJA$", "dashboardUrl": "https://xapuestas-3m62.vercel.app", "botKey": "..." },
    { "nombre": "JIJAZOS", "dashboardUrl": "https://TU-PROYECTO.vercel.app", "botKey": "..." }
  ]
}
```
Luego doble clic en **INICIAR-BOT.bat**. Para elegir el grupo de JIJAZOS, pega el link de invitación del grupo en el panel **WhatsApp** del dashboard.

## Cómo calcula
- Monto = capital inicial × stake % (mínimo 15%)
- Ganada: monto × (cuota − 1) · Perdida: −monto · Nula: 0
- El % de cada jijazo es sobre el capital inicial

## Archivos
- `public/`: dashboard, login y página /diario (HTML, CSS y JS separados)
- `api/index.js`: entrada para Vercel
- `src/`: API, cálculos, mensajes y base de datos
- `bot/`: bot de WhatsApp para tu PC
- `config.json`: nombre, prefijo de datos, stake mínimo, hora del resumen
