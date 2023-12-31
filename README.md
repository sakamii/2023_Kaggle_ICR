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

## 데이터셋 설명
- 이 대회 데이터는 세 가지 연령 관련 질환과 관련된 50개 이상의 익명화된 건강 특성으로 구성되어 있습니다. 여러분의 목표는 주어진 주제가 이러한 질환 중 하나에 진단된 것인지 여부를 예측하는 것입니다. 이는 이진 분류 문제입니다.

- 이것은 코드 대회(Code Competition)이므로 실제 테스트 세트는 숨겨져 있습니다. 이 버전에서는 올바른 형식의 샘플 데이터를 제공하여 솔루션 작성을 돕습니다. 여러분의 제출이 평가되는 경우, 이 예시 테스트 데이터는 전체 테스트 세트로 대체될 것입니다. 전체 테스트 세트에는 약 400개의 행이 있습니다.

## 파일 및 필드 설명
- train.csv - 훈련 세트
    - Id: 각 관찰에 대한 고유 식별자
    - AB-GL: 56개의 익명화된 건강 특성. EJ를 제외한 모든 특성은 숫자입니다.
    - Class: 이진 목표 변수. 1은 주체가 세 가지 조건 중 하나에 진단된 것을 나타내고, 0은 그렇지 않은 것을 나타냅니다.

- test.csv - 테스트 세트. 여러분의 목표는 이 세트의 주제가 각각의 두 클래스에 속하는 확률을 예측하는 것입니다.
- greeks.csv - 훈련 세트에만 사용 가능한 추가 메타데이터
  - Alpha: 존재하는 연령 관련 조건을 식별합니다.
    - A: 연령 관련 조건 없음. 클래스 0에 해당합니다.
    - B, D, G: 세 가지 연령 관련 조건. 클래스 1에 해당합니다.
  - Beta, Gamma, Delta: 세 가지 실험적 특성.
  - Epsilon: 이 주체의 데이터 수집 날짜입니다. 주의할 점은 테스트 세트의 모든 데이터는 훈련 세트 수집 후에 수집되었다는 것입니다.

- sample_submission.csv - 올바른 형식의 샘플 제출 파일입니다. 자세한 내용은 평가 페이지를 참조하세요.

## 규칙
### 참가자당 한 개의 계정
- 여러 개의 계정으로 Kaggle에 가입할 수 없으며, 따라서 여러 개의 계정으로 제출할 수 없습니다.

### 팀 외부에서의 비공개 공유 금지
- 팀 외부에서 코드나 데이터를 비공개로 공유하는 것은 허용되지 않습니다. 포럼에 모든 참가자가 이용할 수 있도록 코드를 공유하는 것은 괜찮습니다.

### 팀 합병
- 팀 합병은 팀 리더가 수행할 수 있습니다. 합병하기 위해서는 합쳐진 팀의 총 제출 횟수가 "팀 합병 마감일"을 기준으로 최대 허용 횟수 이하이어야 합니다. 최대 허용 횟수는 하루에 제출할 수 있는 횟수에 대회가 진행된 일수를 곱한 값입니다.

### 팀 제한
- 팀의 최대 인원은 5명입니다.

### 제출 횟수 제한
- 하루에 최대 1개의 엔트리를 제출할 수 있습니다.

- 심사를 위해 최대 2개의 최종 제출물을 선택할 수 있습니다.

### 대회 일정
- 대회 일정(참가 신청 마감일, 최종 제출 마감일, 시작일, 팀 합병 마감일 등)은 대회 개요 > 일정 페이지에서 확인할 수 있습니다.

### 대회별 약관
#### **대회 제목**: ICR - 연령 관련 조건 식별

#### **대회 주최**: Invitro Cell Research

#### **대회 주최자 주소**: 106 Grand Avenue, Englewood, NJ 07631

#### **대회 웹사이트**: https://www.kaggle.com/competitions/icr-identify-age-related-conditions

**총 상금: 60,000달러**

- 1등 상금: 18,000달러

- 2등 상금: 15,000달러

- 3등 상금: 10,000달러

- 4등 상금: 7,000달러

- 5등 상금: 5,000달러

- 6등 상금: 5,000달러

#### **우승자 라이선스 유형**: 비독점적

#### **데이터 접근 및 사용**: 사용자 정의 - 대회 전용

