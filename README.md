# PineScript Indicators: Auto Multi‑Confluence & Auto MACD

Guía rápida para instalar, configurar y usar los indicadores en TradingView.

## Indicadores
- Auto Multi‑Confluence Signal
  - Genera etiquetas de Buy/Sell basadas en 6 fuentes: Tendencia actual, Momentum, Estructura, Volumen/Order Flow, Ichimoku y MACD.
  - Detecta Divergencias y Trend Shift (cruce de `ma1` con `ma2`).
  - Incluye “frescura” de señal (no persigue señales viejas) y tabla de estado.
- Auto MACD Indicator
  - MACD con parámetros auto‑ajustados por timeframe.
  - Dibuja histograma y líneas de MACD/Signal y provee alertas de cruce con Signal y cruce por 0.

## Instalación en TradingView
- Abre TradingView → Pine Editor.
- Copia el contenido de `Auto Multi-Confluence Signal.pine` y presiona “Add to chart”.
- Copia el contenido de `Auto MACD Indicator.pine` y presiona “Add to chart”.
- Guarda cada script con un nombre (ej.: “Auto Multi‑Confluence” y “Auto MACD”).

## Configuración rápida
- Timeframe
  - Activa “Use Current Chart Resolution” para que el indicador use el TF del gráfico.
  - Si prefieres otro TF, desactívalo y selecciona uno en “Use Different Timeframe”.
- Auto‑params
  - Mantén “Auto‑Adjust Parameters by Timeframe” activado para presets óptimos por TF.
- Señales (Multi‑Confluence)
  - `Min Confluence (out of 6)`: recomendado 5/6 para intradía, 4/6 si quieres más señales.
  - `Max Bars Since Base`: 2 por defecto; evita perseguir señales tardías.
  - Opciones de visualización: Divergence, Trend Shifts y Tabla.

## Cómo usar
- Scalping (1m/5m)
  - Entra tras el cierre de la vela con señal (Buy/Sell) y MACD del lado correcto de 0.
  - Confirma que 5m no contradiga y, idealmente, que su histograma acompañe.
  - Evita ventanas de apertura/noticia; preferir “Volume Strength: Above Vol MA”.
- Intradía (15m/30m)
  - Requiere confluencia mínima alta (5/6). Ejecuta sólo en cierre de 15m.
  - Confirma en 30m (orden de MAs y MACD acercándose/por debajo/encima de 0 según dirección).

## Alertas
- Multi‑Confluence
  - “Buy Signal” y “Sell Signal” están disponibles como alertas del script.
- Auto MACD
  - “MACD Cross” (cruce con Signal) y “MACD Zero Cross” (cruce por 0).
  - Configura las alertas desde el panel de alertas de TradingView.

## Lectura de la Tabla (Multi‑Confluence)
- Macro Trend: `ma2` vs `EMA100` del mismo TF.
- Current Signal: precio vs `ma1` y orden `ma1 > ma2`.
- Momentum: `ta.mom` positivo y creciendo.
- Market Structure: condición simple de HH/HL; puede retrasarse en giros.
- Volume & Order Flow: vela con cuerpo alineado y volumen sobre su media.
- Volume Strength: volumen sobre la media de volumen del TF.

## Buenas prácticas
- Ejecuta en cierre de vela; evita intrabar.
- Confirma en TF superior para sesgo; usa MACD por 0 como validación de régimen.
- No persigas señales con más de 2–3 velas de antigüedad.
- Gestiona riesgo: stop por estructura o `ATR` 1.5–2×; toma parciales cuando el histograma pierde fuerza.

## Archivos
- `Auto Multi-Confluence Signal.pine`: indicador principal de confluencia.
- `Auto MACD Indicator.pine`: MACD con presets por TF.
- `Guia-Operativa-MTF.md`: guía operativa con escenarios (apertura, cruces, rangos).

## Soporte
Si necesitas presets específicos por activo o reglas adicionales (p. ej., exigir estructura a favor para imprimir señal), abre un issue o ajusta los inputs en el panel del indicador.
