# Student grades predict models

학생의 성적을 상, 중, 하로 예측하는 머신러닝 모델을 학습, 예측, 평가합니다.

## 데이터셋

- **gender**: 학생의 성별 (M: 남성, F: 여성)
- **NationaliTy**: 학생의 국적
- **PlaceofBirth**: 학생이 태어난 국가
- **StageID**: 학생이 다니는 학교 (초,중,고)
- **GradeID**: 학생이 속한 성적 등급
- **SectionID**: 학생이 속한 반 이름
- **Topic**: 수강한 과목
- **Semester**: 수강한 학기 (1학기/2학기)
- **Relation**: 주 보호자와 학생의 관계
- **raisedhands**: 학생이 수업 중 손을 든 횟수
- **VisITedResources**: 학생이 과목 공지를 확인한 횟수
- **Discussion**: 학생이 토론 그룹에 참여한 횟수
- **ParentAnsweringSurvey**: 부모가 학교 설문에 참여했는지 여부
- **ParentschoolSatisfaction**: 부모가 학교에 만족했는지 여부
- **StudentAbscenceDays**: 학생의 결석 횟수 (7회 이상/미만)
- **Class**: 학생의 성적 등급 (L: 낮음, M: 보통, H: 높음)

## EDA

데이터를 분석하기 전에 데이터의 특징을 시각화하고 이해하는 과정입니다.  
아래의 순서대로 진행됩니다.

1. **데이터의 기본 정보 확인**
   - `df.info()`, `df.columns`, `df.head()`, `df.shape`
   - 결측치(누락된 값) 확인: `df.isnull().sum()`
2. **데이터 분포 파악**
   - 카운트플롯: `sns.countplot()`
   - 히스토그램: `sns.histplot()`
   - 박스플롯: `sns.boxplot()`
   - 산점도: `sns.scatterplot()`
   - 파이플롯: `plt.pie()`
3. **데이터 관계 확인**
   - 상관계수: `df.corr()`, `sns.heatmap()`

## 모델 학습, 평가

1. **모델 선택**
   - 랜덤 포레스트
   - 로지스틱 회귀
   - XGBoost
2. **피쳐 선택, 추출 가공**
   - 모델에 맞는 피쳐 선정, 가공
   - 관계가 낮은 피쳐 제거: `df.drop()`
   - 라벨 인코딩, 원-핫 인코딩
3. **파라미터 최적화**
   - 최적 파라미터 구하기: `grid_search.fit()`
   - 최적 파라미터 이용해서 예측
4. ## **ROC 커브로 최적화**
   - 모델의 성능을 ROC 커브와 AUC 점수를 통해 평가
   - `roc_curve()`, `roc_auc_score()`를 활용하여 최적의 임계값 찾기
   - FPR과 TPR의 균형을 고려하여 모델 조정
5. **예측**
   - `model.predict()`
   - `model.predict_proba()` 를 이용하여 확률 기반 예측 수행
6. **평가**
   - 정확도, 정밀도, 재현률, f1 스코어

## 결론

- 파라미터 최적화로 Metric을 성공적으로 개선했습니다.
- Logistic Regression은 이진 분류에 적합한 모델이고, 다중 클래스 분류에는 적합하지 않습니다.

## 파일 구조

```
📂 data                         # 데이터셋이 위치한 디렉토리
    └──📄 xAPI-Edu-Data.csv     # 학생 성적에 관한 데이터
📂 notebooks                    # 쥬피터 노트북들이 위치한 디렉토리
    └──📄 eda.ipynb             # EDA
    └──📄 sklearn.ipynb         # sklearn을 이용한 학생 성적 예측
📄 README.md                    # README
```
