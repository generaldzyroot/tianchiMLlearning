# PCA

- 内积与投影
  <img src="https://latex.codecogs.com/gif.latex?A\cdot&space;B=|A||B|cos&space;\alpha" title="A\cdot B=|A||B|cos \alpha" />

  若|A|=1，那么A与B的内积=B向A所在直线投影的矢量长度

- 基

  <img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3,2&space;\end{bmatrix}" title="\begin{bmatrix} 3,2 \end{bmatrix}" />本身并不能精确的表示一个向量，实际上向量<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x,y&space;\end{bmatrix}" title="\begin{bmatrix} x,y \end{bmatrix}" />表示线性组合<img src="https://latex.codecogs.com/gif.latex?x\begin{bmatrix}&space;1,0&space;\end{bmatrix}^T" title="x\begin{bmatrix} 1,0 \end{bmatrix}^T" />+<img src="https://latex.codecogs.com/gif.latex?y\begin{bmatrix}&space;0,1&space;\end{bmatrix}^T" title="y\begin{bmatrix} 0,1 \end{bmatrix}^T" />.其中基表示<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;1,0&space;\end{bmatrix}" title="\begin{bmatrix} 1,0 \end{bmatrix}" />，<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;0,1&space;\end{bmatrix}" title="\begin{bmatrix} 0,1 \end{bmatrix}" />如果我们要换成新基<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;1,1&space;\end{bmatrix}" title="\begin{bmatrix} 1,1 \end{bmatrix}" />,<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;-1,1&space;\end{bmatrix}" title="\begin{bmatrix} -1,1 \end{bmatrix}" />.首先，我们希望新基的模是1，这样就方便我们直接点乘得到其在新基上的坐标,如标准化后<img src="https://latex.codecogs.com/gif.latex?x_{1}&space;=&space;\begin{bmatrix}&space;\frac{1}{\sqrt{2}},\frac{1}{\sqrt{2}}&space;&&space;\end{bmatrix}" title="x_{1} = \begin{bmatrix} \frac{1}{\sqrt{2}},-\frac{1}{\sqrt{2}} & \end{bmatrix}" />,<img src="https://latex.codecogs.com/gif.latex?x_{2}&space;=&space;\begin{bmatrix}&space;-\frac{1}{\sqrt{2}},\frac{1}{\sqrt{2}}&space;&&space;\end{bmatrix}" title="x_{2} = \begin{bmatrix} -\frac{1}{\sqrt{2}},\frac{1}{\sqrt{2}} & \end{bmatrix}" />。<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3,2&space;\end{bmatrix}" title="\begin{bmatrix} 3,2 \end{bmatrix}" />在新基上的坐标即为<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x_1^T\\&space;x_2^T&space;\end{bmatrix}\cdot&space;\begin{pmatrix}&space;3\\&space;2&space;\end{pmatrix}=\begin{pmatrix}&space;\frac{5}{\sqrt{2}}\\&space;-\frac{1}{\sqrt{2}}&space;\end{pmatrix}" title="\begin{bmatrix} x_1^T\\ x_2^T \end{bmatrix}\cdot \begin{pmatrix} 3\\ 2 \end{pmatrix}=\begin{pmatrix} \frac{5}{\sqrt{2}}\\ -\frac{1}{\sqrt{2}} \end{pmatrix}" />

  推广：

  若有m个二维向量，只要将二维向量按列排成一个两行的m列矩阵，用“基矩阵”乘以这个矩阵，就得到了所有这些向量在新基下的坐标

  进一步推广：

  如果我们有M个N维向量，想将其变换为由R个N维向量表示的新空间中。首先将R个基按行组成矩阵A，然后将向量按列组成矩阵B，AB中的第m列为B中第m列变换后的结果

  - 数学表示为

    <img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;P_1\\&space;P_2\\&space;...\\&space;P_R&space;\end{pmatrix}\cdot&space;\begin{pmatrix}&space;a_1&space;&a_2&space;&...&space;&a_M&space;\end{pmatrix}=\begin{pmatrix}&space;P_1a_1&space;&&space;P_1a_2&space;&...&space;&&space;P_1a_M\\&space;P_2a_1&space;&&space;P_2a_2&space;&...&space;&&space;P_2a_M\\&space;...&space;&...&space;&&space;...&space;&...&space;\\&space;P_Ra_1&space;&&space;P_Ra_2&space;&...&space;&&space;P_Ra_M&space;\end{pmatrix}" title="\begin{pmatrix} P_1\\ P_2\\ ...\\ P_R \end{pmatrix}\cdot \begin{pmatrix} a_1 &a_2 &... &a_M \end{pmatrix}=\begin{pmatrix} P_1a_1 & P_1a_2 &... & P_1a_M\\ P_2a_1 & P_2a_2 &... & P_2a_M\\ ... &... & ... &... \\ P_Ra_1 & P_Ra_2 &... & P_Ra_M \end{pmatrix}" />

    <img src="https://latex.codecogs.com/gif.latex?P_i" title="P_i" />为一个行向量，表示第i个基。<img src="https://latex.codecogs.com/gif.latex?a_j" title="a_j" />是一个列向量，表示第j个原始数据记录

  - 矩阵相乘的新的解释

    **是将右边的矩阵中的每一列列向量变换到左边矩阵中每一行的行向量为基所表示的空间中**

