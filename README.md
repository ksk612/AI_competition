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
 1) 관련된 데이터셋을 MMSI 기준으로 Concat
 2) 공간정보를 활용한 feature engineering
 3) 데이터 선형성 검증 - PCA를 통한 차원축소 후 scatter plot을 통해 선형성 검증 (선형성 X)
 4) 비선형적 데이터에 강력한 Tree-base model을 soft-voting하여 모델구축
    




