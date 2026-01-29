# Smart Trading Bot - TradingView Indicators (100% Synced)

**Última actualización**: 29 de Enero, 2026  
**Estado**: ✅ 100% Sincronizado con Smart Trading Bot (Python)

---

## 🎯 Propósito

Esta suite de indicadores replica **exactamente** la lógica del **Smart Trading Bot** en TradingView, permitiéndote:

- ✅ **Visualizar** qué ve el bot en tiempo real
- ✅ **Entender** por qué el bot operó o rechazó una señal
- ✅ **Anticipar** trades antes de que el bot los ejecute
- ✅ **Validar** la calidad de las señales visualmente
- ✅ **Monitorear** el trailing stop en tiempo real

---

## 📊 Indicadores Incluidos

### 1. **All_In_One_Overlay.pine** (Panel Principal) 🔥

**Título en TradingView**: "Smart Trading Bot - All-In-One (100% Synced)"

**Componentes**:
- 🤖 **Bot Ready Indicator**: Celda maestra que indica si el bot ejecutará trades
- 🎯 **Multi-Confluence Signals**: Flechas azules (BUY) y rojas (SELL) con scoring 5/9
- ⏰ **Optimal Hours Filter**: Valida horarios óptimos por símbolo (auto-detección)
- 🚫 **Avoid Windows Filter**: Evita ventanas de alta manipulación (Londres/NY/Tokyo/Rollover)
- 📊 **ADX Adaptativo**: Threshold dinámico por sesión (18/20/25)
- 📈 **ATR Trailing Stop**: Línea dinámica para gestión de SL (2.5x ATR)
- 📊 **Institutional VWAP**: Precio promedio ponderado por volumen
- 🟩 **Auto Order Blocks**: Zonas institucionales de soporte/resistencia (lookback 2)
- 📋 **Dashboard en Tiempo Real**: Tabla con 9 indicadores de estado

**Sincronización con el Bot**:
- ✅ Confluence Threshold: **5** (igual que bot)
- ✅ ADX Adaptativo: **18/20/25** según sesión
- ✅ Horarios Óptimos: **23 símbolos** sincronizados con `symbols_config.py`
- ✅ Ventanas Restrictivas: **4 ventanas** sincronizadas con `core_config.py`
- ✅ Order Blocks: **Lookback 2** (estándar Bill Williams)
- ✅ ATR Multiplier: **2.5x** (igual que bot)

### 2. **All_In_One_Bottom.pine** (Panel Inferior)

**Título en TradingView**: "Bot-Synced Bottom Combo (MACD + RVOL)"

**Componentes**:
- 📉 **Auto MACD**: MACD con parámetros 12/26/9 (sincronizado con bot)
- 📊 **Professional RVOL**: Volumen relativo con colores inteligentes
  - 🟡 Amarillo (> 2.5): Climax - Bot rechaza
  - 🟢 Verde (> 1.2): Volumen fuerte
  - ⚪ Gris (0.8-2.5): Normal - Bot acepta
  - 🟣 Morado (< 0.8): Débil - Bot rechaza

---

## 🚀 Instalación en TradingView

### Paso 1: Importar Overlay

1. Abre **Pine Editor** en TradingView
2. Copia el código de `All_In_One_Overlay.pine`
3. Guárdalo como "Bot Suite Overlay"
4. Añádelo al gráfico (Panel Principal)

### Paso 2: Importar Bottom

1. Copia el código de `All_In_One_Bottom.pine`
2. Guárdalo como "Bot MACD+RVOL"
3. Añádelo al gráfico (Panel Inferior)

### Paso 3: Configurar Parámetros

**IMPORTANTE**: Usa estos valores para mantener sincronización:

| Parámetro | Valor Recomendado | ¿Cambiar? |
|-----------|-------------------|-----------|
| **Symbol Type** | AUTO | ✅ Dejar en AUTO |
| **Enable Optimal Hours** | ✅ Activado | ❌ NO desactivar |
| **Enable Avoid Windows** | ✅ Activado | ❌ NO desactivar |
| **Min Confluence** | 5 | ❌ NO cambiar |
| **OB Pivot Lookback** | 2 | ❌ NO cambiar |
| **ATR Multiplier** | 2.5 | ❌ NO cambiar |
| **RVOL MA Length** | 20 | ❌ NO cambiar |

