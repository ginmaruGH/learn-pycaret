# 競馬予想で始めるデータ分析・機械学習

## Git

```bash
# リモートリポジトリのコピーを作成
git clone <repository-name>
```

---

## Pythonのバージョン指定

```bash
asdf local python 3.8.15
```

---

## 仮想環境の構築

```bash
# 仮想環境の構築
python3 -m venv venv
```

```bash
# 仮想環境への切り替え
source venv/bin/activate
```

```bash
# pipのアップグレード
pip install --upgrade pip
```

```bash
# 仮想環境にインストールされているパッケージの一覧作成
pip freeze > requirements.txt
```

```bash
# requirements.txtからパッケージをインストール
pip install -r requirements.txt
```

```bash
# requirements.txtからすべてのパッケージをアップグレード
pip install --upgrade -r requirements.txt
```

```bash
# 仮想環境の終了
deactivate
```

---

## ディレクトリ構成

```bash
.
├── main.ipynb                    # 実行コード
├── data                          # データを保存
│   ├── html                      # netkeiba.comからスクレイピングしたhtmlを保存
│   │   ├── horse                 # /horse/ページからスクレイピングしたhtmlを保存
│   │   ├── ped                   # /horse/ped/ページからスクレイピングしたhtmlを保存
│   │   └── race                  # /race/ページからスクレイピングしたhtmlを保存
│   ├── master                    # マスタを保存
│   ├── raw                       # rawデータを保存
│   │   ├── results.pickle        # レース結果テーブル（コード実行で生成）
│   │   ├── horse_results.pickle  # 馬の過去成績テーブル（コード実行で生成）
│   │   ├── race_info.pickle      # レース情報テーブル（コード実行で生成）
│   │   ├── peds.pickle           # 血統テーブル（コード実行で生成）
│   │   ├── return_tables.pickle  # 払い戻しテーブル（コード実行で生成）
│   └── tmp                       # 一時的なファイルを保存
├── models                        # 学習済みモデルを保存
└── modules                       # モジュール（ソースコードが書かれている部分）
    ├── constants                 # 定数
    ├── policies                  # 予測スコアの算出ロジックや、馬券購入戦略
    ├── preparing                 # スクレイピング〜rawデータの作成
    ├── preprocessing             # 前処理
    ├── training                  # 訓練
    └── simulation                # 回収率シミュレーション
```

## データフロー

![全体図](./images/overall_data_flow.png)

![スクレイピング](./images/scraping_data_flow.png)
