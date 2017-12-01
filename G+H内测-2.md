* 文字问题：
1. `thin`和`fat`的`1`和`0`反了
2. `Problem 2`的题目表述中重复了单词：`buying buying price`

* 内容问题
  在我做完了之后感觉题目难度不高，但做的时候难度很高。主要原因是需要使用的其他函数的用途不明确，比如`problem 1`中的`map()`函数，`data['status'].map({'thin':0, 'fat':1}).astype(int)`这一串代码不查肯定不会，我查了也还是不会，建议这一题的代码这样让学生写：

```Python
# grader format
import pandas as pd
import numpy as np
from sklearn import tree
def tree_test(x_test):

    # YOUR CODE HERE
    data = pd.read_csv('./pbl-ch3-weight.csv') #读取数据
    data['status'] = data['status'].map({'thin':0, 'fat':1}).astype(int) #这行代码用于将数据进行转化，即将thin转化为0，将fat转化为1
    data_tmp=data.values #这行代码用于将表头去掉

    x_train=data_tmp[:,0:2] #...
    y_train=data_tmp[:,2] #...
   
    '''这段注释中的代码让学生来写
    clf = tree.DecisionTreeClassifier()
    clf.fit(x_train, y_train)
    result = clf.predict(x_test)
    '''
    return result

    raise NotImplementedError()
```

例如上面的代码，让学生写的代码只有三行，是和AI相关的内容，而上面的几行我们帮学生写的代码，作为代码+注释的形式写给学生，让学生能够看懂就可以了

`Problem 2`的第一题，我建议把下面两行代码给到学生，并加上注释

```Python
le = LabelEncoder() #这里需要用到的LabelEncoder()是用于...
le.fit(ds[name]) #这里将需要的data的指定列传入，将其内部所有的标签进行归类编码
```
然后剩下的内容让学生进行编写，学生可以有一定的思路