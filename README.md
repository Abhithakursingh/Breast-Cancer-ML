 Breast-Cancer-ML
import numpy as np
import pandas as pd
from sklearn import model_selection,neighbors,preprocessing

df=pd.read_csv('E:\Breast-cancer-wisconsin.data.txt')
df.replace('?',-99999,inplace=True)
df.drop(df['id'],1,inplace=True)

X=np.array(df.drop(['class'],1))
y=np.array(df['class'])

X_train,X_test,y_train,y_test=model_selection.train_test_split(X,y,test_size=0.2)

clf=neighbors.KNeighborsClassifier()

clf.fit(X_train,y_train)
confidence=clf.score(X_test,y_test)
print(confidence)
