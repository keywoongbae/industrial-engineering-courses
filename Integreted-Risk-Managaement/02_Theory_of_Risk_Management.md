## 02. Theory of Risk Management

### Definition of Risk management

- 리스크 관리의 정의
  - 조직이 직면한 손실 노출을 식별하고, 이러한 노출을 처리하는데 가장 적합한 기술을 선택하는 과정
- Loss exposure as a practical proxy for risk
  - 손실이 발생하는지 여부에 관계없이 손실이 발생할 수 있는 모든 상황 또는 상황.
- 왜 리스크관리가 어려운가?
  - Lack of data, risk dynamics (changing environment)
  - Asset prices following rather unstable processes
  - Very large numbers of risk factors are present
  - 리스크에 영향을 주는 모든 변수를 한번에 모델링하기가 어렵다.

### Risk Management Process

1. **Determine the objectives**
   
   - 손실 이전의 목적인지 손실 이후의 목적인지를 확인한다.
     - 손실 이전의 목적(Pre-loss objectives)
       - Prepare for potential losses in the most economical way
       - Reduce anxiety
       - Meet any legal obligations(bisel)
     - 손실 이후의 목적(Post-loss objectives)
       - Survival of the firm
       - Continue operating (business continuity)
       - Stability of earnings
       - Continued growth of the firm
       - Minimize the effects that a loss will have on other persons and on society
   - 가치를 극대화한다.
     - 리스크 관리의 궁극적인 목적은 사업에서 다른 기능의 궁극적인 목적들과 같다.
     - 이는 리스크관리의 목적이 조직의 가치를 극대화하는 것이라는 뜻이다.
   
2. **Risk identification**
   - Key of risk identification
     - major하거나 minor한 모든 손실 지출들을 확인한다.
     - undetected risk를 고려하고 관리한다.
   - Method of Risk Identification
     - Risk Identification techniques : 서류 분석, flowchart, communication system, monitoring systsem
     - Risk Identification tools : 리스크 분석 설문지, 지출 체크리스트, 보험 정책 체크리스트, 전문가, 과거 손실 데이터

3. **Risk evaluation / analysis**

   - 리스크를 관리하는데는 3가지 정량적 평가방법이 있다.

     - Case 1 : Risk in a narrow sense as a risk of claim occurrence
       - Risk evaluation relies on the complete probability distribution
       - Risk valuation is possible
     - Case 2 : Risk in a narrow sense as downside risk
       - Relative to a reference point
       - Risk evaluation covers only a portion of the outcome distribution
       - Risk valuation is only partially possible
     - Case 3 : Risk in a broader sense
       - Risk evaluation relies on the complete probability distribution
       - Risk valuation is possible
     - <img src=".\img\image-20230914165350783.png" alt="image-20230914165350783" style="zoom: 67%;" />

   - **[1] Risk measures : Risk in a broader sense**

     - 분산 측정 (Measures of dispersion)
       - (1) 분산/표준편차
         - $\text{Var}(X) = \sigma^2(X) = E[(X-E(X))^2] = E(X^2)-E(X)^2$
       - (2) 변동계수 구하기
         - Risk-Reward Ratio : $\sigma(X) / E(X)$

     - 실제 위험률이 증가할 수 있는 상황에 대한 추가 측정 방법 (Supplementary measures of "hazard")
       - (1) 분포의 치우침 (왜도, Skewness)
         - $\gamma = E[(\frac{X-E(X)}{\sigma(X)})^3]$
       - (2) 분포의 몰림 정도 (첨도, Kurtosis)
         - <img src=".\img\The-difference-between-skewness-and-kurtosis.webp" alt="What Is Kurtosis? | Definition, Examples & Formula" style="zoom: 50%;" />
         - 정규분포의 첨도는 3이며, 3보다 큰 경우(랩토컬틱)를 *Excess Kurtosis*라고 함.

   - **[2] Risk measures : Risk in a narrower sense (downside risk)**

     - 분산 측정 (Measures of dispersion)
       - (1) 준분산 (Semi-variance)
         - $\text{SemiVar}(X) = E[\max(E(X) - X, 0)^2]$
         - 위험한 지역에 대한 변동성을 계산하는데 도움이 됨.
     - 위험 상황에 대한 측정 (Measures of hazard)
       - (1) Lower Partial Moments (LPM)
         - 수익률 데이터에서 상승분을 제외하고 하락분만 사용하여 위험도를 측정하는 방법
         - $\text{LPM}_k(X) = E[\max(Y-X,0)^k] = \int_{-\infin}^{Y} (Y-X)^k dF_X$
         - LPM에는 특수 케이스가 2가지가 있다. 
           - Special Case I : Ruin(default) probability, Insolvency ($k=0, Y=0$)
             - $k=0, Y=0$ 일 때,
               $  \text{LPM}_0 = \int_{-\infin}^{0}{dFX} = P(X<0), \ X = A-L$ (A : Asset, L : Liabilities)
               $\text{LPM}_0 = P(A-L<0) \rightarrow$ Default Probability, Ruin Probability (Insolvency)  
           - Special Case II : Partial expected value ($k=1, Y=0$)
             - $k=1, Y=0$ 일 때,
               $  \text{LPM}_1 (X) = E[\max(0-X, 0)^1] = E[X | X<0]$
               $\int_{-\infin}^{0}{xf(x)dx}$ ($x$ : 손실의 심각도 (양), $f(x)$ : 손실의 빈도수)

   - **[3] Risk measures : Value-at-Risk and Tail-Value-at-Risk**

     - Value-at-Risk (VaR)

       - 정상시장에서 예상보유기간동안 주어진 신뢰수준에서 발생할 수 있는 최대손실금액으로 정의된다.
       - 향후 t일 동안 x원 이상 손해 보지 않을 c%의 신뢰 수준에서 확신한다면 x원이 VaR이다.
       - $\text{VaR}(X) = -F^{-1}(\alpha) = -\text{inf}\{x | F(x)\geq \alpha \}, \forall \alpha \in [0,1]$

     - Tail-Value-at-Risk (TVarR) or Expected Shortfall (ES)

       - $\text{TVaR}_{\alpha}(X) = -E(X|X \leq \text{VaR}_{\alpha})$
       - TVaR은 $\text{LPM}_1 / \text{LPM}_0$과 같다. (조건부 기대값)
       - $\frac{LPM_1(X)}{LPM_0(X)} = E[(Y-X | X \leq Y)] = E[(-X |X \leq 0)]$

     - 좋은 리스크 관리 방법은 ? $\rightarrow$ coherent, robust해야 한다.

       - 견고한 리스크 방법의 조건 (Axioms of a coherent risk measure)
         - Monotonicity : if $X \leq Y \sim \rho(X) \leq \rho (Y)$
         - Sub-addictivity : $\rho(X+Y) \leq \rho(X) + \rho(Y)$
         - Positive to Homogeneuity : $\rho(\lambda x) = \lambda \rho(x), \ \forall x \geq 0$
         - Translation invariance : $\alpha \in \R \sim \rho(x+\alpha) = \rho(x)-\alpha$
       - T-VaR은 4가지 조건이 전부 해당되지만, VaR은 Sub-addictivity가 해당되지 않음.
       - 그럼에도 VaR을 많이 쓰는 이유는 TVaR은 꼬리 쪽의 분포에 따라서 값이 엄청 커질 수 있음.

     - Example

       - A firm is evaluating a project with potential payoff $X \sim \mathcal{N}(10,10^2)$. How much equity capital (EC) is needed to achieve one period default probability of 1% ($=\alpha$)

         > <img src=".\img\image-20230914175553538.png" alt="image-20230914175553538" style="zoom:50%;" />
     
   - **Steps to evaluate risks**
   
     - (1) 심도에 기반해서 우선순위 매기기 : Criticality analysis
       - Critical risk / Important risk / Unimportant risk
     - (2) 가능성과 우선순위 매기기
       - d
   
