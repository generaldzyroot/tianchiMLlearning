# Bayes&Decision Tree

## Naive Bayes

### MAP: Maximum A Posterior

<img src="https://latex.codecogs.com/gif.latex?\omega_{MAP}=arg&space;\underset{\omega_i&space;\in&space;\omega&space;}{max}P(\omega_i|a_1,a_2,...,a_n)" title="\omega_{MAP}=arg \underset{\omega_i \in \omega }{max}P(\omega_i|a_1,a_2,...,a_n)" />

<img src="https://latex.codecogs.com/gif.latex?\omega_{MAP}=arg&space;\underset{\omega_i&space;\in&space;\omega&space;}{max}\frac{P(a_1,a_2,...,a_n|\omega_i)P(\omega_i)}{P(a_1,a_2,...,a_n)}" title="\omega_{MAP}=arg \underset{\omega_i \in \omega }{max}\frac{P(a_1,a_2,...,a_n|\omega_i)P(\omega_i)}{P(a_1,a_2,...,a_n)}" />

<img src="https://latex.codecogs.com/gif.latex?\omega_{MAP}\propto&space;arg&space;\underset{\omega_i&space;\in&space;\omega&space;}{max}P(a_1,a_2,...,a_n|\omega_i)P(\omega_i)" title="\omega_{MAP}\propto arg \underset{\omega_i \in \omega }{max}P(a_1,a_2,...,a_n|\omega_i)P(\omega_i)" />

条件独立

<img src="https://latex.codecogs.com/gif.latex?\omega_{MAP}\propto&space;arg&space;\underset{\omega_i&space;\in&space;\omega&space;}{max})P(\omega_j)\prod_{j}P(a_j|\omega_i)" title="\omega_{MAP}\propto arg \underset{\omega_i \in \omega }{max})P(\omega_j)\prod_{j}P(a_j|\omega_i)" />



### 独立

<img src="https://latex.codecogs.com/gif.latex?P(B|A)=P(B)" title="P(B|A)=P(B)" />

根据贝叶斯公式可得

<img src="https://latex.codecogs.com/gif.latex?\begin{aligned}&space;P(A\cap&space;B)&=P(A)P(B|A)\\&space;&=P(A)P(B)&space;\end{aligned}" title="\begin{aligned} P(A\cap B)&=P(A)P(B|A)\\ &=P(A)P(B) \end{aligned}" />

### 条件独立

<img src="https://latex.codecogs.com/gif.latex?\begin{aligned}&space;P(A|G,B)=P(A|G)&space;\end{aligned}" title="\begin{aligned} P(A|G,B)=P(A|G) \end{aligned}" />

根据贝叶斯公式可得

<img src="https://latex.codecogs.com/gif.latex?\begin{aligned}&space;P(A,B|G)&=\frac{P(A,B,G)}{P(G)}\\&space;&=\frac{P(A|G,B)P(B,G)}{P(G)}\\&space;&=P(A|B,G)P(B|G)\\&space;&=P(A|G)P(B|G)&space;\end{aligned}" title="\begin{aligned} P(A,B|G)&=\frac{P(A,B,G)}{P(G)}\\ &=\frac{P(A|G,B)P(B,G)}{P(G)}\\ &=P(A|B,G)P(B|G)\\ &=P(A|G)P(B|G) \end{aligned}" />

### 独立与不相关的关系

当两组特征的协方差为0时，表示这两组特征不相关、

但不相关是指线性不相关，如y=x^2 很明显，两者并不独立，但是其协方差为0