---

## 📋 Cómo Interpretar las Señales

### 🤖 Regla de Oro: "BOT READY"

**La celda "🤖 BOT READY" es el indicador maestro.**

#### ✅ BOT READY = YES (Verde)

**Significado**: Todos los filtros del bot están cumplidos.

**Condiciones**:
- ✅ Horario óptimo activo para el símbolo
- ✅ Fuera de ventanas restrictivas
- ✅ ADX > threshold adaptativo

**Acción**: Si aparece una **flecha azul (BUY)** o **flecha roja (SELL)**, el bot **EJECUTARÁ** ese trade (asumiendo que no ha alcanzado límites de concurrencia).

#### ❌ BOT READY = NO (Rojo)

**Significado**: Al menos un filtro crítico falló.

**Posibles causas**:
- ❌ Fuera de horario óptimo (ej: UK100 a las 23:00 UTC)
- ❌ Dentro de ventana restrictiva (ej: 13:30-15:00 UTC apertura NY)
- ❌ ADX insuficiente (ej: ADX 15 cuando requiere 25)

**Acción**: **Ignorar todas las flechas**. El bot NO operará.

---

## 📊 Dashboard de Estado (Tabla)

La tabla en la esquina superior derecha muestra 9 indicadores:

| # | Indicador | Descripción |
|---|-----------|-------------|
| 1 | 🤖 **BOT READY** | Indicador maestro (verde = bot operará) |
| 2 | ⏰ **Optimal Hours** | Estado del horario óptimo |
| 3 | 🚫 **Avoid Window** | Estado de ventanas restrictivas |
| 4 | **ADX Req/Actual** | Threshold adaptativo vs ADX actual |
| 5 | **Filtro [TF]** | Tendencia en timeframe superior |
| 6 | **Tendencia [TF]** | Tendencia en timeframe actual |
| 7 | **Momentum** | Dirección del momentum |
| 8 | **Volume** | Fuerza del volumen |
| 9 | **Confluence** | Score alcista/bajista |

---

## ⏰ Horarios Óptimos por Símbolo

### Timezone: UTC-3 (Chile/Argentina)

| Símbolo | Horario UTC | Horario UTC-3 (Local) |
|---------|-------------|------------------------|
| **GOLD** | 01:00-20:00 | 22:00-17:00 (día siguiente) |
| **EURUSD** | 07:00-16:00 | 04:00-13:00 |
| **GBPUSD** | 07:00-17:00 | 04:00-14:00 |
| **US30/US100/US500** | 13:00-22:00 | 10:00-19:00 |
| **UK100** | 08:00-17:00 | 05:00-14:00 |
| **BTCUSD/ETHUSD** | 07:00-21:00 | 04:00-18:00 |

**Recomendación**: Opera símbolos que tengan horarios óptimos en tu franja horaria preferida.

---

## 🚫 Ventanas Restrictivas (Evitar)

El bot NO opera en estas ventanas (alta manipulación):

| Ventana | Horario UTC | Horario UTC-3 | Razón |
|---------|-------------|---------------|-------|
| **Londres Open** | 07:30-09:00 | 04:30-06:00 | Manipulación institucional |
| **NY Open** | 13:30-15:00 | 10:30-12:00 | Volatilidad extrema (NFP, CPI) |
| **Tokyo Open** | 00:00-01:30 | 21:00-22:30 | Spreads altos |
| **Rollover** | 21:50-23:10 | 18:50-20:10 | Rollover bancario |

---

## ✅ Checklist de Señal Válida

Para que una flecha azul/roja = Trade del bot:

- [ ] **🤖 BOT READY** = ✅ YES (verde)
- [ ] **Confluence** ≥ 5 (ver tabla)
- [ ] **RVOL** entre 0.8 y 2.5 (columnas grises, no amarillas ni moradas)
- [ ] **Precio NO sobreextendido** (< 2x ATR de EMA 100)
- [ ] **No hay Order Block contrario cercano** (< 1 ATR)
- [ ] **Bot tiene < 6 posiciones abiertas** (verificar externamente)
- [ ] **Bot tiene < 2 posiciones en este símbolo** (verificar externamente)