4. Risk management in a narrow sense.

   - Risk financing measures



Case that successfully managed risks

- Engineering & Construction industry cases.
  - (1) d



## The rationale of a firm's risk-taking

### Interest rates over time

### First-mover : Tesla

### The Risk-Return Trade-off (1/2)

There is a reward for bearing risk

### The Risk-Return Trade-off (2/2)

The greater the potential reward, the greater the risk.



## How can we measure a firm's return associated with its risk?

### Portfolio expected returns



### Portfolio variance



### Variance-covariance approach



### Mean-Variance model



### Efficient frontier



## The Measure of Risk-based Return

### Firm's return associated with its risk.

risk에 대한 기대 : 체계적위험에 의한 리스크

보상을 어떻게 measure할 것인가?

체계적 위험을 어떻게 measure할 것인가?

beta라는 척도를 사용 (체계적 위험을 다루고 있는 지표.)

$ \underset{\text{for asset } i}{\beta_i} = \frac{\sigma_{r_i, r_m}}{\sigma_{\sigma_{r_m}}^2}$

$r_i$ : asset i return, $r_m$ : return on the market(S&P 500, DAX, KOSPI)

$\beta_m = \frac{\sigma_{r_m, r_m}}{\sigma^2_{r_m}} = \frac{\sigma^2_{r_m}}{\sigma^2_{r_m}}=1$

$\beta <1 : \sigma_{r_i, r_m} < \sigma^2_{r_m}$

마켓에서의 리스크가 내 것보다 리스크보다 크다.

내가 좀더 안전한 자산에 투자를 하고 있음을 의미.

$\beta >1 : \sigma_{r_i, r_m} > \sigma^2_{r_m}$

내 자산의 움직임이 시장의 움직임보다 크다.

내가 좀더 위험한 자산에 투자를 하고 있음을 의미.



### Reward-to-risk ratio

마켓에서의 ratio : $\frac{E(R_m)-R_f}{\beta_m}=E(R_m)-R_f$(Market Risk Premium) 

<경제학에서의 시장균형>

B라는 자산의 비율이 8일 때, 

B의 수요 증가. 

B의 값 하락

A와 B가 균형을 맞춤.



### CAPM

$\frac{E(R_i)-R_f}{\beta_i} = E(R_m)-R_f$

in the market quilibrium.



우리가 알고자하는것 : $E(R_i)$

$E(R_i) = R_f + \beta_i(E(R_m)-R_f)$

자산의 체계적 위험으로 자산의 기대수익을 계산하는 것.

- 화폐의 시간가치 ($R_f$에 담고 있음.)
- 체계적 위험을 감수함으로써 발생하는 보상 ($E(R_m)-R_f$)
- 체계적 위험의 사이즈 ($\beta_i$)



### RM and value creation

- RM을 잘하면 회사의 가치가 높아진다. -> flexibility in capital financing

- 위험을 반영해서 결정하면 기본적으로 회사의 가치가 증가하게 됨.