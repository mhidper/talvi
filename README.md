# Terms of Trade Analysis for Latin America and Vulnerable Economies

## 🎯 Overview

TALVI implements the **WP/19/21 methodology** (Gruss & Kebhaj, 2019) for calculating monthly Commodity Terms of Trade (CTOT) indices. This project focuses on Brazil as a case study, providing a comprehensive tool for measuring income gains and losses derived from international commodity price fluctuations.

The CTOT index measures **windfall gains and losses of income** as a percentage of GDP, making it essential for:
- External vulnerability analysis
- Macroeconomic policy design
- Fiscal impact assessment
- Investment risk evaluation

## 📊 Key Features

✅ **Real commodity prices** (deflated by G7 CPI)  
✅ **Time-varying weights** (3-year lagged moving averages)  
✅ **45+ commodities** mapped from HS codes to IMF series  
✅ **Monthly frequency** adaptation of WP/19/21 annual methodology  
✅ **Group decomposition** analysis by commodity categories  
✅ **Comprehensive visualization** tools  

## 🚀 Quick Start

### Installation

```python
# Clone the repository
git clone https://github.com/mhidper/talvi.git
cd talvi

# Install dependencies
pip install -r requirements.txt
```

### Basic Usage

```python
from src.ctot_calculator import MonthlyWP1921_CTOT_Calculator, calculate_monthly_ctot_wp1921

# Define your country data
gdp_brasil = {
    1997: 8.83206e11,
    1998: 8.63711e11,
    # ... add your GDP data
}

# Calculate monthly CTOT
monthly_results, monthly_weights, annual_weights = calculate_monthly_ctot_wp1921(
    imf_file_path="data/external-data.xls",
    trade_df=your_trade_data,
    country_code='76',  # Brazil
    country_name='Brasil',
    gdp_dict=gdp_brasil,
    cpi_deflator=your_cpi_deflator
)
```

## 📈 Core Methodology

The CTOT index follows the WP/19/21 specification:

```
ΔLog(CTOT_t) = Σ ΔP_j,t × Ω_i,j,t
```

Where:
- `ΔP_j,t` = Log change in real price of commodity j
- `Ω_i,j,t` = Weight of commodity j for country i in period t
- `Ω_i,j,t = (Exports_j - Imports_j) / GDP`

### Key Components

1. **Real Prices**: Nominal IMF prices deflated by G7 CPI (base 2016=100)
2. **Time-Varying Weights**: 3-year lagged moving averages to avoid endogeneity
3. **Comprehensive Mapping**: HS 6-digit codes to IMF commodity series
4. **Group Analysis**: Decomposition by Energy, Metals, Food, etc.

## 🗂️ Project Structure

```
talvi/
├── README.md                      # This file
├── requirements.txt               # Python dependencies
├── data/
│   ├── external-data.xls          # IMF commodity prices
│   └── gdp_brasil.py              # Brazil GDP data
├── src/
│   ├── ctot_calculator.py         # Main calculator class
│   └── utils.py                   # Utility functions
├── notebooks/
│   ├── 01_ctot_calculation.ipynb  # Main analysis notebook
│   └── 02_group_analysis.ipynb    # Group decomposition
├── results/
│   ├── monthly_ctot_brasil.csv    # Final CTOT series
│   └── plots/                     # Generated visualizations
└── docs/
    ├── methodology.tex            # Complete methodology (LaTeX)
    └── user_guide.md              # Detailed usage guide
```

## 📊 Sample Results for Brazil

### Key Statistics (1997-2024)
- **Mean monthly change**: 0.02% of GDP
- **Standard deviation**: 0.45% of GDP
- **Largest positive shock**: +3.1% of GDP
- **Largest negative shock**: -2.8% of GDP
- **Average commodities**: 38 per month

### Volatility Ranking by Group
1. **Energy** (38.4% of total volatility)
2. **Metals** (26.1%)
3. **Food & Beverages** (20.5%)
4. **Agricultural Raw Materials** (11.0%)
5. **Fertilizers** (4.0%)

## 🔗 Data Sources

| Source | Content | Usage |
|--------|---------|-------|
| **IMF Primary Commodity Prices** | Monthly nominal prices (45+ commodities) | Core price data |
| **UN Comtrade** | Bilateral trade flows (HS 6-digit) | Trade weights calculation |
| **OECD** | Consumer Price Indices (G7 countries) | Price deflator |
| **World Bank** | GDP in current USD | Weight normalization |

## 📚 Theoretical Foundation

Based on **Gruss, B. & Kebhaj, S. (2019)**. "Commodity Terms of Trade: A New Database." *IMF Working Paper WP/19/21*.

Key innovations in this implementation:
- Monthly frequency adaptation
- Updated CPI deflator methodology
- Enhanced commodity mapping
- Group decomposition analysis
- Real-time visualization tools

## 🛠️ Technical Requirements

- **Python**: 3.8+
- **Key Libraries**: pandas, numpy, matplotlib, seaborn
- **APIs**: UN Comtrade, OECD
- **Data Format**: Excel, CSV
- **Memory**: ~2GB for full historical data

## 📈 Usage Examples

### Basic CTOT Calculation
```python
# Initialize calculator
calc = MonthlyWP1921_CTOT_Calculator()

# Load and process data
prices = calc.load_imf_prices("data/external-data.xls", cpi_deflator=cpi_data)
mapped_trade = calc.map_trade_to_commodities(trade_data)
weights = calc.calculate_time_varying_weights(annual_weights)

# Calculate monthly CTOT
results = calc.calculate_monthly_ctot(prices, weights)
```

### Group Analysis
```python
# Analyze contributions by commodity group
contributions = calc.calculate_group_contributions(prices, weights, results)
calc.plot_group_contributions(contributions, "Brazil")
calc.analyze_group_contributions(contributions, "Brazil")
```

## 🔍 Validation & Quality Checks

- ✅ **Methodology validation**: Exact replication of WP/19/21 formulas
- ✅ **Data quality**: Robust handling of missing values
- ✅ **Economic validation**: Captures known historical shocks
- ✅ **Technical validation**: Comprehensive error handling

## 🌍 Applications

This tool is particularly valuable for:

- **Central Banks**: Monetary policy analysis
- **Finance Ministries**: Fiscal impact assessment
- **International Organizations**: Country risk evaluation
- **Researchers**: Academic studies on external shocks
- **Private Sector**: Investment and hedging strategies

## 📖 Documentation

- 📄 **Complete Methodology**: [`docs/methodology.pdf`](docs/methodology.pdf)
- 📖 **User Guide**: [`docs/user_guide.md`](docs/user_guide.md)
- 📓 **Example Notebooks**: [`notebooks/`](notebooks/)
- 🔧 **API Documentation**: See docstrings in [`src/`](src/)

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs or issues
- Suggest new features
- Submit pull requests
- Improve documentation

## 📧 Contact & Support

- **Issues**: Use GitHub Issues for bug reports
- **Questions**: Open a Discussion thread
- **Email**: [Your contact information]

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **IMF Research**: Original WP/19/21 methodology
- **UN Statistics**: Comtrade database access
- **OECD**: Statistical data provision
- **Open Source Community**: Python ecosystem

---

**⭐ Star this repository if you find it useful!**
