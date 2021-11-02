dtc = DecisionTreeClassifier(max_depth=5)
dtc_model = dtc.fit(X_train, y_train)

rfc = RandomForestClassifier(n_estimators=500, n_jobs=2, random_state=0)   #.values gives the values in an array of shape (n,1)\
rfc_model = rfc.fit(X_train, y_train.values.ravel())     #.ravel() converts array to shape (n,)\

from sklearn import tree \'96 for Decision tree visualization}
