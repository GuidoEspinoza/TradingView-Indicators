# PineScript Indicators: Auto Multi‑Confluence & Auto MACD

Guía rápida para instalar, configurar y usar los indicadores en TradingView.

## Indicadores
- Auto Multi‑Confluence Signal
  - Genera etiquetas de Buy/Sell basadas en 6 fuentes: Tendencia actual, Momentum, Estructura, Volumen/Order Flow, Ichimoku y MACD.
  - **Nueva lógica "Strong Signal":** Prioriza cruces de tendencia (Trend Shift) confirmados por MACD y Momentum, requiriendo menos confluencia.
  - **Anti-Repainting:** Lógica corregida para asegurar que las señales no desaparezcan tras el cierre de vela.
  - Detecta Divergencias y Trend Shift (cruce de `ma1` con `ma2`).
  - Incluye “frescura” de señal y tabla de estado.
- Auto MACD Indicator
  - MACD con parámetros auto‑ajustados por timeframe.
  - **Anti-Repainting:** Garantiza estabilidad en histograma y cruces.
  - Dibuja histograma y líneas de MACD/Signal y provee alertas de cruce.

## Instalación en TradingView
- Abre TradingView → Pine Editor.
- Copia el contenido de `Auto Multi-Confluence Signal.pine` y presiona “Add to chart”.
- Copia el contenido de `Auto MACD Indicator.pine` y presiona “Add to chart”.
- Guarda cada script con un nombre (ej.: “Auto Multi‑Confluence” y “Auto MACD”).

## Configuración rápida
- Timeframe
  - Activa “Use Current Chart Resolution” para que el indicador use el TF del gráfico.
- Auto‑params
  - Mantén “Auto‑Adjust Parameters by Timeframe” activado.
- Señales (Multi‑Confluence)
  - `Min Confluence`: **3/6 por defecto** (antes 5). El sistema es más sensible a cruces de tendencia.
  - `Max Bars Since Base`: **3 por defecto**; da un poco más de margen para confirmar la entrada.
  - La lógica interna prioriza automáticamente las señales fuertes (Cruce EMA + MACD), saltándose filtros menores en timeframes bajos.

## Cómo usar
- Scalping (1m/5m)
  - **Precaución:** El sistema es más sensible. Busca señales de "Cruce Fuerte" (Strong Signal).
  - Filtra: Opera solo a favor de la tendencia de 15m/30m.
- Intradía (15m/30m) - **RECOMENDADO**
  - Fiabilidad superior al 70%.
  - Busca señales de Buy/Sell acompañadas de cruce de MACD.
  - Ideal para cuentas pequeñas buscando consistencia ($10 riesgo/trade).

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