- 대회는 미국 및 세계의 거주자를 대상으로 하며, 다만 크림반, 도네츠크인민공화국(DNR), 루한스크인민공화국(LNR), 쿠바, 이란, 시리아, 북한 거주자 또는 미국의 수출 통제나 제재를 받는 사람은 참가할 수 없습니다. 기타 지역별 규정이 적용될 수 있으므로, 자신이 기술 기반 대회에 참여할 자격이 있는지 확인하기 위해 현지 법률을 확인하시기 바랍니다. 대회 주최자는 현지 법률을 준수하기 위해 필요한 경우 대체 상금을 수여할 권리를 보유합니다.

- 이 대회는 데이터 과학 분야를 홍보하고 발전시키기 위한 기술 기반 대회입니다. 참가를 위해서는 대회 웹사이트를 통해 등록해야 합니다. 대회 제출물("서브미션")은 대회 웹사이트에 명시된 요구사항을 준수해야 합니다. 서브미션은 대회 웹사이트에 설명된 평가 메트릭에 따라 점수가 매겨집니다. 대회 규칙을 준수하는 한, 최고 점수를 받은 참가자에게 상금이 수여될 것입니다. 자세한 대회 규칙은 아래를 참조하세요.

A. 대회별 규칙
- 아래의 일반 대회 규칙에 추가하여, 대회 주최자가 요구하는 이 대회별 규칙을 이해하고 동의합니다:

#### 외부 데이터
- 다음 조항은 아래의 일반 규칙 섹션 7.C.를 대체합니다: "대회 웹사이트에서 명시적으로 다르게 언급되지 않는 한, 당신은 Competition Data 이외의 데이터를 모델 및 서브미션을 개발하고 테스트하는 데 사용할 수 없습니다. 대회 주최자는 Competition Data 이외의 데이터 사용이나 Competition Data를 대회 웹사이트와 이 규칙에서 허용된 방식 이외로 사용하는 것을 발견한 참가자를 언제든지 제외할 권리를 보유합니다."

1. 우승자 라이선스
  - 아래의 일반 규칙 섹션 11 (우승자 의무)에 따라, 대회 우승자인 경우, 다음과 같은 라이선스를 대회 주최자에게 부여하고 부여할 것입니다:
  - 비독점적: 당신은 대회 주최자 및 대회 주최자의 지정자에게 전세계적으로 비독점적인 하위라이선스 가능한, 이전 가능한, 완전히 지급된, 무료로 사용할 수 있는, 영구적인, 돌이킬 수 없는 권리를 부여하고 부여할 것입니다. 이 권리에는 상금을 받은 서브미션 및 해당 서브미션을 생성하기 위해 사용된 소스 코드를 사용, 복제, 배포, 파생물 작성, 공개적으로 실행, 공개적으로 표시, 디지털적으로 실행, 제작, 판매, 판매 제안 및 수입할 수 있는 권리가 포함됩니다. 상금 수여를 위해 일반적으로 상업적으로 이용 가능한 소유하지 않은 소프트웨어를 사용하여 서브미션을 생성했지만 대회 주최자가 부담할 수 있는 비용으로 구입할 수 있는 경우, 이전 문장의 라이선스는 해당 소프트웨어에 대해 적용되지 않습니다.

2. 자동화된 기계 학습 도구 (AMLT)
- 개별 참가자와 팀은 자동화된 기계 학습 도구("AMLT") (예: Google AutoML, H2O Driverless AI 등)를 사용하여 서브미션을 생성할 수 있습니다. 다만, 참가자 또는 팀은 AMLT에 대한 적절한 라이선스를 보유하여 대회 규칙을 준수할 수 있어야 합니다.
- 다음 조항은 아래의 일반 대회 규칙 섹션 11의 끝에 추가됩니다: "AMLT를 사용하여 서브미션을 생성한 개별 참가자 및 팀은 상금을 받을 수 있습니다. 그러나 명확하게 말하자면, 잠재적인 우승자의 서브미션은 여전히 이 규칙, 특히 A.1 (우승자 라이선스), B.11 (우승자 의무), B.17 (보증, 면책 및 해제) 섹션의 요구 사항을 충족해야 합니다."


B. 일반 대회 규칙

1. 구속력 있는 동의
- 대회에 참가하기 위해서는 대회 웹사이트의 조항과 내용을 참조하는 공식 대회 규칙("규칙")에 동의해야 합니다. 이 규칙은 대회 웹사이트와 상기 대회별 규칙을 통합하여 구성됩니다. 참가 전에 이 규칙을 주의 깊게 읽어 이해하고 동의해야 합니다. 또한, 대회에 응모하는 것은 이 규칙에 동의하는 것으로 간주됩니다. 이 규칙에 동의하지 않는 경우, 대회에 응모할 수 없으며, 이 대회와 관련된 상금("상금")을 받을 자격이 없습니다. 이 규칙은 대회와 관련하여 참가자와 대회 주최자 간의 구속력 있는 법적 계약을 형성합니다.

