長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
tt<-data.frame()
for(i in 2582:2591){

ptturl<-paste("https://www.ptt.cc/bbs/Tech_Job/index",i,".html",sep='')
pttContent <-read_html(ptturl)
post_title <- pttContent %>%
html_nodes(".title") %>%
html_text() 
post_author <- pttContent %>%
html_nodes(".author") %>%
html_text() 
post_push <- pttContent %>%
html_nodes(".nrec") %>%
html_text()
ptt_page<-pttContent %>%
html_nodes(".btn wide") %>%
html_attr("href")

post<-data.frame(Title=post_title, Push=post_push,Author=post_author)
tt<-rbind(tt,post)

}
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk

knitr::kable(tt)
```

| Title                                               | Push | Author       |
|:----------------------------------------------------|:-----|:-------------|
| (已被mmkntust刪除) <sht255>                         | 10   | -            |
| 〔疑惑〕台GG要在竹南設廠的傳聞有下文嗎？            | 39   | q99518g      |
| (本文已被刪除) \[lovetire\]                         | 12   | -            |
| \[請益\] Offer請益 英業達/鴻海                      | 34   | kusahara     |
| \[請益\] 聯電職務請益                               | 11   | blacktea0930 |
| \[請益\] offer請益 garmin自動化機構/國外sales       | 8    | Blueicex     |
| \[面試\] 友達晶材IE面試與錄取                       | 13   | nick800418   |
| (本文已被刪除) \[pptgov\]                           |      | -            |
| \[請益\] offer 選擇(美光vs力晶）                    | 43   | chsweet      |
| Fw: \[請益\] 科技工程師練英文                       | 5    | ggggggh      |
| \[請益\] offer 上無註明保障年月薪                   | 26   | ck49         |
| \[心得\] 面試心得(乾坤/正新/台灣荏原/Lam/)          | 8    | Sorry5566    |
| \[徵才\] 汐止-徵求會PHP與SQL的工程師                | 8    | MobileMan    |
| \[請益\] 頎邦科技                                   | 4    | popularman   |
| \[面試\] 台達化學公司(前鎮廠) 工作環境與福利        | 5    | tcl2830      |
| \[請益\] 點晶科技 推嗎                              | 5    | okmijnuhb    |
| (本文已被刪除) \[tcl2830\]                          |      | -            |
| \[心得\] 面試心得(基恩斯/精材/ASML/艾克爾)          | 30   | Sorry5566    |
| (本文已被刪除) \[Kovainen\]                         | 6    | -            |
| (本文已被刪除) \[nntn\]                             | 3    | -            |
| 敬鵬-資訊系統開發管理師                             | 2    | incoterms    |
| \[請益\] 美亞科技                                   | 6    | key9028      |
| \[新聞\] 總經理巡廠要整理桌面　群創員工爆比當兵     | 34   | zzzz8931     |
| Re: \[討論\] 關於機台零件是不是都撐到最後？         | 1    | c1823akimo   |
| 創群科技                                            | 13   | jamiefly     |
| \[討論\] 有人因為辦公室太舊太髒離職的嗎??           | 48   | yamakazi     |
| (本文已被刪除) \[VamYU\]                            | 12   | -            |
| Re: \[心得\] 我在拓凱(台中工業區)的日子             | 6    | simplep2002  |
| Re: \[新聞\]【台GG別走動畫】台積傳將赴美砸5千億建3  | 2    | egnaro123    |
| (本文已被刪除) \[tomandjim\]                        | 3    | -            |
| (本文已被刪除) \[piggg\]                            |      | -            |
| \[徵才\] 交大電子所誠徵碩士級研究助理               | 1    | xgin         |
| \[情報\] 國網中心擴大舉辦工讀生/實習生徵才活動      |      | ZhaoYun      |
| \[請益\] 亞太國際電機 製程 疑問                     | 1    | ian00727     |
| \[徵才\] 掃描器/光學元件/韌體工程師 BioInspira, Inc |      | Herc         |
| (本文已被刪除) \[Crosswise\]                        | 1    | -            |
| Re: \[心得\]小寶跟大寶 真的不一樣                   | 25   | ikeru        |
| Re: \[請益\] Offer請益 英業達/鴻海                  | 1    | wer11        |
| (本文已被刪除) \[pjc202\]                           |      | -            |
| (本文已被刪除) \[piggg\]                            | 8    | -            |
| 捷普 綠點刀具                                       | 3    | tn372845     |
| \[請益\] 日商安立知                                 | 5    | pjc202       |
| \[情報\] 蘋果申請具備iPhone核心之Macbook產品        | 4    | zxcvxx       |
| \[請益\]有人收到德州儀器技術行銷工程師面試邀請?     | 4    | wer11        |
| \[請益\] 請問陸資的IC設計公司                       | 10   | DigiTalent   |
| \[請益\] 德州儀器設備工程師實習                     | 4    | oeys         |
| \[討論\] 國家光電好嗎                               |      | chag06       |
| Re: \[請益\] 請問陸資的IC設計公司                   | 20   | DigiTalent   |
| \[請益\] 是否該調往偏鄉工作？                       | 54   | NakiXIII     |
| (本文已被刪除) \[lponnn\]                           | 5    | -            |
| (本文已被刪除) \[dfg512\]                           | 3    | -            |
| \[請益\] Advantest二手設備商                        | 5    | CA42         |
| Fw: \[請益\] 夜間進修                               |      | neon2102     |
| \[請益\] 華通電腦                                   | 6    | jackjack0805 |
| \[討論\] 矽品好像沒有板上說的那麼不好吧~            | 65   | goodlike     |
| (本文已被刪除) \[ScrewYou\]                         | 15   | -            |
| \[討論\] 台積電VS中油                               | 12   | ej4g4        |
| (本文已被刪除) \[p4818046\]                         | 1    | -            |
| \[請益\] 金屬工業中心面試                           | 1    | huaygina     |
| \[請益\] 在職碩班選擇請益，中興vs中央               | 11   | AKFG         |
| Re: \[討論\] 台積電VS中油                           | 8    | tomtowin     |
| \[請益\] 台積vs世界                                 | 55   | q7w8s5       |
| \[請益\] 暑期實習請益                               | 5    | quasi        |
| Fw: \[台北\] 推手媒體誠徵後端工程師                 |      | ssmartdan841 |
| (本文已被刪除) \[sheu123\]                          | 1    | -            |
| \[請益\] Offer請益(仁寶/緯創)                       | 14   | johnnypk321  |
| \[新聞\] 台積i8單 下月量產                          | 20   | unrest       |
| \[討論\] 聯穎光電面試                               |      | key9028      |
| \[請益\] 大中積體電路                               |      | pieceofacake |
| \[請益\] 弘馳公司 面試前的準備                      | 3    | AlioAlio     |
| \[討論\] 離職最後一根稻草                           | 51   | NTUlosers    |
| \[請益\]力成panel fan-out 製程整合 & 群創製程       | 5    | vacfann      |
| Re: \[討論\] 試用期超過三個月                       | 4    | dakkk        |
| \[討論\] （樹林）瑞傳 smt                           |      | usa71111     |
| \[請益\] 關於AirU x FinTech                         | 1    | Wizarc       |
| \[新聞\] 虧得一塌糊塗 太陽能矽晶圓廠等待黎明        | 17   | ErioT        |
| \[請益\] 台積測試設備助工                           | 24   | qlb144       |
| \[請益\] 推薦的layout工程師工作                     | 8    | ihavejason   |
| \[討論\] 一天實際工作的時數？                       | 8    | lukenming    |
| \[請益\] 面試要報告的 碩士論文                      | 2    | KIRA47       |
| \[心得\] 皮卡丘 五年工作心得                        | 23   | xx10231202   |
| \[請益\] 請問南科統新光訊                           | 3    | ggyy08957    |
| \[請益\] 新規則，休息日加班請假？                   | 17   | ggg1356114   |
| \[新聞\]新日光永旺能源獲8億聯貸 持續擴建太陽能      |      | moonth66     |
| \[新聞\] 工程師癱瘓全台YouBike 恐賠2242萬           | 29   | kellywu      |
| (本文已被刪除) \[hebeisme5566\]                     | 1    | -            |
| \[請益\] 台達研究院面試?                            | 3    | Aloha0527    |
| \[問卷\]數位族群數位金融潛力研究                    |      | olivesu      |
| \[請益\] 高雄日月光 offer                           | 13   | RacingSport  |
| Re: \[討論\] 台積電VS中油                           | 11   | FcukYouChina |
| \[請益\] 暢星科技                                   |      | Eighteen18   |
| \[新聞\] IC設計兩岸較勁 台廠轉型壓力加劇            | 8    | Nicher116    |
| (本文已被刪除) \[Kalisi\]                           | 6    | -            |
| \[討論\] 工程師的定義?                              | 30   | nhcuejunk    |
| Fw: \[徵才\]台中外商徵angular / hybrid app開發人員  |      | uborek       |
| \[請益\] Offer請益 怡利/友達                        | 8    | ccc0901      |
| (本文已被刪除) \[sercet0728\]                       |      | -            |
| (本文已被刪除) \[Pand\]                             | 2    | -            |
| \[徵才\] 北科車輛所徵求碩士級專任助理兩名           |      | Pocky5566    |
| \[請益\] 利得儀器-工程部助工                        |      | shinfon      |
| \[聘書\] 昇陽光電 VS 漢磊科技                       | 7    | qazwsx517    |
| Re: \[心得\] 皮卡丘 五年工作心得                    | 5    | magic704226  |
| 宜特 Ic 測試助理工程師面試                          | 3    | yens1        |
| (本文已被刪除) \[KEEPLOVING\]                       |      | -            |
| (本文已被刪除) \[scntu\]                            | 1    | -            |
| \[新聞\] 就是要力挺！仁寶參與樂視致新現增7億人      | 11   | wahaha23     |
| \[情報\] 智慧醫療人才培育計畫 徵求赴美人才          |      | Gojilla      |
| \[情報\] 智慧機械及航太研發補助計畫宣導說明會       |      | gil729181    |
| \[請益\] 漢民客服工程師（中科）                     | 16   | qoo63112000  |
| \[情報\] 台灣史丹福醫材人培計畫 徵求赴美人才        |      | Gojilla      |
| \[請益\] 有人聽過縯忠實業嗎？                       |      | foc0327      |
| \[請益\] 30歲製造業轉職                             | 9    | shesaya1     |
| Re: \[請益\] 新規則，休息日加班請假？               | 7    | eladamri     |
| \[問卷\] 科技業知識分享影響之探討(抽小七禮卷)       |      | awkman       |
| \[請益\] 台塑網面試                                 | 1    | pttstrider   |
| (本文已被刪除) \[d062637776\]                       | 1    | -            |
| (本文已被刪除) \[shrines\]                          |      | -            |
| j:引戰文                                            | X2   | -            |
| (本文已被刪除) \[likeyoutoboy\]                     |      | -            |
| \[請益\] 桃園和台北的薪水                           | 7    | J774         |
| \[請益\] offer請益 友達/華碩                        | 20   | s98115145    |
| \[請益\] 什麼狀況下會選擇"不"出國工作               | 42   | douglennon   |
| \[新聞\] 《國際產業》人腦結合電腦抗AI，傳馬斯       | 10   | BBMADE       |
| Re: \[請益\] 關於台積電分紅制度                     | 10   | magic704226  |
| Re: \[請益\] 什麼狀況下會選擇"不"出國工作           | 11   | kenshin528   |
| (本文已被刪除) \[Heymandiyya\]                      | 11   | -            |
| \[新聞\] 【大立光小心囉～】原來蘋果2013年起　就     | 19   | qazxc1156892 |
| Re: \[請益\] 什麼狀況下會選擇"不"出國工作           | 8    | lovebridget  |
| \[請益\] Offer請益 應材CSE/其它                     | 8    | Chaobig      |
| (本文已被刪除) \[c08516\]                           |      | -            |
| Re: \[請益\] 南部 or 北部工作問題                   | 3    | Hatake       |
| (本文已被刪除) \[sendtony6\]                        | 8    | -            |
| \[請益\] 河洛半導體 光學FAE                         | 7    | zeromichael  |
| (已被lovewsc刪除) <zxc45693>版規七                  | X2   | -            |
| (本文已被刪除) \[va1kyrie\]                         | 8    | -            |
| \[討論\] 電的問題對科技業是否影響頗大?              | 39   | lovepork     |
| \[新聞\] 盼台積電落腳路竹　花媽喊話：給高雄一個     | 38   | zzzz8931     |
| (本文已被刪除) \[blowblow5566\]                     | 14   | -            |
| \[請益\] 光學+通訊 不錯嗎？                         | 17   | a40232145    |
| (本文已被刪除) \[lattecoffee\]                      | 2    | -            |
| Re: \[情報\] 台積電IT 人才招募中                    | 5    | wer11        |
| \[請益\] Apple NPI相關職缺的面試/工作經驗           | 3    | sugiuchi     |
| (本文已被刪除) \[ken89112344\]                      | 34   | -            |
| (本文已被刪除) \[aleed\]                            |      | -            |
| \[北部\] 交通大學電機所誠徵博士後、研士專任研究員   |      | ctl224611    |
| \[請益\] offer的薪資結構                            | 4    | smallcheng   |
| (本文已被刪除) \[scott0327\]                        |      | -            |
| (本文已被刪除) \[KKKKJAY\]                          | 7    | -            |
| Re: 請問55歲以上的RD都去那了？                      | 25   | Assyla       |
| \[請益\] 環鴻英文機上考                             | 5    | zz66         |
| \[請益\] 非研發職在科技業的發展?                    | 8    | WINNERVVV    |
| (本文已被刪除) \[werz\]                             |      | -            |
| \[請益\] 環球水泥                                   |      | cyshe89713   |
| \[請益\] offer 明泰/亞旭                            | 4    | ck49         |
| \[新聞\] 宏達電Vive獨立 年中宣布                    | 31   | jumpballfan  |
| (本文已被刪除) \[PauFrank5566\]                     | X2   | -            |
| \[請益\] 請問在design team做 sw                     | 11   | Anonynous    |
| (已被mmkntust刪除) <a467455> 板規一                 | X3   | -            |
| (本文已被刪除) \[magic704226\]                      | 1    | -            |
| \[請益\] offer請益                                  | 1    | nuer0225     |
| \[請益\] 晶睿的二面                                 | 1    | tiyico       |
| \[討論\] 台北東區以東 有做server的公司?             | 4    | sustaned     |
| Re: \[討論\] 台積電VS中油                           | 3    | tomtowin     |
| (本文已被刪除) \[pinkkate\]                         | 9    | -            |
| (已被mmkntust刪除) <lovebridget> 板規三             | 6    | -            |
| \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強        | 24   | momoko0581   |
| \[請益\] 大立光製成助理工程師職務                   | 12   | S0031104     |
| \[情報\] 區塊鏈是採用大型主機銀行的完美資料保護     |      | chunnitu     |
| (已被mmkntust刪除) <yryang> 板規一                  | 4    | -            |
| \[討論\] 南茂南科測試產品工程師                     |      | chag06       |
| \[新聞\] 晶片中心授課講師費惹議 國研院澄清          |      | nickerChen   |
| \[請益\] 億光 樹林廠 研發工程師                     | 8    | amo1126      |
| (本文已被刪除) \[zxc0312\]                          | 20   | -            |
| \[請益\]大家在校園徵才登入投遞履歷收到面試了嗎?     | 21   | wer11        |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強    | 21   | outzumin     |
| \[請益\] 思創數位，華泰電子子公司                   | 1    | johnse5533   |
| \[請益\] 天鈺 & 捷達創新                            | 2    | Electrical29 |
| (本文已被刪除) \[siriusc\]                          | 34   | -            |
| \[情報\] 區塊鏈革命--如何影響貨幣、商業並改變世     | 2    | zxcvxx       |
| \[請益\] 帆宣M6(上海吉威電子)                       | 7    | lchfrog      |
| \[情報\] 陶氏化學CDP面試                            | 7    | chengyuche   |
| \[請益\] 晨星面試                                   | 5    | Nippey       |
| \[請益\] 鴻騰與漢民的選擇                           | 12   | issue1990    |
| \[新聞\] 奇景光電助力：iPhone 8 或配備革命性        | 12   | sb5471       |
| \[新聞\] 群創加薪了！新總座宣布4月加發獎金          | 59   | kellywu      |
| \[請益\] 想請教竹科的技術員                         | 2    | beautyeye    |
| \[情報\] 裕隆集團2017校園徵才(另有暑期實習)         |      | ppttno1      |
| 創意電子 面試                                       | 8    | treliopop    |
| (已被mmkntust刪除) <zaq763> 版規六                  |      | -            |
| (本文已被刪除) \[stanleychao\]                      |      | -            |
| \[請益\] offer 廣達/鴻海                            | 9    | olymsix      |
| \[新聞\] 這家隱形冠軍年終20個月起跳　擬徵才130      | 11   | oijkue       |
| \[請益\] 台中有推薦的設備供應商嗎？                 | 2    | tortoise56   |
| (本文已被刪除) \[Cersei\]                           |      | -            |
| \[請益\] SGS/全國公證                               | 6    | sampo10102   |
| \[新聞\] 東芝半導體10搶1　台積、紫光也參戰          | 4    | thanksyou    |
| 新唐 測試設備面試                                   | 1    | game36919    |
| Re: \[新聞\] 這家隱形冠軍年終20個月起跳　擬徵才130  | 3    | pinkowa      |
| \[請益\] 漢微科(漢民微測)值得一投嗎?                | 6    | hstf         |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最      | 14   | join183club  |

解釋爬蟲結果
------------

``` r
str(tt)
```

    ## 'data.frame':    200 obs. of  3 variables:
    ##  $ Title : Factor w/ 196 levels "\n\t\t\t\n\t\t\t\t(已被mmkntust刪除) <sht255>\n\t\t\t\n\t\t\t",..: 1 19 3 15 17 14 9 5 13 20 ...
    ##  $ Push  : Factor w/ 41 levels "","10","11","12",..: 2 10 4 9 3 15 5 1 12 13 ...
    ##  $ Author: Factor w/ 137 levels "-","blacktea0930",..: 1 12 1 7 2 3 9 1 4 6 ...

解釋:共爬出了200篇的文章，有些文章已被刪除。

``` r
table(tt$Author)
```

    ## 
    ##            - blacktea0930     Blueicex      chsweet         ck49 
    ##           50            1            1            1            2 
    ##      ggggggh     kusahara    MobileMan   nick800418    okmijnuhb 
    ##            1            1            1            1            1 
    ##   popularman      q99518g    Sorry5566      tcl2830   c1823akimo 
    ##            1            1            2            1            1 
    ##    egnaro123         Herc     ian00727        ikeru    incoterms 
    ##            1            1            1            1            1 
    ##     jamiefly      key9028  simplep2002        wer11         xgin 
    ##            1            2            1            4            1 
    ##     yamakazi      ZhaoYun     zzzz8931         AKFG         CA42 
    ##            1            1            2            1            1 
    ##       chag06   DigiTalent        ej4g4     goodlike     huaygina 
    ##            2            2            1            1            1 
    ## jackjack0805     NakiXIII     neon2102         oeys       pjc202 
    ##            1            1            1            1            1 
    ##     tn372845       zxcvxx     AlioAlio        dakkk        ErioT 
    ##            1            2            1            1            1 
    ##   ihavejason  johnnypk321       KIRA47    lukenming    NTUlosers 
    ##            1            1            1            1            1 
    ## pieceofacake       q7w8s5       qlb144        quasi ssmartdan841 
    ##            1            1            1            1            1 
    ##     tomtowin       unrest     usa71111      vacfann       Wizarc 
    ##            2            1            1            1            1 
    ##    Aloha0527      ccc0901   Eighteen18 FcukYouChina   ggg1356114 
    ##            1            1            1            1            1 
    ##    ggyy08957      kellywu     moonth66    nhcuejunk    Nicher116 
    ##            1            2            1            1            1 
    ##      olivesu    Pocky5566  RacingSport      shinfon       uborek 
    ##            1            1            1            1            1 
    ##   xx10231202       awkman     eladamri      foc0327    gil729181 
    ##            1            1            1            1            1 
    ##      Gojilla         J774  magic704226   pttstrider    qazwsx517 
    ##            2            1            2            1            1 
    ##  qoo63112000     shesaya1     wahaha23        yens1    a40232145 
    ##            1            1            1            1            1 
    ##       BBMADE      Chaobig   douglennon       Hatake   kenshin528 
    ##            1            1            1            1            1 
    ##  lovebridget     lovepork qazxc1156892    s98115145  zeromichael 
    ##            1            1            1            1            1 
    ##    Anonynous       Assyla    ctl224611   cyshe89713  jumpballfan 
    ##            1            1            1            1            1 
    ##     nuer0225   smallcheng     sugiuchi    WINNERVVV         zz66 
    ##            1            1            1            1            1 
    ##      amo1126     chunnitu Electrical29   johnse5533      lchfrog 
    ##            1            1            1            1            1 
    ##   momoko0581   nickerChen     outzumin     S0031104     sustaned 
    ##            1            1            1            1            1 
    ##       tiyico    beautyeye   chengyuche    game36919         hstf 
    ##            1            1            1            1            1 
    ##    issue1990  join183club       Nippey       oijkue      olymsix 
    ##            1            1            1            1            1 
    ##      pinkowa      ppttno1   sampo10102       sb5471    thanksyou 
    ##            1            1            1            1            1 
    ##   tortoise56    treliopop 
    ##            1            1

解釋:wer11最多，有4篇;然後kellywu,key9028,chag06,zxcvxx,ck49,sorry5566,zzzz8931,Digtalent等等的是2篇。

結論: wer11他po的文章都關於面試、人才招募相關議題。 大部分的文章開頭都是offer\[請益\]，其他文章都在分享關於科技公司的心得之類的。 另外200篇之中就有50篇的文章被刪除，佔全部的1/4。
