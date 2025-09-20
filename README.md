# QGISmodels
動作確認はWindowsのみ。GRASS GISを使うものはユーザ名は半角英数のみ。
## DuplicatePolygonSplitting.model3
重複ポリゴン分割
ユースケースは、線形に沿った一部重複した図枠ポリゴンを重複なしに分割し、図枠内のラスタ・ベクタをクリップして、重複を無くす


- 入力データ
![01input](https://github.com/user-attachments/assets/7a9371ec-bcc0-408b-9aa5-17bd226898f7)

- 重複の分割
![02div](https://github.com/user-attachments/assets/0cb6686b-2ee3-41af-a25c-37093f049cb4)

- 出力データ
![03div](https://github.com/user-attachments/assets/d4475987-0f25-437a-abaa-3206c4269cde)

## SmoothContour.model3
滑らかな等高線を作成する
入力のDEMを高解像度化（アップスケーリング）した後にコンターを作成する。等高線のファイルサイズは大きくなる。
![SMOOTHCONTOUR](https://github.com/user-attachments/assets/b41b3546-a6c5-492c-b59c-dca1214bde43)
分割数に奇数（3,5,7..）を指定すると、セル中央の値が変化しない（元の標高値が変化しない）。
![elev](https://github.com/user-attachments/assets/db4f6d5f-fab4-4b4e-8c5b-7afeecd45eb4)


## 水文解析
### Fill small nodata.model3
 標高穴埋め。海（ラスタの外周と接するnodata）、埋めた後も孔が残ったnodataは埋めない。大きな水域（nodata）を中途半端に埋めるというユースケースはないと思ったことから作成。
<img width="2091" height="764" alt="fill small nodata" src="https://github.com/user-attachments/assets/c5438c4b-b702-495f-a288-7984a9d07fd6" />

### Fill sinks by terraflow.model3
　r.terraflowによる凹地埋め
  [GrassGIS,QGISを使った水文解析 凹地の平滑化について](https://qiita.com/mooya/items/a07a63393b222795bb17) 参照
 
### Waterflow by watershed.model3
　水文解析（流向、流路）watershed。
  [GrassGIS,QGISを使った水文解析](https://qiita.com/mooya/items/6b802d585e5546a2e693) 参照

### Make basin polygon.model3
　[r.outletによる流域ポリゴン作成](https://qiita.com/mooya/items/6b802d585e5546a2e693#%E6%B5%81%E5%9F%9F%E3%81%AE%E4%BD%9C%E6%88%90)
　r.outletは谷口（流出点）の指定が座標指定だが、モデルでラッピングして、ポイントベクタ指定としている。反復処理を使用することで複数流域をまとめて作成できる（別々のレイヤに出力されるのであとで、マージする）
<img width="1612" height="754" alt="make basins polygon" src="https://github.com/user-attachments/assets/2cc79f8a-c14c-453d-9a12-500e3eb7d838" />

