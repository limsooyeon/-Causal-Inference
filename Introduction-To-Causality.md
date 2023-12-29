# 01 - Introduction To Causality

| -   |
|:----|


## Data Science is Not What it Used to Be (or it Finally Is)

> Jim colins - 데이터 과학을 맥주와 거품층으로 비유
> 1. 맥주 : 통계 기초, 과학적 호기심, 복잡한 문제에 대한 열정
> 2. 거품 : 결국 사라질 비현실적인 기대

&Rightarrow; 수학과 통계에 대한 지식은 습득하기 어렵기 때문에 가치 있음.

&nbsp; 포기하지 말고 **the Brave and True**를 위한 퀘스트를 깨보자

## Answering a Different Kind of Question

ML은 예측 종류의 질문 유형에 매우 잘 답함.

그러나, ML은 만병 통치약이 아님

연관을 인과관계로 만드는 방법을 알아내보자

## When Association Is Causation

예) "태블릿을 제공하는 학교가 그렇지 않은 학교보다 더 나은 성과를 보인다"

태블릿을 제공하는 학교가 더 부유할 가능성이 있음

따라서, 태블릿 없이도 평균보다 더 나은 결과를 얻을 수 있음

이 때문에 태블릿을 준다고 학업 성취도가 향상된다고 결론 내릴 수 없으나

태블릿은 높은 학업 성과와 **관련이 있다**고 말할 수 있다



### Notation

- $T_{i}$ : 단위 i의 treatment
  
  - ![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_ixhE0x/스크린샷 2023-12-29 오후 5.28.44.png)

- $Y_{i}$ : treatment가 영향을 미치는 변수

- potention outcomes (잠재적 결과)

    - facual (사실) : 일어난 결과 &rightarrow; $Y_{0i}$ 
    - counterfactual (반사실) : 일어나지 않은 결과 &rightarrow; $Y_{1i}$ 

- 개별 치료 효과 : $Y_{1i} - Y_{0i}$ 

    - 잠재적 결과 중 하나만 관찰할 수 있기 때문에, 개별 치료 효과를 알 수 없음.

- 평균 처리 효과 
  - $ATE = E[Y_{1}-Y{0}]$
- treatment 대상에 대한 평균 treatment 효과 
  - $ATT = E[Y_{1}-Y{0}|T=1]$


예) "태블릿을 제공하는 학교가 그렇지 않은 학교보다 더 나은 성과를 보인다"

&rarr; 

$Y_{1i}$  : 학생 i가 태블릿이 있는 교실에 있을 때의 학업 성취도

$Y_{0i}$  : 학생 i가 태블릿이 없는 교실에 있을 때의 학업 성취도

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_piyzTK/스크린샷 2023-12-29 오후 5.40.45.png)

*(두가지 잠재적 결과를 모두 안다고 가정)*

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_JTUu7C/스크린샷 2023-12-29 오후 5.41.41.png)
![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_bmg7z7/스크린샷 2023-12-29 오후 5.41.55.png)

&Rightarrow; treatment를 받은 학교의 경우, 태블릿이 학업성취도를 평균 75점 감소시켰다는 것을 의미


실제는 아래와 같은 데이터
![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_uiMMPI/스크린샷 2023-12-29 오후 5.43.46.png)

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_900ZI4/스크린샷 2023-12-29 오후 5.44.12.png)

위의 결과와 매우 다름

연관성을 인과관계로 착각한 것

## Bias

Bias는 연관성을 인과관계와 다르게 만드는 것

Counterfactual을 관찰할 수는 없지만 추론할 수는 있음

연관성

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_Soxi7f/스크린샷 2023-12-29 오후 5.47.11.png)

인과관계

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_hzT8Z3/스크린샷 2023-12-29 오후 5.47.54.png)

연관성 &rarr; 인과관계
![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_G6vfbZ/스크린샷 2023-12-29 오후 5.49.15.png)
![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_sH7lSe/스크린샷 2023-12-29 오후 5.49.33.png)
![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_xIwRtu/스크린샷 2023-12-29 오후 5.50.02.png)

&Rightarrow; 연관성은 treatment 대상에 대한 효과에 bias를 더한 것과 같음

bias는 실험군과 대조군이 treatment를 받기 전 얼마나 다른지를 나타냄

만약,

![](../../../../../../../var/folders/cn/v74_4qls5sq2cm503qv8d5mskqcwj8/T/TemporaryItems/NSIRD_screencaptureui_48MPeT/스크린샷 2023-12-29 오후 5.53.44.png)
이면,

연관 = 인과

