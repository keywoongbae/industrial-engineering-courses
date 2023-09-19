## 2. Matrix decompositions

### 스팩트럼 분해 (Spectral Decomposition)

THEOREM

- $A \in \R^{n \times n }$을 따르는 대각 행렬 A에 대해서, 대각행렬 D($D = diag(d_1, d_2, .., d_n)$)와 직교행렬 V($VV^T = I, V^TV = I_n$)가 있다면 $A = VDV^T$와 같이 표현될 수 있다. 

스팩트럼 분해는 행렬 A를 eigenvalue로 표현되는 조각들로 분해하는 것이다. 

스팩트럼 분해는 아래를 가정한다.

- $d_i \in \R$인 $d_i$값들은 행렬 A의 고유값들이다.
- $V = \begin{bmatrix} v_1, v_2, ..., v_n \end{bmatrix}$라고 하면, $v_i$는 $d_i$와 연관된 고유벡터이다.
- $A = VDV^T=\Sigma^{n}_{i=1} d_i v_i v_i^T$

### 특이값 분해 (Singular value decomposition)

- 특이값 분해는 스펙트럼 분해의 일반화된 형태이며, 모든 행렬에 대해 적용이 가능하다.
- 어떤 실수 행렬 $X (m \times n, m \geq n)$도 아래와 같은 꼴로 분해가 가능하다.
  - $ A = UDV^T$

**THEOREM**

- $n \geq p$인 ​행렬 $A$에 대해서, $n \times p$인 행렬 $U$와 $p \times p$인 행렬 $D$와 $V$로 다음과 같은 분해가 가능하다.
  - $A = UDV^T$
    - $U$는 
  - $D = diag(d_1, ..., d_p), d_j \geq 0$ 
  - $U^T U = V^T V = I_p$
- 아래 내용도 추가로 알아둘 것.
  - $\mathcal{C}(U) = \mathcal{C}(A)$, 그리고 $\mathcal{C}(V)=\mathcal{R}(A)$
  - $d_j$는 A의 특이값이라고 불린다.
  - $u_j$는 A의 left singular vector라고 한다.
  - $v_j$는 A의 right singular vector라고 한다.
  - $A^TA = VD^2V^T$

**주성분 분석**

- **주성분 분석**은 흔히 쓰이는 차원 축소 방법이며, 여러 데이터들이 모여 하나의 분포를 이룰 때 이 분포의 주성분을 분석해주는 방법이다. 
- ![img](.\img\img.gif)
- **주성분**은 그 방향으로 데이터들의 분산이 가장 큰 방향벡터를 의미한다. **데이터셋에서 분산이 최대인 축을 찾는 과정**을 말한다.
- ![img](.\img\232FCB42527C51481B)
- 위의 그림을 보면, e1 방향일 때 데이터들의 분산, 즉 흩어진 정도가 제일 크다. 그리고 e1에 수직이면서 그 다음으로 데이터들의 분산이 가장 큰 방향은 e2이다.
- 주성분 분석은 다음과 같이 이루어진다고 할 수 있다.
  - $\alpha \in \R^p $ 인 $\alpha$에 대해서, $x_i$가 $X$의 $i$번째 열이라고 하면, $\hat{Var}(X \alpha) = \frac{1}{n} \Sigma^{n}_{i=1} (x^T_i \alpha)^2$이라고 하자.
  - 주성분 분석을 통해 아래 식을 해결하고자 한다.
    - $\hat{\alpha} = \underset{\vert \vert \alpha \vert \vert _2 \leq1}{argmax} \{\hat{Var}(X \alpha)\} = \underset{\vert \vert \alpha \vert \vert _2 \leq 1}{argmax} \{\alpha ^T \frac{X^TX}{n} \alpha\}$
  - $X = UDV^T$가 $X$의 SVD라고 하자.
  - 

- 

### Low rank approximation

- $A = UDV^T$의 특이값 분해를 생각해본다.
  - $A = \begin{bmatrix} u_1, ... ,u_p\end{bmatrix} \begin{bmatrix} d_1, ...,... \\...,...,... \\...,...,d_p\end{bmatrix} \begin{bmatrix} v_1^T \\ ... \\ v^T_p\end{bmatrix} = d_1u_1v_1^T + ...,d_pu_pv^T_p$, $(d_1 \geq d_2 \geq .. \geq d_p)$
  - 이때 만약 $D_k = diag(d_1, ...,d_k ,0,...,0)$이라고 하면, A는 $A_k = UD_kV^T$로 근사될 수 있다.
  -  $A_k = \begin{bmatrix} u_1, ... ,u_k\end{bmatrix} \begin{bmatrix} d_1, ...,... \\...,...,... \\...,...,d_k\end{bmatrix} \begin{bmatrix} v_1^T \\ ... \\ v^T_k\end{bmatrix} = d_1u_1v_1^T + ...,d_ku_kv^T_k$
