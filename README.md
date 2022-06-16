# AB_testing
Notes of learning AB testing

## 定義
對兩群(或多群)條件一樣的樣本，在實驗期間內對實驗組施加一個行為或體驗，而控制組狀況不變，並指定一個有興趣的觀察指標。<br>
實驗結束後以是否有統計顯著了解這個體驗有無對有興趣的指標有無影響力，藉此決定是否要正式將此體驗推廣給所有用戶。<br>

## 限制
僅能針對能夠清楚區別變量的操作因子進行更動，且僅能測量可清楚量化的指標。例如，如有興趣的指標是什麼物品是用戶期望在商場有的，<br>
即不適用以AB testing找出答案。<br>

## 步驟1. 選擇追蹤指標
* 使用Customer Funnel，從商業目標找出目標指標
* 追蹤指標種類：
> * 1.click through probability(uid/cookie): 一段時間算一組，有點的相異人數/看的相異人數
> * 2.click through probability(page view id): 一段時間算一組，有點的相異click id/看的相異page view id
> * 3.click through rate: 直接把click總數/vie總數
> * 4.1和2時間很短的下部會差異太大，可以方便計算的2為先
* 注意：盡量不要選擇很難取得或要觀察很久才能得到結論的指標
* 注意：先觀察一下指標過往每週指標浮動，觀察有無週末、促銷、等特殊浮動現象
* 注意：比較指標不同平台等是否有不同的浮動

## 步驟2+3. 追蹤指標的summary metric的選擇
* 指標的總量，加總、平均數等、總rate
* 需考量以下三面向選擇什麼作為summary(畫過去值的直方圖)
* sensitivity：改變是否有反應
* robustness：是否穩定
* variability：分布標準
=>列出該指標數字、分佈、d，probability多為二項分配，rate為柏松分配

## 步驟2+3. A/A testing
* 以此了解指標特性和其適合度
* 看出robustness和 sensitivity
* 計算指標的variability
* 觀察指標分佈
* 計算信賴區間

## 步驟4. 選擇不變指標
* 不會因爲實驗而變動的比率
* 總數，例如總cookie/uid/pageview...

## 步驟5. 設計實驗
* 指標單位
> 要和分類單位一樣
* 目標族群
> 思考你的功能會針對哪群人有效，但一開始做整個實驗還是針對多元的人較好，因為會有非預期的影響，你會希望觀察到
* 樣本數和做多久
> 定好alpha,beta以決定要納入的樣本數和實驗時程
> 時間最好跨越多不同的時間，少人但久一點比多人短一點好 

## 步驟6. 實驗後
* Sanity Check：沒過就不行
>查看invariant是否差異大、總數是否不合理的差異大(檢定)
* 結論矛盾時：想清楚原因和各種商業邏輯、檢查資料找出原因
* 多指標：要用綜合的1-alpha來測量顯著性，方法有兩種，B法較保守