- 协方差矩阵及优化目标

  上面讨论了可以选择不同的基对同样一组数据给出不同的表示，而如果基的数量少于向量本身的维数，就达到了降维的效果。但是如何选择基才是最优的？如何投影才能尽可能的保留原有的信息呢？



​		直观的想法是让数据在投影的面尽可能的分散，方差越大越好

- 方差

​		一个变量的方差就是每个元素与变量均值差的平方和的均值

<img src="https://latex.codecogs.com/gif.latex?Var(a)&space;=&space;\frac{1}{m}\sum_{i=1}^{m}(a_i-\mu&space;)^2" title="Var(a) = \frac{1}{m}\sum_{i=1}^{m}(a_i-\mu )^2" />

​		为了方便处理，我们将数据中心化，将其均值变为0，可得

<img src="https://latex.codecogs.com/gif.latex?Var(a)&space;=&space;\frac{1}{m}\sum_{i=1}^{m}a_i^2" title="Var(a) = \frac{1}{m}\sum_{i=1}^{m}(a_i)^2" />

​		所以上面的问题就转化成：寻找一个一维基，使得所有数据变换为这个基上的坐标后，方差值最大

- 协方差

  方差的情况只适用于一维数据，当考虑高维数据时，比如三维降到二维，我们希望第一个维度的方差最大，当第二个维度时，我们就不应该选择方差最大的情况。（因为这与第一个维度几乎重合），我们希望这两个维度包含尽可能多的信息。所以这两个维度应该是不具有线性的相关性。（p.s y = x^2 x,y一定不独立，但是协方差为0）在数学上我们用协方差表示其相关性，协方差的公式为

<img src="https://latex.codecogs.com/gif.latex?Cov(a,b)=\frac{1}{m}\sum_{i=1}^{m}(a_i-\mu_a)(b_i-\mu_b)" title="Cov(a,b)=\frac{1}{m-1}\sum_{i=1}^{m}(a_i-\mu_a)(b_i-\mu_b)" />

​		当我们对数据进行中心化后，

<img src="https://latex.codecogs.com/gif.latex?Cov(a,b)=\frac{1}{m}\sum_{i=1}^{m}a_ib_i" title="Cov(a,b)=\frac{1}{m-1}\sum_{i=1}^{m}a_ib_i" />

​	   当协方差为0时，表示两个变量线性不相关。为了让协方差为0，我们选择第二个基时只能在第一个基正交的方向上选择，因此最终选择的两个方向一定是正交的

