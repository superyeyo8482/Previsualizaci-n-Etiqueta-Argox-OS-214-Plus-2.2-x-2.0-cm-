# Previsualizador de Etiquetas para Joyería

Herramienta interactiva para diseñar y previsualizar etiquetas de joyería de 2.2 x 2.0 cm. Permite ajustar la posición de cada elemento visualmente y genera el comando de impresión en **PPLA** (para impresoras Argox OS-214 Plus) o **ZPL** (para Zebra ZD220). Incluye integración con Google Sheets para enviar el comando directamente a la impresora.

## 🚀 Características

- **Canvas interactivo**: Simula la etiqueta a tamaño real (2.2 cm × 2.0 cm) con elementos móviles.
- **Ajuste de coordenadas**: Modifica las posiciones de logo, material, precio, código de barras e ID mediante campos numéricos.
- **Generación de comandos**:
  - **PPLA**: Comando listo para Argox (lenguaje PPLA).
  - **ZPL**: Comando listo para Zebra (lenguaje ZPL).
- **Botón de copia**: Copia el comando generado al portapapeles para pegarlo en Google Sheets o cualquier otro software.
- **Integración con Google Sheets**: Script de Apps Script listo para recibir el comando y enviarlo a la impresora vía USB o red.

## 📦 Tecnologías utilizadas

- HTML5, CSS3, JavaScript (vanilla)
- Google Apps Script (para la integración con Sheets)

## 🧪 Uso

### 1. Abrir la herramienta
- Abre el archivo `preview.html` en cualquier navegador moderno.
- Verás una simulación de la etiqueta (recuadro blanco) y controles a la derecha.

### 2. Ajustar coordenadas
- Los campos de texto contienen las coordenadas X,Y de cada elemento (en puntos, según el sistema de coordenadas de la impresora).
- Modifica los valores y haz clic en **Actualizar** para mover el elemento en la previsualización.
- También puedes arrastrar los elementos directamente en el canvas (soporte básico para ajuste visual).

### 3. Generar comando de impresión
- Selecciona el tipo de comando: **PPLA** (Argox) o **ZPL** (Zebra).
- Haz clic en **Generar comando**.
- Aparecerá el código completo listo para enviar a la impresora.
- Usa el botón **Copiar al portapapeles** para copiarlo.

### 4. Integrar con Google Sheets
#### Script de Apps Script
Copia el siguiente código en el editor de Apps Script de tu hoja de cálculo:

```javascript
// Configuración: cambia según tu impresora
var IMPRESORA = "USB001";  // Para Argox en Windows (puerto)
// var IMPRESORA = "192.168.1.100"; // Para Zebra en red

function imprimirComando(comando) {
  // Envía el comando a la impresora (ejemplo con USB)
  var tempFile = "C:\\temp\\etiqueta.prn";
  var fso = new ActiveXObject("Scripting.FileSystemObject");
  var file = fso.CreateTextFile(tempFile, true);
  file.Write(comando);
  file.Close();
  var shell = new ActiveXObject("WScript.Shell");
  shell.Run("cmd /c copy /b \"" + tempFile + "\" " + IMPRESORA, 0, true);
}
