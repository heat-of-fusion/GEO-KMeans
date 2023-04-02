# GEO-KMeans

### 프로젝트의 목적
KMeans 알고리즘을 공부하면서 이 알고리즘을 사용하여 어떤 문제를<br/>
해결할 수 있을지 고민을 해봤습니다.<br/>

그러다가 문뜩 K-Means 알고리즘과 대한민국의 인구밀도 산점도를 활용하면 <br/>
대한민국의 인구 밀도에 따른 최적화된 행정구역을 재구성할 수 있지 않을까 <br/>
생각이 들었습니다.

그래서 인터넷에서 데이터셋들을 찾고, 해당 데이터셋들을 활용하여<br/>
위의 문제를 해결해봤습니다.<br/>

<hr/>

### 데이터셋 출처
행정구역별 위도/경도 데이터셋: https://skyseven73.tistory.com/23<br/>
행정구역별 인구 수 데이터셋: https://www.data.go.kr/data/15097972/fileData.do

<hr/>

### 데이터 전처리
-행정구역별 인구 수 데이터
|    |   행정기관코드 | 기준연월   | 시도명     | 시군구명   | 읍면동명   |    계 |   남자 |   여자 |   만0세남자 |   만1세남자 |   만2세남자 |   만3세남자 |   만4세남자 |   만5세남자 |   만6세남자 |   만7세남자 |   만8세남자 |   만9세남자 |   만10세남자 |   만11세남자 |   만12세남자 |   만13세남자 |   만14세남자 |   만15세남자 |   만16세남자 |   만17세남자 |   만18세남자 |   만19세남자 |   만20세남자 |   만21세남자 |   만22세남자 |   만23세남자 |   만24세남자 |   만25세남자 |   만26세남자 |   만27세남자 |   만28세남자 |   만29세남자 |   만30세남자 |   만31세남자 |   만32세남자 |   만33세남자 |   만34세남자 |   만35세남자 |   만36세남자 |   만37세남자 |   만38세남자 |   만39세남자 |   만40세남자 |   만41세남자 |   만42세남자 |   만43세남자 |   만44세남자 |   만45세남자 |   만46세남자 |   만47세남자 |   만48세남자 |   만49세남자 |   만50세남자 |   만51세남자 |   만52세남자 |   만53세남자 |   만54세남자 |   만55세남자 |   만56세남자 |   만57세남자 |   만58세남자 |   만59세남자 |   만60세남자 |   만61세남자 |   만62세남자 |   만63세남자 |   만64세남자 |   만65세남자 |   만66세남자 |   만67세남자 |   만68세남자 |   만69세남자 |   만70세남자 |   만71세남자 |   만72세남자 |   만73세남자 |   만74세남자 |   만75세남자 |   만76세남자 |   만77세남자 |   만78세남자 |   만79세남자 |   만80세남자 |   만81세남자 |   만82세남자 |   만83세남자 |   만84세남자 |   만85세남자 |   만86세남자 |   만87세남자 |   만88세남자 |   만89세남자 |   만90세남자 |   만91세남자 |   만92세남자 |   만93세남자 |   만94세남자 |   만95세남자 |   만96세남자 |   만97세남자 |   만98세남자 |   만99세남자 |   만100세남자 |   만101세남자 |   만102세남자 |   만103세남자 |   만104세남자 |   만105세남자 |   만106세남자 |   만107세남자 |   만108세남자 |   만109세남자 |   만110세이상남자 |   만0세여자 |   만1세여자 |   만2세여자 |   만3세여자 |   만4세여자 |   만5세여자 |   만6세여자 |   만7세여자 |   만8세여자 |   만9세여자 |   만10세여자 |   만11세여자 |   만12세여자 |   만13세여자 |   만14세여자 |   만15세여자 |   만16세여자 |   만17세여자 |   만18세여자 |   만19세여자 |   만20세여자 |   만21세여자 |   만22세여자 |   만23세여자 |   만24세여자 |   만25세여자 |   만26세여자 |   만27세여자 |   만28세여자 |   만29세여자 |   만30세여자 |   만31세여자 |   만32세여자 |   만33세여자 |   만34세여자 |   만35세여자 |   만36세여자 |   만37세여자 |   만38세여자 |   만39세여자 |   만40세여자 |   만41세여자 |   만42세여자 |   만43세여자 |   만44세여자 |   만45세여자 |   만46세여자 |   만47세여자 |   만48세여자 |   만49세여자 |   만50세여자 |   만51세여자 |   만52세여자 |   만53세여자 |   만54세여자 |   만55세여자 |   만56세여자 |   만57세여자 |   만58세여자 |   만59세여자 |   만60세여자 |   만61세여자 |   만62세여자 |   만63세여자 |   만64세여자 |   만65세여자 |   만66세여자 |   만67세여자 |   만68세여자 |   만69세여자 |   만70세여자 |   만71세여자 |   만72세여자 |   만73세여자 |   만74세여자 |   만75세여자 |   만76세여자 |   만77세여자 |   만78세여자 |   만79세여자 |   만80세여자 |   만81세여자 |   만82세여자 |   만83세여자 |   만84세여자 |   만85세여자 |   만86세여자 |   만87세여자 |   만88세여자 |   만89세여자 |   만90세여자 |   만91세여자 |   만92세여자 |   만93세여자 |   만94세여자 |   만95세여자 |   만96세여자 |   만97세여자 |   만98세여자 |   만99세여자 |   만100세여자 |   만101세여자 |   만102세여자 |   만103세여자 |   만104세여자 |   만105세여자 |   만106세여자 |   만107세여자 |   만108세여자 |   만109세여자 |   만110세이상여자 |
|---:|---------------:|:-----------|:-----------|:-----------|:-----------|------:|-------:|-------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|------------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|-------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|--------------:|------------------:|
|  0 |     1111051500 | 2023-02-28 | 서울특별시 | 종로구     | 청운효자동 | 11605 |   5325 |   6280 |          14 |          22 |          25 |          29 |          20 |          39 |          46 |          56 |          45 |          40 |           57 |           61 |           57 |           54 |           60 |           60 |           58 |           54 |           70 |           58 |           58 |           63 |           63 |           65 |           75 |           64 |           78 |           80 |           72 |           79 |           92 |           75 |           70 |           65 |           66 |           73 |           55 |           68 |           70 |           65 |           83 |           90 |           93 |          102 |           73 |           70 |           89 |           90 |           92 |          102 |           93 |          115 |           87 |           95 |           93 |           78 |           90 |           80 |           60 |           63 |           77 |           87 |           85 |           58 |           72 |           62 |           44 |           67 |           50 |           48 |           46 |           30 |           39 |           37 |           34 |           43 |           36 |           25 |           44 |           25 |           43 |           32 |           29 |           25 |           25 |           22 |           21 |           14 |            8 |           14 |            4 |            5 |            3 |            2 |            0 |            3 |            1 |            2 |            2 |            1 |             1 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |          24 |          25 |          22 |          24 |          30 |          19 |          43 |          41 |          45 |          47 |           52 |           52 |           58 |           47 |           61 |           61 |           73 |           36 |           50 |           43 |           57 |           50 |           66 |           67 |           90 |           69 |           81 |           83 |           90 |           79 |          109 |           83 |           75 |           87 |           85 |           67 |           80 |           82 |           95 |           94 |           98 |          117 |          134 |          112 |          115 |           98 |          106 |          118 |          113 |          120 |          116 |          101 |          111 |          116 |          104 |          116 |           85 |          105 |           92 |           90 |           76 |           84 |           81 |           94 |           79 |           76 |           84 |           62 |           60 |           52 |           69 |           49 |           55 |           62 |           50 |           56 |           59 |           54 |           49 |           55 |           56 |           39 |           36 |           41 |           38 |           24 |           22 |           23 |           18 |           17 |           12 |           11 |            6 |            5 |            6 |            3 |            2 |            2 |            1 |            1 |             1 |             1 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |
|  1 |     1111053000 | 2023-02-28 | 서울특별시 | 종로구     | 사직동     |  9120 |   4060 |   5060 |          12 |          24 |          12 |          22 |          20 |          26 |          37 |          43 |          33 |          26 |           29 |           33 |           24 |           21 |           39 |           30 |           21 |           26 |           34 |           26 |           30 |           32 |           33 |           47 |           44 |           46 |           50 |           55 |           63 |           69 |           87 |           81 |           79 |           70 |           48 |           50 |           58 |           42 |           53 |           49 |           72 |           78 |           61 |           49 |           54 |           58 |           68 |           59 |           73 |           67 |           72 |           82 |           80 |           71 |           74 |           67 |           60 |           60 |           57 |           62 |           65 |           72 |           73 |           66 |           48 |           70 |           56 |           55 |           45 |           32 |           41 |           22 |           22 |           32 |           28 |           29 |           24 |           30 |           29 |           22 |           35 |           22 |           28 |           22 |           28 |           20 |           21 |           13 |           15 |           12 |            7 |            5 |            1 |            5 |            5 |            5 |            1 |            1 |            3 |            0 |             1 |             0 |             0 |             0 |             0 |             0 |             1 |             0 |             0 |             0 |                 0 |           9 |          17 |          16 |          20 |          21 |          25 |          36 |          30 |          34 |          36 |           41 |           32 |           45 |           33 |           35 |           39 |           33 |           42 |           42 |           40 |           39 |           40 |           36 |           58 |           58 |           67 |           73 |           87 |           82 |           84 |           97 |           89 |           90 |           55 |           71 |           88 |           58 |           83 |           77 |          110 |           82 |           77 |           76 |           75 |           67 |           84 |           84 |           81 |           71 |           77 |           90 |           70 |           97 |          101 |           84 |           82 |           68 |           69 |           81 |           77 |           74 |           74 |           75 |           82 |           74 |           62 |           57 |           56 |           45 |           50 |           50 |           31 |           46 |           48 |           37 |           46 |           39 |           30 |           43 |           37 |           45 |           37 |           35 |           33 |           34 |           28 |           22 |           20 |           20 |           11 |           11 |            8 |           11 |           10 |            6 |            3 |            3 |            3 |            0 |            2 |             1 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |
|  2 |     1111054000 | 2023-02-28 | 서울특별시 | 종로구     | 삼청동     |  2322 |   1104 |   1218 |           2 |           2 |           2 |           2 |           3 |           4 |           6 |           6 |           4 |           7 |            8 |            8 |            9 |           12 |            8 |           13 |           12 |           15 |            7 |           10 |            5 |            8 |           13 |           17 |           15 |           13 |           18 |           12 |           10 |           16 |           21 |           11 |           17 |            9 |           25 |            9 |            7 |           11 |           13 |           17 |           19 |           14 |           19 |           21 |           13 |           15 |           13 |           14 |           15 |           12 |           14 |           19 |           20 |           16 |           23 |           20 |           15 |           15 |           20 |           18 |           16 |           23 |           17 |           22 |           24 |           16 |           13 |           21 |           17 |           16 |           14 |            8 |            7 |           20 |           14 |           17 |            5 |            7 |            9 |            9 |            7 |           11 |            9 |            5 |            3 |            3 |            7 |            6 |            1 |            1 |            5 |            1 |            2 |            2 |            0 |            1 |            2 |            0 |            0 |            0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             1 |             0 |             0 |                 0 |           3 |           2 |           3 |           4 |           3 |          11 |           1 |           9 |           2 |          12 |            5 |           11 |            8 |            9 |            8 |            7 |            6 |            4 |            9 |            5 |            4 |           11 |           13 |           13 |           13 |           18 |           12 |           21 |           20 |           16 |           18 |           18 |           15 |           15 |           18 |           14 |           14 |           12 |           16 |           15 |           23 |           18 |           20 |           20 |           13 |           19 |            9 |           11 |           21 |           23 |           20 |           19 |           19 |           17 |           17 |           21 |           13 |           28 |           17 |           13 |           19 |           24 |           20 |           20 |           27 |           23 |           19 |           17 |           21 |           10 |           24 |           10 |            8 |           12 |           15 |           17 |           15 |           10 |           13 |            6 |           17 |           15 |            9 |           10 |            5 |           10 |           10 |            6 |            7 |            7 |            2 |            3 |            2 |            3 |            1 |            1 |            0 |            0 |            0 |            0 |             1 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |
|  3 |     1111055000 | 2023-02-28 | 서울특별시 | 종로구     | 부암동     |  9178 |   4340 |   4838 |          13 |          14 |           6 |          21 |          12 |          17 |          33 |          25 |          28 |          30 |           51 |           42 |           49 |           44 |           38 |           52 |           47 |           48 |           49 |           57 |           42 |           47 |           67 |           40 |           60 |           49 |           66 |           82 |           67 |           60 |           67 |           58 |           67 |           53 |           49 |           47 |           44 |           61 |           49 |           66 |           63 |           50 |           57 |           69 |           58 |           62 |           63 |           54 |           66 |           80 |           84 |           81 |           84 |           81 |           66 |           79 |           59 |           67 |           76 |           78 |           69 |           72 |           60 |           82 |           69 |           54 |           58 |           60 |           45 |           53 |           42 |           34 |           33 |           32 |           34 |           48 |           26 |           31 |           32 |           22 |           34 |           26 |           21 |           20 |           13 |           21 |           14 |           10 |           13 |            3 |            5 |            3 |            3 |            1 |            1 |            1 |            0 |            1 |            0 |            0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |          12 |          12 |           8 |          14 |          18 |          27 |          26 |          26 |          31 |          36 |           34 |           26 |           35 |           32 |           37 |           39 |           39 |           43 |           44 |           48 |           43 |           57 |           49 |           56 |           70 |           66 |           41 |           59 |           67 |           59 |           71 |           59 |           56 |           49 |           47 |           48 |           70 |           62 |           56 |           67 |           60 |           77 |           83 |           82 |           66 |           74 |           83 |           71 |           89 |          105 |           81 |           99 |           94 |           98 |           99 |           83 |           83 |           89 |           79 |           84 |           73 |           72 |          102 |           76 |           66 |           78 |           67 |           77 |           57 |           45 |           51 |           32 |           36 |           49 |           39 |           56 |           42 |           39 |           27 |           32 |           31 |           41 |           24 |           37 |           23 |           27 |           18 |           20 |           12 |           13 |            9 |           12 |            5 |            7 |           10 |            5 |            5 |            0 |            1 |            0 |             2 |             1 |             1 |             0 |             0 |             0 |             0 |             0 |             0 |             0 |                 0 |
|  4 |     1111056000 | 2023-02-28 | 서울특별시 | 종로구     | 평창동     | 17602 |   8212 |   9390 |          33 |          46 |          37 |          56 |          57 |          54 |          57 |          80 |          73 |          71 |           72 |           55 |           80 |           70 |           67 |          101 |           70 |           63 |           83 |           89 |           80 |           99 |          126 |          100 |           94 |           92 |          115 |          115 |          116 |          126 |          101 |          112 |          107 |           88 |           90 |          102 |           80 |           96 |          100 |          107 |          102 |          130 |          133 |          121 |          106 |           91 |          117 |           92 |          117 |          147 |          133 |          149 |          148 |          146 |          150 |          145 |          121 |          144 |          148 |          114 |          172 |          165 |          149 |          144 |          131 |          124 |          124 |          110 |          101 |           91 |           99 |           57 |           62 |           70 |           73 |           67 |           57 |           43 |           38 |           51 |           43 |           51 |           39 |           40 |           39 |           31 |           25 |           28 |           20 |           16 |           12 |           10 |            2 |            1 |            5 |            1 |            1 |            0 |            2 |            1 |             2 |             0 |             0 |             0 |             1 |             0 |             0 |             0 |             0 |             0 |                 0 |          29 |          31 |          50 |          49 |          35 |          47 |          46 |          71 |          70 |          68 |           71 |           74 |           93 |           61 |           77 |           81 |           84 |           75 |           95 |           81 |           80 |           97 |          106 |          115 |          104 |          111 |          116 |          112 |          128 |          126 |          112 |           99 |           92 |           92 |           97 |          119 |          125 |          110 |          109 |          123 |          151 |          151 |          145 |          136 |          130 |          123 |          122 |          129 |          146 |          176 |          178 |          178 |          179 |          186 |          204 |          172 |          170 |          174 |          152 |          171 |          156 |          168 |          184 |          129 |          146 |          158 |          133 |          128 |          133 |          104 |           89 |           69 |           58 |           66 |           89 |           76 |           82 |           71 |           78 |           53 |           48 |           67 |           56 |           58 |           50 |           55 |           40 |           34 |           42 |           27 |           19 |           20 |           15 |            9 |           10 |           11 |           10 |            1 |            4 |            3 |             2 |             2 |             0 |             1 |             0 |             0 |             1 |             0 |             1 |             0 |                 0 |
