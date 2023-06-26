# 2022_Seoul_BigdataCampus_Conference
🏆 2022 서울시 빅데이터 컨퍼런스 서울시 창조경제혁신상(최우수) 수상 작품<br>
<div align="center">
  <h1>🥈 2022 서울시 빅데이터 컨퍼런스<br><br>
  🚆 지하철 9호선 신설역 수요인원 예측 모델 개발 및 정책 제안</h1>
</div>
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/ac520ab3-bba0-4d5b-bf8f-7f1fdeaa38eb"></h3>
<h4> 💭 Language : Python <br><br>
     📌 FrameWork : Scikit-learn <br><br>
     📝 Library : Pandas, Numpy, Matplotlib, Seaborn, Haversine, Geopandas <br><br>
     🛠  Tool : Jupyter <br><br>
     📅 진행기간 : 2022.09.01 ~ 2022.11.30</h4>
        
### 👨‍👦‍👦 팀원소개
<table>
<tbody>
  <tr>
    <td align="center"><img src="" width="20px;" alt=""><br /><b>팀장 : 유제우</b></a><br /></td>
    <td align="center"><img src="" width="20px;" alt=""/><br /><b>팀원 : 이희구</b></a><br /></td>
    <td align="center"><img src="" width="20px;" alt=""/><br /><b>팀원 : 이현중</b></a><br /></td>
   <tr/>
</tbody>
</table>
<br>
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/d86cd4c1-f384-4629-9595-012c54bc98fb" height = 600px></h3>


.
# 🔊 프로젝트 개요
* 출퇴근 시간 지하철 내부의 혼잡률은 겉잡을 수 없이 심하기 때문에 압사사고, 안전사고 등이 쉽게 일어날 수 있다는 점을 고려<br>
* 최근 이태원 참사 사건으로 인해 혼잡률, 밀집률에 대한 분석 필요성 증가<br>
* 9호선의 경우 개통후 현재까지도 부정적인 여론이 형성되는 호선으로 주목<br>
* 4개의 신설역 개통전에 효율적인 정책도입이 필요
<br><br>

# 💡 주제 기획
* 특정한 시간(출퇴근 시간, 스포츠 경기시간 등)에 특정한 호선을 이용하게 되면 위험할 정도로 사람이 붐비는 밀집현상을 누구나 겪어봤을 것이라는 생각에서 해당 프로젝트의 아이디어 기획<br>
* 현재 9호선을 ‘지옥철’ 혹은 ‘콩나물 시루’와 같이 별명만 들어도 숨이 막히는 호선으로 지목<br>
* 9호선의 경우, 생긴 후 부터 현재까지도 부정적인 여론이 형성되는 호선으로 주목<br>
* 이를 통해 프로젝트에서 진행할 주제를 9호선 신설역 수요예측 및 정책 제안으로 확정
<br>

# 💡 분석 기획
* 교통 도메인의 지식을 이해하고자, 교통 관련 현업에 계신 교통 데이터 분석 멘토님에게 자문을 구함<br>
* 지하철 수요예측 관련 레퍼런스를 참고하며, 지하철 수요예측에 이용될 데이터 수집과, 전처리 기법, EDA 그리고 모델링까지, 해당 프로젝트의 전체적인 흐름 및 아키텍처 구상<br>
* 모델의 성능을 향상시키기 위한 추가적인 데이터수집 및 변수 추가와 적절한 회귀모델 선택, 하이퍼파라미터 튜닝을 진행<br><br>
<br>

