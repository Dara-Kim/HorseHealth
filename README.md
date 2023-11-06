# HorseHealth
Kaggle playground Competition-Predict Health Outcomes of Horses

Start Date - September 12, 2023<br/>
Final Submission Deadline - October 2, 2023
## 목차
1. [대회 소개 및 목표](#대회-소개-및-목표)
2. [데이터 셋 설명](#데이터-셋-설명)
3. [코드](#코드)
4. [결과 및 한계점](#결과-및-한계점)

## 대회 소개 및 목표

Horse Survival Dataset을 이용해 말의 생존 여부를 3가지로 예측.
- Lived
- Euthanized
- Died

## 데이터 셋 설명

원본 데이터: https://www.kaggle.com/datasets/yasserh/horse-survival-dataset/data

말의 건강 상태 데이터 

- train.csv - the training dataset; outcome is the (categorical) target
- test.csv - the test dataset; your objective is to predict outcome
- sample_submission.csv - a sample submission file in the correct format

## 코드
모델 설명 <br/>
다른 모델을 선택한 이유 <br/>
e.g. 이러이러해서 이걸 추가하면 좋을 것 같고 성능이 어떻게 변했다 <br/>
모델 간 비교 <br/>
기술적인 부분은 표로 (평가 지표를 이용해서) <br/>


1. origin data 활용
2. feature engineering
   - 새로운 feature 생성
   - 컬럼 특성별 label encoding
   - 컬럼 특성별 scaling (별도의 scaler는 사용하지 않음)
   - *scaler를 사용하면 점수 하락*
   - 결측 행 제거
   - 범주형 feature의 결측값은 중간값으로
   - 숫자형 feature의 결측값은 KNNImputer로
3. 모델 선정: Lazy predict
   - lgbm의 feature importance 기준 feature 삭제
   - xgb, lgb, cat 모델 사용
   - optuna로 하이퍼파라미터 조정
4. stacking classifier 사용
   
## 결과 및 한계점

**1. 결과**<br/> 
- public score로는 88점이 넘는 팀도 있었음
- 그러나 public과 private 모두 78점으로 변동이 없었던 내 코드가 우승 <br/>
원인: 학습 데이터(public)와 대회 측 채점 데이터(private)의 분포 차이 <br/>
   -> Data shake up이 발생했다고 표현<br/>

**2. 안정적인 성능의 이유**<br/>   
- Feature간의 관계성 파악하고 Feature Engineering에 반영
- Optuna를 이용해 하이퍼파라미터 최적화
- 학습을 과하게 시키지 않음<br/>
+운이 정말 좋았음<br/>

**3. 아쉬운 점**<br/>
- 대회 종료 12시간 전 직관으로 짠 코드
- 다양하게 학습시켜보지 못한 점
- Random seed 고정하지 않음
   -> 같은 우승 코드이지만 Optuna를 시도했던 최적 하이퍼파라미터 조합이 없어졌다
