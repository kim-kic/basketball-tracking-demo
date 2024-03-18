---
marp: true
#theme: gaia
theme: mygaia
class: invert
size: 16:9
math: katex
header: "AIシステム開発学科"
---

<!-- headingDivider: 1 -->
<!-- _class: lead -->

# バスケットボール選手の<br>トラッキング:basketball:

2024年4月16日(火)
金晟基


# タイトル

<!-- paginate: true -->
<!-- header: "バスケットボール選手のトラッキング"-->

# Ultralytics 社$^\dagger$
<!-- _header: ""-->

![bg left:40% width:90%](https://assets-global.website-files.com/6479eab6eb2ed5e597810e9e/65bf0578ede71e497341db0d_Blog_thumbnail_1920x1080.webp)

- LAのAI企業
- Ultralytics HUB
  - ノーコードでモデル作成が可能
- Ultralytics YOLO (V8.1)
  - 検出 / detection
  - セグメンテーション / segmentation
  - 分類 / classification
  - 追跡 / tracking
  - 姿勢推定 / pose estimation

> $\dagger$ https://www.ultralytics.com/


# YOLO
<!-- _header: ""-->

![bg left:40% width:80%](../../fig/textbook1.jpeg)

- "You Only Look Once" 
- "You only live once." （人生、一度きり）の頭字語


# ライセンス

- AGPL-3.0 ライセンス$^\dagger$
  - The GNU Affero General Public License
  - オープンソース
  - 無料
  - コピーレフト（商用利用禁止）
  - すべてのソフトウェアとAIモデルがオープンソースである必要
  - プロジェクト全体を同じライセンスでオープンソース化する必要


> $\dagger$ https://www.ultralytics.com/ja/license


# 環境構築

## 仮想環境の作成
```bash
$ python3 -m venv .venv
```
* より細かくバージョン指定する際は`$ python3.10 -m venv .venv`など
* $(base)などが表示されている場合
  * condaのベース環境が立ち上がっています。
    * condaの仮想環境を作る
    * `deactivate`して、pipで管理する

> Python環境構築ガイド https://www.python.jp/install/macos/virtualenv.html

---
## 仮想環境の起動

```bash
$ . .venv/bin/activate
```
または
```bash
$ source .venv/bin/activate
```

---

## インストール$^\dagger$

```bash
(.venv)　$ pip install ultralytics
```

> $\dagger$ https://docs.ultralytics.com/ja/quickstart/#use-ultralytics-with-python




# トラッキング


```Python
from ultralytics import YOLO

# モデルの読み込み（物体検知モデル）
model = YOLO('yolov8n.pt')  # Load an official Detect model

source='https://www.youtube.com/watch?v=RZsCJZVLwmg'

# Perform tracking with the model
results = model.track(source=source, show=True)  # Tracking with default tracker

results = model.track(source="https://youtu.be/LNwODJXcvt4", show=True, tracker="bytetrack.yaml")  # Tracking with ByteTrack tracker
```