# 🔎 데이터 수집
|데이터셋|출처|
|------|:------:|
|서울시 지하철 시간대별 승객 수|서울시 빅데이터캠퍼스|
|서울시 지하철 30분 단위 이용 통계|서울시 빅데이터캠퍼스|
|서울시 버스정류장 공간데이터|서울시 빅데이터캠퍼스|
|우수중소기업 공간데이터|서울시 빅데이터캠퍼스|
|서울시 주요시설과 집객시설 공간데이터|서울시 빅데이터캠퍼스|
|서울시 대학교 공간데이터|서울시 빅데이터캠퍼스|
|서울시 지하철호선별, 역별 승하차 인원 정보|공공 데이터 포털|
|서울시 주요 공원 현황 데이터|서울 열린 데이터 광장|
|서울시의 지상관측(날씨, 온도, 강수량) 데이터|기상청|
|서울시 대학교 인원 정보|크롤링|
|서울시 중,고등학교 인원 정보 데이터|크롤링|
|각 호선별 지하철의 량 수|검색|
<br>


# 🔎 데이터 전처리
## 1) 파생변수 생성
|데이터|파생변수 산출방법|파생변수|
|------|:-------------:|:--:|
|지하철 호선별, 역별 승하차 인원 정보|휴일이 누적될 때마다 +1|누적휴일|
|서울시 버스 정류장 공간데이터|Haversine을 사용해 지하철 역 반경 500m 시설물 개수를 추출|버스정류장 개수|
|우수중소기업 공간데이터|Haversine을 사용해 지하철 역 반경 500m 시설물 개수를 추출|중소기업 개수|
|서울시 주요시설과 집객시설 공간 데이터|Haversine을 사용해 지하철 역 반경 500m 시설물 개수를 추출|행정, 교육/보건, 레저/관광/예술, 숙박/음식, 산업, 영화관 개수, 백화점 개수|
|서울시 대학교 공간데이터|Haversine을 사용해 지하철 역 반경 500m 시설물 개수를 추출|대학생수|
|서울시 공원 현황 데이터|Haversine을 사용해 지하철 역 반경 500m 시설물 개수를 추출|공원 개수|

## 2) 데이터 범주화 
|원본 변수명|파생변수 산출방법|변수명|
|:------:|:-------------:|:---:|
|최고기온, 최저기온|최저 -12도 이하 / 최고 35도 이상 = 1 / 그 외의 온도 = 0|기온|
|강수량|0 mm: 정상 / 1-20 mm: 약한비 / 21-50 mm: 보통비 / 50- mm: 강한비|1일우량|
|month|12-2월: 겨울 / 3-5월: 봄 / 6-8월: 여름 / 9-11월: 가을|계절|<br><br><br>

<br><br>

# 📊 EDA(탐색적 데이터 분석)
## 1) 승하차에 영향을 주는 요인들 확인
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/c5155f19-1c34-4d24-ad21-28bd7109dab6"></h3>

* 휴일이 겹칠수록 승하차 수 감소<br>

* 날씨(한파, 폭염)의 영향으로 승하차 수 감소<br>

* 대학교 역 주변은 방학 시즌에 승하차 수가 눈에 띄게 감소<br>

* 강수량이 높아질수록 승하차 수 감소(예외적으로 매우 강한 비가 내릴때는 보통으로 내릴때보다 승하차 수가 많은 특이한 현상 발생)<br><br>

## 2) 역별 시간대별 승하차 인원 확인
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/69085d34-2497-4e2f-acf4-0509a0435918"></h3>

* 상업지역은 시간과 관계없이 골고루 유동인구가 분포합니다.

* 주거지역은 출근시간에는 승차가, 퇴근시간에는 하차가 많습니다.

* 업무지역은 출근시간에는 하차가, 퇴근시간에는 승차가 많습니다.
<br><br>
# 📄 Modeling
## 1) K-means clustering
<h3 align="center"><img src= https://github.com/LHG-Git/project/assets/100845169/72117835-2fb5-451f-a343-3c49078b02ae></h3>

* <strong>Group0</strong>은 시간과 관계없이 승하차 분포가 고르기 때문에 <strong>상업그룹</strong><br> 
* <strong>Group1</strong>은 오전에는 승차에, 오후에는 하차에 분포가 되어 있기 때문에 <strong>주거그룹</strong><br>
* <strong>Group2</strong>는 오전에는 하차에, 오후에는 승차에 분포가 되어 있기 때문에 <strong>업무그룹</strong><br><br>

