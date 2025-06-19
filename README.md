# 2025 해군해병대 인공지능 경진대회

◼︎ 대회기간 : 25.5.28.(수) ~ 5.29.(목) / 27시간 무박진행

◼︎ 주최/후원 : 해군 및 해병대 (주최), IBK기업은행 (후원) 

## 출제문제

◼︎ 문제1 : AIS데이터를 통한 의심선박 분류

◼︎ 문제2 : AIS데이터를 통한 북한선박 분류

◼︎ 데이터 : 해안지역에서 획득한 AIS데이터

## 해결과정

### 의심선박 분류
<img width="791" alt="스크린샷 2025-06-19 오후 8 32 49" src="https://github.com/user-attachments/assets/f5ef7f06-1ca3-4f65-a535-ab16d309a5d6" />

 - 관련된 데이터셋을 MMSI 기준으로 Concat
    
 - 공간정보를 활용한 feature engineering
 
 - 데이터 선형성 검증 - PCA를 통한 차원축소 후 scatter plot을 통해 선형성 검증 (선형성 X)
 
 - 비선형적 데이터에 강력한 Tree-base model을 soft-voting하여 모델구축


### 북한선박 식별 
 * 극복해야할 문제의 특성 : MMSI별 timestamp 길이의 차이, 개별선박의 AIS on/off로 인한 결측치, class의 불균형
   
 - 1차 접근 : Transformer 기반 모델
   
   <img width="734" alt="스크린샷 2025-06-19 오후 8 44 51" src="https://github.com/user-attachments/assets/f70ba3bd-a394-4c42-9970-f30906767596" />

   Transformer 모델적용을 위한 방법 : 1시간 단위로 시간단위 통일(positional encoding은 시간적 순서를 학습), 원본대비 데이터크기 감소(1시간 이외 불필요 data삭제)

   1차접근의 결과 및 한계점 : F1_score 기준 0.91~2정도 수준 / 단순한 데이터대비 모델의 복잡성, 하이퍼파라미터 최적화가 미흡(대회시간 상 제한)

- 2차 접근 : Boosting 계열 pivot

   모델적용을 위한 방법 : Feature engineering을 통해 통계적 특성을 추가변수로 생성(위경도, 속도, 북한근처해역 활동여부, 경계선 횡단여부 등)

   사용된 모델 : Catboost(class의 불균형을 고려하여 1:4비율로 설정하여 모델구축)


### 결과

<img width="718" alt="스크린샷 2025-06-20 오전 5 56 51" src="https://github.com/user-attachments/assets/1813afc6-b346-41a3-88fa-265ebe798f3b" />

의심선박 식별(0.9979) / 북한선박 식별(1.0000)