​	**降维的目标：将一组N维向量降到K维（K大于0小于N），其目标是选择K个单位（模为1）正交基，使得原始数据变换到这组基上后，各个字段间两两协方差为0，二字段的方差则尽可能地大（在正交的约束下，取最大的K个方差）**

- 协方差矩阵

  最终要达到的目的与变量内方差及变量间协方差有密切关系。因此我们希望将两者统一表示，仔细观察发现，两者均可以表示为内积的形式，而内积又与矩阵密切相关，于是我们有：

  假设我没只有a和b两个字段，那么我们将它们按行组成矩阵X

  <img src="https://latex.codecogs.com/gif.latex?X=\begin{pmatrix}&space;a_1&space;&&space;a_2&space;&&space;...&space;&a_m&space;\\&space;b_1&space;&&space;b_2&space;&...&space;&b_m&space;\end{pmatrix}" title="X=\begin{pmatrix} a_1 & a_2 & ... &a_m \\ b_1 & b_2 &... &b_m \end{pmatrix}" />

  然后我们用X乘以X的转置，并乘上系数1/m

  <img src="https://latex.codecogs.com/gif.latex?\frac{1}{m}XX^T=\begin{pmatrix}&space;\sum_{i=1}^{m}a_i^2&space;&\sum_{i=1}^{m}a_ib_i&space;\\&space;\sum_{i=1}^{m}b_ia_i&space;&\sum_{i=1}^{m}b_i^2&space;\end{pmatrix}=\begin{pmatrix}&space;Cov(a,a)&space;&&space;Cov(a,b)\\&space;Cov(b,a)&space;&&space;Cov(b,b)&space;\end{pmatrix}" title="\frac{1}{m}XX^T=\begin{pmatrix} \sum_{i=1}^{m}a_i^2 &\sum_{i=1}^{m}a_ib_i \\ \sum_{i=1}^{m}b_ia_i &\sum_{i=1}^{m}b_i^2 \end{pmatrix}=\begin{pmatrix} Cov(a,a) & Cov(a,b)\\ Cov(b,a) & Cov(b,b) \end{pmatrix}" />

  这个矩阵对角线上的两个元素分别是两个字段的方差，而其它元素是a和b的协方差，两者被统一到了一个矩阵中

  根据矩阵相乘的运算规则，这个结论推至一般情况：

  **设我们有m个n维数据记录，将其按列排除n乘m的矩阵<img src="https://latex.codecogs.com/gif.latex?X_{n,m}" title="X_{n,m}" />，设<img src="https://latex.codecogs.com/gif.latex?C=\frac{1}{m}XX^T" title="C=\frac{1}{m}XX^T" />，则C是一个对称矩阵，其对角线分别是各个字段的方差，而第i行j列和第j列i行的元素相同，表示i，j两个字段的协方差**

