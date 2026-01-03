# Regime Detection and Adaptive Trading

**Autor:** Francisco Encina Aballay

**Curso:** Aprendizaje de Máquinas

**Institución:** Universidad Técnica Federico Santa María

**Fecha:** Enero 2026

## 📋 Descripción

Proyecto de investigación que investiga si sistemas de trading adaptativo basados en detección automática de regímenes de mercado mediante Hidden Markov Models (HMM) y Machine Learning especializado pueden superar estrategias pasivas.

**Resultado principal:** El sistema adaptativo generó pérdidas de -15.5% vs +152.3% del buy-and-hold, demostrando las limitaciones del market timing algorítmico en mercados eficientes.

---

## 📁 Estructura del Proyecto
```
.
├── 01_data_extraction/
│   ├── 01_data_extraction.ipynb
│   ├── data_processed.csv
│   └── 01_basic_eda.png
│
├── 02_regime_detection/
│   ├── 02_regime_detection.ipynb
│   ├── data_with_regimes.csv
│   ├── hmm_model.pkl
│   ├── scaler.pkl
│   ├── regime_names.pkl
│   ├── 02_regime_timeline.png
│   ├── 02_transition_matrix.png
│   └── 02_regime_duration.png
│
├── 03_ml_models/
│   ├── 03_ml_models_by_regime.ipynb
│   ├── predictions_test.csv
│   ├── regime_models.pkl
│   ├── baseline_model.pkl
│   ├── 03_regime_distribution.png
│   ├── 03_model_comparison.png
│   └── 03_feature_importance.png
│
├── 04_backtesting/
│   ├── 04_backtesting_trading_strategy.ipynb
│   ├── backtesting_metrics.csv
│   ├── strategy_returns.csv
│   ├── performance_by_regime.csv
│   ├── 04_cumulative_returns.png
│   ├── 04_drawdowns.png
│   └── 04_metrics_comparison.png
│
└── README.md
```

---

## 🚀 Ejecución

### Requisitos
```bash
pip install yfinance pandas numpy matplotlib seaborn scikit-learn xgboost hmmlearn
```

### Orden de ejecución

1. **Step 1 - Extracción de datos:**
```bash
   jupyter notebook 01_data_extraction/01_data_extraction.ipynb
```
   - Descarga datos del S&P 500 (1993-2025)
   - Calcula features técnicos
   - Output: `data_processed.csv`

2. **Step 2 - Detección de regímenes:**
```bash
   jupyter notebook 02_regime_detection/02_regime_detection.ipynb
```
   - Entrena HMM con 3 estados
   - Detecta Bull Market, Consolidation, High Volatility
   - Output: `data_with_regimes.csv`, modelos guardados

3. **Step 3 - Modelos ML:**
```bash
   jupyter notebook 03_ml_models/03_ml_models_by_regime.ipynb
```
   - Entrena baseline XGBoost genérico
   - Entrena modelos especializados por régimen
   - Output: `predictions_test.csv`

4. **Step 4 - Backtesting:**
```bash
   jupyter notebook 04_backtesting/04_backtesting_trading_strategy.ipynb
```
   - Implementa estrategias de trading
   - Compara vs Buy & Hold
   - Output: métricas y gráficos finales

---

## 📊 Resultados Principales

### Detección de Regímenes (HMM)
- **Bull Market:** 40.4% observaciones, +22.5% retorno anual, 9% volatilidad
- **Consolidation:** 40.6% observaciones, +6% retorno anual, 16% volatilidad
- **High Volatility:** 19.0% observaciones, +2.3% retorno anual, 31% volatilidad

### Accuracy Modelos ML (Test Set)
| Modelo | Accuracy |
|--------|----------|
| Baseline genérico | 56.0% |
| Bull Market (especializado) | 55.7% |
| Consolidation (especializado) | 55.9% |
| High Volatility (especializado) | 45.7% ⚠️ |

### Performance Trading (2019-2025)
| Estrategia | Retorno Total | Sharpe Ratio | Max Drawdown |
|------------|---------------|--------------|--------------|
| **Buy & Hold** | **+152.3%** | **0.764** | **-33.72%** |
| Baseline ML | +50.3% | 0.347 | -29.94% |
| Adaptive Strategy | -15.5% ❌ | -0.158 | -38.72% |
| Regime-Aware | -38.0% ❌ | -0.916 | -42.61% |

---

## 🔑 Conclusiones Clave

1. ✅ **Metodología rigurosa:** HMM detectó correctamente eventos históricos (COVID-19, crisis 2008)
2. ❌ **Especialización contraproducente:** Modelos por régimen no superaron baseline genérico
3. ❌ **Market timing falló:** Accuracy 56% insuficiente para estrategias binarias long/cash
4. ⚠️ **Sample size crítico:** Regímenes raros (<2000 obs) sufren overfitting severo
5. 💡 **Lección principal:** En mercados eficientes, buy-and-hold pasivo es difícil de superar

---

## 📚 Tecnologías Utilizadas

- **Python 3.10**
- **Librerías:** pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, hmmlearn
- **Datos:** Yahoo Finance API (yfinance)
- **Período:** 1993-2025 (32 años, 8,086 observaciones)

---

## 📄 Documentos Relacionados

- Paper completo: `paper.pdf`
- Poster académico: `poster.pdf`
- Presentación: `slides.pdf`

---

## 📧 Contacto

**Francisco Encina Aballay**
Email: fcoencinaaba@gmail.com
GitHub: fcoencina

---

## 📝 Licencia

Este proyecto es material académico para el curso de Aprendizaje de Máquinas.