- 이때 프로베니우스 놈의 근사 오차는 다음과 같이 표현된다.
  - $||A - A_F||^2_F = tr((A-A_k)^T(A-A_k)) = d^2_{k+1} + .. +d^2_{p}$
  - 위의 식은 아래와 같이 표현될 수 있다.
  - $A_k = \underset{M : rank(M) = k}{\text{argmin}}||A-M||_F$

### 특이값 분해 계산 (Computation of SVD)

- SVD에는 다양한 알고리즘이 존재함.

- rank가 1인 SVD에 대해서, 아래 식을 최소화하는 반복적인 방법을 소개한다.
  
  - **Rank가 1이다?** : 행렬의 일차독립인 행 또는 열의 최대 개수가 1이다. 행렬의 피봇의 개수가 1이다. 행렬의 열벡터들에 의해 생성된 벡터공간의 차원이다.
    - 
  - $f(x,y,s) = \vert \vert A - s\text{x}\text{y}^T\vert\vert ^2 _F$
  - $\text{x} \in \R^m, \text{y} \in \R^n, \vert\vert \text{x} \vert \vert _2= \vert\vert \text{y} \vert \vert _2 =1, s > 0$
  
- 이러한 문제를 bi-convex 문제라고 한다.

### **ACS(Alternate Convex Search) 알고리즘**

- ACS 알고리즘은 다음과 같이 진행된다.
  1. 먼저 $y^0$를 $\vert \vert y^0 \vert \vert _2 = 1$로 설정하여 초기화한다.
  2. $\text{x}^t = \frac{A\text{y}^{t-1}}{\vert \vert A \text{y}^{t-1} \vert \vert _2}$로, $y^t = \frac{A^T \text{x}^t}{\vert \vert A^T \text{x}^t \vert \vert _2}$, 그리고 $s = \vert \vert A^T \text{x}^t \vert \vert _2$로 업데이트 한다.
- A의 left singular vector는 $AA^T$를 고유값분해해서 얻어진 직교행렬의 열백터이며, right singular vector는 $A^TA$를 고유값분해해서 얻어진 직교행렬의 열벡터를 말한다.
- ACS알고리즘은 가장 큰 고유벡터를 찾는 것과 관련이 있다.
  - $y^{t+1} = \frac{A^TAy^t}{\vert \vert A^TA y^t \vert \vert _2}$

### Matrix Norms

- Matrix norm은 어떤 벡터를 길이나 사이즈 같은 양적 수치로 맵핑하기 위한 함수이다.

**DEFINITION** 

- Matrix norm은 요소 벡터들이 행렬인 벡터 공간의 벡터 노름이다.
- Matrix norm은 모든 A와 B에 대해서 $\vert\vert AB \vert \vert \leq \vert \vert A \vert \vert \ \vert \vert B \vert \vert$을 성립하면 하위 곱셈이다.

**EXAMPLE**

- $l^p$놈에 대해서, $1\leq p\leq \infin$하고 $\text{A} \in \R^{m \times n}$인 경우에 다음과 같은 식을 만족한다.
  - $\vert \vert \text{A}\vert \vert _p = \underset{\text{x} \neq 0}{\text{sup}} \{\frac{\vert \vert \text{Ax} \vert \vert _p }{\vert \vert \text{x} \vert \vert _p} \}$

**THEOREM**

- $l^p$ operator norm은 $\R^{m \times n}$공간에서 sub-multiplicative하다.
- $||\text{ABx}||_p \leq ||\text{A}||_p ||\text{Bx}||_p \leq ||\text{A}||_p ||\text{B}||_p ||\text{x}||_p$

**Special cases**

- $||\text{A}||_1 = \underset{1 \leq j \leq n}{\text{max}} \Sigma^{m}_{i=1} |a_{ij}|$ 
- $||A||_{\infin} = \underset{1 \leq i \leq m}{\text{max}} \Sigma^{n}_{j=1} |a_{ij}|$ 
- $||\text{A}||_2 $는 A 중 가장 큰 특이값이다.

프로베니우스 놈

