# tv-hub

Catálogo de apps para **TVHub** (Android TV). TVHub lee:

```
https://raw.githubusercontent.com/hernandez-devb/tv-hub/main/apps.json
```

`TVHub.apk` en este repo es la última versión de TVHub (para instalar en TV box nuevos y para que se actualice sola).

## Formato de `apps.json`

```jsonc
{
  "title": "Mis apps",
  "notice": "Texto que aparece arriba en todos los TV box (vacío = no se muestra)",
  "apps": [
    {
      "name": "GeeSports",                // nombre en la tarjeta
      "package": "com.live.geesports",    // nombre interno de la app (no cambia entre versiones)
      "category": "Deportes",             // opcional: agrupa en secciones
      "icon": "https://.../icono.png",    // opcional: si no, usa el ícono de la app instalada
      "description": "Deportes en vivo",  // opcional

      // Fuente recomendada: "apk" (link directo) y/o "code" (código de Downloader)
      "apk": "https://.../geesports.apk",
      "code": "123456",
      "versionCode": 12,                  // si es mayor que el instalado → "Actualizar"
      "versionName": "3.9",
      "changelog": "Qué cambió",          // opcional

      // Opcional: otras versiones o espejos (menú → "Elegir versión")
      "sources": [
        { "label": "Mirror", "code": "654321", "versionCode": 12, "versionName": "3.9" },
        { "label": "Versión anterior", "apk": "https://.../geesports-3.8.apk", "versionCode": 11, "versionName": "3.8" }
      ],

      "hidden": false                     // true = no se muestra en el menú
    }
  ]
}
```

- Si una fuente tiene `apk` y `code`, TVHub descarga del `apk` y muestra el código en la tarjeta (para usarlo en Downloader si hace falta).
- Si solo tiene `code`, TVHub resuelve el código por su cuenta (no necesita Downloader).
- Los códigos de todas las fuentes aparecen al pie de la tarjeta.

**Cuando una app cambia de link**: reemplaza `apk`/`code` y sube `versionCode`.

**Para publicar una nueva versión de TVHub**: reemplaza `TVHub.apk` y sube el `versionCode` de la entrada `com.tvhub.app`.
