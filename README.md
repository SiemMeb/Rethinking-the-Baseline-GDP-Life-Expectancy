# Rethinking the Baseline: GDP & Life Expectancy

A data science project asking: **can economic prosperity explain differences in life expectancy?**
It combines a regression analysis with time-series checks (stationarity tests and a fixed-effects panel model) and interactive matplotlib and Plotly graphs.

**Notebook:** [`rethinking-the-baseline-gdp-longevity.ipynb`](rethinking-the-baseline-gdp-longevity.ipynb)
**Kaggle version:** <!-- paste your Kaggle notebook link here -->

## Data

World Bank Open Data API, 20 selected countries, analysis year **2024** (the latest year with complete data for all three indicators).

| Indicator | Code |
|---|---|
| GDP per capita (current US$) | `NY.GDP.PCAP.CD` |
| Life expectancy at birth (years) | `SP.DYN.LE00.IN` |
| Population, total | `SP.POP.TOTL` |

## Methods

1. Data collection and cleaning (complete-case analysis, log transform of GDP)
2. Correlation analysis (Pearson, log-GDP Pearson, Spearman)
3. Linear vs. quadratic regression, with F-test and leave-one-out validation
4. Time-series validation: ADF stationarity tests and Panel OLS with country and time fixed effects
5. Residual analysis (which countries over- or under-perform the model)
6. Interactive Plotly dashboard with a country spotlight dropdown

## Key results

| Metric | Result |
|---|---:|
| Pearson (raw GDP) | 0.722 |
| Pearson (log GDP) | 0.885 |
| Spearman | 0.839 |
| Linear R² | 0.784 |
| Quadratic R² | 0.795 |
| Panel OLS coefficient on log GDP (country + time fixed effects) | +4.66 years (p = 0.014) |

- Most of the strong correlation is a **between-country** pattern. The **within-country** effect is real but much smaller.
- Largest positive residuals: India, Rwanda, Japan, Ethiopia, Korea. Largest negative: Nigeria, South Africa, United States, Kenya.
- Results are observational and **do not establish causation**.

## Run it

```bash
git clone https://github.com/SiemMeb/Rethinking-the-Baseline-GDP-Life-Expectancy.git
cd Rethinking-the-Baseline-GDP-Life-Expectancy
pip install -r requirements.txt
jupyter lab
```

The notebook pulls data from the World Bank API, so an internet connection is required.

## Limitations

Only 20 countries are included (those with complete data), and correlation is not causation. See the notebook for the full discussion.

## Author

**Siem Mebrahtu**: Data Scientist · [GitHub](https://github.com/SiemMeb)

## License

Apache-2.0, see [LICENSE](LICENSE).
