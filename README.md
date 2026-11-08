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

## Instalar en Android
**App de Android (APK)**, con avisos: descargar el `.apk` de la [última versión](https://github.com/diazepamina-creator/entreno-correctivo/releases/latest) e instalarlo. Las actualizaciones se instalan encima y conservan los datos. Avisos: entreno, paseo, P3 si el día va en blanco (se cancela al marcarlo), rutina de noche, revisión del domingo, compra y tanda de cocina.

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
| `apk/` | Proyecto de Capacitor para la APK; la compila GitHub Actions (`.github/workflows/apk.yml`) y la publica en Releases. La firma (`correctivo.keystore`) es fija para que las actualizaciones se instalen encima |
