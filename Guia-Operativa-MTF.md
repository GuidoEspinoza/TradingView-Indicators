# Guía operativa: Auto Multi‑Confluence + Auto MACD

## Objetivo
- Definir cuándo operar con alta probabilidad, aprovechando la nueva sensibilidad del indicador a los cruces de tendencia.

## Principios
- **Señal Fuerte (Prioritaria):** Cruce de MAs + MACD Histograma a favor + Momentum. Esta señal requiere menos confluencia (3/6).
- **Señal Estándar:** Requiere más confirmación de otros factores (RSI, Ichimoku, Volumen).
- Ejecuta sólo en cierre de vela.
- Usa 15m/30m para mayor fiabilidad.

## Protocolo general de entrada
- Detecta señal en el TF de entrada (Buy/Sell).
  - Si es por **Cruce Fuerte** (Trend Shift + MACD), la señal es agresiva.
  - Si es por **Divergencia/RSI**, busca confirmación extra de volumen.
- Confirma en el TF superior:
  - MACD del lado correcto del 0.
  - Orden de medias coherente.
- Ejecución:
  - Usa órdenes STOP (Buy Stop/Sell Stop) 1-2 pips por encima/debajo de la vela señal.

## Escenarios clave
- Aperturas/Noticias
  - Evita operar los primeros 15 minutos. El indicador ahora es más sensible y puede dar falsos cruces por volatilidad inicial.
- Cruce de EMA (Trend Shift)
  - Ahora el indicador prioriza esto. Si ves etiqueta "Buy" justo en el cruce de medias con MACD verde, es una entrada de alta probabilidad.
- Rangos/Choppy
  - El sistema bajó su exigencia de confluencia (de 5 a 3). **Peligro:** En rangos generará más señales falsas.
  - **Filtro:** Si las medias están planas, IGNORA las señales aunque el indicador las marque.

## Reglas por timeframe
- 1m/5m (scalping agresivo)
  - **Alta sensibilidad:** El indicador marcará muchos cruces.
  - **Filtro obligatorio:** Solo toma señales en la dirección de la tendencia de 30m.
  - Si 30m es alcista, ignora todas las etiquetas "Sell" en 1m/5m.
- 15m/30m (intradía - Recomendado)
  - **Zona de Confort:** Aquí la reducción de confluencia brilla.
  - Señales más limpias y recorridos de 30-50 pips.
  - Ideal para cuentas de balance bajo/medio ($500).

## Gestión del riesgo (Plan $500 USD)
- **Riesgo por trade:** Fijo al 2% ($10 USD). No exceder.
- **Apalancamiento:** 1:200 (Solo para margen, no para sobreoperar).
- **Stop Loss:**
  - Mínimo técnico: 15 Pips (en 1m/5m) y 25 Pips (en 15m/30m).
  - Nunca menos de eso, el ruido te sacará.
  - Ubicación: Debajo del último swing low o ATR x 1.5.
- **Take Profit:**
  - Ratio 1:1.5 mínimo (Arriesga $10 para ganar $15).
  - Meta diaria: $25 USD (5%). Con 2 operaciones positivas estás hecho.

## Checklist antes de operar
- Señal en cierre del TF de entrada y MACD del lado del 0.
- TF superior no en contra; ideal si su histograma acompaña.
- Filtros de frescura y fuerza pasan.
- Volumen acompaña; no estás en ventana de apertura/noticia.
- Stop y TP definidos; la señal no tiene más de 2–3 velas de antigüedad.

## Referencias en el código
- Confluencia mínima y señales: `Auto Multi-Confluence Signal.pine:209-221`.
- Frescura de señal: `Auto Multi-Confluence Signal.pine:31, 196-205, 211, 217`.
- Fuerza (pendiente vs ATR) aplicada a Buy/Sell: `Auto Multi-Confluence Signal.pine:158-161, 214, 221`.
- Tabla de volumen y fuerza: `Auto Multi-Confluence Signal.pine:286-293`.
- Alertas de MACD y cruce por 0: `Auto MACD Indicator.pine:64-65`.

## Ajustes recomendados
- Si en 1m hay demasiadas falsas señales, reduce `signalMaxAge` a 1 y/o sube el umbral de fuerza.
- Mantén los presets por timeframe; ajusta sólo tras observar patrones repetidos en un activo específico.
