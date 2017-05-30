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

Get everything in the same order just before converting it to an np array:
x_test = x_test.reindex_axis(sorted(x_test.columns), axis=1)

From SO:
To select rows whose column value equals a scalar, some_value, use ==:

df.loc[df['column_name'] == some_value]
To select rows whose column value is in an iterable, some_values, use isin:

df.loc[df['column_name'].isin(some_values)]
Combine multiple conditions with &:

df.loc[(df['column_name'] == some_value) & df['other_column'].isin(some_values)]
To select rows whose column value does not equal some_value, use !=:

df.loc[df['column_name'] != some_value]
isin returns a boolean Series, so to select rows whose value is not in some_values, negate the boolean Series using ~:

df.loc[~df['column_name'].isin(some_values)]
