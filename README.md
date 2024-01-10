# Linear interpolation

Excute code script:

```bash
python linear_interpolate.py
```

### Find trending lines using linear interpolation
Step 1: Calculate Exponentially Weighted Moving Average 'ema' from 'Close' price with `com = 200` to specify decay in terms of center of mass. In general, the 50- and 200-day EMAs are used as indicators for long-term trends, [[source](https://www.investopedia.com/terms/e/ema.asp)]. To know more about ewm function in python, visit [this document](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.ewm.html). <br>

Step 2: Calculate Percentage Change 'diff_pc' by `(data['Close'] / data['ema']) - 1`. In details, this is element-wise division between 'Close' and 'ema'.<br>

Step 3: Defining [bull & bear](https://www.investopedia.com/insights/digging-deeper-bull-and-bear-markets/#:~:text=Key%20Takeaways,stocks%20are%20declining%20in%20value.) signal and return 'Signal' values. If 'diff_pc' > 0, this means 'increase' and return 1. If 'diff_pc' < 0, mean 'decrease' and return -1. If 'diff_pc' = 0, mean remain constant and return 0.<br>

Step 4: Define how many consecutive signals are needed to change trend. In default, I set `min_signal = 2 `. The more 'min_signal', the longer fit lines to fit more data. From that it results in fewer linear lines and less accuracy.<br>