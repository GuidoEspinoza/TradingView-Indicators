# Guía operativa: Auto Multi‑Confluence + Auto MACD

## Objetivo
- Definir cuándo operar con alta probabilidad, evitando rangos, aperturas y falsas rupturas.

## Principios
- Usa el timeframe de entrada para el timing y el superior para el sesgo.
- Ejecuta sólo en cierre de vela del TF de entrada.
- Exige confluencia suficiente y fuerza de movimiento antes de entrar.

## Protocolo general de entrada
- Detecta señal en el TF de entrada (Buy/Sell) y espera el cierre.
- Confirma en el TF superior:
  - MACD del lado correcto del 0 y/o cruce por 0 cercano.
  - Orden de medias (`ma1` por encima/debajo de `ma2`) coherente con la señal.
- Verifica filtros del indicador:
  - Frescura de señal activa (no perseguir señales viejas).
  - Fuerza mínima de pendiente vs ATR (evita rangos/choppy).
- Comprueba volumen:
  - "Volume and Order Flow" alineado y "Volume Strength" sobre su media.

## Escenarios clave
- Aperturas/Noticias
  - Evita operar los primeros 10–15 minutos (indices USA) o 3–5 minutos en 1m.
  - Requiere confirmación adicional del TF superior y volumen real, no sólo mechas.
- Cruce de EMA (Trend Shift)
  - Trata el cruce `ma1`/`ma2` como base de señal, no como confirmación suficiente.
  - Entra sólo si MACD e histograma acompañan y hay confluencia mínima.
- Cruce de MACD por 0
  - Usa el cruce por 0 para confirmar régimen; completa posición o añade tamaño.
- Rangos/Choppy
  - Eleva el umbral de fuerza (pendiente vs ATR) o espera 1–2 velas de confirmación.
  - No operes si el precio oscila alrededor de `ma2` sin pendiente.

## Reglas por timeframe
- 1m/5m (scalping)
  - Señal en cierre + MACD del lado del 0 + histograma 2 barras a favor.
  - Confirmación en 5m; 15m no debe estar claramente en contra.
  - Ventana de silencio en apertura; evita mechas largas anómalas.
  - Entrada parcial: 50% al cierre, añade si la siguiente vela confirma.
- 15m/30m (intradía)
  - Confluencia mínima alta (5/6) y cierre de vela de disparo.
  - 30m confirma sesgo (MAs y MACD hacia o bajo/encima del 0).
  - Espera 1–2 velas de confirmación en contextos de rango o tras noticias.

## Gestión del riesgo
- Stop por estructura (último swing) o por encima/debajo de `ma2` del TF de entrada.
- Alternativa objetiva: `ATR` 1.5–2× del TF de entrada.
- Parciales en 0.8–1.0R o cuando el histograma pierde altura 2–3 barras.
- Riesgo total por idea: 0.5–1% en scalping; 1–2% en intradía.

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
