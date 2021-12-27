# Airbnb 資料分析 — 台北住宿該怎麼選擇？

[Medium - Airbnb 資料分析 — 台北住宿該怎麼選擇](https://jasmine880809.medium.com/airbnb-%E8%B3%87%E6%96%99%E5%88%86%E6%9E%90-%E5%8F%B0%E5%8C%97%E4%BD%8F%E5%AE%BF%E8%A9%B2%E6%80%8E%E9%BA%BC%E9%81%B8%E6%93%87-%E9%99%84python%E7%A8%8B%E5%BC%8F%E7%A2%BC-9b0f34a21e74)（與以下內容相同，Medium 的排版比較容易閱讀）


# **【 Introduction 】**

![https://miro.medium.com/max/1400/0*YxLUXwwxxz6BAxLP.png](https://miro.medium.com/max/1400/0*YxLUXwwxxz6BAxLP.png)

Airbnb 的出現，當初是創辦人為了籌措下個月的房租，偶然發現自己所居住的城市即將舉辦工業設計師世界大會，住宿的需求突然大增，他們突發其想把房間打造成供應氣墊床(AirBed)和早餐(Breakfast)的民宿 ，提供了人們另一種住宿的選擇。

## `Airbnb = AirBed + Breakfast`

以「 共享經濟 」為概念，Airbnb 打造一個房東與房客互相連結的平台，比較特別的是，Airbnb 上的房源可能來自一間空著沒有人住的房間。在 Airbnb 出現前，很多的房東並沒有考慮要將房間出租，就只是把空著的房間當作家裡閒置的空間，而 Airbnb 帶來了全新的概念 — — 房屋分租。

以下使用 Python 進行分析，分析主題包含 Overview — 房源 價格、供給＆需求、分佈地區、Airbnb 住宿評價，程式碼放在 [GitHub](https://github.com/Jasmine-fe/Airbnb-DataAnalysis)

# **【 Dataset 】**

資料：[Airbnb 房源、訂單資訊](http://insideairbnb.com/get-the-data.html)

區域：台北

時間區間：一年 (2021.11.01–2022.10.30)

房源數量： 4545 個

# **【 Overview 】**

> 住一個晚上要多少錢？
> 

![https://miro.medium.com/max/1400/1*nSleaSF9q9xOXbr-64_-nw.png](https://miro.medium.com/max/1400/1*nSleaSF9q9xOXbr-64_-nw.png)

以 $1000 為一個區間，最多的是落在 $1000 — $1999

- 有 81.7 % 的房間一晚在 $3000 元以下
- 超過 $8000 元的房源數量少，一共 149 間，佔總體的 3.2 %

好奇一晚最貴要多少錢~

結果是一晚 30 萬，看起來是在大安區的城堡，不過對於房屋並沒有太多的描述，只有寫交通便宜四個字，不確定這個房源是否是當一般住宿或是有其他用途（有些 Airbnb 的房源很有特色，可當作戲劇場地租借）。

![https://miro.medium.com/max/1400/1*Vbd5rpvnkGYxIojGMM7VsQ.png](https://miro.medium.com/max/1400/1*Vbd5rpvnkGYxIojGMM7VsQ.png)

> 目前 Airbnb 的訂房率如何，現在要出去玩是否能找到住宿？
> 

如果供過於求，房東無法有效地在 Airbnb 這個平台找到房客，或是供不應求，房客無法在平台上找到適合自己的住宿，都會導致用戶流失，Airbnb 在供給與需求方面是否有達到平衡呢？

![https://miro.medium.com/max/1400/1*01PX6N_T_UIWr0NQKRIm3w.png](https://miro.medium.com/max/1400/1*01PX6N_T_UIWr0NQKRIm3w.png)

                 房源供給與需求 ( 2 月刊登房源數有明顯的下降，是因為 2 月只有 28 天的關係 )

以目前的狀況來看，未來一年的房源供給量還很充足，**目前看起來供給 > 需求，不過考慮到大家可能會等時間比較靠近時才開始規劃訂房，以目前時間點的數據，只能反映部分的需求量。**

本來猜想已預訂房源數量會隨著時間下降，許多人可能是活動前幾天才會預定住宿，讓我意外的是，刊登房源數量變化不大的情況下，預定房源竟然是在與現在相隔快半年後的 2022.5 月後大幅上升，太意外了！猜想有幾個原因

1. 2021 年受到 Covid-19 的影響，出遊的次數下降，明年產生了「報復性旅遊」
2. 6–9月是學生們快樂的暑假，需求大幅增加

( 覺得自己對於這張圖還沒有找到很合適的詮釋，只有想到上述 2 個解釋，如果有其他想法歡迎在留言區分享～ )

# **【 哪裡最適合出去玩？】**

> 房源最為充足的是？ 萬華區、中正區、大安區
> 

![https://miro.medium.com/max/1400/1*YoAVIwMD2GIb66Ms4JGBkg.png](https://miro.medium.com/max/1400/1*YoAVIwMD2GIb66Ms4JGBkg.png)

**房源最多的前三名 — 萬華區、中正區、大安區**

> 房源數量與旅遊景點數量的相關性有多高？
> 

我們看一下 [臺北旅遊網](https://www.travel.taipei/zh-tw) 提供的觀光地圖，觀光地點最密集的地方集中在兩個黑色圈圈裡，包含房源前六多的區域，***看來 Airbnb 的用戶住宿需求與旅行是息息相關的，旅遊景點多的地方房源也會比較多***。

- 萬華區 (1)、中正區 (2)、中山區 (4)、大同區 (6)
- 大安區(3)、信義區 (5)

![https://miro.medium.com/max/1400/1*hEAGXgwfGAypfbAiAi2V6g.png](https://miro.medium.com/max/1400/1*hEAGXgwfGAypfbAiAi2V6g.png)

> 房源數量是否與熱鬧程度相關？
> 

這邊的地區熱鬧程度用捷運人流數量來衡量，我們用 2021-10, 11 月的 [台北捷運 各站進出量統計](https://www.metro.taipei/cp.aspx?n=FF31501BEBDD0136) 資料找出每日進出站人數最多的前 5 個捷運站，看一下人多的捷運站是否房源比較多？

![https://miro.medium.com/max/1400/1*Q_p7XATZLbE6G6d7TWStig.png](https://miro.medium.com/max/1400/1*Q_p7XATZLbE6G6d7TWStig.png)

1. 台北車站 -中正區 (2)
2. 市政府 — 信義區 (5)
3. 西門 — 萬華區(1)、中正區 (2)
4. 中山 — 大同區 (6)
5. 忠孝復興 — 大安區 (3)

( 西門站位在中正、萬華區的交界 )

每日進出站人數 Top5 的捷運站，幾乎都是有兩條可換線的站，交通便利，例如台北車站：淡水信義線 + 板南線。***而 Top5 的捷運站，都落在房源排名前 6 的區域（ 總共 12 個區域 ），交通便利、捷運站人流多的地方房源比較多。***

> 哪個地區會是最便宜跟最貴的呢？
> 

先猜一下，最貴 — 信義區，最便宜 — 南港區

答案揭曉！！

![https://miro.medium.com/max/1400/1*RwLSqUnfPyNxaK3E2h67dg.png](https://miro.medium.com/max/1400/1*RwLSqUnfPyNxaK3E2h67dg.png)

( Boxplot 白色點代表平均，Box 上緣為 75 分位數、中間 50 分位數、下緣 25分位數 )

## `最貴 — 北投區，最便宜 — 南港區`

出乎意料的，台北蛋黃區 — 大安、***信義區的價格與大同、萬華、中山區差不多， 現在知道了～住的離 101 比較近 並不會比較貴！***

而最貴的北投區價格分佈區間很廣，其他區域的 75 分位數在 $2000–$3000 之間，但是北投區的 75 分位數為 $4367，直接比別的區域高出一千多塊。捷運新北投站有著名的北投圖書館外，北投公園的兩旁有有許多的溫泉會館，猜測可能是溫泉相關的住宿價格會比較高～

> 北投區的價格較高是否與溫泉有關？
> 

北投區總共有 98 個房源，其中 66.3% 包含了溫泉相關的關鍵字

![https://miro.medium.com/max/1400/1*g5TJmAcArgI9UbFIdvVXgA.png](https://miro.medium.com/max/1400/1*g5TJmAcArgI9UbFIdvVXgA.png)

下圖可看出，溫泉的住宿(hotspring-True)平均每晚價格是非溫泉住宿(hotspring-False)的 2 倍多，由此可知，***因為溫泉的加持，北投區成為台北平均一晚價格最高的區域！***

![https://miro.medium.com/max/1400/1*8rIBx3UpUZLg2xp5LPj84w.png](https://miro.medium.com/max/1400/1*8rIBx3UpUZLg2xp5LPj84w.png)

# **【 對於 Airbnb 住宿的滿意度 】**

> 顧客滿意度高，才有可能留得住人，究竟房客對於 Airbnb 的住宿的滿意程度如何呢？
> 

評論分數 （ review_scores_rating ），分數區間：0–5 ，大家會給他 5 星好評嗎？

![https://miro.medium.com/max/1400/1*HYHBuAsMweVNrzohhsQhvQ.png](https://miro.medium.com/max/1400/1*HYHBuAsMweVNrzohhsQhvQ.png)

**大部分的評論分數都 > 4 分， 4.75 — 5 分的數量最多，大家對於 Airbnb 住宿的滿意程度蠻高的！**

> 如果你是房東，希望評論分數高一點，需要提升哪些指標？
> 

指標 ( [ref: Airbnb — star ratings](https://www.airbnb.com/help/article/1257/star-ratings) )

- 房東：host_is_superhost：是否為 super hosthost_listings_count：房源數量
- 評論：review_scores_accuracy：房間是否符合 Airbnb 上面的照片、描述review_scores_cleanliness：乾淨程度review_scores_checkin： check-in 的流程是否快速簡單review_scores_communication：訊息回覆即時性review_scores_location：居住地點安全、便利性review_scores_value：房間是否符合價格， CP 值高低reviews_per_month：每月的評論數量review_scores_rating：整體評論分數

![https://miro.medium.com/max/1400/1*TwjgI_hRBlZ5bS8N16saIw.png](https://miro.medium.com/max/1400/1*TwjgI_hRBlZ5bS8N16saIw.png)

                               (藍色框框 — 其他指標與 review_scores_rating 的相關係數)

房客最在意的前三個指標是：

1. 乾淨程度 (review_scores_cleanliness)
2. CP 值 (review_scores_value)，房間是否符合價格
3. 一致性 (review_scores_accuracy)，房間是否符合 Airbnb 上面的照片、描述

除了用「 評論分數 」判斷之外，Airbnb 有明確的定義成為 [star host](https://www.airbnb.com/d/superhost) 的四個條件：顧客滿意度高、接待經驗豐富、退訂率低 （不包含天災、旅遊警戒限制等情況）、快速且頻繁的回覆訊息

![https://miro.medium.com/max/1400/1*rBOTZa0K_H3xrwmiufi-2Q.png](https://miro.medium.com/max/1400/1*rBOTZa0K_H3xrwmiufi-2Q.png)

                                                                  [Airbnb superhost](https://www.airbnb.com/d/superhost)

有 27% 房源的房東是 Super Host

![https://miro.medium.com/max/1400/1*rTK1xWQpwolgoxU66ANKiw.png](https://miro.medium.com/max/1400/1*rTK1xWQpwolgoxU66ANKiw.png)

super host — t: true, f: false

不過，10 個指標中， super_host 與 review_scores_rating 之間的相關性排名第八，相關性 0.27，***房東是否是 super host 與評論分數高低，兩者的關係呈弱相關而已。***

> 這些評價較低的房源，在乾淨程度、CP值、位置…等等方面的平均分數是多少？
> 

取 review_scores_rating< 4 分的房源來看，總共有 136 個房源，許多是落在 3–4 分這個區間

![https://miro.medium.com/max/1400/1*7ghU3Niaa8QxEn4FpTj4Sw.png](https://miro.medium.com/max/1400/1*7ghU3Niaa8QxEn4FpTj4Sw.png)

從各方面的評論分數來看，這三點是最需要加強的！

1. CP 值 (review_scores_value)，房間是否符合價格
2. 乾淨程度 (review_scores_cleanliness)
3. 一致性 (review_scores_accuracy)，房間是否符合 Airbnb 上面的照片、描述

![https://miro.medium.com/max/1400/1*K7NrZ2JApcoOCGoZY_i_jA.png](https://miro.medium.com/max/1400/1*K7NrZ2JApcoOCGoZY_i_jA.png)

**與前面用相關係數得出的結論符合！**相關係數1- 3 名分別是 乾淨程度、CP 值、一致性。房東們如果想提高評論分數，可以考慮先從相關性最高的三點 ( 乾淨、CP 值、實體與照片描述一致 ) 開始改善！

# **【 Summary 】**

![https://miro.medium.com/max/1400/0*0MTjfOYEh3cEyB2v.gif](https://miro.medium.com/max/1400/0*0MTjfOYEh3cEyB2v.gif)

                          ref: [Airbnb — Imagining a world where people can belong anywhere](https://design.studio/work/airbnb)

這次從 Airbnb 的資料集中，可以發現每個地區房源有不同的特性，例如 北投有許多溫泉住宿所以是全台北市 Airbnb 上平均每一晚住宿價格最貴的地方，也可以從評論中發現，房客對於住宿最在意的是這三點 — 乾淨、CP 值、實體與照片描述一致，這些都是一筆一筆訂單資料背後隱藏的訊息。Airbnb 的出現，不只是帶來另一種住宿的選擇，他們的目標是讓人們在世界各處都可以 Live Like A Local，透過 Airbnb ，深度旅遊變得更容易了，旅人在異鄉也能輕鬆的與他人交流。
