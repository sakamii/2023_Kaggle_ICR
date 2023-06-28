# 2023_Kaggle_ICR
- [ICR - Identifying Age-Related Conditions](https://www.kaggle.com/competitions/icr-identify-age-related-conditions)

## 목표
- 목표는 사람이 세 가지 의료 상태 중 어떤 것에 해당하는지를 예측하는 것입니다. 특정 사람이 세 가지 의료 상태 중 하나 이상을 가지고 있는지(Class 1), 아니면 세 가지 의료 상태 중 어떤 것도 가지고 있지 않은지(Class 0)를 예측하는 모델을 만드는 것입니다. 건강 특성의 측정 데이터를 사용하여 모델을 훈련시면 됩니다.

- 이러한 의료 상태를 가지고 있는지를 확인하기 위해서는 환자로부터 정보를 수집하는 데 오랜 시간과 침입적인 절차가 필요합니다. 예측 모델을 사용하면 이 프로세스를 단축시킬 수 있으며, 이러한 상태와 관련된 핵심 특성을 수집한 다음 이러한 특성을 인코딩하여 환자의 세부 정보를 보호할 수 있습니다.

- 작업을 통해서 특정 특성의 측정값과 잠재적인 환자 상태 간의 관계를 연구자들이 발견하는 데 도움을 주게 될 것입니다.

## 내용
- 나이는 단지 숫자일 뿐이라고 말하지만, 노화와 함께 다양한 건강 문제가 발생합니다. 심장 질환과 치매부터 청력 상실과 관절염까지, 노화는 다양한 질병과 합병증의 위험 요소입니다. 생물 정보학이라는 성장하는 분야에는 생물학적 노화를 늦추고 뒤집을 수 있는 개입 방법과 주요한 노화 관련 질병을 예방하는 연구가 포함됩니다. 데이터 과학은 적은 샘플 수일지라도 다양한 데이터로 문제를 해결하는 새로운 방법을 개발하는 데 기여할 수 있습니다.

- 현재 XGBoost와 랜덤 포레스트와 같은 모델들이 의료 상태를 예측하는 데 사용되고 있지만, 이러한 모델의 성능은 충분하지 않습니다. 생명이 걸린 중대한 문제를 다룰 때, 모델은 다른 경우에도 신뢰성 있고 일관되게 올바른 예측을 해야 합니다.

- 2015년에 설립된 대회 주최기관인 [InVitro Cell Research, LLC (ICR)](https://invitrocellresearch.com/)은 재생과 예방 개인 맞춤형 의학에 초점을 맞춘 민간 자금 기반의 회사입니다. 뉴욕시 권역에 위치한 그들의 사무실과 연구실은 최첨단 연구 공간을 제공합니다. InVitro Cell Research의 과학자들은 그들을 독특하게 만드는 요소로, 노화하는 인간을 빠르게 치료하는 방법에 대한 연구를 안내하고 정의하는 데 도움을 줍니다.

- 이 대회에서는 건강 특성 데이터의 측정값을 사용하여 생물 정보학에서 중대한 문제를 해결하는 데 참여하게 될 것입니다. 최소한의 훈련 데이터를 기반으로 사람이 세 가지 의료 상태 중 하나 이상을 가지고 있는지를 예측하는 모델을 만들어 기존 방법을 개선하는 것이 목표입니다.

- 여러분은 생물 정보학의 성장하는 분야를 발전시키고 다양한 데이터로 복잡한 문제를 해결하기 위한 새로운 방법을 탐색하는 데 도움이 될 수 있습니다.

## 평가
- 제출물은 균형 잡힌 로그 손실(balanced logarithmic loss)을 사용하여 평가됩니다. 이를 통해 각 클래스가 최종 점수에 대해 거의 동일한 중요성을 갖게 됩니다.

- 각 관측값은 클래스 0 또는 클래스 1 중 하나입니다. 각 관측값에 대해 각 클래스에 대한 확률을 제출해야 합니다. 그런 다음 다음 공식을 사용합니다.

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mtext>Log Loss</mtext>
  <mo>=</mo>
  <mfrac>
    <mrow>
      <mo>&#x2212;<!-- − --></mo>
      <mfrac>
        <mn>1</mn>
        <msub>
          <mi>N</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
      </mfrac>
      <munderover>
        <mo>&#x2211;<!-- ∑ --></mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi>i</mi>
          <mo>=</mo>
          <mn>1</mn>
        </mrow>
        <mrow class="MJX-TeXAtom-ORD">
          <msub>
            <mi>N</mi>
            <mrow class="MJX-TeXAtom-ORD">
              <mn>0</mn>
            </mrow>
          </msub>
        </mrow>
      </munderover>
      <msub>
        <mi>y</mi>
        <mrow class="MJX-TeXAtom-ORD">
          <mn>0</mn>
          <mi>i</mi>
        </mrow>
      </msub>
      <mi>log</mi>
      <mo>&#x2061;<!-- ⁡ --></mo>
      <msub>
        <mi>p</mi>
        <mrow class="MJX-TeXAtom-ORD">
          <mn>0</mn>
          <mi>i</mi>
        </mrow>
      </msub>
      <mo>&#x2212;<!-- − --></mo>
      <mfrac>
        <mn>1</mn>
        <msub>
          <mi>N</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
      </mfrac>
      <munderover>
        <mo>&#x2211;<!-- ∑ --></mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi>i</mi>
          <mo>=</mo>
          <mn>1</mn>
        </mrow>
        <mrow class="MJX-TeXAtom-ORD">
          <msub>
            <mi>N</mi>
            <mrow class="MJX-TeXAtom-ORD">
              <mn>1</mn>
            </mrow>
          </msub>
        </mrow>
      </munderover>
      <msub>
        <mi>y</mi>
        <mrow class="MJX-TeXAtom-ORD">
          <mn>1</mn>
          <mi>i</mi>
        </mrow>
      </msub>
      <mi>log</mi>
      <mo>&#x2061;<!-- ⁡ --></mo>
      <msub>
        <mi>p</mi>
        <mrow class="MJX-TeXAtom-ORD">
          <mn>1</mn>
          <mi>i</mi>
        </mrow>
      </msub>
    </mrow>
    <mn>2</mn>
  </mfrac>
</math>


- 여기서 (N_{c})는 클래스 (c)의 관측값 수입니다. (\log)는 자연 로그를 나타내며, (y_{c i})는 관측값 (i)가 클래스 (c)에 속하는 경우에는 1이고 그렇지 않은 경우에는 0입니다. (p_{c i})는 관측값 (i)가 클래스 (c)에 속할 확률입니다.

- 주어진 행에 대한 제출된 확률은 합이 1이 될 필요는 없습니다. 왜냐하면 점수를 매기기 전에 재조정되기 때문입니다(각 행은 행 합으로 나누어집니다). 로그 함수의 극단을 피하기 위해 각 예측 확률은 다음과 같이 바뀝니다.
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mo movablelimits="true" form="prefix">max</mo>
  <mo stretchy="false">(</mo>
  <mo movablelimits="true" form="prefix">min</mo>
  <mo stretchy="false">(</mo>
  <mi>p</mi>
  <mo>,</mo>
  <mn>1</mn>
  <mo>&#x2212;<!-- − --></mo>
  <msup>
    <mn>10</mn>
    <mrow class="MJX-TeXAtom-ORD">
      <mo>&#x2212;<!-- − --></mo>
      <mn>15</mn>
    </mrow>
  </msup>
  <mo stretchy="false">)</mo>
  <mo>,</mo>
  <msup>
    <mn>10</mn>
    <mrow class="MJX-TeXAtom-ORD">
      <mo>&#x2212;<!-- − --></mo>
      <mn>15</mn>
    </mrow>
  </msup>
  <mo stretchy="false">)</mo>
</math>

### 제출 파일
- 테스트 세트의 각 id에 대해, 두 개의 클래스에 대한 확률을 예측해야 합니다. 파일은 헤더를 포함하고 다음과 같은 형식을 가져야 합니다.
```
Id,class_0,class_1
00eed32682bb,0.5,0.5
010ebe33f668,0.5,0.5
02fa521e1838,0.5,0.5
040e15f562a2,0.5,0.5
046e85c7cc7f,0.5,0.5
...
```

## 타임라인
2023년 5월 11일 - 시작일.

2023년 8월 3일 - 참가 신청 마감일. 대회에 참가하기 위해서는 이 날짜 이전에 대회 규칙을 수락해야 합니다.

2023년 8월 3일 - 팀 합병 마감일. 이는 참가자가 팀에 가입하거나 팀을 합병할 수 있는 마지막 날입니다.

2023년 8월 10일 - 최종 제출 마감일.

모든 마감 시간은 해당 날짜의 11:59 PM UTC를 기준으로 하며, 별도로 명시되지 않는 한 대회 주최자는 필요에 따라 대회 일정을 업데이트할 권한을 보유합니다.

## 코드 요구사항
이 대회에는 노트북을 통해 제출해야 합니다. 커밋 후 "제출" 버튼을 활성화하기 위해 다음 조건을 충족해야 합니다:

- CPU 노트북의 실행 시간은 9시간 이하여야 합니다.
- GPU 노트북의 실행 시간은 9시간 이하여야 합니다.
- 인터넷 접근이 비활성화되어야 합니다.
- 제출 파일의 이름은 submission.csv여야 합니다.

더 자세한 제출 방법에 대해서는 코드 대회 FAQ를 참조하시기 바랍니다. 그리고 제출 오류가 발생하는 경우 코드 디버깅 문서를 확인해주세요.