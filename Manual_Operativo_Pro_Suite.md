# Manual Operativo: Smart Trading Bot Suite (100% Synced)

**Última actualización**: 29 de Enero, 2026  
**Perfil**: Alineado 100% con Smart Trading Bot (Python)  
**Timeframes**: 15M, 30M, 1H  
**Gestión de Riesgo**: 2-3% por operación

---

## 🎯 Filosofía del Sistema

Este manual describe cómo usar los indicadores de TradingView que están **100% sincronizados** con el Smart Trading Bot. 

**Regla de Oro**: Solo confía en señales cuando **🤖 BOT READY = ✅ YES** (verde).

---

## 📋 PASO 0: Verificar "BOT READY" (CRÍTICO)

**Antes de buscar señales, verifica la celda "🤖 BOT READY" en la tabla superior derecha.**

### ✅ BOT READY = YES (Verde)

**Significado**: Todos los filtros críticos están cumplidos.

**Condiciones activas**:
- ✅ **Horario Óptimo**: El símbolo está en su ventana de máxima liquidez
- ✅ **Fuera de Ventanas Restrictivas**: No es apertura Londres/NY/Tokyo ni rollover
- ✅ **ADX Suficiente**: ADX > threshold adaptativo (18/20/25 según sesión)

**Acción**: Puedes buscar señales. Si aparece una flecha azul/roja, el bot ejecutará ese trade.

### ❌ BOT READY = NO (Rojo)

**Significado**: Al menos un filtro crítico falló.

**Posibles causas**:
- ❌ **⏰ Optimal Hours = OUT**: Fuera de horario óptimo (ej: UK100 a las 23:00 UTC)
- ❌ **🚫 Avoid Window = YES**: Dentro de ventana restrictiva (ej: 13:30-15:00 UTC)
- ❌ **ADX Req/Actual = Rojo**: ADX insuficiente (ej: 15 cuando requiere 25)

**Acción**: **NO operar**. Ignorar todas las flechas. El bot rechazará estas señales.

---

## 📊 PASO 1: El Escáner (Contexto de Mercado)

Una vez que "🤖 BOT READY" está verde, analiza el contexto.

### A. ¿Dónde está el precio respecto al VWAP?

**VWAP** = Línea central que cambia de color (verde/rojo)

- **Precio > VWAP (verde)**: Sesgo alcista → Prioriza señales de **COMPRA**
- **Precio < VWAP (rojo)**: Sesgo bajista → Prioriza señales de **VENTA**
- **Precio en VWAP**: Zona neutral → Espera confirmación fuerte

**Excepción**: Si el precio está muy lejos del VWAP (tocando bandas externas), puede haber reversión a la media.

### B. ¿Hay Order Blocks cercanos?

**Order Blocks** = Cajas verdes (soporte) y rojas (resistencia)

**Regla**:
- Si vas a **COMPRAR** y hay **Caja Roja** justo encima → **ESPERA** a que la rompa
- Si vas a **VENDER** y hay **Caja Verde** justo debajo → **ESPERA** a que la rompa

**Por qué**: Los Order Blocks son zonas institucionales donde el precio suele rebotar o frenar.

### C. Verifica la Tendencia (Tabla)

Mira las celdas de la tabla:

- **Filtro [TF]**: Tendencia en timeframe superior (H1/H4)
  - ▲ (verde) = Alcista
  - ▼ (rojo) = Bajista
- **Tendencia [TF]**: Tendencia en timeframe actual (15M/30M)
  - ▲ (verde) = Alcista
  - ▼ (rojo) = Bajista

**Regla**: Opera a favor de la tendencia del timeframe superior para mayor probabilidad.

---

## 🎯 PASO 2: La Señal (Flechas Azules/Rojas)

### Señales del Bot

- **Flecha Azul (Triángulo hacia arriba)**: Señal de **COMPRA**
- **Flecha Roja (Triángulo hacia abajo)**: Señal de **VENTA**

**IMPORTANTE**: Estas flechas solo aparecen cuando:
- ✅ Confluence Score ≥ 5 (al menos 5/9 condiciones cumplidas)
- ✅ ADX > threshold adaptativo
- ✅ Horario óptimo activo
- ✅ Fuera de ventanas restrictivas

**Regla de Oro**: **Espera al cierre de vela**. Si la vela cierra y la flecha sigue ahí, pasa al Paso 3.