2. 자격 요건
- A. 대회에 응모하기 위해서는 다음의 자격 요건을 충족해야 합니다:
  - (i) Kaggle.com의 등록된 계정 소지자여야 합니다.
  - (ii) 만 18세 이상 또는 거주 지역의 법정 성년기(대회 주최자와 합의하지 않은 한 부모/보호자의 동의를 받았어야 함) 이상이어야 합니다.
  - (iii) 크림 반도, 소위 도네츠크인사람공화국 (DNR), 루한스크인사람공화국 (LNR), 쿠바, 이란, 시리아 또는 북한의 거주자가 아니어야 합니다.
  - (iv) 미국의 수출 통제 또는 제재 조치의 대상인 개인 또는 단체의 대리인이 아니어야 합니다. (https://www.treasury.gov/resource-center/sanctions/Programs/Pages/Programs.aspx 참조)

- 회사, 교육기관 또는 기타 법적 개체의 대표자로서 참가하는 경우, 이 규칙은 개별적으로 당신과 당신이 대표하거나 소속된 개체에 구속력이 있습니다. 당신이 다른 당사자의 직원, 계약자, 또는 대리인으로서 직무 범위 내에서 행동하는 경우, 그러한 당사자가 당신의 행동에 대해 충분히 인식하고 동의했으며, 상금을 포함한 가능한 수상에 동의했음을 보증합니다. 또한, 당신의 행동이 당신의 고용주 또는 개체의 정책과 절차를 위반하지 않음을 보증합니다.

- 대회 주최자는 자격을 확인하고 언제든지 분쟁에 대해 중재할 권리를 보유합니다. 대회와 관련하여 참가자의 신원, 거주지, 우편 주소, 전화번호, 이메일 주소, 권리 소유 또는 대회 참가에 필요한 정보와 관련하여 거짓 정보를 제공한 경우, 참가자는 즉시 대회에서 제외될 수 있습니다.

- B. 상기 대회별 규칙 또는 대회 엔티티의 내부 정책이 허용하지 않는 한, 대회 엔티티의 직원, 인턴, 계약자, 임원 및 이사는 대회에 참가할 수 있지만 상금을 받을 자격이 없습니다. "대회 엔티티"는 대회 주최자, Kaggle Inc., 그리고 그들의 관련 법인, 자회사 및 계열사를 의미합니다. 대회 엔티티의 참가자인 경우, 참가자는 자신의 참가에 대한 적용 가능한 내부 정책에 따라 구속됩니다.

3. 주최자 및 호스팅 플랫폼
- 해당 대회는 상기 주최자에 의해 후원되며, Kaggle Inc.("Kaggle")가 대회 주최자를 대표하여 호스팅합니다. Kaggle은 대회 주최자의 독립적인 계약사로, 여러분과 대회 주최자 간의 어떠한 협정에 대해서도 관련이 없습니다. Kaggle이 잠재적인 대회 수상자를 선정하거나 상금을 수여하는 것과 관련하여 어떠한 책임도 지지 않음을 이해하셔야 합니다. Kaggle은 대회 호스팅에 관련된 일부 행정 기능을 수행할 것이며, 여러분은 이 규칙에 따라 Kaggle에 관련된 조항을 준수할 것에 동의합니다. Kaggle.com 계정 소지자이자 Kaggle 대회 플랫폼의 사용자로서, 여러분은 이 규칙에 추가로 Kaggle 이용 약관(www.kaggle.com/terms)에 동의하고 그에 따르는 것을 기억하셔야 합니다.

4. 대회 기간
- 상금을 위한 목적으로, 대회는 시작일과 시간부터 최종 제출 마감일까지 실행됩니다(이 기간을 "대회 기간"이라고 합니다). 대회 일정은 변경될 수 있으며, 대회 주최자는 대회 기간 동안 추가적인 중간 마감일을 도입할 수 있습니다. 업데이트된 또는 추가된 마감일은 대회 웹사이트에서 공지될 것입니다. 마감일 변경에 대한 최신 정보를 확인하기 위해 정기적으로 대회 웹사이트를 확인하는 것은 여러분의 책임입니다. 여러분은 자신의 위치에서 해당하는 시간대를 결정하는 데 책임이 있습니다.

5. 대회 응모
- 응모 또는 당첨을 위해 어떠한 구매도 필요하지 않습니다. 대회에 응모하기 위해서는 응모 마감일 이전에 대회 웹사이트에 등록하고, 대회 웹사이트를 통해 응모 및 제출하는 지침을 따라야 합니다. 여러분의 제출물은 대회 웹사이트에서 명시된 방식과 형식에 따라 제출되어야 하며, 모든 기타 요구사항을 준수해야 합니다("요구사항"). 제출물은 대회 웹사이트에서 명시된 제출 마감일 이전에 접수되어야 합니다. 명시된 마감일에 접수되지 않은 제출물은 상금 수여 대상이 될 수 없습니다.

- 제출물은 검증 데이터셋 또는 테스트 데이터 레코드의 수작업 레이블링 또는 인간 예측 정보를 사용하거나 포함해서는 안 됩니다.

- 대회가 시간적으로 분리된 훈련 및/또는 테스트 데이터를 사용하는 다단계 대회인 경우, 각 대회 단계에서 요구되는 한 개 이상의 유효한 제출물이 대회 웹사이트에서 설명된 방식으로 제출되어야 상금 수여 대상이 됩니다.

- 제출물이 전체 또는 일부가 알아보기 어렵거나 불완전하거나 손상되었거나 변조되었거나 위조되었거나 사기로 획득된 경우에는 무효입니다. 대회 주최자는 제출 요건을 충족하지 않는 제출물을 제출하는 참가자를 제외시키기 위해 이 규칙을 준수하지 않는 참가자를 제명할 권리를 보유합니다.

6. 개인 및 팀
- A. 개인 계정: 여러분은 오직 하나의 고유한 Kaggle.com 계정으로만 제출물을 제출할 수 있습니다. 여러분이 여러 Kaggle 계정을 통해 제출물을 제출하거나 여러분을 대리할 가짜 계정을 위조하려 시도하는 경우에는 제명될 수 있습니다. 대회 웹사이트에서 명시된 대회당 최대 제출 횟수까지 하루에 제출물을 제출할 수 있습니다.
- B. 팀: 대회 웹사이트 가이드라인에 따라 여러 개인이 팀으로 협업할 수 있습니다("팀"). 그러나 여러분은 하나의 팀에만 가입하거나 형성할 수 있습니다. 각 팀 구성원은 개별적인 Kaggle 계정을 가진 개인이어야 합니다. 팀에 가입하기 전에 개별적으로 대회에 등록해야 합니다. 공식적인 팀 가입을 위해 Kaggle 계정으로 전송된 팀 알림 메시지에 응답하여 팀 구성원임을 확인해야 합니다. 팀 구성원은 대회 웹사이트에 명시된 최대 팀 규모를 초과해서는 안 됩니다.
- C. 팀 통합: 팀은 대회 웹사이트를 통해 팀 통합을 요청할 수 있습니다. 팀 통합은 다음 조건을 충족하는 경우 허용될 수 있습니다: (i) 통합된 팀이 최대 팀 규모를 초과하지 않아야 합니다. (ii) 통합된 팀이 통합 요청일의 팀당 허용 제출 횟수를 초과하지 않아야 합니다. (iii) 통합이 어떠한 통합 마감일이나 대회 마감일보다 이전에 완료되어야 합니다. (iv) 제안된 통합된 팀이 이 규칙의 모든 요구사항을 충족해야 합니다.

7. 대회 데이터
- "대회 데이터"는 대회 참가를 위해 대회 웹사이트에서 제공되는 데이터 또는 데이터 세트를 의미하며, 대회 웹사이트에서 제공되는 프로토타입이나 실행 가능한 코드를 포함합니다. 대회 데이터에는 비공개 및 공개 테스트 세트가 포함됩니다. 어떤 데이터가 어떤 세트에 속하는지는 참가자에게 제공되지 않을 것입니다.
  A. 데이터 접근 및 사용
    - 대회 사용 전용: 대회 데이터에는 대회 참가 및 Kaggle.com 포럼에서만 사용할 수 있습니다. 대회 주최자는 대회 웹사이트와 이 규칙에서 허용된 방식 이외로 대회 데이터를 사용하는 참가자를 탈락시킬 권리를 보유합니다.

  B. 데이터 보안
    - 귀하는 대회 데이터에 공식적으로 동의하지 않은 사람들이 액세스하지 못하도록 합리적이고 적절한 조치를 취하여야 합니다. 대회 데이터를 대회에 참가하지 않은 어떤 당사자에게 전송, 복제, 게시, 재배포하거나 제공하거나 이용할 수 없습니다. 대회 데이터의 무단 전송 또는 무단 액세스가 가능한 사실을 알게 된 경우 즉시 Kaggle에 통보하고 무단 전송 또는 액세스를 해결하기 위해 Kaggle과 협력하는 것에 동의합니다.

  C. 외부 데이터
    - (구체적인 대회 규칙의 "외부 데이터"를 참조하십시오.) 대회 데이터 이외의 데이터("외부 데이터")를 사용하여 제출물을 개발하고 테스트할 수 있습니다. 그러나 외부 데이터는 모든 대회 참가자가 대회 목적을 위해 동일하게 사용할 수 있도록 공개적으로 이용 가능하며 다른 참가자에게 비용을 청구하지 않아야 합니다. 이 섹션 7.C(외부 데이터)에 따른 외부 데이터의 사용은 11조(수상자 의무)를 포함하여 대회 규칙의 다른 의무를 제한하지 않습니다.

8. 제출 코드 요구 사항
  A. 개인 코드 공유
    - 대회 기간 동안 대회 데이터나 대회와 관련된 다른 소스 코드나 실행 가능한 코드("대회 코드")를 개인적으로 공유하는 것은 허용되지 않습니다(대회 웹사이트나 대회 특정 규칙에서 특별히 허용되는 경우 제외). 팀 간에 대회 코드를 공유하는 것도 허용되지 않으며, 팀 병합이 발생하는 경우에만 가능합니다. 이러한 대회 코드의 공유는 이 대회 규칙의 위반으로 간주되며, 탈락의 결과를 가져올 수 있습니다.
  B. 공개 코드 공유
    - 지적 재산권을 침해하지 않는 한 대회 코드를 공개적으로 공유할 수 있습니다. 대회 코드나 그와 관련된 코드를 공개적으로 공유하기로 선택하는 경우, 모든 참가자의 이익을 위해 Kaggle.com의 토론 포럼이나 대회와 직접 관련된 노트북에 해당 코드를 공유해야 합니다. 이러한 공유에 의해, 공유된 코드는 상업적 이용을 제한하지 않는 Open Source Initiative 승인 라이선스(www.opensource.org 참조)에 따라 라이선스가 부여된 것으로 간주됩니다. 이러한 대회 코드나 대회 코드에 따라 생성되거나 의존하는 모델에 대한 상업적 이용을 제한하지 않는 Open Source Initiative 승인 라이선스(www.opensource.org 참조)에 따라 라이선스가 부여된 공개 소스 코드만 사용해야 합니다.

  C. 오픈 소스 사용
    - 구체적인 대회 규칙에서 별도로 명시되지 않는 한, 제출물을 생성하는 데 모델에서 오픈 소스 코드를 사용하는 경우, 상업적 이용을 제한하지 않는 Open Source Initiative 승인 라이선스(www.opensource.org 참조)에 따라 라이선스가 부여된 오픈 소스 코드만 사용해야 합니다.

9. 수상자 선정
- 각 제출물은 대회 웹사이트에 명시된 평가 지표에 따라 점수화되고 순위가 매겨집니다. 대회 기간 동안 현재 순위는 대회 웹사이트의 공개 리더보드에서 확인할 수 있습니다. 잠재적인 수상자는 이 규칙을 준수하는 한 대회의 비공개 리더보드 순위에 의해 결정됩니다. 공개 리더보드는 공개 테스트 세트를 기반으로 하며, 비공개 리더보드는 비공개 테스트 세트를 기반으로 합니다.
- 동점인 경우, 대회에 처음으로 제출된 제출물이 우승자가 됩니다. 잠재적인 수상자가 어떤 이유로 탈락된 경우, 다음으로 높은 점수를 받은 제출물이 잠재적인 수상자로 선택됩니다.

10. 수상자 발표 및 탈락
- 잠재적인 수상자는 이메일로 통지됩니다.
- 잠재적인 수상자가 (i) 첫 번째 통지 시도로부터 1주일 이내에 회신하지 않거나 (ii) 최종 제출 마감일 후 1주일 이내에 Kaggle에게 잠재적인 수상자로 지명받기를 원하지 않거나 상장을 받고 싶지 않다고 통지하는 경우, 각각 (i)와 (ii) 경우 해당 잠재적인 수상자는 어떤 상장도 받지 못하며, 대회 심사 기준에 따라 모든 유효한 응모 기록을 기준으로 대체 잠재적인 수상자가 선정됩니다.

- (i)와 (ii)의 경우, Kaggle은 참가자를 탈락시킬 수 있습니다. 그러나 (ii)의 경우, Kaggle의 요청에 따라 잠재적인 수상자는 이 규칙을 준수하는 것을 검증하기 위해 코드와 문서를 제공할 수 있습니다. 잠재적인 수상자가 Kaggle의 만족을 얻는 코드와 문서를 제공한 경우, 해당 참가자는 이 항목에 따라 탈락되지 않습니다.

- 대회 주최자는 참가자가 부정한 방법으로 대회의 합법적인 운영을 저해하려고 시도하거나, 사기, 기만 또는 불공정한 경기 행위 또는 학대로 다른 참가자, 대회 주최자 또는 Kaggle을 위협하거나 괴롭히는 경우에는 언제든지 해당 참가자를 대회에서 탈락시킬 수 있습니다.

- 탈락된 참가자는 Kaggle의 재량에 따라 대회 리더보드에서 제거될 수 있습니다. 대회 리더보드에서 참가자가 제거되는 경우 Kaggle 대회 플랫폼과 관련된 추가적인 수상 기능(예: Kaggle 포인트 또는 메달)도 수여되지 않을 수 있습니다.

- 최종 리더보드 목록은 Kaggle.com에서 공개적으로 표시됩니다. 대회 주최자의 결정은 최종적이며 구속력이 있습니다.

11. 수상자 의무
- 상금을 받기 위한 조건으로, 수상자는 다음과 같은 의무를 이행해야 합니다:

  - (a) 수상 작품을 생성하는 데 사용된 최종 모델의 소프트웨어 코드와 관련 문서를 경쟁 주최자에게 제공해야 합니다. 제공되는 소프트웨어 코드는 문서화 지침을 따라야 하며, 수상 작품을 생성할 수 있어야 하며, 소프트웨어 실행 코드를 성공적으로 빌드하거나 실행하기 위해 필요한 자원에 대한 설명을 포함해야 합니다. 최종 모델의 소프트웨어 코드가 귀하가 소유하지 않은 상용 소프트웨어를 포함하고 있으며 경쟁 주최자가 부담 없이 입수할 수 있는 경우, 해당 소프트웨어의 코드 대신 해당 소프트웨어와 입수 방법, 수상 작품을 복제하는 데 필요한 매개 변수 또는 기타 정보를 식별해야 합니다.

  - (b) 경쟁 주최자에게 경쟁 별 규칙에 명시된 대로 수상 작품에 대한 라이선스를 부여하고, 이를 부여할 권리가 제한되지 않았음을 보증해야 합니다.

  - (c) Competition Sponsor 또는 Kaggle이 요구하는 Prize 수락 문서를 서명하고 반환해야 합니다. 이에는 (i) 자격 인증서, (ii) 규칙에 따른 라이선스, 해제 및 기타 협정, 그리고 (iii) 미국 세무 양식(예: 미국 거주자의 경우 IRS 양식 W-9, 외국 거주자의 경우 IRS 양식 W-8BEN 또는 이후의 동등한 양식)이 포함될 수 있습니다.

12. 상금
- 상금은 Competition 웹사이트에서 설명된 대로 제공되며, Competition 웹사이트에서 설명된 시간 동안 수상에 대해서만 사용할 수 있습니다. 어떤 상금을 받을 확률은 경쟁 기간 동안 받은 자격을 갖춘 제출의 수와 참가자의 기술에 따라 달라집니다.
- 모든 상금은 경쟁 주최자가 참가자의 자격과 이 규칙을 준수하며, 수상 작품이 제출 요구 사항을 준수하는지 검토 및 확인한 후에 지급됩니다. 제출이 이 대회 규칙을 준수하지 않는 사실이 밝혀진 경우, 경쟁 주최자는 재량에 따라 다음 중 하나의 조치를 취할 수 있습니다: (i) 제출을 탈락시키거나 (ii) 잠재적인 수상자에게 제출에서 식별된 모든 문제를 통보한 후 1주일 이내에 이를 해결하도록 요구합니다(라이선스 충돌 해결, 소프트웨어 라이선스에 필요한 모든 의무 이행, 소프트웨어 제한 사항을 위반하는 소프트웨어 제거 등).

- 잠재적인 수상자는 10조에 따라 수상자로 지명되는 것을 거절할 수 있습니다.

- 잠재적인 수상자는 요구되는 모든 상금 수락 문서를 통보 받은 후 2주 이내에 반환해야 하며, 그렇지 않을 경우 잠재적인 수상자는 상금을 포기한 것으로 간주되고 다른 잠재적인 수상자가 선정됩니다. 상금은 경쟁 주최자나 Kaggle이 필요한 상금 수락 문서를 받은 후 약 30일 이내에 수여됩니다. 상금의 양도나 양도는 허용되지 않습니다.

- 2조의 자격 요건을 충족하지 않는 경우 어떠한 상금도 받을 자격이 없습니다.

- 팀이 금전적인 상금을 수상한 경우, 해당 상금은 자격을 갖춘 팀 구성원 간에 균등하게 분배됩니다. 다른 상금 분배를 원하는 경우 팀이 일치하여 상금 분배를 선택하고 Kaggle에 통보해야 합니다.

13. 세금
- 상금에 부과되는 모든 세금은 수상자의 책임입니다. 잠재적인 수상자에 대한 지급은 관련 주, 연방, 지방 및 외국(도지사 국제) 세금 신고 및 원천 징수 요구 사항을 준수하기 위해 경쟁 주최자 또는 Kaggle이 요청한 모든 문서를 제출하는 것이 요구됩니다. 상금은 경쟁 주최자가 법적으로 원천 징수할 의무가 있는 세금을 제외한 금액으로 지급됩니다. 잠재적인 수상자가 요구되는 문서를 제공하지 않거나 관련 법률을 준수하지 않는 경우, 상금이 포기될 수 있고 경쟁 주최자는 대체 잠재적인 수상자를 선정할 수 있습니다. 미국 거주자인 수상자는 상금 금액에 해당하는 IRS 양식-1099를 받게 됩니다.

14. 일반 조건
- 모든 연방, 주, 지방 및 지역의 법령과 규정을 준수해야 합니다.

15. 홍보
- 법률에 금지되지 않는 한, 경쟁 주최자, Kaggle 및 해당 계열사는 귀하의 이름과 유사성을 추가 보상 없이 광고 및 홍보 목적으로 사용할 수 있다는 데 동의합니다.

16. 개인 정보
- 대회 주최자와 Kaggle은 대회 계정 등록 절차 및 대회 중에 참가자가 제공한 개인 식별 정보(이름, 우편 주소, 전화 번호, 이메일 주소 등)를 수집, 저장, 공유 및 기타 사용할 수 있습니다. Kaggle은 이러한 개인 식별 정보의 수집, 저장, 공유 및 기타 사용에 관해 독립적인 컨트롤러 역할을 하며, 개인 식별 정보를 Kaggle의 개인 정보 보호 정책(www.kaggle.com/privacy)에 따라 사용할 것입니다. Kaggle.com 계정 소지자로서, 계정에 로그인하거나 Kaggle 지원팀(www.kaggle.com/contact)에 문의하여 Kaggle이 보유한 개인 데이터에 대한 액세스, 검토, 수정, 이전 또는 삭제 요청을 할 수 있는 권리가 있습니다.
- 대회 주최자는 참가자와 대회 주최자 간의 이 계약을 이행하기 위해, Kaggle은 참가자의 개인 식별 정보를 대회 주최자에게 전달할 것입니다. 대회 주최자는 이러한 개인 식별 정보에 대해 독립적인 컨트롤러 역할을 하며, 해당 개인 식별 정보에 관련된 모든 미국 및 외국의 데이터 보호 의무를 준수하기로 동의합니다. Kaggle은 대회 주최자 주소에 명시된 국가로 참가자의 개인 식별 정보를 전송할 것이며, 해당 국가는 참가자의 거주 국가와 다를 수 있습니다. 해당 국가는 참가자의 거주 국가와 유사한 개인 정보 보호 법과 규정을 갖지 않을 수 있습니다.

17. 보증, 면책 및 해제
- 참가자는 제출물이 자신의 독자적인 창작물임을 보증합니다. 따라서 제출물의 독점적인 소유자이자 권리 보유자이며, 제출물을 제출하고 필요한 라이선스를 부여할 권리가 있다는 것을 보증합니다. 참가자는 다음과 같은 어떤 제출물도 하지 않기로 동의합니다: (i) 제삼자의 소유권, 지적 재산권, 산업 재산권, 개인 또는 도덕적 권리 또는 저작권, 상표권, 특허권, 영업 비밀, 개인 정보, 공개 또는 비밀 유지 의무 등을 포함한 어떠한 권리도 침해하지 않는다는 것, 혹은 (ii) 해당 규정, 미국 및 외국의 주·연방 법률 등을 포함한 모든 적용 가능한 법률을 위반하지 않는다는 것입니다.
- 법률이 허용하는 최대한도로, 참가자는 본 규칙에 명시된 보증 위반, 행위, 기본 사항, 혹은 본 보증 조항 위반으로 인한 책임, 청구, 요구, 손해, 비용 및 비용을 언제든지 대회 주체로부터 면책시키고 면책시키기로 동의합니다. 법률이 허용하는 최대한도로, 참가자는 다음과 같은 사항으로부터 대회 주체를 방어하고 면책하며, 이에 대한 모든 청구, 행동, 소송, 형사 처벌, 그리고 모든 손실, 책임, 손해, 비용 및 비용(합리적인 변호사 비용 포함)을 포함한 모든 요구 사항에 대해 대회 주체를 보호할 것입니다: (a) 제삼자의 소유권, 지적 재산권, 산업 재산권, 개인 또는 도덕적 권리 또는 저작권, 상표권, 특허권, 영업 비밀, 개인 정보, 공개 또는 비밀 유지 의무 등을 침해하는 참가자의 제출물 또는 제출한 다른 자료, (b) 대회와 관련하여 참가자가 제공한 어떠한 부정한 표현도, (c) 참가자의 이 규칙, 적용 가능한 미국 또는 외국의 주·연방 법률을 위반하는 어떠한 비준수도, (d) 대회와 관련하여 참가자 이외의 당사자가 제기한 청구 사항, (e) 상장의 수령, 소지, 남용 또는 사용, 대회 및 대회와 관련된 활동에 참여함으로써 발생하는 어떠한 청구 사항도 포함합니다.

- 참가자는 대회 주체로부터 다음과 관련된 어떠한 책임도 면제합니다: (a) 대회 웹사이트의 고장 또는 기타 문제, (b) 제출물의 수집, 처리 또는 보유에 관한 오류, (c) 상금이나 우승자에 대한 인쇄, 제공 또는 발표에 대한 오타나 기타 오류.

18. 인터넷
- 대회 주체는 시스템 오류, 실패한 컴퓨터 또는 기타 통신 전송 장치의 오작동, 하드웨어나 소프트웨어의 오류 등으로 인해 대회 웹사이트의 동작이 방해를 받거나 늦어지거나, 손상되거나, 잘못된, 완전하지 않거나, 읽을 수 없거나, 배달할 수 없거나, 파괴된 제출물이나 참가자의 신청 자료, 시스템 또는 인간의 오류와 실패, 전화망 또는 회선, 케이블 연결, 위성 전송, 서버나 공급자의 기술적인 오작동, 인터넷이나 대회 웹사이트의 트래픽 혼잡 등으로 인해 참가자의 참여 능력이 제한될 수 있는 경우에 대해서는 책임을 지지 않습니다.

19. 취소, 수정 또는 탈락의 권리
- 대회가 컴퓨터 바이러스, 버그, 조작, 무단 개입, 부정 행위, 기술적인 결함 또는 대회의 진행, 안전, 공정, 성실성, 적법한 진행에 영향을 주는 기타 모든 원인으로 인해 계획된 대로 진행되지 못하는 경우, 대회 주최자는 대회를 취소, 종료, 수정 또는 중단할 권리를 보유합니다. 대회 주최자는 제출 절차나 대회의 기타 부분을 고의로 방해하는 참가자를 탈락시킬 권리도 보유합니다. 참가자가 대회 웹사이트를 포함한 웹사이트를 고의로 훼손하거나 대회의 적법한 운영을 저해하는 경우, 이는 형법과 민법을 위반하는 행위입니다. 이러한 시도가 있을 경우, 대회 주최자와 Kaggle 모두 해당 참가자에 대해 관련 법률의 모든 범위 내에서 손해배상을 청구할 권리를 보유합니다.

20. 고용 제안이나 계약의 내용이 아님
- 제출물, 상금 수여, 이 규칙의 어떠한 조항도 참가자와 대회 주체 사이에 고용 관계, 공동 경영 관계, 계약, 대리인 또는 대리인 관계를 형성하거나 해당 사항에 관한 암시를 구성하지 않습니다. 참가자는 대회 주최자와 Kaggle에 대한 임무, 신뢰, 비밀유지 의무, 상호 고용 의무, 계약 의무, 대리인 의무, 프리랜서 의무, 대리인 관계, 공동 경영 관계가 없음을 명시적으로 인정합니다.

21. 적용 가능한 법률
- 이 계약은 미국 캘리포니아주의 법률에 따라 규정되며, 미국 연방 법원이 배타적인 관할권을 갖습니다. 이 계약은 모든 참가자에 대해 적용되며, 미국 또는 외국의 어떠한 지역에서도 실행될 수 있습니다.