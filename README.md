# ICT Concepts TradingView Indicator

A comprehensive Pine Script v5 indicator built around **Inner Circle Trader (ICT)** concepts. Designed to be clean, modular, and easy to customize directly from the TradingView settings panel.

---

## Features

### PD Arrays
| Feature | Description |
|---|---|
| **Order Blocks (OB)** | Last bullish/bearish candle before a strong opposing move. Bullish OBs and Bearish OBs are drawn in distinct pastel colors. |
| **Breaker Blocks (BB)** | Former Order Blocks that price has broken through, flipping polarity. |
| **Mitigation Blocks (MB)** | Candles that created an imbalance and are being revisited / partially filled. |

### Liquidity
| Feature | Description |
|---|---|
| **Equal Highs (EQH)** | Two or more swing highs at approximately the same level — dashed resistance lines. |
| **Equal Lows (EQL)** | Two or more swing lows at approximately the same level — dashed support lines. |
| **Liquidity Sweeps** | Detected when price spikes beyond an EQH/EQL level but closes back inside. Labeled `SSL Sweep` or `BSL Sweep`. |

### Market Structure
| Feature | Description |
|---|---|
| **MSS** | Market Structure Shift — impulsive break of a significant swing high/low. |
| **ChoCH** | Change of Character — first corrective break, signaling a potential reversal. |

### CISD (Change in State of Delivery)
Detects the breakout candle after at least two consecutive inside bars (consolidation), marking the shift from accumulation/distribution to expansion. Shown as a label with optional background highlight.

### Imbalances
| Feature | Description |
|---|---|
| **Fair Value Gaps (FVG)** | Three-candle patterns with a gap between candle[2] high and candle[0] low (bullish) or vice-versa (bearish). |
| **Inversion FVGs (IFVG)** | A prior FVG that price has re-entered and closed through, flipping its nature. |

### Dashboard
A compact info panel in the **top-right** corner displaying:
- **Bias** — Bullish / Bearish / Neutral (calculated from structure + price position + FVG presence)
- **Structure** — Current structural trend direction
- **FVG** — Whether a fresh FVG is present on the current bar
- **Timeframe** — Active chart timeframe

---

## Installation

1. Open TradingView and navigate to the **Pine Script Editor** (bottom panel).
2. Copy the full contents of [`ict_indicator.pine`](./ict_indicator.pine).
3. Paste it into the editor and click **Add to chart**.
4. Adjust settings in the **Inputs** panel to your preference.

---

## Configuration

All settings are organized into logical groups in the Inputs panel:

| Group | Key Settings |
|---|---|
| PD Arrays — Order Blocks | Toggle, colors, extend bars, swing lookback |
| PD Arrays — Breaker Blocks | Toggle, bull/bear colors |
| PD Arrays — Mitigation Blocks | Toggle, bull/bear colors |
| Liquidity | Toggle EQH/EQL, sweep detection, tolerance |
| Market Structure | Toggle MSS/ChoCH, colors, lookback |
| CISD | Toggle, background color |
| Imbalances — FVG / IFVG | Toggle FVG, toggle IFVG, colors, extend bars |
| Dashboard | Toggle, bias window (hours) |

---

## Visual Style

The indicator uses a **soft pastel color scheme** to keep the chart readable:

| Element | Default Color |
|---|---|
| Bullish Order Block | Soft green (`#4CAF50`, 75% transparency) |
| Bearish Order Block | Soft red (`#F44336`, 75% transparency) |
| Bullish Breaker Block | Soft cyan (`#00BCD4`, 75% transparency) |
| Bearish Breaker Block | Soft orange (`#FF9800`, 75% transparency) |
| Bullish FVG | Light green (`#A5D6A7`, 75% transparency) |
| Bearish FVG | Light red (`#EF9A9A`, 75% transparency) |
| Bullish IFVG | Light cyan (`#80DEEA`, 75% transparency) |
| Bearish IFVG | Light amber (`#FFCC80`, 75% transparency) |
| EQH Lines | Pastel red (`#EF9A9A`) |
| EQL Lines | Pastel blue (`#90CAF9`) |
| MSS Labels | Purple (`#AB47BC`) |
| ChoCH Labels | Teal (`#26C6DA`) |
| Dashboard BG | Dark navy (`#1E1E2E`) |

---

## Notes

- Designed for **Pine Script v5** only.
- Performance is optimized by capping stored objects (boxes, lines, labels) at 20-30 per type.
- No emojis are used anywhere in the code or labels.
- All features can be toggled on/off independently.