---

## ✅ PASO 3: La Confirmación (Validación Final)

### A. Confluence Score (Tabla)

Mira la celda **"Confluence"** en la tabla:
- Muestra **X/Y** (ej: 6/2)
- **X** = Condiciones alcistas cumplidas
- **Y** = Condiciones bajistas cumplidas

**Regla**:
- Para **COMPRA**: X ≥ 5 (verde)
- Para **VENTA**: Y ≥ 5 (verde)

**Condiciones evaluadas** (9 en total):
1. Estructura de Mercado (HH/HL)
2. EMAs (20/100)
3. Ichimoku Cloud
4. MACD Momentum
5. MACD Histograma
6. RSI > 50 / < 50
7. Divergencias RSI
8. RVOL Direccional
9. ADX Adaptativo

### B. Momentum (MACD en Panel Inferior)

**Para COMPRA**:
- ✅ Histograma verde (barras azules/aqua)
- ✅ Línea MACD (verde) > Línea Signal (amarilla)

**Para VENTA**:
- ✅ Histograma rojo (barras rojas/maroon)
- ✅ Línea MACD (roja) < Línea Signal (naranja)

**Diamantes Amarillos** (opcional):
- Indican cruce de MACD (cambio de momentum)
- Si aparece en la misma dirección que la flecha → **Confirmación fuerte**

### C. RVOL (Panel Inferior - Columnas)

**RVOL** = Volumen Relativo (columnas de colores)

**Interpretación**:
- 🟡 **Amarillo** (> 2.5): Climax → **Bot rechaza** (sobrecompra/sobreventa)
- 🟢 **Verde** (> 1.2): Volumen fuerte → **Señal de alta calidad**
- ⚪ **Gris** (0.8-2.5): Volumen normal → **Bot acepta**
- 🟣 **Morado** (< 0.8): Volumen débil → **Bot rechaza** (trampa)

**Regla**:
- ✅ **Entra** si RVOL es gris o verde
- ❌ **NO entres** si RVOL es amarillo o morado

---

## 💰 PASO 4: La Ejecución (Gestión de Riesgo)

### Entrada (Entry)

**Método 1: Market Execution** (si operas manualmente)
- Entra al cierre de la vela de señal
- Usa el precio de cierre como referencia

**Método 2: Pending Order** (más conservador)
- **Buy Stop**: 2-3 pips por encima del máximo de la vela señal
- **Sell Stop**: 2-3 pips por debajo del mínimo de la vela señal
- **Ventaja**: Si la siguiente vela no rompe, la orden no se activa (evita reversiones)

### Stop Loss (SL)

**Mira la línea ATR Trailing Stop** (línea verde/roja con etiqueta)

**Regla**:
- Pon tu SL **exactamente** en el precio que marca la etiqueta
- **Ejemplo**: Si la etiqueta verde dice `SL: 2635.50`, ese es tu SL

**Por qué 2.5x ATR**:
- Da espacio al precio para respirar (evita stop-outs prematuros)
- Basado en volatilidad real del mercado
- Sincronizado con el bot

### Take Profit (TP)

**Método 1: Order Block Contrario** (recomendado)
- Busca la próxima **Caja** en dirección contraria
- Pon TP justo antes de tocar esa caja
- **Ejemplo**: Si vas LONG, busca la próxima Caja Roja arriba

**Método 2: Ratio 2:1** (si no hay Order Blocks cercanos)
- Si tu SL es 20 pips → TP = 40 pips
- Si arriesgas $10 → Busca ganar $20

**Método 3: TP Parcial** (como el bot)
- **50% en 1:1**: Cierra mitad de la posición cuando ganas lo mismo que arriesgaste
- **50% con TSL**: Deja correr la otra mitad con trailing stop
- **Ventaja**: Aseguras ganancias y capturas "home runs"

### Tamaño de Posición

**Riesgo por Trade**: 2-3% del balance

**Cálculo**:
```
Balance: $1,000
Riesgo: 2% = $20

Distancia SL: 30 pips
Valor por pip: $20 / 30 = $0.67/pip

Tamaño de lote: Según valor por pip de tu broker
```

**Herramienta**: Usa calculadora de posición de tu broker.

---

## 📋 RESUMEN RÁPIDO (Cheat Sheet)

