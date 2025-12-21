# Manual Operativo: Pro Suite Trading System
**Perfil:** Cuenta $500 USD | Riesgo $10/Trade | Timeframe 15m/30m

---

## 1. EL ESCÁNER (¿Qué miro primero?)
Antes de buscar señales, define el campo de juego.

### A. ¿Dónde está el precio respecto al VWAP? (Línea central)
*   **Precio > VWAP:** Solo buscamos **COMPRAS (Longs)**. Ignora señales de venta.
*   **Precio < VWAP:** Solo buscamos **VENTAS (Shorts)**. Ignora señales de compra.
*   *Excepción:* Si el precio está muy lejos (tocando las bandas externas), puedes operar una reversión a la media (regreso al VWAP), pero con mitad de riesgo.

### B. ¿Hay obstáculos cercanos? (Cajas Rojas/Verdes)
*   Mira los **Order Blocks**.
*   Si vas a Comprar y tienes una **Caja Roja** justo encima: **NO ENTRES**. Espera a que la rompa.
*   Si vas a Vender y tienes una **Caja Verde** justo debajo: **NO ENTRES**. Espera a que la rompa.

---

## 2. EL GATILLO (La Señal)
Una vez que el contexto es favorable (ej: Precio sobre VWAP y sin techos cercanos):

### Espera la etiqueta "BUY" o "SELL"
*   Esta etiqueta es tu alerta. **NO** entres inmediatamente cuando aparece.
*   **Regla de Oro:** Espera al **CIERRE DE VELA**. Si la vela cierra y la etiqueta sigue ahí, pasamos al paso 3.

---

## 3. LA CONFIRMACIÓN (El Juicio Final)
Mira el panel inferior (MACD + RVOL).

### A. MACD (Momentum)
*   **Para Compras:** ¿El histograma es verde o está cruzando hacia arriba?
*   **Para Ventas:** ¿El histograma es rojo o está cruzando hacia abajo?
*   *Si el MACD contradice la señal (ej: Señal BUY pero MACD bajando fuerte), ANULA LA OPERACIÓN.*

### B. RVOL (Volumen Real - El Detector de Mentiras)
Mira la barra de volumen correspondiente a la vela de señal.
*   **Barra Verde/Amarilla:** ✅ Luz Verde. Los bancos están entrando. **ENTRA.**
*   **Barra Gris:** ⚠️ Precaución. Puedes entrar, pero reduce riesgo.
*   **Barra Violeta:** ❌ **PROHIBIDO.** Es una trampa de mercado sin volumen.

---

## 4. LA EJECUCIÓN (Cómo poner la orden)

### Entrada (Entry)
*   No uses "Market Execution". Usa órdenes pendientes.
*   **Buy Stop:** 2 pips por encima de la vela señal.
*   **Sell Stop:** 2 pips por debajo de la vela señal.
*   *Por qué:* Si la siguiente vela no rompe el máximo/mínimo, la orden no se activa y te salvas de una reversión.

### Stop Loss (SL)
*   Mira la **Línea ATR (Verde/Roja)** en el gráfico.
*   Pon tu SL exactamente en el precio que marca la etiqueta de la línea.
*   *Ejemplo:* Si la etiqueta roja dice `1.0520`, ese es tu SL.

### Take Profit (TP)
*   Mira el siguiente **Order Block (Caja)** contrario.
*   Pon tu TP justo antes de que el precio toque esa caja.
*   Si no hay cajas cercanas, busca un ratio 1:2 (Si arriesgas $10, busca ganar $20).

---

## RESUMEN RÁPIDO (Cheat Sheet)

| Paso | Pregunta | Condición para COMPRA (Long) | Condición para VENTA (Short) |
| :--- | :--- | :--- | :--- |
| **1** | **VWAP** | Precio > Línea Central | Precio < Línea Central |
| **2** | **Bloques** | No hay Caja Roja cerca arriba | No hay Caja Verde cerca abajo |
| **3** | **Señal** | Etiqueta **BUY** confirmada | Etiqueta **SELL** confirmada |
| **4** | **MACD** | Histograma Verde / Cruzando Up | Histograma Rojo / Cruzando Down |
| **5** | **RVOL** | Barra Verde o Amarilla | Barra Verde o Amarilla |
| **6** | **Ejecutar** | Buy Stop + SL en Línea Verde | Sell Stop + SL en Línea Roja |

---
*Creado por tu Asistente de IA para operar en Pepperstone/TradingView.*
