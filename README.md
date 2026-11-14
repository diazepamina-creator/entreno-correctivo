# Correctivo

App web instalable (PWA) para registrar entrenamiento y hábitos:

- **Hoy**: resumen del día, mañana (sueño, energía, suplementos), mantenimiento P3, core y movilidad, bloque correctivo, bloque de fuerza o complejo, airbike y cierre (hábitos, paseo, peso y cintura).
- **Semana**: calendario de la semana y resumen de sesiones, sueño, proteína, paseos y medidas.
- **Progreso**: gráficas e historial.
- **Copia de seguridad** en JSON y exportación a CSV.

Los registros se guardan **solo en el navegador del móvil**; este repositorio no contiene datos personales.

## Coach con Claude
Con una clave de la API de Claude (se pone en Ajustes y se guarda solo en el móvil, fuera de las copias):
- **¿Qué me toca hoy?**: la sesión del día según los últimos 14 días, el sueño, el tiempo disponible y el material.
- **Registrar en texto**: se escribe o se dicta lo hecho y rellena los campos, con vista previa antes de guardar.
- **Pregúntale**: dudas sobre el plan, con el contexto de los datos.
- **Revisión de la semana** (pestaña Semana) e **informe del mes**.
- **Cocina**: propuesta de menú con los platos tipo y lista de la compra a partir del menú.
- Avisos de progresión en la fuerza cuando toca subir de pareja.

Solo se envían datos a la API al pulsar un botón.

## Sesión de airbike por Bluetooth
La consola de la Maniak Torque emite datos por Bluetooth con el estándar FTMS (vatios, RPM, distancia; un dato por segundo). Desde la tarjeta Airbike, «Sesión con la bici · Bluetooth» abre una pantalla con los vatios y las RPM en directo y entrenos guiados: A&A con la franja de vatios objetivo, alta estimulación con las RPM objetivo, rodaje suave con aviso si te pasas, y los dos tests (sprint de 10 s y 5 minutos), con pitidos y cuenta atrás. Al terminar, resumen por series con la caída del rendimiento y comparación con la sesión anterior, y se guarda en el día. Funciona en la app de Android y en Chrome. `ble.html` es la página de diagnóstico que se usó para averiguar el protocolo.

## Instalar en Android
**App de Android (APK)**, con avisos: descargar el `.apk` de la [última versión](https://github.com/diazepamina-creator/entreno-correctivo/releases/latest) e instalarlo. Las actualizaciones se instalan encima y conservan los datos. Avisos: entreno, paseo, P3 si el día va en blanco (se cancela al marcarlo), rutina de noche, revisión del domingo, compra y tanda de cocina.

### Cambio de firma (3.0.1)
Hasta la 3.0.0 la firma de la APK estaba en este repositorio, a la vista. Desde la 3.0.1 hay una firma nueva que no está aquí: GitHub Actions la recibe por dos secretos (`APK_FIRMA` y `APK_CLAVE`). Android no deja instalar una APK con otra firma encima de la anterior, así que, una sola vez:
1. En la app vieja: **copia de seguridad** (y apunta la clave de la API si no la tienes a mano: no va en la copia).
2. Desinstalar la app.
3. Instalar la 3.0.1 o posterior.
4. Importar la copia y volver a poner la clave. Activar de nuevo los avisos.

**Web instalable (PWA)**, sin avisos:
1. Abrir la dirección de GitHub Pages en **Chrome**.
2. Menú ⋮ → **Instalar aplicación**.
3. Funciona sin conexión.

Los datos de la web y de la APK son independientes: para pasarlos, copia de seguridad en una e importarla en la otra.

## Archivos
| Archivo | Contenido |
|---|---|
| `index.html` | La aplicación completa |
| `manifest.webmanifest` | Datos de instalación |
| `sw.js` | Funcionamiento sin conexión |
| `icon-*.png`, `apple-touch-icon.png` | Iconos |
| `capacitor.js` | Puente con Android (en la web no hace nada) |
| `apk/` | Proyecto de Capacitor para la APK; la compila GitHub Actions (`.github/workflows/apk.yml`) y la publica en Releases. La firma no está en el repositorio: llega por los secretos `APK_FIRMA` y `APK_CLAVE`, y es fija para que las actualizaciones se instalen encima |
