y = amount_default
y2 = amount_not_default
X = only_default[only_default.columns.difference(['LIMIT_BAL'])]
X2 = only_not_default[only_not_default.columns.difference(['LIMIT_BAL'])]

X1_train, X1_test, y1_train, y1_test = train_test_split(X, y, test_size=0.20, random_state=123)
X2_train, X2_test, y2_train, y2_test = train_test_split(X2, y2, test_size=0.20, random_state=123)

rfc = RandomForestClassifier(n_estimators=200, n_jobs=2, random_state=0)   #.values gives the values in an array of shape (n,1)
default_model = rfc.fit(X1_train, y1_train.values.ravel())     #.ravel() converts array to shape (n,)
not_default_model = rfc.fit(X2_train, y2_train.values.ravel())

default_pred = default_model.predict(X1_test)
not_default_pred = not_default_model.predict(X2_test)

metrics.accuracy_score(y1_test, default_pred)
Accuracy =  0.36814276272306673

metrics.accuracy_score(y2_test, not_default_pred)
Accuracy =  0.6038167938931298
