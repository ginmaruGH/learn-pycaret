# [Function（関数）](https://pycaret.gitbook.io/docs/get-started/functions)

This page lists all the functions of PyCaret

このページでは、PyCaret の全関数をリストアップします。

## [Initialize（初期化）](./03_01_initialize.ipynb)

### setup

This function initializes the experiment in PyCaret and prepares the transformation pipeline based on all the parameters passed in the function. The setup function must be called before executing any other function. It only requires two parameters: data and target. All the other parameters are optional.

この関数は、PyCaret の実験を初期化し、関数内で渡されたすべてのパラメータに基づいて変換パイプラインを準備します。setup 関数は、他の関数を実行する前に呼び出す必要があります。この関数が必要とするパラメータは、data と target の 2 つだけです。他のパラメータはすべてオプションです。

---

## [Train（訓練）](./03_02_train.ipynb)

### compare_models

This function trains and evaluates the performance of all the models available in the model library using cross-validation. The output of this function is a scoring grid with average cross-validated scores.

この関数は、モデルライブラリで利用可能なすべてのモデルについて、交差検証を用いて学習と性能評価を行います。この関数の出力は、交差検証された平均スコアを持つスコアリンググリッドです。

### create_model

This function trains and evaluates the performance of a given model using cross-validation. The output of this function is a scoring grid with cross-validated scores along with mean and standard deviation.

この関数は、交差検証を利用して、与えられたモデルの性能を学習および評価します。この関数の出力は、交差検証されたスコアと平均および標準偏差を含むスコアリンググリッドです。

---

## [Optimize（最適化）](./03_03_optimize.ipynb)

### tune_model

This function tunes the hyperparameters of a given model. The output of this function is a scoring grid with cross-validated scores of the best model. Search spaces are pre-defined with the flexibility to provide your own. The search algorithm can be random, bayesian, and a few others with the ability to scale on large clusters.

この関数は、与えられたモデルのハイパーパラメータを調整します。この関数の出力は、最良のモデルの交差検証済みスコアを含むスコアリンググリッドです。探索空間はあらかじめ定義されているが、独自の空間を提供することも可能です。探索アルゴリズムは、ランダム探索、ベイジアン探索、および大規模クラスタでのスケールアップが可能な他のいくつかのアルゴリズムを使用できます。

### ensemble_model

This function ensembles a given model. The output of this function is a scoring grid with cross-validated scores of the ensembled model. Two methods `Bagging` or `Boosting` can be used for ensembling.

この関数は、与えられたモデルをアンサンブルします。この関数の出力は、アンサンブルされたモデルの交差検証されたスコアを含むスコアリンググリッドです。アンサンブルには、`Bagging` と `Boosting` の2つの手法があります。

### blend_models

This function trains a Soft Voting / Majority Rule classifier for given models in a list. The output of this function is a scoring grid with cross-validated scores of a Voting Classifier or Regressor.

この関数は、リスト内の指定されたモデルに対して、ソフト投票/多数決分類器を学習します。この関数の出力は、Voting Classifier または Regressor の交差検証されたスコアを含むスコアリンググリッドです。

### stack_models

This function trains a meta-model over given models in a list. The output of this function is a scoring grid with cross-validated scores of a Stacking Classifier or Regressor.

この関数は、リスト内の指定されたモデルに対してメタモデルを学習させます。この関数の出力は、スタッキング分類器またはリグレッサの交差検証されたスコアを持つスコアリンググリッドです。

### optimize_threshold

This function optimizes the probability threshold for a given model. It iterates over performance metrics at different probability thresholds and returns a plot with performance metrics on the y-axis and threshold on the x-axis.

この関数は、与えられたモデルの確率の閾値を最適化します。異なる確率の閾値におけるパフォーマンスメトリクスを繰り返し、パフォーマンスメトリクスをY軸に、閾値をX軸にとったプロットを返します。

### calibrate_model

This function calibrates the probability of a given model using isotonic or logistic regression. The output of this function is a scoring grid with cross-validated scores of calibrated classifier.

この関数は、等張回帰またはロジスティック回帰を用いて、与えられたモデルの確率を校正します。この関数の出力は、校正された分類器の交差検証されたスコアを含むスコアリンググリッドです。

---

## [Analyze（分析）](./03_04_analyze.ipynb)

### plot_model

This function analyzes the performance of a trained model on the hold-out set. It may require re-training the model in certain cases.

この関数は、ホールドアウトセットにおける学習済みモデルのパフォーマンスを分析します。場合によっては、モデルの再トレーニングが必要になることがあります。

### evaluate_model

This function uses `ipywidgets` to display a basic user interface for analyzing the performance of a trained model.

この関数は `ipywidgets` を用いて、学習済みモデルの性能を分析するための基本的なユーザインタフェースを表示します。

### interpret_model

This function analyzes the predictions generated from a trained model. Most plots in this function are implemented based on the SHAP (Shapley Additive exPlanations).

この関数は、学習済みモデルから生成された予測値を解析します。この関数のほとんどのプロットは、SHAP (Shapley Additive exPlanations) に基づいて実装されています。

### dashboard

This function generates the interactive dashboard for a trained model. The dashboard is implemented using the ExplainerDashboard project.

