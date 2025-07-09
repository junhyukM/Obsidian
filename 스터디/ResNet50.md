## ✅ ResNet50 임베딩 방식: "이미지의 시각적 패턴만" 추출

---
### 🔧 기본 개요
- ResNet50은 CNN(Convolutional Neural Network) 계열의 모델
- 원래 목적은 **1000개의 이미지 분류** (예: 고양이, 개, 버스...)
- 하지만 **마지막 분류층(Softmax)** 전에 나오는 **특징 벡터**를 **임베딩**으로 사용
---
### 📌 구조 요약
1. 입력: `224x224 RGB 이미지`
2. 여러 층의 **Conv → BatchNorm → ReLU → Pooling** 반복
3. 각 블록에는 **Residual connection**이 포함됨
4. 마지막에 **Global Average Pooling (GAP)**  
    → 이게 전체 이미지의 정보 요약
5. FC (Fully Connected Layer): 일반적으로 2048차원
6. (원래는 분류기 softmax가 붙지만 **우리는 이 전단계만 사용**)
---
### 🧠 임베딩 추출 과정

```plaintext
이미지 (224x224x3)
↓ Conv layers + Residual blocks (50층)
↓ Global Average Pooling (공간 축 평균)
↓ FC layer → 결과: (1, 2048) 벡터
```

이 **2048차원 벡터**가 이 이미지의 임베딩

---

### ✅ 특성
- 입력 이미지의 **시각적 패턴 (윤곽, 색상, 텍스처, 위치)** 중심으로 학습됨
- 클래스 라벨을 기준으로 학습되어 **"비슷한 시각적 특징"을 가진 이미지를 가깝게** 만듦