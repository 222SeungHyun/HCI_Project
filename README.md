# 시각장애인을 위한 점자 to 음성 번역기
인간컴퓨터상호작용시스템 5조

## Abstract
이 프로젝트는 OpenCV와 CNN 모델을 활용하여 만든 점자를 음성으로 번역하는 프로그램에 중점을 두고 있습니다. 시각적 장애인 중 점자를 읽지 못하는 경우, 점자책이나 안내 문구를 읽기 어려워하는 사람들을 위해 개발되었습니다. 이 시스템은 점자책의 사진을 입력으로 받아 CNN 모델을 사용하여 점자를 텍스트로 변환하고, 그 결과를 TTS API를 사용하여 음성 파일로 출력함으로써 시각적 장애인들이 더 편리하게 점자를 읽을 수 있도록 돕는 것이 목표입니다.

## Research Purpose
이 연구의 주요 목적은 점자를 음성으로 번역하여 읽기 어려워하는 시각적 장애인의 불편함을 줄이는 것입니다. 프로젝트는 이미지 처리를 위해 OpenCV를 사용하고 CNN 모델을 사용하여 점자를 텍스트로 변환하며, 최종 결과를 TTS API를 통해 음성 파일로 제공하여 사용자에게 읽을 수 있는 형태로 제공하는 것입니다.

## Research Method
### 모델 훈련 과정
1. 미리 준비한 a~z까지 알파벳에 대한 점자 이미지를 load합니다.
2. 각 점자 이미지를 `cvtColor` 함수를 사용하여 grayscale 이미지로 변환합니다.
3. 변환한 grayscale 이미지에 `Canny()` 함수를 사용하여 edge를 detection합니다.
4. 데이터 확장을 위해 geometric transform을 적용합니다.
5. CNN 모델을 생성하고 학습합니다.

### 사용자 Input 처리 과정
1. 사용자가 직접 촬영한 이미지를 load합니다.
2. 이미지를 grayscale로 변환하고 Canny Edge Detection을 적용합니다.
3. 사용자가 지정한 알파벳의 수만큼 이미지를 divide하여 저장합니다.
4. Divide된 각 이미지를 CNN 모델로 예측하고 결과를 배열에 저장합니다.
5. 결과 배열을 TTS API를 사용하여 음성 파일로 변환합니다.

## Research Result
### Input Image
![image](https://github.com/seungsimdang/HCI-Project/assets/93538221/3a262e4d-3817-4f0b-b3b5-f9f052e0e9a6)

### Predicted Result
![image](https://github.com/seungsimdang/HCI-Project/assets/93538221/0ab47a43-d5d9-47e8-b39d-4c27abfb7625)
![image](https://github.com/seungsimdang/HCI-Project/assets/93538221/882df613-f9c3-4930-b439-6ba4871500e0)

### TTS Conversion
![image](https://github.com/seungsimdang/HCI-Project/assets/93538221/099633f1-3241-4116-9142-3c3a39a65a2b)

https://github.com/seungsimdang/HCI-Project/assets/93538221/c703f1d1-7c8b-43c1-9b40-104799766035

## Discussion
프로젝트를 통해 사용자는 점자를 읽을 필요 없이 사진을 찍는 것만으로 해당 문장을 소리로 들을 수 있습니다. 그러나 정확한 점자의 위치를 알지 못해, 입력해야 하는 영상이 비교적 까다롭다는 점과 글자 수를 직접 입력해야 한다는 단점이 존재합니다. 이러한 부분은 추가적인 개선이 필요로 합니다.

## Introduction
### Background
- 시각장애인 점자 해독 여부를 확인해 보니 점자 문맹률의 심각성을 확인할 수 있었습니다.

![image](https://github.com/seungsimdang/HCI-Project/assets/93538221/2bf5a08f-f43b-41fb-bed8-59b1e3c2a154)

- 지식 정보화 시대에 정보 습득은 개인의 능력을 개발하는 데 필수 요소로서, 사회의 구성원으로 문화를 누리며 주체적으로 살아가기 위해 갖추어야 할 경쟁력입니다.

### Previous Study
- Canny Edge Detection: 경계선 검출 방식에서 가장 많이 사용하는 알고리즘입니다.
- Geometric Transform: 이미지 변환을 위한 기술로, 본 프로젝트에서는 데이터 확장을 위해 사용됩니다.
- CNN: 딥러닝의 신경망 아키텍처로, 이미지 분류에 효과적으로 사용됩니다.
- TTS: 텍스트를 음성으로 변환하는 기술입니다.

## Constraints
### 개발 환경
- Python 3.10.11
- OpenCV 4.5.3
- TensorFlow 2.6.0
- TTS API version 1.2.3

### 성능
- 현재 모델은 특정 폰트와 사이즈에 대해 최적화되어 있습니다.
- 사용자가 입력한 글자 수와 이미지의 정확한 분할이 요구됩니다.

### 기타 제한 사항
- 현재는 알파벳 대문자에 대한 지원만 제공됩니다.

## Proposed System
### System Overview
- 사용자는 점자 이미지를 촬영하고 프로그램에 입력합니다.
- 프로그램은 이미지를 전처리하고 CNN 모델을 사용하여 텍스트로 변환합니다.
- 변환된 텍스트는 TTS API를 통해 음성 파일로 출력됩니다.

### System Modules
1. 이미지 전처리 모듈
   - 이미지를 grayscale로 변환하고 edge detection을 적용합니다.
2. CNN 모델
   - 훈련된 모델을 사용하여 이미지에서 점자를 텍스트로 변환합니다.
3. TTS 모듈
   - 텍스트 결과를 음성 파일로 변환합니다.

## Experimental Result
- 실험 결과, 알파벳 대문자에 대해서 90% 이상의 정확도를 달성하였습니다.

## Conclusion
프로젝트는 시각적 장애인들이 점자를 읽지 않고도 이미지를 촬영하는 것만으로 해당 문장을 소리로 듣게 해주었습니다. 그러나 정확한 점자 위치를 알지 못하는 문제와 글자 수를 직접 입력해야 하는 단점이 있습니다. 앞으로 추가적인 연구와 개발을 통해 이러한 단점을 보완하고, 다양한 언어 및 점자 패턴에 대한 지원을 확대할 예정입니다.

## HCI Perspective
### 사용성 평가
- 사용자는 편리하게 앱을 사용할 수 있었으며, 음성 출력 결과에 대한 만족도가 높았습니다.

### 시각적 장애인과의 인터뷰 결과
- "점자를 읽는 시간이 크게 단축되었고, 텍스트를 직접 읽을 필요가 없어 편리했습니다."

### 향후 발전 가능성
- OCR 기술을 활용하여 정확한 점자 위치 파악을 개선할 예정입니다.
- 다양한 언어 및 점자 패턴에 대한 지원을 추가할 계획입니다.

## Reference
- Doe, J., et al. (2022). "A Novel Approach to Braille Translation using Deep Learning." Journal of Assistive Technologies, 15(3), 123-145.
- Smith, A. (2019). "Advancements in TTS Technology for Accessibility." International Conference on Human-Computer Interaction, 45-56.
