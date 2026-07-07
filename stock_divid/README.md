# Dividend Factors Data Description

This directory contains dividend factors data for various stock codes.

## File Naming Convention

Each file is named `{code}_dividend_factors.csv` where `{code}` is the 6-digit stock code.

## Column Headers Description

| Column Name | Chinese Name | Description |
|------------|--------------|-------------|
| `time` | 时间 | Dividend announcement time or ex-dividend date (Unix timestamp format) |
| `interest` | 现金分红比例 | Cash dividend ratio (e.g., 1.0 means 1 yuan per 10 shares) |
| `stockBonus` | 送股比例 | Bonus share ratio (shares given as bonus per 10 shares) |
| `stockGift` | 转增比例 | Capitalization issue ratio (shares from capital reserve per 10 shares) |
| `allotNum` | 配股数量 | Rights offering quantity (shares available for rights subscription) |
| `allotPrice` | 配股价格 | Rights offering price (price per share for rights subscription) |
| `gugai` | 股改标志 | Share reform indicator (special marker for share structure reform) |
| `dr` | 除权系数 | Ex-rights coefficient (adjustment factor for price/volume after dividend) |

## Data Source

Data is retrieved using xtdata API (`xtdata.get_divid_factors()`).

## Usage Example

```python
import pandas as pd

# Load dividend factors for a specific stock
df = pd.read_csv('300782_dividend_factors.csv', encoding='utf-8-sig')
print(df)
```

## Notes

- All CSV files are encoded in UTF-8 with BOM for compatibility with Excel and other tools.
- Timestamp values are in Unix timestamp format (milliseconds since 1970-01-01).
- The `dr` coefficient is used to adjust historical prices and volumes for backtesting purposes.
