<img src="https://private-user-images.githubusercontent.com/1713215/378243314-28c1ab4b-77e4-4e22-9006-9fddf2a1b89c.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzQyNjEsIm5iZiI6MTcyOTQ3Mzk2MSwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MzMxNC0yOGMxYWI0Yi03N2U0LTRlMjItOTAwNi05ZmRkZjJhMWI4OWMucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDEyNjAxWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTg3MjBlMTQxYWY1YTA2YjlmZTA3ZjZjZDk1Y2MzNjM3ZjJkMGQxMzgwZjE0OTA1ZGEzZjUxZjgwNDk2OGYxZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.9oIYNKo1A_oLhd-V0qMkGuwEDQSNeDj6CgMmMCW4qxU" width="100%" height="auto" alt="PLATEAU TouchDesigner Plugin" />

# PLATEAU TouchDesigner Plugin

PLATEAU TouchDesigner Pluginは、TouchDesignerでPLATEAUの3D都市モデルデータを簡単に扱えるようにするためのツールです。主に以下の機能を提供しています。

- CityGML形式の3D都市モデルをOBJ形式で出力する機能
	- 使いたいエリア（メッシュ毎）を指定する機能
	- 特定の地点を中央に設定する機能
	- 地物（建築物、道路など）をフィルタリングする機能
	- 地物のLOD（Level of Detail）を指定する機能
- 属性情報をCSV形式で出力する機能

なお、TouchDesignerの特性上、以下の機能は提供していません。

- 地物のテクスチャを含めた3D都市モデルの出力機能

# サンプルプロジェクト

TBD

# 動作環境

### アプリバージョン

動作確認環境：TouchDesigner: 2023.11760

これ以降のバージョンでも動作しますが、上記バージョンにて開発・検証が行われているため不具合などが発生する可能があります。

### OS
Microsoft Windows10 / 11
Apple MacOS10.15以上

### グラフィックス
Nvidia GeForce GTX1650以上
AMD Radeon RX6400以上

### CPU
Intel CPU 10世代以上
Ryzen 5000シリーズ以上

### メモリ
8GB以上

上記スペックはあくまでも推奨環境となります。

# PLATEAU TouchDesigner Pluginの利用方法

PLATEAU TouchDesigner Pluginは、TouchDesignerでPLATEAUの3D都市モデルデータを簡単に扱えるようにするためのツールです。
そのため、利用にはTouchDesignerのアプリ本体が必要です。リポジトリページにある動作環境をご覧頂き環境をご準備の上以下の方法でご利用ください。

## プラグイン利用前の準備

1. プラグインのダウンロードと起動について
2. CityGMLファイルの準備

## 1. プラグインのダウンロードと起動について

プラグインは以下のURLからダウンロードが可能です。

