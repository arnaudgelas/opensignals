# ysignals

## Install

```
pip install -U git+http://github.com/jrdi/ysignals.git@master#egg=ysignals
```

## Usage

```python
from pathlib import Path

from ysignals.data import yahoo
from ysignals.features import RSI, SMA

db_dir = Path('db')

yahoo.download_data(db_dir)

features_generators = [
    RSI(num_days=5, interval=14, variable='adj_close'),
    RSI(num_days=5, interval=21, variable='adj_close'),
    SMA(num_days=5, interval=14, variable='adj_close'),
    SMA(num_days=5, interval=21, variable='adj_close'),
]

train, test, live, feature_names = yahoo.get_data(db_dir, features_generators=features_generators)
```
