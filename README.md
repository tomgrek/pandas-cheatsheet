# Pandas & Data Wrangling Cheatsheet

See the Jupyter Notebook!

To add:

Discretize: prop['latitude'] = pd.qcut(prop['latitude'], 20, labels=False)

Remove outliers: df[df.apply(lambda x: np.abs(x - x.mean()) / x.std() < 3).all(axis=1)]

Find by value: lgb.loc[lgb['ParcelId'] == 10754147]

Merge: b=pd.merge(left=my, right=lgb, on=('ParcelId'))

Add dfs

Make categorical into one-hot:
train['transactiondate_quarter'] = train['transactiondate'].dt.quarter
pd.get_dummies(train['transactiondate_quarter'], prefix='q')
d = pd.get_dummies(train['transactiondate_quarter'], prefix='q')
train.join(d)

Select rows which are not nan:
prop[~np.isnan(prop['censustractandblock'])]
