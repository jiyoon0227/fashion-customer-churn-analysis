# Fashion Customer Churn Analysis

# 패션 커머스 고객 이탈 예측 프로젝트
> H&M 트랜잭션 데이터를 활용하여 고객의 구매 패턴을 분석하고 이탈 위험을 예측합니다.

## 📂 프로젝트 구조
- **01_data_preparation.ipynb**: 데이터 정제 및 이탈 정의 
- **02_feature_engineering_eda.ipynb**: 고객/상품 피처 생성 및 탐색적 분석
- **03_model_training.ipynb**: 머신러닝 모델 학습 및 평가
- **04_business_strategy.ipynb**: 비즈니스 인사이트 및 전략 도출 
---

## Step 01: 데이터 정제 및 이탈(Churn) 정의

### 1. 데이터 클리닝 (Outlier Removal)
- **리셀러 제거**: 상위 0.1% 구매 건수(385건) 이상인 고객을 이상치로 판단하여 제거했습니다. 이를 통해 일반 고객의 패턴을 왜곡하는 노이즈를 방지했습니다.
- **동시 구매 처리**: 동일 날짜에 발생한 여러 건의 트랜잭션을 하나의 '방문'으로 처리하여 순수한 재방문 주기(Days Diff)를 산출했습니다.

### 2. 이탈(Churn)의 과학적 정의
- **재구매 주기 분석**: 데이터 분석 결과, 재방문 고객의 **84.6%가 90일 이내에 다시 구매**하는 것을 확인했습니다.
- **기준 확립**: 이에 따라 마지막 구매 후 **90일간 활동이 없는 고객을 '이탈(1)'**로 정의했습니다.

### 3. 주요 시각화 (EDA)
| 이상치 제거 기준 (상위 0.1%) | 누적 재구매 확률 분포 |
| :---: | :---: |
| ![이상치그래프]
<img width="1035" height="553" alt="image" src="https://github.com/user-attachments/assets/e5b8ed42-b30a-4324-b79f-833a2c0ba199" />
| ![확률그래프]
<img width="863" height="553" alt="image" src="https://github.com/user-attachments/assets/dfb7b8a7-bbac-4d9d-ab4f-82e45032b77c" />


> *그래프 설명: 왼쪽은 리셀러를 정의한 기준선이며, 오른쪽은 90일 이내 재구매 확률이 수렴하는 지점을 보여줍니다.*
