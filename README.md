# Pro Suite Trading System (PineScript v6)

Este proyecto contiene una suite profesional de indicadores para TradingView, optimizados para Scalping y Day Trading en timeframes de 15m y 30m, con gestión de riesgo integrada.

## Estructura del Proyecto

### 1. Indicadores Principales (All-In-One)
Diseñados para cuentas gratuitas de TradingView (máximo 2 indicadores por gráfico).

- **`All_In_One_Overlay.pine`** (Panel Principal)
  - **Auto Multi-Confluence Signal**: Alertas de dos niveles (Triángulos de Confluencia y Diamantes de Momentum).
  - **Institutional VWAP**: Referencia de precio promedio ponderado por volumen.
  - **Auto Order Blocks**: Zonas de oferta y demanda automáticas.
  - **ATR Trailing Stop**: Línea dinámica para gestión de stop loss.
  - *Anti-Repainting*: Lógica optimizada para evitar repintado de señales.

- **`All_In_One_Bottom.pine`** (Panel Inferior)
  - **Auto MACD**: MACD con parámetros ajustables y alertas.
  - **Professional RVOL**: Volumen relativo para detectar actividad institucional.
  - Visualización combinada para ahorrar espacio.

### 2. Documentación
- **`Manual_Operativo_Pro_Suite.md`**: Guía completa de la estrategia, reglas de entrada/salida, y gestión de riesgo (2% por operación).

### 3. Scripts Individuales (`/scripts_individuales`)
Componentes modulares para referencia o uso aislado:
- `ATR_Trailing_Stop.pine`
- `Auto_Order_Blocks.pine`
- `Institutional_VWAP.pine`
- `Professional_RVOL.pine`

## Instalación en TradingView

1. Abre **Pine Editor** en TradingView.
2. Copia el código de `All_In_One_Overlay.pine` y guárdalo como "Pro Suite Overlay".
3. Añádelo al gráfico (Panel Principal).
4. Copia el código de `All_In_One_Bottom.pine` y guárdalo como "Pro Suite Bottom".
5. Añádelo al gráfico (Panel Inferior).

## Configuración Recomendada

- **Timeframes**: 15m (Scalping agresivo) o 30m (Intraday estable).
- **Gestión de Riesgo**: 2% del balance por operación (ver Manual).
- **Broker**: Pepperstone (recomendado para ejecución rápida).

## Notas de Actualización
- Se han eliminado los archivos antiguos (`Auto MACD Indicator.pine`, etc.) para evitar confusiones.
- La lógica "Strong Signal" está activa por defecto para capturar inicios de tendencia.
