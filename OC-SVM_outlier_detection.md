Introduction
---

The result of one-class svm doesn't seem to be good, so we plan to look into the real data (to check the excel form of data directly) to see if there's any insight.

We checked `A-BFP運転データ(異常)` and `A-BFP運転データ(正常)` for every RUN X file which matches with `Aボイラのみ稼働` pattern, from data in [here](https://drive.google.com/drive/folders/0B-VyaNCvKIeGTVVycEQwakMxc2s)


Average, Minimum, Maximum
---

Firstly, I can only think about the value of average, minimum, and maximum.

<details>
<summary>Tables Here</summary>

A to I correspondingly means:

|   | A                         | B                                | C                                  | D                            | E                                           | F                                             | G               | H                         | I                         |
|---|---------------------------|----------------------------------|------------------------------------|------------------------------|---------------------------------------------|-----------------------------------------------|-----------------|---------------------------|---------------------------|
|   | 1J0032 Aﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ電流 | 1J0030 ﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ出口給水流量 | 1J0019 Aﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ入口ｽﾄﾚ-ﾅ差圧 | 1J0014 ﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ出口圧力 | 1J0024 Aﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ用電動機軸受温度(CP側) | 1J0026 Aﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ用電動機軸受温度(反CP側) | 1R0000 大気温度 | 1P0028 ﾊﾞ-ﾅ冷却水戻り温度 | 1J0033 Bﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ電流 |

**A-BFP運転データ(異常)**

|         | A      | B      | C    | D    | E      | F      | G      | H      | I      |
|---------|--------|--------|------|------|--------|--------|--------|--------|--------|
| average | 18.48  | 34.13  | 0.72 | 7.58 | 50.61  | 35.17  | 12.16  | 45.70  | 0.027  |
| min     | 15.50  | 16.86  | 0.23 | 6.80 | 33.44  | 21.13  | 2.22   | 39.78  | 0.004  |
| max     | 20.80  | 49.35  | 1.22 | 8.20 | 70.35  | 60.13  | 21.5   | 52.20  | 0.041  |
| count   | 35,401 | ←      | ←    | ←    | ←      | ←      | ←      | ←      | ←      |


**A-BFP運転データ(正常) RUN 48**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 17.81  | 31.98 | 0.76 | 7.64 | 46.68 | 31.77 | 9.34  | 45.86 | 0.019 |
| min     | 14.89  | 15.32 | 0.12 | 7.29 | 30.10 | 19.75 | 0.93  | 38.40 | 0.001 |
| max     | 19.13  | 39.86 | 1.24 | 8.29 | 61.13 | 43.32 | 18.07 | 51.87 | 0.034 |
| count   | 10,081 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 49**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 18.15  | 34.25 | 0.76 | 7.54 | 50.49 | 35.53 | 13.28 | 50.18 | 0.027 |
| min     | 14.72  | 14.46 | 0.17 | 7.16 | 35.03 | 25.05 | 6.85  | 38.01 | 0.018 |
| max     | 19.43  | 41.98 | 1.11 | 8.27 | 62.77 | 46.40 | 21.17 | 58.88 | 0.041 |
| count   | 10,081 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 50-1**

|         | A     | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|-------|-------|------|------|-------|-------|-------|-------|-------|
| average | 17.29 | 28.42 | 0.63 | 7.78 | 58.77 | 44.27 | 19.81 | 45.72 | 0.039 |
| min     | 13.99 | 9.83  | 0.14 | 7.36 | 49.44 | 39.46 | 18.89 | 38.49 | 0.032 |
| max     | 18.87 | 38.22 | 1.06 | 8.40 | 65.18 | 48.22 | 22.50 | 51.64 | 0.041 |
| count   | 2,881 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 50-2**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 17.66  | 31.18 | 0.66 | 7.67 | 64.98 | 50.35 | 26.52 | 48.60 | 0.043 |
| min     | 14.86  | 15.06 | 0.20 | 7.32 | 50.04 | 42.16 | 20.55 | 40.95 | 0.038 |
| max     | 18.82  | 38.71 | 1.05 | 8.29 | 82.98 | 62.39 | 32.25 | 52.85 | 0.061 |
| count   | 11,521 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 50**

|         | A     | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|-------|-------|------|------|-------|-------|-------|-------|-------|
| average | 15.36 | 17.30 | 0.34 | 8.21 | 57.22 | 42.37 | 20.36 | 41.34 | 0.039 |
| min     | 14.80 | 15.37 | 0.21 | 7.56 | 50.35 | 38.07 | 18.71 | 35.24 | 0.034 |
| max     | 18.20 | 33.91 | 0.83 | 8.29 | 62.40 | 46.26 | 21.95 | 50.50 | 0.041 |
| count   | 1,441 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 51**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 18.32  | 33.63 | 0.85 | 7.56 | 59.77 | 44.07 | 18.90 | 46.61 | 0.040 |
| min     | 15.19  | 0     | 0.37 | 6.73 | 53.32 | 38.70 | 13.89 | 39.61 | 0.031 |
| max     | 20.84  | 41.52 | 1.51 | 8.24 | 65.67 | 50.04 | 23.72 | 51.40 | 0.043 |
| count   | 15,841 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 53-1**

|         | A     | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|-------|-------|------|------|-------|-------|-------|-------|-------|
| average | 15.86 | 20.13 | 0.49 | 8.13 | 59.31 | 41.88 | 20.33 | 43.37 | 0.037 |
| min     | 14.48 | 12.91 | 0.29 | 6.93 | 52.59 | 38.76 | 19.49 | 39.48 | 0.029 |
| max     | 20.06 | 46.81 | 1.12 | 8.33 | 66.33 | 43.96 | 21.78 | 49.35 | 0.041 |
| count   | 1,441 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 53-2**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 18.25  | 33.75 | 0.81 | 7.58 | 56.93 | 45.35 | 21.71 | 48.64 | 0.039 |
| min     | 15.16  | 16.18 | 0.35 | 7.11 | 45.02 | 38.69 | 19.08 | 39.18 | 0.028 |
| max     | 19.81  | 43.26 | 1.20 | 8.26 | 71.65 | 50.69 | 28.09 | 54.21 | 0.043 |
| count   | 12,961 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 54-1**

|         | A      | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|--------|-------|------|------|-------|-------|-------|-------|-------|
| average | 18.22  | 33.43 | 0.71 | 7.59 | 57.17 | 50.46 | 27.41 | 49.59 | 0.047 |
| min     | 15.32  | 17.55 | 0.22 | 6.92 | 52.44 | 45.91 | 24.70 | 42.51 | 0.041 |
| max     | 20.11  | 47.08 | 1.20 | 8.26 | 61.58 | 53.93 | 32.48 | 53.49 | 0.062 |
| count   | 11,521 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

**A-BFP運転データ(正常) RUN 54**

|         | A     | B     | C    | D    | E     | F     | G     | H     | I     |
|---------|-------|-------|------|------|-------|-------|-------|-------|-------|
| average | 16.83 | 25.62 | 0.54 | 7.91 | 54.60 | 47.15 | 27.00 | 48.99 | 0.044 |
| min     | 15.41 | 17.89 | 0.23 | 7.22 | 51.36 | 42.19 | 25.22 | 43.68 | 0.040 |
| max     | 19.30 | 40.68 | 1.07 | 8.23 | 58.24 | 51.39 | 29.85 | 68.84 | 0.056 |
| count   | 1,441 | ←     | ←    | ←    | ←     | ←     | ←     | ←     | ←     |

</details>

By seeing the average, min, max values between `A-BFP運転(正常)` and `A-BFP運転(異常)` tables, I am afraid that I can not tell the difference between them.


The Shape of Data
---

One-class SVM is an unsupervised algorithm that learns a decision function for novelty detection: classifying new data as similar or different to the training set.

And some say that using the One-Class SVM and its ability to capture the shape of the data set, hence performing better when the data is strongly non-Gaussian, i.e. with two well-separated clusters;

I hope I did not mistake it.

So I just plot the histogram for in [this example1][R6], and getting a plot like this:
<<<<<<<PUT YOUR RESULT>>>>>>>>

And now I am wondering how `A-BFP運転データ(正常)` looks like.

Just try only for **A-BFP運転データ(正常) RUN 48**:

`A` to `I` correspondingly means the feature/column (1J0032 Aﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ電流, 1J0030 ﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ出口給水流量, ..., 1J0033 Bﾎﾞｲﾗ給水ﾎﾟﾝﾌﾟ電流) in the training dataset.

<<<<<<<PUT YOUR RESULT>>>>>>>>
<<<<<<<PUT YOUR RESULT>>>>>>>>
<<<<<<<PUT YOUR RESULT>>>>>>>>
<<<<<<<PUT YOUR RESULT>>>>>>>>

The last picture does not seem to be easy to understand. However, the feature/column `A`, `B`, `C` seem to be well-separated. While `G` to `I` seems like a Gaussian distributed dataset.

What if we only feed Column `A` to `C` into the one-class SVM model? I am not sure. Do you have any advice?





RBF One-Class SVM parameters
---

Three parameters we may know in RBF SVM: C, nu, and gamma.

The relation between C and nu is governed by the following formula:

```
nu = A+B/C
```
A and B are constants. So we can see `nu` and `C` are in an inverse relation.


I will skip the definitions of all the parameters and just jump to a table like this:

|       | low value                         | high value                        |
|-------|-----------------------------------|-----------------------------------|
| C     | small number of SVs, underfitting | large number of SVs, overfitting  |
| nu    | large number of SVs, overfitting  | small number of SVs, underfitting |
| gamma | large number of SVs, overfitting  | small number of SVs, underfitting |

So you see the precision heatmap of `A-BFP運転データ`:

`nu = 0.01` means we want almost zero tolerance in errors for traning data. The model may select a large number of SVs which is easy to cause overfitting with the training data. Therefore, with combination of any `gamma` value, the precision of normal test data is very high. While the precision of abnormal test data is relatively low.


The precision heatmap of `中圧窒素運電データ` is as well.



Try Other Outlier Detection Model
---

I am not sure if the performance of One-Class SVM might change depending on the data distribution, I mean, *the way how data is seperated*. I am wondering this because the examples I have seen([example1][R6]), they technically generate the training dataset with two well-separated clusters.

Just for giving a quick try, I have referred to this tutorial: [Outlier detection with several methods][R5], and tried the other two models called `Robust covariance` and `Isolation Forest`.

### Robust covariance

This is a model for detecting outliers in a Gaussian distributed dataset. Although we do not know the distribution and how it looks like of our high-dimensional data, I still plan to try it out.

The proportion of outliers in the data set needs to be set as a parameter. Since we do not know the amount of outlier, I ran the program with range of `outliers_fraction = [0.01, 0.03, 0.05, 0.1, 0.3, 0.5 ,1]`.

Below is the result of fitting **A-BFP運転データ**.
<<<<<<<PUT YOUR RESULT>>>>>>>

However, the performance is not better than One-Class SVM.


### Isolation Forest

When trying to import the library of `IsolationForest` model, an error message says:

```
ImportErrorTraceback (most recent call last)
<ipython-input-5-58be3052909f> in <module>()
      5 from sklearn import svm
      6 from sklearn.covariance import EllipticEnvelope
----> 7 from sklearn.ensemble import IsolationForest
      8 import matplotlib.pyplot as plt
      9 import timeit

ImportError: cannot import name IsolationForest
```

This is because `IsolationForest` needs the version of sklearn >= 0.18. Currently sklearn in Datalab is 0.17.1. It is not recommended to update packages which are installed in Datalab by default([ref][R4]). So I skipped to do an experiment with `IsolationForest` model.


Reference
---
- [sklearn.svm.OneClassSVM][R1]
- [RBF SVM parameters][R2]
- [Does the parameter C affect one class SVM?][R3]
- [Outlier detection with several methods][R5]
- [One-class SVM with non-linear kernel (RBF)][R6]

[R1]: http://scikit-learn.org/stable/modules/generated/sklearn.svm.OneClassSVM.html#sklearn.svm.OneClassSVM
[R2]: http://scikit-learn.org/stable/auto_examples/svm/plot_rbf_parameters.html
[R3]: https://www.quora.com/Does-the-parameter-C-affect-one-class-SVM
[R4]: http://stackoverflow.com/questions/36692174/running-sklearn-0-17-in-google-cloud-datalab
[R5]: http://scikit-learn.org/stable/auto_examples/covariance/plot_outlier_detection.html
[R6]: http://scikit-learn.org/stable/auto_examples/svm/plot_oneclass.html#sphx-glr-auto-examples-svm-plot-oneclass-py

