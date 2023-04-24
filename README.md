# 로그데이터를 활용한 VIP 고객 세그먼트 예측
![Goog_GA_4_Hero_56a6d78e8a](https://user-images.githubusercontent.com/15994105/233963912-ddf41e58-7827-4ff1-8c23-857c26b64e46.png)

## TOC
- [로그데이터를 활용한 VIP 고객 세그먼트 예측](#로그데이터를-활용한-vip-고객-세그먼트-예측)
- [프로젝트 개요](프로젝트-개요)
  * [A. 데이터 소개](#a-데이터-소개)
  * [B. 목표 설정](b-목표-설정)
  * [C. 문제 정의 및 해결](#c-문제-정의-및-해결)
    + [AS-IS](#as-is)
    + [TO-BE](#to-be)
    + [WRAP UP](#wrap-up)
  * [D. 결과](#d-결과)
- [Deck of Project](#deck-of-project)
- [Methods Used](#methods-used)
- [Contributing Members](#contributing-members)
- [Reference](#reference)

## 프로젝트 개요
### A. 데이터 소개
본 프로젝트는 캐글 컴피티션 'Google Analytics Customer Revenue Prediction' 데이터셋을 활용하였습니다.\
해당 컴피티션의 최종 목표는 각 고객의 로그변환된 매출을 예측하는 것입니다. 이커머스 데이터는 매출의 편차로 인한 데이터셋의 불균형이 존재합니다. 이는 정확한 매출 예측을 방해하므로, 주최 측에서 로그 변환된 매출을 요구하였습니다.\
하지만, 저희는 부정확한 매출값 예측보다 매출 기여도가 높은 고객 세그먼트를 정확히 예측하는 것이 비즈니스에 더 큰 가치를 준다고 판단했습니다. 따라서, 해당 컴피티션의 데이터셋을 활용하되, 비즈니스적으로 더 활용도가 높은 새로운 목표를 설정하였습니다.

### B. 목표 설정
본 프로젝트는 다음과 같은 문제를 해결하고자 합니다.
'GStore의 마케팅팀에서 타겟 프로모션을 준비중인 상황. 고객의 GA로그 데이터로 매출 기여도가 높은 VIP 타겟을 예측하여 전달하라.'

### C. 문제 정의 및 해결
<img width="1200" alt="process" src="https://user-images.githubusercontent.com/15994105/233964581-7f65dabe-cb97-466a-b6df-43e49b5babcc.png">

데이터셋의 99%가 미구매자인 점, 구매자의 매출 기여도 편차가 큰 점이 예측을 어렵게 만들었습니다. 하나의 모델로는 목표를 달성하기 어렵다고 판단했고, 문제를 단계별로 정의하여 해결하고자 했습니다.

#### AS-IS
1. 1%만이 구매자인 데이터의 불균형을 극복해야 합니다.
2. 구매자간 매출 기여도의 편차가 큰 불균형을 극복해야 합니다.
3. 매출 기여도가 높을 타겟을 정의하고 전달해야 합니다.
#### TO-BE
1. VIP는 미구매자일 수 없기 때문에, 분류 모델을 통해 99%의 미구매자를 제거합니다.
2. 로그스케일링을 통해 불균형을 완화하고 회귀 모델을 통해 구매자의 가치를 예측합니다.
3. RFM 분석기법을 통해 파레토 법칙에 의거한 80%의 매출을 발생시킬 20%의 세그먼트를 도출합니다.
#### WRAP UP
- 99%의 0값을 분류하고, 1%의 예상 수익을 도출한 뒤, RFM 분석기법을 통해 수익의 80%를 견인하는 소수의 고객 세그먼트를 예측 

### D. 결과
<img width="1200" alt="vips" src="https://user-images.githubusercontent.com/15994105/233964218-dcc47a8e-ea25-4404-91eb-545c64707940.png">

결과적으로 Test 데이터의 고객 296,530명 중 1.2%인 약 3,769명의 VIP를 탐지할 수 있었습니다.\
이 VIP 세그먼트는 Test 데이터의 매출 81%를 기여합니다. \
따라서 GoogleAnalytics의 로그 데이터만으로 파레토법칙에 의거한 VIP 세그먼트를 예측한다는 목표를 달성했습니다.

## Deck of Project
프로젝트를 정리한 PPT 자료입니다.\
[Classify VIP segements with Ecommerce Log Data](https://drive.google.com/file/d/1lSFeUWyrIV9VeYH-AckUFrC4Baqo0RbD/view?usp=sharing)

## Methods Used
- 머신러닝
	- LightGBM LGBMclassifier
	- sklearn RandomForestregressor
- 세그먼트 도출
	- RFM Customer Relationship Management Method
- 시각화
	- plotly
	- matplotlib
	- seaborn
- 데이터 전처리
	- pandas
	- numpy
- 개발 환경
	- Colab
	- Python 3.9

## Contributing Members
| Name   | github |
| ------ | ------ |
| 김수진 |  [githubsujin · GitHub](https://github.com/githubsujin)      |
| 나인성 |    [InSung-Na · GitHub](https://github.com/inSung-Na)    |
| 남영   | [skadudd · GitHub](https://github.com/skadudd)       |
| 황승주 |   [peracer · GitHub](https://github.com/peracer)     |

## Reference
- 주영혁; 한상만. 수익성 있는 고객의 웹사이트 방문행동특성에 관한 연구: 수익모델간 비교를 중심으로. 마케팅연구, 2001, 16.2: 69-91.
- 김동석, et al. RFM 모형의 가중치 선택에 관한 연구. 2021. PhD Thesis. 제주대학교 대학원.
- 김규곤, et al. 고객 세분화를 위한 최적 RFM 모형 구축에 관한 연구. Journal of the Korean Data Analysis Society, 2004, 6.6: 1829-1840.
- 이영진, et al. CRFM 모형을 이용한 고객세분화와 모형평가. Journal of The Korean Data Analysis Society, 2010, 12.6: 3283-3293.