#### EDA과정에서 업무지역과 주거지역은 출퇴근 시간에 유동인구가 밀집되어 있다는 근거를 통해, <strong>Group1과 Group2를 통합</strong><br>
#### <strong>클러스터링 기법을 통해 최종적으로 Group0(상업 그룹)과 Group1(업무주거 그룹)으로 분류</strong><br><br><br>

## 2) ANOVA검정
* EDA 및 분석을 통해 사용하고자 하는 변수가 승하차 인원 값에 미치는 영향이 <strong>통계적으로 유의한지 확인하기 위해 진행</strong><br><br><br>


## 3) 변수선정
|변수선정|변수|
|:------:|---|
|공통변수|노선명, 버스정류장 개수, 노선수, 계절, 기온, 공원 개수, 요일, 휴일여부, 누적휴일, 1일우량, 량|
|상업그룹 변수|산업, 숙박/음식, 레저/관광/예술, 영화관 개수, 백화점 개수|
|업무주거그룹 변수|행정, 대학생 수, 학생 수(중,고등), 교육/보건, 중소기업 개수|<br><br>
<br>


## 4) Hold-Out 검정
* <strong>Lidge, Lasso, RandomForest, Xgboost, DecisionTree, LightGBM</strong> 등 여러 회귀분석 모델들 중 모델 선정을 위한 <strong>Hold-Out 검정</strong>을 진행<br>
* 그 결과, <strong>9호선 신설역 수요 예측에 LightGBM 모델이 가장 적합할 것이라 판단하여 진행</strong><br><br><br>

## 5) LightGBM
#### <strong>LightGBM 모델을 통한 승하차수 예측</strong>,<strong>평균 절대 오차값인 MAE값을 통한 모델 성능 검증</strong><br><br>
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/2346017d-3083-46b1-828b-ba5be613f923" width = 500px height = 300px></h3>

#### (1차) : 파라미터 조정 및 k-fold 교차검증을 이용하지 않고, LightGBM 모델의 default값 그대로 초기 예측을 진행 

* <strong>상업그룹의 MAE : 2600명, 업무주거그룹의 MAE값 : 2100명</strong><br><br>
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/8c5522d5-9b82-4be0-a05c-faaa40cb8710" width = 500px height = 300px></h3>

#### (2차) : 하이퍼 파라미터 튜닝을 통해 최적의 파라미터 값을 지정 및 5차 k-fold를 이용하여 노이즈 값을 최소화한 후 예측을 진행


* <strong>상업그룹의 MAE값이 1500명, 업무주거그룹의 MAE값 990명<br>
  
### 결론 : 오차 값이 1000~1100명 정도 감소하여 성능이 향상 👍<br><br>
<br>

## 6) 모델 성능 향상
* 최적의 하이퍼 파라미터 값을 이용하기 위해, <strong>하이퍼파라미터 튜닝</strong> 진행<br><br>
* 노이즈 값을 없애고자, <strong>K-Fold 교차 검증</strong> 진행<br><br>
<br>

# 💻 예측결과
### 1) 역별 예측 결과
<h3 align="left"><img src="https://github.com/LHG-Git/project/assets/100845169/369cd3a7-8618-42a7-ad4d-cf3150945743" width = 1000px height = 400px></h3>

* 현재 9호선 역별 일평균 수요 승객은 2.7만명
* 길동생태공원, 명일공원역은 비교적 원활
* 샘터공원역은 9호선 일평균 수치와 비슷
* 고덕역은 다양한 인프라가 형성되어 있어 약 3.8만명으로 1일 승하차 평균을 크게 넘어 유동인구 혼잡 예상<br><br>

### 2) 혼잡률
<h3 align="center"><img src="https://github.com/LHG-Git/project/assets/100845169/ba09e4e5-8643-4570-8c1a-4fe10b46bd82" width = 500px height = 300px></h3>