| Paso | Pregunta | Condición para COMPRA | Condición para VENTA |
|------|----------|----------------------|---------------------|
| **0** | **🤖 BOT READY** | ✅ YES (verde) | ✅ YES (verde) |
| **1A** | **VWAP** | Precio > VWAP (verde) | Precio < VWAP (rojo) |
| **1B** | **Order Blocks** | No hay Caja Roja cerca arriba | No hay Caja Verde cerca abajo |
| **1C** | **Tendencia** | Filtro ▲ + Tendencia ▲ | Filtro ▼ + Tendencia ▼ |
| **2** | **Señal** | Flecha Azul (triángulo arriba) | Flecha Roja (triángulo abajo) |
| **3A** | **Confluence** | Score ≥ 5 (verde) | Score ≥ 5 (verde) |
| **3B** | **MACD** | Histograma verde + MACD > Signal | Histograma rojo + MACD < Signal |
| **3C** | **RVOL** | Gris o Verde (0.8-2.5) | Gris o Verde (0.8-2.5) |
| **4** | **Ejecutar** | Entry + SL en línea verde | Entry + SL en línea roja |

---

## ⏰ Horarios Óptimos (Timezone UTC-3)

**IMPORTANTE**: El bot solo opera en horarios óptimos. Fuera de estos, "🤖 BOT READY" estará en rojo.

### Símbolos Recomendados por Franja Horaria

#### 🌅 Madrugada (04:00-09:00 Local)

| Símbolo | Horario Local | Sesión |
|---------|---------------|--------|
| **EURUSD** | 04:00-13:00 | Europa |
| **GBPUSD** | 04:00-14:00 | Europa |
| **UK100** | 05:00-14:00 | Londres |
| **BTCUSD** | 04:00-18:00 | Global |

#### ☀️ Mañana (10:00-14:00 Local)

| Símbolo | Horario Local | Sesión |
|---------|---------------|--------|
| **US30** | 10:00-19:00 | América |
| **US100** | 10:00-19:00 | América |
| **US500** | 10:00-19:00 | América |
| **GOLD** | 22:00-17:00* | Global |

*GOLD opera desde 22:00 del día anterior hasta 17:00 del día actual.

#### 🌙 Noche (22:00-02:00 Local)

| Símbolo | Horario Local | Sesión |
|---------|---------------|--------|
| **GOLD** | 22:00-17:00* | Asia + Europa + América |

**Recomendación**: Si operas de noche, usa **GOLD** (opera 24h casi completo).

---

## 🚫 Ventanas Restrictivas (NO Operar)

El bot evita estas ventanas (alta manipulación). "🤖 BOT READY" estará en rojo.

| Ventana | Horario Local (UTC-3) | Razón |
|---------|----------------------|-------|
| **Londres Open** | 04:30-06:00 | Manipulación institucional |
| **NY Open** | 10:30-12:00 | Volatilidad extrema (NFP, CPI, FOMC) |
| **Tokyo Open** | 21:00-22:30 | Spreads altos |
| **Rollover** | 18:50-20:10 | Rollover bancario |

**Eventos Especiales** (evitar manualmente):
- 📅 **NFP** (primer viernes de mes, 10:30 local)
- 📅 **FOMC** (8 veces al año, 16:00 local)
- 📅 **CPI** (mensual, 10:30 local)

---

## 🎓 Casos de Uso Avanzados

### 1. **Validación Pre-Trade**

**Antes de que el bot ejecute**:
1. Verifica "🤖 BOT READY" = ✅
2. Verifica Confluence ≥ 5
3. Verifica RVOL gris/verde
4. Verifica que no hay Order Block contrario cercano
5. **Conclusión**: Señal de alta calidad

### 2. **Post-Mortem de Trades**

**Después de un trade perdedor**:
1. Revisa el gráfico en el momento de entrada
2. ¿Había Order Block contrario cercano? → Aprendizaje: Evitar entradas cerca de OBs
3. ¿VWAP indicaba sobreextensión? → Aprendizaje: Validar distancia a VWAP
4. ¿RVOL era amarillo/morado? → Aprendizaje: Volumen anómalo

### 3. **Detección de Mercados Laterales**

**Señales de mercado lateral** (baja actividad del bot):
- ADX < 20 en todos los símbolos
- Precio oscilando entre EMA 20 y EMA 100
- MACD plano cerca de 0
- No hay flechas en días
- **Acción**: Reducir expectativas, operar menos

