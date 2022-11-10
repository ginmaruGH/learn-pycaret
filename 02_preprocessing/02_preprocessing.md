# [Preprocessing（前処理）](https://pycaret.gitbook.io/docs/get-started/preprocessing)

This page lists all the data preprocessing and transformation parameters in the setup.

このページでは、セットアップにおけるすべてのデータ前処理および変換パラメータを一覧表示します。

<!-- TOC -->
- [Preprocessing（前処理）](#preprocessing前処理)
  - [Data Preparation（データ準備）](#data-preparationデータ準備)
    - [Missing Values（欠測値）](#missing-values欠測値)
    - [Data Types（データ型）](#data-typesデータ型)
    - [One-Hot Encoding（ワンホットエンコーディング）](#one-hot-encodingワンホットエンコーディング)
    - [Ordinal Encoding（順序エンコーディング）](#ordinal-encoding順序エンコーディング)
    - [Cardinal Encoding（基本エンコーディング）](#cardinal-encoding基本エンコーディング)
    - [Handle Unknown Levels（未知のレベルの扱い）](#handle-unknown-levels未知のレベルの扱い)
    - [Target Imbalance（ターゲット不均衡）](#target-imbalanceターゲット不均衡)
    - [Remove Outliers（外れ値の除去）](#remove-outliers外れ値の除去)
  - [Scale and Transform（尺度と変換）](#scale-and-transform尺度と変換)
    - [Normalize（正規化）](#normalize正規化)
    - [Feature Transform（特徴量変換）](#feature-transform特徴量変換)
    - [Target Transform（ターゲット変換）](#target-transformターゲット変換)
  - [Feature Engineering（特徴量エンジニアリング）](#feature-engineering特徴量エンジニアリング)
    - [Feature Interaction（特徴量の相互作用）](#feature-interaction特徴量の相互作用)
    - [Polynomial Features（多項式特徴量）](#polynomial-features多項式特徴量)
    - [Trigonometry Features（三角法の特徴量）](#trigonometry-features三角法の特徴量)
    - [Group Features（グループの特徴量）](#group-featuresグループの特徴量)
    - [Bin Numeric Features（ビン数値特徴量）](#bin-numeric-featuresビン数値特徴量)
    - [Combine Rare Levels（レアレベルの組み合わせ）](#combine-rare-levelsレアレベルの組み合わせ)
    - [Create Clusters（クラスターの作成）](#create-clustersクラスターの作成)
  - [Feature Selection（特徴量の選択）](#feature-selection特徴量の選択)
    - [Feature Selection（特徴量の選択）](#feature-selection特徴量の選択-1)
    - [Remove Multicollinearity（多重共線性の除去）](#remove-multicollinearity多重共線性の除去)
    - [Principal Component Analysis（主成分分析）](#principal-component-analysis主成分分析)
    - [Ignore Low Variance（分散が小さい場合は無視する）](#ignore-low-variance分散が小さい場合は無視する)
  - [Other setup parameters（その他の設定パラメータ）](#other-setup-parametersその他の設定パラメータ)
    - [Required Parameters（必須パラメータ）](#required-parameters必須パラメータ)
    - [Experiment Logging（実験ログの記録）](#experiment-logging実験ログの記録)
    - [Model Selection（モデル選択）](#model-selectionモデル選択)
    - [Other Miscellaneous（その他雑多なもの）](#other-miscellaneousその他雑多なもの)

## [Data Preparation（データ準備）](https://pycaret.gitbook.io/docs/get-started/preprocessing/data-preparation)

### [Missing Values（欠測値）](02-01_data_preparation.ipynb#missing_values)

Datasets for various reasons may have missing values or empty records, often encoded as blanks or NaN. Most of the machine learning algorithms are not capable of dealing with the missing values.

データセットにはさまざまな理由で欠損値や空のレコードがあり、しばしば空白やNaNとしてエンコードされます。機械学習アルゴリズムの多くは、このような欠損値を扱うことができません。

### [Data Types（データ型）](02-01_data_preparation.ipynb#data_types)

Each feature in the dataset has an associated data type such as numeric, categorical, or Datetime. PyCaret automatically detects the data type of each feature.

データセット内の特徴量には、Numeric、Categorical、Datetime などのデータ型が関連付けられています。PyCaret は各特徴のデータ型を自動的に検出します。

### [One-Hot Encoding（ワンホットエンコーディング）](02-01_data_preparation.ipynb#one_hot_encoding)

Categorical features in the dataset contain the label values (ordinal or nominal) rather than continuous numbers. Most of the machine learning algorithms are not capable of handling categorical data without encoding.

データセット中のカテゴリ特徴量には、連続数ではなくラベル値（順序または名義）が含まれます。機械学習アルゴリズムの多くは、エンコーディングを行わないとカテゴリデータを扱うことができません。

### [Ordinal Encoding（順序エンコーディング）](02-01_data_preparation.ipynb#ordinal_encoding)

When the categorical features in the dataset contain variables with intrinsic natural order such as Low, Medium, and High, these must be encoded differently than nominal variables (where there is no intrinsic order for e.g. Male or Female).

データセット内のカテゴリ特徴量にLow, Medium, Highのような自然順位を持つ変数がある場合、名目変数（男性、女性などの自然順位のない変数）とは異なる方法でエンコードする必要があります。

### [Cardinal Encoding（基本エンコーディング）](02-01_data_preparation.ipynb#cardinal_encoding)

When categorical features in the dataset contain variables with many levels (also known as high cardinality features), then typical One-Hot Encoding leads to the creation of a very large number of new features.

データセット内のカテゴリ特徴量が多値の変数（高基準特徴量）を含む場合、従来のOne-Hot Encodingでは非常に多くの新規特徴量を生成してしまいます。

### [Handle Unknown Levels（未知のレベルの扱い）](02-01_data_preparation.ipynb#handle_unknown_levels)

When categorical features in the dataset contain unseen variables at the time of predictions, it may cause problems for the trained model as those levels were not present at the time of training.

データセット内のカテゴリ特徴量が予測時に未知の変数が含まれる場合、学習時にそのレベルが存在しないため、学習済みモデルに問題が生じることもあります。

### [Target Imbalance（ターゲット不均衡）](02-01_data_preparation.ipynb#target_imbalance)

When the training dataset has an unequal distribution of target class it can be fixed using the `fix_imbalance` parameter in the setup.

学習データセットにターゲットクラスの不均衡がある場合、セットアップの `fix_imbalance` パラメータで修正できます。

### [Remove Outliers（外れ値の除去）](02-01_data_preparation.ipynb#remove_outliers)

The `remove_outliers` function in PyCaret allows you to identify and remove outliers from the dataset before training the model.

PyCaretの `remove_outliers` 関数を使うと、モデルを学習する前にデータセットから外れ値を識別して取り除くことができます。

---

## [Scale and Transform（尺度と変換）](https://pycaret.gitbook.io/docs/get-started/preprocessing/scale-and-transform)

### [Normalize（正規化）](02-02_scale_and_transform.ipynb#normalize)

Normalization is a technique often applied as part of data preparation for machine learning. The goal of normalization is to rescale the values of numeric columns in the dataset without distorting the differences in the ranges of values.

正規化とは、機械学習のためのデータ準備の一環としてしばしば適用される手法です。正規化の目的は、データセットの数値列の値を、値の範囲の違いを歪めることなく再スケール化することです。

### [Feature Transform（特徴量変換）](02-02_scale_and_transform.ipynb#feature_transform)

While normalization rescales the data within new limits to reduce the impact of magnitude in the variance, Feature transformation is a more radical technique. Transformation changes the shape of the distribution.

正規化とはデータを新しい範囲に再尺度化し、分散の大きさの影響を小さくすることです。特徴量変換はより根本的な手法です。分布の形状を変化させます。

### [Target Transform（ターゲット変換）](02-02_scale_and_transform.ipynb#target_transform)

Target Transformation is similar to feature transformation as it will change the shape of the distribution of the target variable instead of the features.

ターゲット変換は、特徴量変換と同様に、特徴量ではなくターゲット変数の分布の形状を変更するものです。

---

## [Feature Engineering（特徴量エンジニアリング）](https://pycaret.gitbook.io/docs/get-started/preprocessing/feature-engineering)

### [Feature Interaction（特徴量の相互作用）](./02-03_feature_engineering.ipynb#feature_interaction)

It is often seen in machine learning experiments when two features combined through an arithmetic operation become more significant in explaining variances in the data than the same two features separately.

機械学習の実験では、2つの特徴量を演算によって組み合わせることで、同じ2つの特徴量を別々に扱うよりもデータの分散を説明する上で有意になることがよく見られます。

### [Polynomial Features（多項式特徴量）](./02-03_feature_engineering.ipynb#polynomial_feature)

In machine learning experiments the relationship between the dependent and independent variable is often assumed as linear, however, this is not always the case. Sometimes the relationship between dependent and independent variables is more complex.

機械学習の実験では、従属変数と独立変数の関係は線形であると仮定されることが多いですが、常にそうであるとは限りません。従属変数と独立変数の関係はより複雑であることがあります。

### [Trigonometry Features（三角法の特徴量）](./02-03_feature_engineering.ipynb#trigonometry_features)

Similar to Polynomial Features, PyCaret also allows creating new trigonometry features from the existing features.

多項式特徴量と同様に、PyCaretでも既存の特徴量から新しい三角法特徴量を作成できます。

### [Group Features（グループの特徴量）](./02-03_feature_engineering.ipynb#group_features)

When a dataset contains features that are related to each other in some way, for example, features recorded at some fixed time intervals, then new statistical features such as mean, median, variance, and standard deviation for a group of such features.

データセットに、ある一定の時間間隔で記録された特徴量など、何らかの形で互いに関連する特徴量が含まれている場合、そのような特徴量のグループに対する平均、中央値、分散、標準偏差などの新しい統計的特徴量を提供します。

### [Bin Numeric Features（ビン数値特徴量）](./02-03_feature_engineering.ipynb#bin_numeric_features)

Feature binning is a method of turning continuous variables into categorical values using the pre-defined number of bins. It is effective when a continuous feature has too many unique values or few extreme values outside the expected range.

特徴量のビン化とは、あらかじめ設定された数のビンを用いて連続変数をカテゴリ値に変換する方法です。連続特徴量に一意な値が多すぎる場合や、予想範囲外の極端な値が少ない場合に有効です。

### [Combine Rare Levels（レアレベルの組み合わせ）](./02-03_feature_engineering.ipynb#combine_rare_levels)

Sometimes a dataset can have a categorical feature (or multiple categorical features) that has a very high number of levels (i.e. high cardinality features). If such feature (or features) are encoded into numeric values, then the resultant matrix is a sparse matrix.

データセットには、非常に多くのレベルを持つカテゴリカル特徴量（または複数のカテゴリカル特徴量）がある場合もあります（すなわち、高基準の特徴量）。このような特徴量を数値に置き換えると、結果として得られる行列は疎行列となります。

### [Create Clusters（クラスターの作成）](./02-03_feature_engineering.ipynb#)

Creating Clusters using the existing features from the data is an unsupervised ML technique to engineer and create new features.

既存の特徴量を利用してクラスタを作成することは、新しい特徴量を設計・作成する教師なしML手法です。

---

## [Feature Selection（特徴量の選択）](https://pycaret.gitbook.io/docs/get-started/preprocessing/feature-selection)

### [Feature Selection（特徴量の選択）]()

Feature Selection is a process used to select features in the dataset that contributes the most in predicting the target variable. Working with selected features instead of all the features reduces the risk of over-fitting, improves accuracy, and decreases the training time.

特徴量選択とは、データセットの中からターゲット変数の予測にもっとも貢献する特徴を選択するためのプロセスです。すべての特徴量ではなく、選択された特徴量で作業を行うことで、オーバーフィットのリスクを減らし精度を向上させ、学習時間を短縮できます。

### [Remove Multicollinearity（多重共線性の除去）]()

Multicollinearity (also called collinearity) is a phenomenon in which one feature variable in the dataset is highly linearly correlated with another feature variable in the same dataset.

多重共線性（共線性ともいう）とは、データセット内のある特徴変数が、同じデータセット内の別の特徴変数と高い線形相関を持つ現象のことです。

### [Principal Component Analysis（主成分分析）]()

Principal Component Analysis (PCA) is an unsupervised technique used in machine learning to reduce the dimensionality of the data. It does so by compressing the feature space.

主成分分析（PCA）は、機械学習においてデータの次元を減らすために用いられる教師なし手法です。これは、特徴空間を圧縮することによって行われます。

### [Ignore Low Variance（分散が小さい場合は無視する）]()

Sometimes a dataset may have a categorical feature with multiple levels, where the distribution of such levels is skewed and one level may dominate over other levels.

データセットには、複数のレベルを持つカテゴリカル特徴量があり、そのレベルの分布が歪んでいて、あるレベルが他のレベルより優勢になることがあります。

---

## [Other setup parameters（その他の設定パラメータ）](https://pycaret.gitbook.io/docs/get-started/preprocessing/other-setup-parameters)

### [Required Parameters（必須パラメータ）]()

There are only two non-optional parameters in the setup function i.e. data and name of the target variable.

set 関数のオプションでないパラメータは、データとターゲット変数の名前の2つだけです。

### [Experiment Logging（実験ログの記録）]()

PyCaret uses MLflow for experiment tracking. A parameter in the setup can be set to automatically track all the metrics, hyperparameters, and other model artifacts.

PyCaretは実験のトラッキングにMLflowを使用しています。セットアップのパラメータを設定することで、すべてのメトリクス、ハイパーパラメータ、その他のモデルの成果物を自動的に追跡できます。

### [Model Selection（モデル選択）]()

Parameters in the setup can be used for setting parameters for the model selection process. These are not related to data preprocessing but can influence your model selection process.

セットアップのパラメータは、モデル選択プロセスのパラメータ設定に使用できます。これらはデータの前処理とは関係ありませんが、モデル選択処理に影響を与えることがあります。

### [Other Miscellaneous（その他雑多なもの）]()

Other miscellaneous parameters in the setup that are used for controlling experiment settings such as using GPU for training or setting verbosity of the experiment

トレーニングにGPUを使用したり、実験の冗長性を設定するなど、実験設定を制御するために使用されるセットアップ内のその他の雑多なパラメータ。

---
