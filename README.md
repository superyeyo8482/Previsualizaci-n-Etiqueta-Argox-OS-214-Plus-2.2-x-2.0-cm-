# Previsualizaci-n-Etiqueta-Argox-OS-214-Plus-2.2-x-2.0-cm-
# Previsualizador de Etiquetas para Argox OS-214 Plus

Herramienta interactiva para diseñar y previsualizar etiquetas de joyería (2.2 x 2.0 cm) utilizando el lenguaje PPLA de la impresora Argox.

## 🖨️ Contexto

Este proyecto nace de la necesidad de imprimir etiquetas pequeñas y resistentes para joyería. La impresora Argox OS-214 Plus funciona con comandos PPLA, diferentes al ZPL de Zebra. Para evitar desperdiciar etiquetas en pruebas, creamos un simulador visual que permite ajustar las coordenadas de cada elemento y generar el código PPLA listo para enviar a la impresora.

## 🎨 Características

- Simula una etiqueta de **2.2 cm de ancho × 2.0 cm de alto** (proporcional en pantalla).
- Elementos configurables:
  - Logo "AC" (texto, posición y tamaño)
  - Material y peso (ej. "Plata 8gr")
  - Precio (formato monetario)
  - Código de barras (simulación visual)
  - ID del producto como texto
- **Arrastre visual** (mediante inputs numéricos) para ajustar coordenadas X e Y de cada elemento.
- **Generación automática** del comando PPLA según las coordenadas definidas.
- Código HTML/CSS/JS puro, sin dependencias externas.

## 🚀 Uso

1. Abre el archivo `index.html` en cualquier navegador moderno.
2. Modifica los valores de coordenadas en los campos de texto y haz clic en "Actualizar" para mover los elementos.
3. Al hacer clic en "Mostrar comando PPLA", verás el código listo para enviar a la impresora Argox (por ejemplo, usando `echo` o un script Python).
4. Puedes copiar el comando y probarlo directamente en la terminal de Linux (Lubuntu, Ubuntu, etc.) con:
   ```bash
   echo -e "comando_generado" > /dev/usb/lp0