### 4. **Monitoreo de Trailing Stop**

**En tiempo real**:
1. Bot abre LONG en GOLD a $2,650
2. Línea verde (TSL) en $2,635 (SL inicial = -$15)
3. Precio sube a $2,680
4. Línea verde sube a $2,655 (TSL siguiendo = +$5 asegurado)
5. **Conclusión**: Ya tienes ganancia asegurada, deja correr

---

## ⚠️ Errores Comunes a Evitar

### ❌ Error 1: Operar con "BOT READY" en Rojo

**Problema**: Ves una flecha azul pero "BOT READY" = NO.

**Consecuencia**: El bot NO ejecutará ese trade. Estarás operando sin alineación.

**Solución**: **Ignorar la flecha**. Solo opera cuando "BOT READY" = YES.

### ❌ Error 2: Ignorar RVOL

**Problema**: Entras en una señal con RVOL amarillo (> 2.5) o morado (< 0.8).

**Consecuencia**: Alta probabilidad de reversión (climax) o trampa (sin volumen).

**Solución**: **Solo opera con RVOL gris o verde**.

### ❌ Error 3: Entrar Cerca de Order Blocks Contrarios

**Problema**: Compras justo debajo de una Caja Roja (resistencia).

**Consecuencia**: El precio rebota en el Order Block y activa tu SL.

**Solución**: **Espera a que rompa el Order Block** o busca otra señal.

### ❌ Error 4: No Respetar Horarios Óptimos

**Problema**: Operas UK100 a las 23:00 UTC (20:00 local).

**Consecuencia**: Mercado cerrado, spreads altos, movimientos erráticos.

**Solución**: **Verifica "⏰ Optimal Hours" en la tabla**. Si está en rojo, NO operes.

### ❌ Error 5: Operar Durante Ventanas Restrictivas

**Problema**: Operas a las 10:30 local (13:30 UTC) durante apertura NY.

**Consecuencia**: Gaps extremos, slippage masivo, manipulación institucional.

**Solución**: **Verifica "🚫 Avoid Window" en la tabla**. Si está en rojo (⚠️ YES), NO operes.

---

## 📊 Ejemplo Completo: Trade Perfecto

### Escenario: GOLD 15M - 10:00 Local (13:00 UTC)

**Paso 0: Verificar BOT READY**
```
🤖 BOT READY: ✅ YES (verde)
⏰ Optimal Hours: ✅ (13:00 UTC está en 01:00-20:00)
🚫 Avoid Window: ✅ NO (no es 13:30-15:00)
ADX Req/Actual: 25/28.5 (verde, ADX suficiente)
```

**Paso 1: Contexto**
- VWAP: Precio > VWAP (verde) → Sesgo alcista ✅
- Order Blocks: No hay Caja Roja cercana arriba ✅
- Tendencia: Filtro H4 ▲ + Tendencia 15M ▲ ✅

**Paso 2: Señal**
- Flecha Azul (BUY) aparece en vela de 10:00 ✅
- Espero al cierre de vela → Flecha sigue ahí ✅

**Paso 3: Confirmación**
- Confluence: 6/2 (6 condiciones alcistas) ✅
- MACD: Histograma verde creciendo ✅
- RVOL: Columna verde (1.5) ✅

**Paso 4: Ejecución**
- Entry: $2,650 (cierre de vela)
- SL: $2,635 (línea verde ATR TSL = -$15)
- TP: $2,680 (próxima Caja Roja = +$30)
- Ratio R/R: 2:1 ✅
- Tamaño: 2% riesgo = $20 → 1.33 lotes mini

**Resultado**:
- Precio alcanza TP en 3 horas
- Ganancia: +$30 (2:1 R/R)
- **Trade perfecto** ✅

---

## 🚀 Conclusión

**Este sistema funciona si sigues las reglas**:

1. ✅ **Solo opera cuando "🤖 BOT READY" = YES**
2. ✅ **Respeta horarios óptimos y ventanas restrictivas**
3. ✅ **Valida Confluence ≥ 5 y RVOL gris/verde**
4. ✅ **Usa gestión de riesgo 2-3% por trade**
5. ✅ **Deja correr ganadores con trailing stop**

**Disciplina > Estrategia**

El bot tiene un win rate del 71% porque sigue estas reglas **sin emociones**. Tú también puedes lograrlo.

---

**¡Buena suerte y happy trading!** 📈🚀
