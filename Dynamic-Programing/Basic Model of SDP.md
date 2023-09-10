### Basic Model of SDP

- Consider a dynamic system which expresses the evolution of some variables, the system's state, under the influence of decisions made at decision epochs.
- Let T denote the set of decision epochs. This subset of the non-negative real numbers may be classified in two ways : as either a discrete set or a continuous and as either a finite and infinite set.
- Let's focus on the discrete and finite set case in the basic model, T = {1,2,.. , N}. (This sequential decision process is called a finite horizon problem.)
- Then, there exists a finite number of stages(or periods), a decision epoch corresponds to the beginning of a stage, and decisions are made at decision epochs
- Let $s_t$ be the state of the system at decision epoch $t$, $s_t \in S$ and $t \in T$, where $S$ is the set of possible states
- Let $a_t$ be the decision (or action) to be selected at a decision epoch t, 
- $S$와 $A_s$는 유한한 집합이다.
- $t$시점에서의 상태 $s_t$에서는 $a_t$라는 액션이 발생하는데, 이것의 결과는 보상 아니면 비용으로 나타나며 $g(s_t, a_t)$로 표현된다.
- 

### Principle of Optimality