---

## 🎯 Casos de Uso

### 1. **Pre-Trade Validation** ⭐⭐⭐⭐⭐

Antes de que el bot ejecute, verifica visualmente:
- ¿"🤖 BOT READY" = ✅?
- ¿Confluence score ≥ 5?
- ¿RVOL normal (gris)?
- ¿Precio no sobreextendido vs VWAP?

### 2. **Post-Mortem Analysis** ⭐⭐⭐⭐⭐

Después de un trade ganador/perdedor:
- Revisa el gráfico en el momento de entrada
- Verifica si había Order Blocks contrarios
- Analiza si VWAP indicaba sobreextensión
- Aprende patrones de alta calidad

### 3. **Market Regime Detection** ⭐⭐⭐⭐

Detecta cuándo el bot tendrá baja actividad:
- ADX < 20 en todos los símbolos
- Precio oscilando entre EMAs
- MACD plano cerca de 0
- No hay flechas en días → Mercado lateral

### 4. **Trailing Stop Monitoring** ⭐⭐⭐⭐⭐

Monitorea en tiempo real cómo se mueve el TSL:
- Bot abre LONG en GOLD a $2,650
- Línea verde (TSL) en $2,635 (SL inicial)
- Precio sube a $2,680
- Línea verde sube a $2,655 (TSL siguiendo)
- **Conclusión**: Ganancia asegurada de +$5/lote

---

## 🔧 Mantenimiento

Si modificas el bot, actualiza estos parámetros en TradingView:

| Parámetro Bot | Archivo | Línea TV | Indicador |
|---------------|---------|----------|-----------|
| `CONFLUENCE_THRESHOLD` | `profiles.py` | 44 | Overlay |
| `ADX_TREND_THRESHOLD` | `profiles.py` | 26-30 | Overlay |
| `optimal_hours` | `symbols_config.py` | 57-79 | Overlay |
| `MARKET_OPEN_AVOID_WINDOWS` | `core_config.py` | 83-91 | Overlay |
| `fractal_n` | `indicators.py` | 72 | Overlay (obLookback) |
| `ATR_MULTIPLIER_FOR_SL` | `profiles.py` | 15 | Overlay (atrMult) |
| `RVOL_MA_LEN` | `profiles.py` | 18 | Bottom (rvolMaLen) |

---

## 📚 Documentación Adicional

- **`SYNC_NOTES.md`**: Notas técnicas de sincronización
- **`Manual_Operativo_Pro_Suite.md`**: Guía operativa completa (actualizada)

---

## ⚠️ Limitaciones

Lo que TradingView **NO puede validar**:

1. **Concurrencia de Posiciones**: No sabe cuántas posiciones tiene el bot abiertas
2. **Balance Actual**: No puede calcular tamaño de posición exacto
3. **Spread en Tiempo Real**: Usa precios mid, no bid/ask
4. **Slippage**: No simula slippage en ejecución

Para estas validaciones, consulta los logs del bot.

---

## 🚀 Próximos Pasos

1. **Importa los indicadores** en TradingView
2. **Configura Symbol Type en "AUTO"**
3. **Verifica que los filtros estén activados**
4. **Observa la celda "🤖 BOT READY"**:
   - Verde = Bot operará
   - Roja = Bot rechazará la señal
5. **Compara con los trades del bot** en los logs

---

## 📞 Soporte

Si encuentras señales que no coinciden con el bot:

1. Verifica que ambos indicadores estén actualizados (versión 2026-01-29)
2. Verifica que los filtros estén activados
3. Compara la hora UTC del gráfico con la hora del bot
4. Revisa los logs del bot para ver por qué rechazó la señal

---

**¡Ahora tienes 100% de alineación con el bot!** 🚀

Las flechas azules/rojas que veas con "BOT READY" verde son **exactamente** los trades que el bot ejecutará.
