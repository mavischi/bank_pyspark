# 銀行行銷資料集
## 解決問題
1. 如何增加下一場行銷活動定期存款的人數？
2. 行銷活動的目標客群？
3. 什麼時間進行行銷活動最佳？

## 資料視覺化
首先了解資料集，將資料集製作視覺化圖表，針對個欄位進行觀察，接著將個別欄位與定期存款與否的進一步製作圖表分析。

## Pipeline
### 特徵工程
這次的資料集中有沒缺失值。而資料集中的工作類型欄位有 unknown 的工作，對於之後的分析沒有太大的幫助，加上只有70筆的資料僅佔總資料的 0.6%，因此我決定將 unknown 的工作類型移除。
將 yes, no 欄位進行 label encoding。

### Baseline
接著進行Baseline 的線性分析、KNN、SVC、梯度提升分類器、決策樹、隨機森林、神經網路、貝氏分類器、XGBoost進行機器學習，從中比較各個機器學習的訓練時間、訓練分數。

## SMOTE
進行 SMOTE 來平衡類別分布，使得訓練集中少數類別樣本數量增加。

## StrandardScaler
進行 StandardScaler，只針對訓練集，避免資料過於擬合。

## 第二次機器學習
進行第二次機器學習並且進行交叉分析，比較每個機器學習的準確性，在進行交叉分析，scoring 預設為 Accuracy，在模型學習與交叉驗證下避免模型太過擬合，所以我選擇training分數 0.949062且交叉驗證的準確率0.857856 的 XGBoost，因此我選定他來做進一步的預測。

## 模型檢驗
計算混肴矩陣並印出可視化混肴矩陣，觀察Precision-Recall、ROC Curve得表現，找出 XGBoost 特徵重要性圖。

## 結論
-我們可以發現 30 歲以下，以及 60 歲以上定期存款的人數較多。
而30-60歲間且存款高於 $10,000 以上的客戶，定期存款的人數也遠高於存款低於 $10,000 的客戶。

-有房屋貸款或是個人貸款的客戶，年紀介於 30-40歲之間，因此在這個年紀間的客戶，較少的機率會定期存款。

-最好的聯繫時間最好在 350 秒以內，大約是6分鐘的時間，活動期間最好的次數為 3 次以下，若次數多反而會降低客戶定期存款的意願。

## 資料來源 
https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset/data
[Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014