この関数は、学習済みモデルの対話型ダッシュボードを生成します。ダッシュボードは、ExplainerDashboardプロジェクトを使用して実装されています。

### deep_check

This function runs a full suite check over a trained model using the deepchecks library. This function is in experimental mode.

この関数は、deepchecksライブラリを用いて、学習済みモデルに対する完全なスイートチェックを実行します。この関数は実験モードです。

### eda

This function generates automated Exploratory Data Analysis (EDA) using the AutoViz project. Fully interactive and exportable.

AutoVizプロジェクトを用いた探索的データ解析（EDA）を自動生成する機能です。完全にインタラクティブでエクスポート可能です。

### check_fairness

This function provides fairness-related metrics between different groups in the dataset for a given model. There are many approaches to evaluate fairness but this function uses the approach known as group fairness, which asks: which groups of individuals are at risk for experiencing harm.

この関数は、与えられたモデルのデータセットにおける異なるグループ間の公平性に関連する指標を提供します。公平性を評価するアプローチはたくさんありますが、この関数では「どのグループの個体が損害を被るリスクがあるか」を問う、グループ公平性として知られるアプローチを使用しています。

### get_leaderboard

This function returns the leaderboard of all models trained in the current setup.

この関数は、現在の設定で学習させた全モデルのリーダーボードを返します。

### assign_model

This function assigns labels to the training dataset using the trained model. It is only available for unsupervised modules.

この関数は、学習済みモデルを用いて学習データセットにラベルを付与します。教師なしモジュールでのみ利用可能です。

---

## [Deploy（配備・展開）](./03_05_deploy.ipynb)

### predict_model

This function generates the label using a trained model.  When unseen data is not passed, it predicts the label and score on the holdout set.

この関数は、学習されたモデルを用いてラベルを生成します。 未経験のデータが渡されない場合は、ホールドアウト・セットでラベルとスコアを予測します。

### finalize_model

This function refits a given model on the entire dataset.

この関数は、データセット全体に対して、与えられたモデルを再フィットします。

### save_model

This function saves the ML pipeline as a pickle file for later use.

この機能は、MLパイプラインを後で使用するためにpickleファイルとして保存します。

### load_model

This function loads a previously saved pipeline.

過去に保存したパイプラインをロードする機能です。

### save_config

This function saves all the global variables to a pickle file, allowing to later resume without rerunning the setup function.

この関数は、すべてのグローバル変数を pickle ファイルに保存し、セットアップ関数を再実行することなく、あとで再開できます。

### load_config

This function loads global variables from a pickle file into Python.

この関数は、pickleファイルからPythonにグローバル変数をロードします。

### deploy_model

This function deploys the entire ML pipeline on the cloud.

この関数は、MLパイプライン全体をクラウド上に展開します。

### convert_model

This function transpiles the trained machine learning model's decision function in different programming languages such as Python, C, Java, Go, C#, etc.

学習した機械学習モデルの決定関数を、Python、C、Java、Go、C#などの異なるプログラミング言語でトランスパイルリングする関数です。

### create_api

This function takes an input model and creates a POST API for inference. It only creates the API and doesn't run it automatically. To run the API, you must run the Python file using `!python`.

この関数は、入力モデルを受け取り、推論用のPOST APIを作成します。APIを作成するだけで、自動的に実行されることはありません。APIを実行するには、`!python`を使用してPythonファイルを実行する必要があります。

### create_docker

This function creates a Dockerfile and requirements.txt for deploying API.

APIをデプロイするためのDockerfileとrequirements.txtを作成する関数です。

### create_app

This function creates a basic gradio app for inference.

この関数は、推論用の基本的なグラディオアプリを作成します。

---

## [Others（その他）](./03_06_others.ipynb)

### pull

Returns the last printed scoring grid. Use `pull` function after any training function to get the metrics in `pandas.DataFrame`.

最後に出力されたスコアリンググリッドを返します。`pandas.DataFrame` に格納されているメトリクスを取得するには、学習関数の後に `pull` 関数を使用します。

### models

Return a table containing all the models available in the imported module of the model library.

モデルライブラリのインポートモジュールで利用可能なすべてのモデルを含むテーブルを返します。

### get_config

This function retrieves the global variables created by the [setup](./03_01_initialize.ipynb#setup) function.

[setup](./03_01_initialize.ipynb#setup) 関数で作成したグローバル変数を取得します。

### set_config

This function resets the global variables.

グローバル変数をリセットします。

### get_metrics

Returns the table of all available metrics used for cross-validation.

交差検証で使用された利用可能なすべてのメトリックのテーブルを返します。

### add_metric

Adds a custom metric to the metric container for cross-validation.

交差検証のためのカスタムメトリックをメトリックスコンテナに追加します。

### remove_metric

Removes a custom metric from the metric container.

カスタムメトリックをメトリックスコンテナから削除します。

### automl

This function returns the best model from all the models in the current setup.

この関数は、現在の設定にあるすべてのモデルの中から最適なモデルを返します。

### get_logs

Returns a table of experiment logs. Only works when `log_experiment = True` when initializing the setup function.

実験ログのテーブルを返します。setup 関数の初期化時に `log_experiment = True` と設定した場合のみ動作します。

### get_system_logs

Read and print logs.log file from the currently active directory.

現在アクティブなディレクトリからlogs.logファイルを読み込んで印刷します。

---