* 고덕역 예측 수요 약 3.8만명
* 고덕역 혼잡률 200% 이상  
* 고덕역의 승하차 수요와 현재 환승역임을 감안하여 급행역으로 선정<br><br>

# 📍 9호선 신설역 그룹화
### 1) 업무주거 그룹 : 길동생태공원, 명일공원역, 고덕역
* <strong>길동생태공원</strong>의 경우 시점역, 천호대로와 동남부 교차로 및 주변의 공원과 더불어 아파트가 밀집<br><br>
* <strong>명일공원역</strong>의 경우 중,고등학교 등 각종 교육시설과 일반 주택 및 아파트가 밀집<br><br> 
* <strong>고덕역</strong>의 경우 고등학교, 병원, 아파트 등 각종 교육 시설이 밀집<br><br> 
* <strong>따라서 길동생태공원, 명일공원역, 고덕역은 업무주거 그룹에 해당</strong><br><br>

### 2) 상업그룹 : 샘터공원역
* <strong>샘터공원역</strong>의 경우엔 고덕 강일 공공주택 1지구가 위치해있고, 고덕비즈밸리 중심 상업지역에 위치<br><br> 
* <strong>따라서 샘터공원역은 상업그룹에 해당</strong><br><br>

# 🚩 정책 제안
### 1) 대각선 신호등 설치
* 대각선 신호등을 설치하지 않으면 유동인구가 많은 지하철역에서 사람들이 몰리는 현상이 발생할 것
* 그러면 공간부족으로 차도에 발을 딛는 사람들이 점점 늘어날 것이고 그들의 안전은 보장할 수 없음 
* 그렇기 때문에 다른 역에 비해 수요승객수가 가장 많은 고덕역의 경우, <strong>사람들이 원활하게 이동할 수 있는 대각선 신호등 배치를 한다면 교통 및 혼잡한 상황을 예방할 수 있을 것으로 예상됨</strong>

### 2) 급행역 선정
* 승하차 수요는 중요한 고려사항이며 고덕역의 경우 환승노선이 2개인 점과, 예측승객수가 3만 명을 넘는 것을 감안했을 때, <strong>급행역으로 선정이 되는 것이 9호선 내부의 혼잡도를 예방할 수 있는 방안임</strong>

### 3) 도심 공동화 예방
* 도시가 성장하면서 땅값이 오르고, 그로인해 상업 시설들이 다수를 차지하게 됨
* 상업 시설의 특성상 상주인구는 매우 적은 대신 유동 인구가 많은 편
* 결국, 도심의 상주인구는 줄어들게 되는데, 이를 예방하기 위해 <strong>상업그룹에 해당하는 고덕역과 샘터 공원역 주변에 신축되는 고층건물에 대해서는 일정비용을 주거 용도로 하여 직장과 주거지가 이웃하도록 짓는다면, 도심공동화 현상을 예방할 수 있을 것으로 예상됨</strong>

### 4) 8량 추진화
* 9호선의 수요승객이 하루 평균 69만 명에서 약 78만 명으로 늘어남 
* 9호선의 지하 박스 구조물 자체는 8량 길이에 맞추어져 있어 신호, 전기, 승강장, 마감, 조명 등 공사를 진행 할 경우 막대한 예산이 들어감
* 9호선 승강장은 최대 8량까지 운행할 수 있도록 설계됐지만 제대로 활용하지 못하고 있음
* 위 예측결과는 9호선 8량화 추진에 힘을 실어줄 수 있는 근거로 활용될 수 있음

### 5) 적절한 출입구 입지 선정
* 지하철 이용의 혼잡도 문제는 단순히 지하철 내부의 현상을 넘어서, 외부로까지 이어짐 
* 위에 언급한 대각선 신호의 문제와 더불어, <strong>출입구의 적절한 위치 선정은 매우 중요한 사항에 해당</strong>