[https://github.com/bassdrum-org/PLATEAU-TouchDesigner-Plugin/archive/refs/heads/main.zip](https://github.com/bassdrum-org/PLATEAU-TouchDesigner-Plugin/archive/refs/heads/main.zip)

ダウンロードファイルはZIPファイルとして保存されるので、ダウンロード完了後にファイルを解凍します。
すると以下のようなファイルが保存されるので、プラグインを利用する場合はこの中にある「PLATEAU-TouchDesigner-Plugin.toe」をダブルクリックで開きます。

## 2. CityGMLファイルの準備

プラグインを利用するにはPLATEAUで配布しているCityGMLデータが必要です。CityGMLデータは以下のサイトからダウンロードが可能です。

[https://www.geospatial.jp/ckan/dataset/plateau](https://www.geospatial.jp/ckan/dataset/plateau)

なお、解凍後のフォルダ構成は変更しないようにしてください。変更すると属性が適切に読み込めないことがあります。
例として渋谷区のデータの場合「13113_shibuya-ku_city_2023_citygml_1_op.zip」というファイルがダウンロードされますが、こちらを解凍し指定の場所にフォルダを移動するのは問題ないですが、中身のファイル構造を変えてしまうと正しくデータが読み込めなくなってしまいます。

# プラグインの利用方法

1. CityGMLファイルの読み込み
2. 平面直角座標系の設定
3. 出力モデルのセンター位置設定
4. 利用メッシュと地物の選択
5. オプションとLODの選択
6. 書き出し

## CityGMLファイルの読み込み

「PLATEAU-TouchDesigner-Plugin.toe」を開くと、下記のような画面が表示されます。まずは先ほど用意したCityGMLファイルを読み込むため、「CityGMLフォルダを選択」の右にあるフォルダアイコンを選択してください。するとフォルダパスが入力欄に追加されるので、選択した場所と合っていれば次へ進みます。

![初期状態](https://private-user-images.githubusercontent.com/1713215/378242161-f6cec20f-7960-4cc1-9428-fa2ff2289e60.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE2MS1mNmNlYzIwZi03OTYwLTRjYzEtOTQyOC1mYTJmZjIyODllNjAucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MGNmZGI0NGVhZjUzZDQ3M2ZjYjgxYjNlN2RiMGFlY2Y5M2NkMmQzZTg5NDJhMjg3YjFkMjQ4Mjg1MzUzZmNkNCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.rJLVCwG5d2jay0JIwFOb2EmNZrOiFnFVUKblf-Osvs0)

初期状態

## 平面直角座標系の設定

続いて「使用する平面直角座標系番号」の選択を行います。座標の変換に使用する計算方法が地域によって異なるため、使用するCityGMLファイルの場所にあったものを選択してください。こちらの選択が完了したら「Next」を押して次の画面に進んでください。

![フォルダ選択済みの状態](https://private-user-images.githubusercontent.com/1713215/378242163-8340d024-28a9-45f2-a3ed-774d9c03c928.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE2My04MzQwZDAyNC0yOGE5LTQ1ZjItYTNlZC03NzRkOWMwM2M5MjgucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MjM0ZjRhNzQ1NTJkM2ZmYWJjMDQ4YTM0MTczY2UzZGU4MWQ3NzJlMGJhMGMzMzY1MzQyNjZjMjM4MWQwYmRiYyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.43LnuB_Qg8h90U0gXFjeGwUNGeorP28Kc9geiiMA8Bo)

フォルダ選択済みの状態

![平面直角座標系番号の一覧](https://private-user-images.githubusercontent.com/1713215/378242164-effa4603-a8ba-416a-9620-e6e6d6ee86b4.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE2NC1lZmZhNDYwMy1hOGJhLTQxNmEtOTYyMC1lNmU2ZDZlZTg2YjQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9M2E1M2QyMDg2YjYyNjhmYzRjYmU3OTM3ODQ3ZGE3ZjVkM2QwZjhiOThiNmM3NzEzN2I5MGFlMjg4N2FiYmQ2OCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.ZKtepW4y39dfUX119Ui9Qz5YSwo5a76FSwtx8teNvCA)

平面直角座標系番号の一覧

## 出力モデルのセンター位置設定

次に、CityGMLファイルをインポートする際の、データの中心座標を指定するための情報を設定します。例えば横浜市のCityGMLファイルを読み込み、中心に横浜駅を設定したい場合は、「施設名称・地名を検索」の欄に「横浜駅」と入力します。すると、横浜駅の位置情報が地図上に表示されます。地図は地理院タイルの1枚分で表示されるため、見つかった地点が端に表示される場合があります。
また、自身で緯度経度を直接設定することも可能です。その場合は上部のタブから「緯度経度から設定」を選択してください。

![初期状態](https://private-user-images.githubusercontent.com/1713215/378242165-66cca8ab-b145-408a-b281-263dffe3e6a2.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE2NS02NmNjYThhYi1iMTQ1LTQwOGEtYjI4MS0yNjNkZmZlM2U2YTIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ODRiMGQ3MTAwZGFmOWRiYThiODlkZGE3ZmI0ZWE0N2ZjYTgxNGU0NWM0OWZhYmRmMzA3NzcyNTFmOGMyMTg1OSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.xP1cSjg7EMkHEFRNnwgfNeGhMJWapy7swGAmAoSzTWA)

初期状態

![横浜駅の位置を検索した状態](https://private-user-images.githubusercontent.com/1713215/378242166-46ee40c9-b8b9-45f7-93d5-0a361fceea85.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE2Ni00NmVlNDBjOS1iOGI5LTQ1ZjctOTNkNS0wYTM2MWZjZWVhODUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MjZmY2I3ZWZjZGZkOTIwZGRiNzVmOWMyNDkzNDQ3ZTY1ZTVhZTg0ZTY4YmI2MjE5MTVhZmUwNThiY2JiOTM4NCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.V6eyW0uCRXXN9UxI5oTu-DPp-5UdW1dxHtp2ZNLDuzU)

横浜駅の位置を検索した状態

![緯度経度を自身で指定した状態](https://private-user-images.githubusercontent.com/1713215/378242170-b94ef2ef-7b87-46e5-9558-2a5a77cb1055.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE3MC1iOTRlZjJlZi03Yjg3LTQ2ZTUtOTU1OC0yYTVhNzdjYjEwNTUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZmEzZTA2ZjRjNTIxMzVkY2Y2NzBkOGJjNDM2ZTI1OTEwMDc4YmUyNWVkOWRiOTI2NDc4ZTIwZTRjYWFjNTg3MCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.meH24wuOUuE26P0c7krW7Ii5naGHNKTPwAdX_JOjExE)

緯度経度を自身で指定した状態

## 利用メッシュと地物の選択

CityGMLファイルが問題なく読み込めると、マップ上にインポート可能な範囲と地物（データにおける分類）のアイコンがメッシュ（※1）毎に表示されます。利用したいエリアを選択（※2）すると、右下に「ビル、橋、道路...」のようにインポート可能な地物が表示されます。この中で利用したいものにチェックを入れて「Next」で次に進みます。

※1 メッシュの区分けについてはこちらのページをご覧ください。
[https://www.mlit.go.jp/plateau/learning/tpc03-1/](https://www.mlit.go.jp/plateau/learning/tpc03-1/)

※2 一度に大量のメッシュを選択すると処理に長い時間がかかる場合があります。まずは少ない数でお試しください。

![CityGMLのメッシュが表示されている状態](https://private-user-images.githubusercontent.com/1713215/378242172-2803a78f-73ee-4adf-8ee4-499e560c5f61.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE3Mi0yODAzYTc4Zi03M2VlLTRhZGYtOGVlNC00OTllNTYwYzVmNjEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YmNjZDkyMTRjOTNkNjUyYzcxYWIyNGMyNzg2YjNiMGU2OTEwMzM5YzQwYjI4MmYyMWYxNDdmNjhjNzIzZjU1OCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.dwa9LjNPfYQz285Vxc7T0PPmN3MsfAZyL5_rk0-bx6s)

CityGMLのメッシュが表示されている状態

![メッシュを選択後、インポートする地物を選択した状態](https://private-user-images.githubusercontent.com/1713215/378242176-cdafece5-cc8c-48c1-815e-8c37ec777ee1.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE3Ni1jZGFmZWNlNS1jYzhjLTQ4YzEtODE1ZS04YzM3ZWM3NzdlZTEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9OGU1YzVmMWNiMjE4YmY2MzQyMWJkNWQ2ZjYzOWYwODQ1MzcxYjYxY2QxZWRkOWM1ODllZDdhODU2MTFmMmE5OSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.egsAraDhTs3XxAbAkivWoavXsuYzc2NqXWD8J9YiELA)

メッシュを選択後、インポートする地物を選択した状態

## オプションとLODの選択

選択したメッシュと地物からデータを書き出す為の設定を行います。出力オプションの説明は以下をご覧ください。

- 「中心座標を設定地点に合わせる」：「出力モデルのセンター位置設定」で設定した位置に出力モデルの中心を合わせるかどうか
- 「属性情報を出力する」：モデルデータと一緒に属性情報をCSVファイルで出力するかどうか

続いて「出力する最大LOD (Level of Detail)」についてですが、LODとはデータの細かさの度合いを表し、数が大きくなるほど精細なデータになります。書き出しまでの処理時間や3Dデータとして扱う際の処理負荷なども重くなってしまうので、ご自身の利用用途に合わせた数値を設定ください。
TouchDesignerでのビジュアル表現などはLOD2、重い場合はLOD1などをおすすめします。
各地物のLOD毎の形状・属性情報については、3D都市モデル標準製品仕様書に定義しています（[https://www.mlit.go.jp/plateaudocument/](https://www.mlit.go.jp/plateaudocument/)）。必要に応じてご参照ください。

![初期状態](https://private-user-images.githubusercontent.com/1713215/378242177-00f77f0d-f164-4c50-87e7-336ae1aef674.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE3Ny0wMGY3N2YwZC1mMTY0LTRjNTAtODdlNy0zMzZhZTFhZWY2NzQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NjhkNGY1OGMzMDcxMTMxYmQwZDNiYzM5YWE4NWNhZTkyYTIzYzQ0NmVmMTEzNmU5OTk2YzY0MzEzNjAxYTIxNSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.fLeiugQqpBpAkxdqXBZh6d_y2-1WBJX-GcYDRVDXKic)

初期状態

![保存先フォルダを選択した状態](https://private-user-images.githubusercontent.com/1713215/378242179-d14637d3-2698-4787-a19e-ec02562ff7ba.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE3OS1kMTQ2MzdkMy0yNjk4LTQ3ODctYTE5ZS1lYzAyNTYyZmY3YmEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YTk2ZGJlNzVhMzM5Njk3YzI1N2M5NWZlMmI1OGYyMmEwNzA4NTJhOWFjMjQ5Zjk2NTgwYzA2M2JjNTdjYTYxMyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.tc3ZvmgkUKPrvAGw16qe4R5hkY4M27Ju5IT6P3N6E4o)

保存先フォルダを選択した状態

## 書き出し

設定が完了したら、「保存先フォルダを選択」右にあるフォルダアイコンから、書き出し先を選択してください。処理に時間がかかるのと、処理中はTouchDesignerアプリで他の動作が行えなくなるのでご注意ください。
書き出しが成功すると、選択した場所に3Dデータの「OBJファイル」、属性情報を書き出した場合は「CSVファイル」が生成されます。

![書き出し処理中の状態　※（応答なし）と出ますが処理は進行しています](https://private-user-images.githubusercontent.com/1713215/378242180-8fdd172c-2533-4775-834f-a6cfab8ea746.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjE4MC04ZmRkMTcyYy0yNTMzLTQ3NzUtODM0Zi1hNmNmYWI4ZWE3NDYucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9Nzc4NDU4OWFjZjRjNjc3MDFkOTBhOGVkZWJkYjExMjVkOGE0MmYyYjcwMGY0ZGFmMGNiZjAxY2JjZDJkNmQwYyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.oKEsYIf9tRX1z840r2W6QlfOBAISJXVifVzU80JR3Gs)

書き出し処理中の状態　※（応答なし）と出ますが処理は進行しています

## テクスチャ込みのデータを使うには

本プラグインではテクスチャ込みのモデルデータの生成には現在対応していません。そのため、テクスチャ込みのモデルデータを生成するにはPLATEAU SDK for Unity / Unrealの利用をおすすめしております。以下、[**PLATEAU SDK for Unity**](https://project-plateau.github.io/PLATEAU-SDK-for-Unity/)を使った手順を紹介します。

なお、2022以前のバージョンのTouchDesignerではFBXデータのテクスチャがうまく読み込まれないので、最新版のTouchDesignerにてご利用ください。

まずは上記SDKのマニュアルに沿ってインストールを行います。その後、テクスチャを含めた状態でUnity上でモデルデータを読み込みます。

![インポート時の設定](https://private-user-images.githubusercontent.com/1713215/378242507-129476e5-b54b-4468-9c5f-095e041edec3.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjUwNy0xMjk0NzZlNS1iNTRiLTQ0NjgtOWM1Zi0wOTVlMDQxZWRlYzMucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9M2JmMTIwZDFhNTk0ZjkwMzBiNWUwM2M4M2RmMmJmYTg3ODM2YTNjNTY3NWIwYjE2MTIzNDk4NzFmNDZjZGRlMSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ._etAvLsuCTThwcXR985LbJ5tMRqBCQG4IhhGn9TdPxs)

インポート時の設定

このようにUnityにモデルデータの追加が行えたら、TouchDesignerに持っていくためFBX形式でエクスポートを行います。

![](https://private-user-images.githubusercontent.com/1713215/378242492-608da1ce-fa66-4338-94d5-179d149e6851.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjQ5Mi02MDhkYTFjZS1mYTY2LTQzMzgtOTRkNS0xNzlkMTQ5ZTY4NTEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9OWJlM2QxYTlmYzM2ZmI3MTM0N2ZjMzVjZWI5NWMzOWY0OWE3NzJmZjdkZGZkNDFiMGY2ZjRkOTlkMTVlNDdmNCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.87SWIpfKUWs_Fm1Uqb20wBA2OLElBnUJOeoQgFp2LgY)

その際の設定内容は以下のとおりです。形式をFBXにして、フォーマットはBinaryで、テクスチャのチェックを入れてください。また座標軸についてはUnityと同様の設定を行います。

![エクスポート時の設定](https://private-user-images.githubusercontent.com/1713215/378242502-b3e257ce-8f24-4826-a167-6c33672cbfa4.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU1MzgsIm5iZiI6MTcyOTQ3NTIzOCwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjUwMi1iM2UyNTdjZS04ZjI0LTQ4MjYtYTE2Ny02YzMzNjcyY2JmYTQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE0NzE4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZDk2ODE3OTAzOTkwN2UyZjBjYTEzNjdkYzRlZGMwZDc4NGQ5YmNlZDRiNjE2MjEzZGJhZmIzZDViZTI1NzU0ZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.zG_mqVCnQqc2ExuIhXcf8X0EDkv5DmGsc1wlhN--R5U)

エクスポート時の設定

書き出されたFBXをTouchDesignerの画面上にドロップすると、このようにテクスチャ込みの状態のFBX COMPとして読み込まれます。

![TouchDesignerで生成されたFBXを読み込んだ状態](https://private-user-images.githubusercontent.com/1713215/378242494-40b4abfb-38bf-4815-92ef-b455fd5c738b.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjk0NzU4NzksIm5iZiI6MTcyOTQ3NTU3OSwicGF0aCI6Ii8xNzEzMjE1LzM3ODI0MjQ5NC00MGI0YWJmYi0zOGJmLTQ4MTUtOTJlZi1iNDU1ZmQ1YzczOGIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MTAyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDEwMjFUMDE1MjU5WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NTM3NTFhY2ZhM2E2ODhlOWFmMzIwYTczNDRiYWUwMWQ0MGYxODZmZDQ4NWUxNWJhMzJiODJjMWZjZmJjNzgyNiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.aFtyaJfDxn1gkKG1i4Vi_G4wgWZ2tO0phbLWPF5y4WQ)

TouchDesignerで生成されたFBXを読み込んだ状態


### 参考資料

- ハンズオン動画（TBD）
- チュートリアル記事（TBD）


# ライセンス
本リポジトリはMITライセンスで提供されています。
本システムの開発は株式会社BASSDRUMが行っています。
ソースコードおよび関連ドキュメントの著作権は国土交通省に帰属します。

# 注意事項
- 現在、本ツールとドキュメントは日本語のみ対応しています。
- 本リポジトリの内容は予告なく変更・削除する可能性があります。
- 本リポジトリの利用により生じた損失及び損害等について、国土交通省はいかなる責任も負わないものとします。

