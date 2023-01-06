# slip20


Q.1 Write a Java Program to implement I/O Decorator for converting uppercase letters to
lower case letters.
Q.2. Write a python program to implement Decision Tree whether or not to play Tennis.



Q.1 Write a Java Program to implement I/O Decorator for converting uppercase letters to
lower case letters.

:import java.io.FilterInputStream;
import java.io.IOException;
import java.io.InputStream;

public class LowerCaseInputStream extends FilterInputStream {
    public LowerCaseInputStream(InputStream in) {
        super(in);
    }

    public int read() throws IOException {
        int c = super.read();
        return (c == -1 ? c : Character.toLowerCase((char) c));
    }

    public int read(byte[] b, int offset, int len) throws IOException {
        int result = super.read(b, offset, len);
        for (int i = offset; i < offset + result; i++) {
            b[i] = (byte) Character.toLowerCase((char) b[i]);
        }
        return result;
    }
}


Q.2. Write a python program to implement Decision Tree whether or not to play Tennis.

://My current code in python: 
from sklearn.cross_validation import train_test_split 
from sklearn.tree import DecisionTreeClassifier 
from sklearn.metrics import accuracy_score 
from sklearn import tree 
from sklearn.preprocessing import LabelEncoder

import pandas as pd 
import numpy as np 

df = pd.read_csv('playTennis.csv') 

lb = LabelEncoder() 
df['outlook_'] = lb.fit_transform(df['outlook']) 
df['temp_'] = lb.fit_transform(df['temp'] ) 
df['humidity_'] = lb.fit_transform(df['humidity'] ) 
df['windy_'] = lb.fit_transform(df['windy'] )   
df['play_'] = lb.fit_transform(df['play'] ) 
X = df.iloc[:,5:9] 
Y = df.iloc[:,9]

X_train, X_test , y_train,y_test = train_test_split(X, Y, test_size = 0.3, random_state = 100) 

clf_entropy = DecisionTreeClassifier(criterion='entropy')
clf_entropy.fit(X_train.astype(int),y_train.astype(int)) 
y_pred_en = clf_entropy.predict(X_test)

print("Accuracy is :{0}".format(accuracy_score(y_test.astype(int),y_pred_en) * 100))


//If you would skip this line:
X_train, X_test , y_train,y_test = train_test_split(X, Y, test_size = 0.3, random_state = 100)


//and change the method parameters to train your model like this:
clf_entropy.fit(X, Y)






