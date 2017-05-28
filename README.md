# Pandas & Data Wrangling Cheatsheet

See the Jupyter Notebook!

To add:

Discretize: prop['latitude'] = pd.qcut(prop['latitude'], 20, labels=False)

Remove outliers: df[df.apply(lambda x: np.abs(x - x.mean()) / x.std() < 3).all(axis=1)]
