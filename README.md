# Kairus

[Descargar Kairus 3.0.0 desde GitHub Releases](https://github.com/McEngelsOP/Kairus/releases/tag/v3.0.0).

App móvil de registro de gastos, ingresos y transferencias para Android e iOS. La interfaz parte de `reference/money-tracker.html`. Conserva el diseño, los iconos, la navegación, el calendario y el teclado de ese prototipo.

Kairus abre en Inicio al cargar el registro local. Los registros, las cuentas, los comprobantes y las preferencias se guardan en el dispositivo. La interfaz se empaqueta dentro de cada app con Capacitor y funciona sin servidor. Los importes se calculan en centavos. Cambiar de moneda modifica el símbolo y el código que se muestran. Las transferencias solo ajustan el saldo de las dos cuentas.

| Apartado | Funciones |
| --- | --- |
| Inicio | Movimientos por mes y día, calendario, búsqueda desde el calendario, edición y eliminación. |
| Gráficos | Categorías, importes diarios y últimos seis meses. |
| Informes | Presupuesto por mes, cuentas y patrimonio. |
| Yo | Apodo, idioma, moneda, estilo de iconos, recordatorios, movimientos recurrentes, Excel con gráficos y copias de seguridad. |
| + | Gastos, ingresos y transferencias con calculadora, categoría, cuenta, fecha, nota, comprobante y repetición. |
| Asistente | Resúmenes calculados con los datos del dispositivo y registro rápido a partir de texto. El dictado exige un motor y un idioma locales disponibles. |

Los vencimientos se registran o se omiten en **Yo → Movimientos recurrentes**. Los avisos diarios se programan en la app instalada con permiso de notificaciones.

En **Yo → Copia y restauración**, guarda un archivo `.kairus` y elígelo en el dispositivo de destino. Las copias anteriores siguen siendo compatibles. La restauración muestra el contenido antes de reemplazar los datos. Los recordatorios se configuran de nuevo en el dispositivo de destino.

En **Yo → Exportar a Excel**, descarga un `.xlsx` con todo el historial. El libro incluye cinco hojas con movimientos, meses, categorías y cuentas, además de dos gráficos editables en Resumen.

## Android

Requiere Node.js 22 o superior, JDK 21 y Android SDK 36.

```bash
npm ci
npm run android:apk
```

El APK de prueba se genera en `android/app/build/outputs/apk/debug/app-debug.apk`. El proyecto puede abrirse con `npm run android:open`. Para distribuir versiones de lanzamiento, configura la firma en Android Studio. Si Android rechaza la actualización por una diferencia de firma, guarda primero una copia de seguridad en la versión anterior antes de desinstalarla.

## iOS

El proyecto apunta a iPhone con iOS 16 o posterior. En una Mac con Xcode 26 o superior:

```bash
npm ci
npm run mobile:ios
npm run ios:open
```

Selecciona el equipo de firma en Xcode para instalar en un iPhone autorizado. La distribución por TestFlight o App Store requiere el archivo firmado y la cuenta de Apple Developer correspondiente.

## Verificación local

```bash
npm ci
npm run check
npm test
```

`index.html` y `src/original.css` contienen la interfaz del prototipo. `src/original.js` conecta los controles con `src/model.js` y `src/storage.js`. Los comandos móviles empaquetan esos recursos y los sincronizan en `android/` e `ios/`.

## Archivo HTML

Descarga `Kairus.html` desde Releases y ábrelo con un navegador. El archivo incluye la interfaz y el código completo, funciona sin conexión y guarda sus datos en ese navegador. Usa **Yo → Copia y restauración** para trasladar el registro a otro navegador o a la app instalada. En el HTML, los recordatorios se descargan como un archivo de calendario.

Para regenerar el archivo desde el código:

```bash
npm ci
npm run build:html
```
