# 2025_AI 미니프로젝트  
**컴퓨터정보공학과 3-A | 202344023 고은지**

## 주제  
**CNN 기반 딥러닝 모델을 사용한 7가지 교통수단 이미지 분류**  
64×64 픽셀 RGB 이미지로 이루어진 교통수단 영상 데이터 분류

---

## 목표  
딥러닝 기반 CNN 모델을 이용하여 아래 7개의 교통수단 이미지를 분류한다:  

- Auto Rickshaws  
- Bikes  
- Cars  
- Motorcycles  
- Planes  
- Ships  
- Trains  

---

## 데이터셋 정보  
- **출처**: [Kaggle - Vehicle Classification Dataset]
- **총 샘플 수**: 5,007장  
- **입력 이미지 크기**: (64, 64, 3)  
- **출력 라벨 수**: 7개  
- **학습용 데이터**: 4,005장 (80%)  
- **테스트용 데이터**: 1,002장 (20%)

---

## 전처리 과정  
- 이미지 크기 통일: `(64, 64)`로 리사이즈  
- 픽셀 정규화: `0~1` 범위로 변환 (`/255`)  
- 라벨 원-핫 인코딩  
- 학습/테스트 데이터 분할: `train_test_split(test_size=0.2)`

---

## 모델 구조 (CNN)

| Layer            | Details                         |
|------------------|----------------------------------|
| Input            | (64, 64, 3)                      |
| Conv2D           | 32 filters, (3×3), ReLU          |
| MaxPooling2D     | Pool size (2×2)                  |
| Conv2D           | 64 filters, (3×3), ReLU          |
| MaxPooling2D     | Pool size (2×2)                  |
| Dropout          | 0.25                             |
| Flatten          |                                  |
| Dense            | 128 units, ReLU                  |
| Dropout          | 0.5                              |
| Output (Dense)   | 7 units, Softmax                 |

- **손실 함수**: `sparse_categorical_crossentropy`  
- **Epochs**: 30  
- **Batch size**: 32  
- **검증 비율**: 20% (`train_test_split` 활용)

---

## 모델 성능  
- **테스트 정확도**: **96.78%**
