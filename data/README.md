# Data requirements

The `raw/` subdirectory contains the following files:

```text
ibm.csv
msft.csv
goog.csv
aapl.csv
amzn.csv
meta.csv
nflx.csv
tsla.csv
orcl.csv
sap.csv
usdjpy.csv
```

Each equity file must contain 2018 daily observations with at least these columns:

- `Date`
- `Close`
- `Adj.Close`

The USD/JPY file must contain:

- `Date`
- `Close`

The notebook expects dates formatted as `DD-Mon-YY`, such as `02-Jan-18`.

The original course materials directed students to obtain equity data from Yahoo Finance and USD/JPY data from Myfxbook. The repository copy normalizes the downloaded filenames and removes two stray non-UTF-8 characters from the USD/JPY column headings; the observations are unchanged.

Before publishing publicly, verify that redistribution is permitted by each data provider. If it is not, remove `data/raw/` and provide retrieval instructions instead.