- 만약 $\sigma_i(A)$가 A의 i번째로 가장 큰 특이값이라면  $||\text{A}||_F = \sqrt{\Sigma^m_{i=1} \Sigma^n_{j=1} a_{ij}^2} = \sqrt{\text{tr}(A^TA)} = \sqrt{\Sigma^{m \wedge n }_{i=1} \sigma^2_{i}(
  A)}$ 로 표현될 수 있다.
- 프로베니우스 놈은 sub-multiplicative하다.
  - $A = UDV^T, A^TA = VD^2V^T$
  - $\text{tr}(A^TA) = \text{tr}(VD^2V^T) = \text{tr}(D^2)$

### Nuclear Norms

DEFINITIONS

- A의 nuclear norm은 A의 모든 특이값들의 합이며, $||A||_*$로 표현된다.

### Nonnegative definite matrices

- A가 대칭행렬이라면 $\Sigma_i d_j v_j v_j^T$로 표기할 수 있다.

- $d_j$가 non-negative하다면, $\text{x}^T A \text{x} = \Sigma_j d_j |\text{x}^T v_j|^2 \geq 0$

**THEOREM**

- $\R^{n \times n}$에 속하는 대칭행렬 A가 있을 때, A가 non-negative라면 아래 조건들을 만족한다.
  - $A \geq 0$이라고 표기하며, $\R^n$에 속하는 모든 $\text{x}$ 에 대해서 $\text{x}^T A \text{x} \geq$ 를 만족한다.
  - A의 모든 고유값들은 non-negative이다.
  - 어떤 B에 대해서 $A = B^TB$
    - $\text{x}^T A \text{x} = \text{x}^T B^T B \text{x} \geq 0$
  - A는 random vector의 공분산 행렬이다.
    - $\text{Var}(X) = A$라고 하면, $\text{Var}(\text{y}^T \text{x}) = \text{y}^T \text{Var}(\text{x}) \text{y}$ (상수는 제곱되어 나오므로.)

### Positive definite matrices



### Square root of a matrix

**EXAMPLE**

- 대칭이고 non-negative한 행렬 $\Sigma$가 있을 때, 어떻게 하면 $\Sigma ^{1/2}$를 찾을 수 있을까?
  - $\Sigma = VDV^T$
  - $\Sigma ^{1/2} = V D^{1/2}V^T$
  - $\Sigma^{1/2} \Sigma^{1/2} = VDV^T = \Sigma$
  - $D= \begin{bmatrix} d_1, ...,... \\...,...,... \\...,...,d_p\end{bmatrix}, D^{1/2} = \begin{bmatrix} \sqrt{d_1}, ...,... \\...,...,... \\...,...,\sqrt{d_p} \end{bmatrix}$
- 다변량 정규분포 $\mathcal{N}(0, \Sigma)$로부터 샘플을 어떻게 생성할 수 있을까?
  - $z = (z_1, z_2, .., z_n)^T \sim \mathcal{N}(0, I_n)$
  - $z_i \sim \mathcal{N}(0,1)$
  - $\text{Var}(\Sigma^{1/2} z) = \Sigma^{1/2} I \ \Sigma^{1/2} \Sigma$라 할 수 있으므로 $\Sigma^{1/2} z \sim \mathcal{N}(0, \Sigma)$

### Convex quadratic function

**DEFINITION**

- $\R^n$에 속하는 모든 x,y에 대해서 $0 \leq \lambda \leq 1$이라고 할 때, 아래 조건을 만족하면 함수 f는 볼록하다.
  - $f(\lambda x + (1-\lambda)y) \leq \lambda f(x) + (1-\lambda)f(y)$

**THEOREM**

- 



<img src="./img\image-20230913205544249.png" alt="image-20230913205544249" style="zoom:50%;" />

### Log determinant function



### MLE for the normal variance model

- $x_1, .., x_n \sim \mathcal{N}(0, \Theta ^{-1})$이라 가정.
- 음의 로그우도함수는 다음과 같음.
  - $\log{\Theta} = -\log{\text{det}(\Theta)} + \text{tr}(S \Theta) + \text{const}, S = n^{-1}\Sigma{x_i x_i^T}$
    - $P_{\Theta}(\text{x}) = (2 \pi)^{-p/2} |\Sigma|^{-1/2} \text{exp}(-\frac{1}{2}\text{x}^T \Sigma^{-1} \text{x})$
    - $\log{P_{\Theta}(\text{x})} = \text{const} + \frac{n}{2}\log{\text{det}(\Theta)} - \frac{n}{2}\frac{\Sigma x_i^T \theta x_i}{n}$
      $= \text{const} + \frac{n}{2}\log{\text{det}(\Theta)} - \frac{n}{2}\text{tr}(S \Theta)$ 
  - $S$는 