- 协方差矩阵的对角化

  所以我们降维的目标就是将协方差矩阵对角化：即去除对角线外的其他元素为0，并且在对角线上将元素按大小从上到下排列

  设原始数据矩阵X对应的协方差矩阵为C，而P是一组基按行组成的矩阵，设Y=PX，即Y是X对P做基变换后的数据。设Y的协方差矩阵为D，我没可以推导一下D和C之间的关系

  <img src="https://latex.codecogs.com/gif.latex?D=\frac{1}{m}YY^T&space;=\frac{1}{m}(PX)(PX)^T&space;=\frac{1}{m}PXX^TP^T&space;=P\frac{1}{m}XX^TP^T&space;=PCP^T" title="D=\frac{1}{m}YY^T =\frac{1}{m}(PX)(PX)^T =\frac{1}{m}PXX^TP^T =P\frac{1}{m}XX^TP^T =PCP^T" />

  这样就清楚了，我们要找的P不是别的，而是**能让原始协方差矩阵对角化的P。即优化目标变成了寻找一个矩阵P，满足<img src="https://latex.codecogs.com/gif.latex?PCP^T" title="PCP^T" />是一个对角阵，并且对角元素按从大到小依次排列，那么P的前K行就是我们要寻找的基，用P的前K行组成的矩阵乘以X从N维降到K维**

  由上文知道，协方差矩阵C是一个对称矩阵，在线性代数中实对称矩阵有一些比较好的性质

  1. 实对称矩阵不同的特征值对应的特征向量必然正交
  2. 设特征值<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />的重根为r，则必然存在r个线性无关的特征向量对应于<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />，因此可以将这r个特征向量单位正交化

  由上面两条可知，一个n行n列的实对称矩阵一定可以找到n个单位正交的特征向量，设这n个特征向量为<img src="https://latex.codecogs.com/gif.latex?e_1,e_2,...,e_n" title="e_1,e_2,...,e_n" />，我们可以将其组成矩阵<img src="https://latex.codecogs.com/gif.latex?E&space;=&space;\begin{pmatrix}&space;e_1&&space;e_2&&space;...&space;&&space;e_n&space;\end{pmatrix}" title="E = \begin{pmatrix} e_1& e_2& ... & e_n \end{pmatrix}" />，则对协方差矩阵C有如下结论：

  <img src="https://latex.codecogs.com/gif.latex?E^TCE=\Lambda&space;=\begin{pmatrix}&space;\lambda&space;_1&space;&&space;&&space;&&space;\\&space;&&space;\lambda&space;_2&space;&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&&space;\lambda&space;_n&space;\end{pmatrix}" title="E^TCE=\Lambda =\begin{pmatrix} \lambda _1 & & & \\ & \lambda _2 & & \\ & & ...& \\ & & & \lambda _n \end{pmatrix}" />



​	<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为对角阵，其对角元素为各特征向量对应的特征值（可能有重复）

​	所以我们已经找到了需要的矩阵P:<img src="https://latex.codecogs.com/gif.latex?P=E^T" title="P=E^T" />

​	

​	即P是协方差矩阵的特征向量单位化后按行排列出的矩阵,其中每一行都是C的一个特征向量.如果设P按照<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />中特征值的的从大到小将特征向量从上到下排列,则用P的前k行组成的矩阵乘以原始数据矩阵X,就得到了我们需要降维后的矩阵Y



