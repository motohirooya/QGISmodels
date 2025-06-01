# QGISmodels
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
入力のDEMを高解像度化（アップスケーリング）した後にコンターを作成する。
分割数に奇数（3,5,7..）を指定すると、セル中央の値が変化しない。
![SMOOTHCONTOUR](https://github.com/user-attachments/assets/b41b3546-a6c5-492c-b59c-dca1214bde43)
