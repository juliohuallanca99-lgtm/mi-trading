# Cómo usar mi-trading (desde la tablet o cualquier navegador)

Este programa se usa en una terminal. Como no hace falta instalar nada en tu equipo, se ejecuta en **GitHub Codespaces**: es una computadora en la nube que se abre desde el navegador.

## 1. Consigue una API key (una sola vez)

Los agentes necesitan un modelo de IA. Elige uno:

- **Claude**: entra en https://console.anthropic.com → API Keys → Create Key (es de pago por uso; recarga unos USD 5).
- **Gemini** (tiene un nivel gratuito): entra en https://aistudio.google.com/apikey.

## 2. Guarda la key en GitHub (una sola vez)

1. Ve a https://github.com/settings/codespaces.
2. En **Codespaces secrets**, pulsa **New secret**.
3. Nombre: `ANTHROPIC_API_KEY` (o `GOOGLE_API_KEY` si usas Gemini). En valor, pega la key.
4. En **Repository access**, elige `mi-trading` y guarda.

## 3. Abre el Codespace

1. En https://github.com/juliohuallanca99-lgtm/mi-trading, pulsa el botón verde **Code** → pestaña **Codespaces** → **Create codespace on main**.
2. Espera 2–3 minutos a que termine de instalar (solo la primera vez).
3. Abajo verás la **Terminal**.

## 4. Ejecuta un análisis

En la terminal, escribe:

```bash
tradingagents
```

Responde las preguntas con las flechas y Enter:

- **Ticker**: por ejemplo `SCCO` (Southern Copper), `BVN` (Buenaventura), `FSM` (Fortuna), `NVDA`, `BTC-USD`.
- **Proveedor**: Anthropic (o Google, según tu key).
- **Profundidad**: "Shallow" es la más rápida y barata para probar.

Al final, guarda el reporte: queda en `~/.tradingagents/` con un `complete_report.html` que puedes descargar.

Para ejecutarlo de una vez, sin preguntas:

```bash
export TRADINGAGENTS_LLM_PROVIDER=anthropic TRADINGAGENTS_QUICK_THINK_LLM=claude-haiku-4-5 TRADINGAGENTS_DEEP_THINK_LLM=claude-sonnet-5
export TRADINGAGENTS_MAX_DEBATE_ROUNDS=1 TRADINGAGENTS_MAX_RISK_ROUNDS=1
tradingagents --ticker SCCO --date 2026-11-20 --analysts market,news,fundamentals --save
```

## Costos y cuidados

- Codespaces da unas 60 horas gratis al mes. **Detén el Codespace** al terminar (github.com/codespaces → ⋯ → Stop).
- Cada análisis consume tokens de tu API key: con Haiku/Sonnet y profundidad baja suele costar centavos de dólar.
- Es una herramienta de investigación, **no una recomendación de inversión**.