- Example

  二维矩阵X

  

  <img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;-1&space;&&space;-1&space;&&space;0&space;&&space;2&space;&&space;0&space;\\&space;-2&space;&&space;0&space;&&space;0&space;&&space;1&space;&&space;1&space;\end{pmatrix}" title="\begin{pmatrix} -1 & -1 & 0 & 2 & 0 \\ -2 & 0 & 0 & 1 & 1 \end{pmatrix}" />

  

  由于其每一行的均值为0,直接求其协方差矩阵

  <img src="https://latex.codecogs.com/gif.latex?C=\frac{1}{5}\begin{pmatrix}&space;-1&space;&&space;-1&space;&&space;0&space;&&space;2&space;&&space;0&space;\\&space;-2&space;&&space;0&space;&&space;0&space;&&space;1&space;&&space;1&space;\end{pmatrix}\begin{pmatrix}&space;-1&space;&&space;-2&space;\\&space;-1&space;&&space;0&space;\\&space;0&space;&&space;0&space;\\&space;2&space;&&space;1&space;\\&space;0&space;&&space;1&space;\end{pmatrix}=\begin{pmatrix}&space;\frac{6}{5}&space;&&space;\frac{4}{5}&space;\\&space;\frac{4}{5}&space;&&space;\frac{6}{5}&space;\end{pmatrix}" title="C=\frac{1}{5}\begin{pmatrix} -1 & -1 & 0 & 2 & 0 \\ -2 & 0 & 0 & 1 & 1 \end{pmatrix}\begin{pmatrix} -1 & -2 \\ -1 & 0 \\ 0 & 0 \\ 2 & 1 \\ 0 & 1 \end{pmatrix}=\begin{pmatrix} \frac{6}{5} & \frac{4}{5} \\ \frac{4}{5} & \frac{6}{5} \end{pmatrix}" />

    求其特征值为<img src="https://latex.codecogs.com/gif.latex?\lambda_1=2,\lambda_2=2/5" title="\lambda_1=2,\lambda_2=2/5" />,特征向量为<img src="https://latex.codecogs.com/gif.latex?c_1\begin{pmatrix}&space;1&space;\\&space;1&space;\end{pmatrix},c_2\begin{pmatrix}&space;-1&space;\\&space;1&space;\end{pmatrix}" title="c_1\begin{pmatrix} 1 \\ 1 \end{pmatrix},c_2\begin{pmatrix} -1 \\ 1 \end{pmatrix}" />.将特征向量标准化后,得<img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;1/\sqrt{2}&space;\\&space;1/\sqrt{2}&space;\end{pmatrix},\begin{pmatrix}&space;-1/\sqrt{2}&space;\\&space;1/\sqrt{2}&space;\end{pmatrix}" title="\begin{pmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \end{pmatrix},\begin{pmatrix} -1/\sqrt{2} \\ 1/\sqrt{2} \end{pmatrix}" />.因此我们的矩阵P为<img src="https://latex.codecogs.com/gif.latex?P=\begin{pmatrix}&space;1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\\&space;-1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\end{pmatrix}" title="P=\begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ -1/\sqrt{2} & 1/\sqrt{2} \end{pmatrix}" />.可以验证将其协方差矩阵对角化,可得

  <img src="https://latex.codecogs.com/gif.latex?PCP^\mathsf{T}=\begin{pmatrix}&space;1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\\&space;-1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\end{pmatrix}\begin{pmatrix}&space;6/5&space;&&space;4/5&space;\\&space;4/5&space;&&space;6/5&space;\end{pmatrix}\begin{pmatrix}&space;1/\sqrt{2}&space;&&space;-1/\sqrt{2}&space;\\&space;1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\end{pmatrix}=\begin{pmatrix}&space;2&space;&&space;0&space;\\&space;0&space;&&space;2/5&space;\end{pmatrix}" title="PCP^\mathsf{T}=\begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ -1/\sqrt{2} & 1/\sqrt{2} \end{pmatrix}\begin{pmatrix} 6/5 & 4/5 \\ 4/5 & 6/5 \end{pmatrix}\begin{pmatrix} 1/\sqrt{2} & -1/\sqrt{2} \\ 1/\sqrt{2} & 1/\sqrt{2} \end{pmatrix}=\begin{pmatrix} 2 & 0 \\ 0 & 2/5 \end{pmatrix}" />

  最后我们用P的第一行乘以数据矩阵得到降维后的表示:

  <img src="https://latex.codecogs.com/gif.latex?Y=\begin{pmatrix}&space;1/\sqrt{2}&space;&&space;1/\sqrt{2}&space;\end{pmatrix}\begin{pmatrix}&space;-1&space;&&space;-1&space;&&space;0&space;&&space;2&space;&&space;0&space;\\&space;-2&space;&&space;0&space;&&space;0&space;&&space;1&space;&&space;1&space;\end{pmatrix}=\begin{pmatrix}&space;-3/\sqrt{2}&space;&&space;-1/\sqrt{2}&space;&&space;0&space;&&space;3/\sqrt{2}&space;&&space;-1/\sqrt{2}&space;\end{pmatrix}" title="Y=\begin{pmatrix} 1/\sqrt{2} & 1/\sqrt{2} \end{pmatrix}\begin{pmatrix} -1 & -1 & 0 & 2 & 0 \\ -2 & 0 & 0 & 1 & 1 \end{pmatrix}=\begin{pmatrix} -3/\sqrt{2} & -1/\sqrt{2} & 0 & 3/\sqrt{2} & -1/\sqrt{2} \end{pmatrix}" />

故PCA算法的步骤总结如下:

设有m条n维数据

1. 将原始数据按列组成n行m列的矩阵X
2. 将X的每一行(代表一个属性字段)进行零均值化,即减去这一行的均值
3. 求出协方差矩阵<img src="https://latex.codecogs.com/gif.latex?C=\frac{1}{m}XX^\mathsf{T}" title="C=\frac{1}{m}XX^\mathsf{T}" />
4. 求出协方差矩阵的特征值及其对应的特征向量
5. 将特征向量按对应的特征值的大小从上到下按行排列成矩阵,取前k行组成矩阵P
6. <img src="https://latex.codecogs.com/gif.latex?Y=PX" title="Y=PX" />即为降维到k维后的数据

## 另一种思路(PCA)
<img src="https://github.com/generaldzyroot/tianchiMLlearning/blob/main/PCA/images/PCA(2).png" div align=center />





<img src="https://latex.codecogs.com/gif.latex?\begin{aligned}&space;J(e)&=\sum_{k=1}^{n}\left&space;\|&space;{x_k}'-x_k&space;\right&space;\|^2\\&space;&=&space;\sum_{k=1}^{n}&space;\left&space;\|&space;\alpha&space;_ke-x_k&space;\right&space;\|^2\\&space;&=&space;\sum_{k=1}^{n}\alpha&space;_k^2\left&space;\|&space;e&space;\right&space;\|^2-2\sum_{k=1}^{n}\alpha&space;_ke^\mathsf{T}x_k&plus;\sum_{k=1}^{n}\left&space;\|&space;x_k&space;\right&space;\|^2\\&space;&=-\sum_{k=1}^{n}\alpha&space;_k^2&plus;\sum_{k=1}^{n}\left&space;\|&space;x_k&space;\right&space;\|^2\\&space;&=-\sum_{k=1}^{n}e^tx_kx_k^te&plus;\sum_{k=1}^{n}\left&space;\|&space;x_k&space;\right&space;\|^2&space;\end{aligned}" title="\begin{aligned} J(e)&=\sum_{k=1}^{n}\left \| {x_k}'-x_k \right \|^2\\ &= \sum_{k=1}^{n} \left \| \alpha _ke-x_k \right \|^2\\ &= \sum_{k=1}^{n}\alpha _k^2\left \| e \right \|^2-2\sum_{k=1}^{n}\alpha _ke^\mathsf{T}x_k+\sum_{k=1}^{n}\left \| x_k \right \|^2\\ &=-\sum_{k=1}^{n}\alpha _k^2+\sum_{k=1}^{n}\left \| x_k \right \|^2\\ &=-\sum_{k=1}^{n}e^tx_kx_k^te+\sum_{k=1}^{n}\left \| x_k \right \|^2 \end{aligned}" />

第二项为常数,暂时不管.第一项中令<img src="https://latex.codecogs.com/gif.latex?S=x_kx_k^t" title="S=x_kx_k^t" />,我们的问题则变为<img src="https://latex.codecogs.com/gif.latex?\underset{e}{max}&space;e^tSe,s.t.\left&space;\|&space;e&space;\right&space;\|=1" title="\underset{e}{max} e^tSe,s.t.\left \| e \right \|=1" />

使用拉格朗日乘数法,得<img src="https://latex.codecogs.com/gif.latex?U=e^TSe-\lambda&space;(e^Te-1)" title="U=e^TSe-\lambda (e^Te-1)" />

对e求偏导,即得<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;U}{\partial&space;e}=2Se-2\lambda&space;e=0" title="\frac{\partial U}{\partial e}=2Se-2\lambda e=0" />

所以<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" /> 是特征值,e是特征向量



参考

https://zhuanlan.zhihu.com/p/77151308

https://blog.codinglabs.org/articles/pca-tutorial.html
