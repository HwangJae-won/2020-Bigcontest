# 2020 Bigcontest 퓨처스리그 

# 1. 개요 
- 주제: KBO 잔여시즌 팀별 승률, 타율 및 방어율 예측
- 수상: 우수상(450개팀 중 6위)
- 기간: 2020.07 ~ 2020.09
- 팀원: 김동우, 김시현, 김재홍, 박준근, 황재원
- 사용 skill: Python
<img width="779" alt="image" src="https://user-images.githubusercontent.com/79994991/166680080-199c10ab-cbbb-4fd3-a73a-e202e42e8c7e.png">

# 2. 타율 및 방어율 분석
<img width="797" alt="image" src="https://user-images.githubusercontent.com/79994991/166682680-bbe90dee-dc8b-479f-997a-29b30801389c.png">

## 2-1) 데이터 
- Raw data: 각 팀별 PA, HIT, AB, BB, IB, HP, SF, KK 등 경기력을 설명할 수 있는 지표 데이터
- statiz 사이트 크롤링을 통해 2020년 잔여 경기 데이터 수집
- 기존 지표들을 활용하여 타율, 방어율에 영향을 미치는 변수들 추가
- 시즌별 팀 누적합으로 요약
- coefficient 및 VIF를 활용하여 적절한 변수 선정

## 2-2) 분석
- irreducible error와 variance가 높은 야구 데이터의 특성을 고려하여 overfitting을 방지하고자 linear regression model 선정
- 그 중, 분산을 안정화할 수 있는 WLS 모델 선정
- residual analysis를 활용하여 outlier 제

## 2-3) 예측 결과 
<img width="789" alt="image" src="https://user-images.githubusercontent.com/79994991/166682623-4eb36b8e-6a7f-40a3-8630-af523c78acc9.png">
<img width="792" alt="image" src="https://user-images.githubusercontent.com/79994991/166682740-c4ac32e9-6fac-44e6-97a8-8fd35cc714b7.png">

# 3. 승률 분석
- 과거 누적 데이터와 미래 승패는 관련 없다고 판단한 후 test set과 같은 시점의 데이터를 독립 변수로 활용하여 예측하기로 분석 방향 설정
- 타율, 방여율의 예측값 활용
- 팀별 조합을 생성하여 feature engineering 실행
<img width="795" alt="image" src="https://user-images.githubusercontent.com/79994991/166682808-00aa7d33-08d5-4730-a188-0aadb233d46e.png">

## 3-1) 사용 모델
- Ridge, Lasso, RF, XGBoost 등의 모델 성능 비교
- test MSE가 낮고, 올해 경기 양상을 잘 반영하는 RF로 최종 예측 진행

## 3-2) 승률 예측 결과
<img width="793" alt="image" src="https://user-images.githubusercontent.com/79994991/166683344-65a1cf44-8735-444b-bd4b-9f2df87f2c34.png">
