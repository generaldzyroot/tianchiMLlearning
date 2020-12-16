# Logistic 数学推导

## logistic funciton

$$\theta$$为参数,共有i个观测值,参数的个数为j个

<img src="https://latex.codecogs.com/gif.latex?h_\theta(x)=g(\theta^T (x))=\frac{e^{\theta^T x}}{1&plus;e^{\theta^T x}" title="y=\frac{e^{\theta}}{1+e^\theta}"/>

<img src="https://latex.codecogs.com/gif.latex?g(z)=\frac{e^z}{1&plus;e^z}&space;=&space;\frac{1}{1&plus;e^{-z}}" title="g(z)=\frac{e^z}{1+e^z} = \frac{1}{1+e^{-z}}" />

当假设y仅有两个取值0,1时

<img src="https://latex.codecogs.com/gif.latex?P(y=1|x;\theta)=h_{\theta}(x)" title="P(y=1|x;\theta)=h_{\theta}(x)" />

<img src="https://latex.codecogs.com/gif.latex?P(y=0|x;\theta)=1-h_{\theta}(x)" title="P(y=0|x;\theta)=1-h_{\theta}(x)" />

似然函数为



<img src="https://latex.codecogs.com/gif.latex?L(\theta)&space;=P(y|x;\theta)=\coprod_{i}P(y^{i}|x^{i};\theta)=\coprod_{i}h_\theta&space;(x^{i})^{y^{i}}\coprod_{i}(1-&space;h_\theta&space;(x^{i})^{1-y^{i}}" title="L(\theta) =P(y|x;\theta)=\coprod_{i}P(y^{i}|x^{i};\theta)=\coprod_{i}h_\theta (x^{i})^{y^{i}}\coprod_{i}(1- h_\theta (x^{i})^{1-y^{i}}" />



两边取对数,得
<img src="https://latex.codecogs.com/gif.latex?l(\theta)&space;=logL(\theta)&space;=\sum_{i=1}^{m}y^ilogh_{\theta}(x^{i})&plus;(1-y^{i})logh_{\theta}(1-x^{i})" title="l(\theta) =logL(\theta) =\sum_{i=1}^{m}y^ilogh_{\theta}(x^{i})+(1-y^{i})logh_{\theta}(1-x^{i})" />

### 梯度求导



<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;l(\theta)}{\partial&space;\theta}\\=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}]\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}][g(\theta^Tx)(1-g(\theta^Tx)]\frac{\partial&space;\theta^Tx}{\partial&space;\theta_j}\\&space;=(y-h_{\theta}&space;x)x_j" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;l(\theta)}{\partial&space;\theta}\\=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}]\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}][g(\theta^Tx)(1-g(\theta^Tx)]\frac{\partial&space;\theta^Tx}{\partial&space;\theta_j}\\&space;=(y-h_{\theta}&space;x)x_j" title="\frac{\partial l(\theta)}{\partial \theta}\\=[y\frac{1}{g(\theta^T x)}-(1-y)\frac{1}{1-g(\theta^T x)}]\frac{\partial g(\theta^T x)}{\partial \theta_j}\\ =[y\frac{1}{g(\theta^T x)}-(1-y)\frac{1}{1-g(\theta^T x)}][g(\theta^Tx)(1-g(\theta^Tx)]\frac{\partial \theta^Tx}{\partial \theta_j}\\ =(y-h_{\theta} x)x_j" /></a>



tips:

<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=(\frac{1}{1&plus;e^{-\theta^T&space;x}})^{'}\\&space;=\frac{-(e^{-\theta^T&space;x})^{'}}{(1&plus;e^{-\theta^T&space;x})^2}\\&space;=\frac{-(e^{-\theta^T&space;x})^{'}}{(1&plus;e^{-\theta^T&space;x})^2}\\&space;=\frac{e^{-\theta^T&space;x}}{(1&plus;e^{-\theta^T&space;x})^2}(\theta^Tx)^{'}\\&space;=\frac{1}{(1&plus;e^{-\theta^T&space;x})}\frac{e^{-\theta^T&space;x}}{(1&plus;e^{-\theta^T&space;x})}(\theta^Tx)^{'}\\&space;=(g(\theta^T&space;x))(1-g(\theta^T&space;x))(\theta^Tx)^{'}" title="\frac{\partial g(\theta^T x)}{\partial \theta_j}\\ =(\frac{1}{1+e^{-\theta^T x}})^{'}\\ =\frac{-(e^{-\theta^T x})^{'}}{(1+e^{-\theta^T x})^2}\\ =\frac{-(e^{-\theta^T x})^{'}}{(1+e^{-\theta^T x})^2}\\ =\frac{e^{-\theta^T x}}{(1+e^{-\theta^T x})^2}(\theta^Tx)^{'}\\ =\frac{1}{(1+e^{-\theta^T x})}\frac{e^{-\theta^T x}}{(1+e^{-\theta^T x})}(\theta^Tx)^{'}\\ =(g(\theta^T x))(1-g(\theta^T x))(\theta^Tx)^{'}" /> 



故

<img src="https://latex.codecogs.com/gif.latex?\theta_j&space;:=\theta_j&plus;\alpha\sum_{i=1}^{m}(y^{i}-h_\theta(x^i))x_j^{i}" title="\theta_j :=\theta_j+\alpha\sum_{i=1}^{m}(y^{i}-h_\theta(x^i))x_j^{i}" />

## BGD 

每计算出一个参数都要遍历这个数据集,故这种方法被称为BGD(Batch gradient descent)

That is for an every step of gradient descent you're going to look at your entire training set

而当你越接近极值时, 函数的每一步step就会越来越小,因为在每次更新参数的时候,都要减去<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />*gradient,而越接近极值时,梯度越低

## SGD

随机梯度下降法(Stochastic gradient descent)

Repeat{

​	For j = 1 to m{

​		<img src="https://latex.codecogs.com/gif.latex?\theta:=\theta-\alpha&space;[h_\theta(x^j)-y^j]x_i^j" title="\theta:=\theta-\alpha [h_\theta(x^j)-y^j]x_i^j" />

​			for all i}

}

即每次更新只用一个样本,这个方法比上面的方法快,但并不是每一次迭代损失函数都会往最低的方向进行,但大的整体方向都会往最低处进行,不会收敛到最优解





# Softmax回归

要想了解好多分类问题的softmax

### 广义线性模型GLM

## softmax function

(要想知道softmax函数是怎么来的,要填GLM的坑，我先把这个求导公式搞定)

<img src="https://latex.codecogs.com/gif.latex?P(y=i|x;\theta)=\frac{e^{\theta_i^T&space;x}}{\sum_{j=1}^{K}e^{\theta_j^T&space;x}}" title="P(y=i|x;\theta)=\frac{e^{\theta_i^T x}}{\sum_{j=1}^{K}e^{\theta_j^T x}}" />

其中K表示一共有K类，当y属于第i类时的概率如上式所示

那么其对数似然函数求导为

<img src="https://latex.codecogs.com/gif.latex?l(\theta)=-\frac{1}{m}[\sum_{i=1}^{m}\sum_{j=1}^{K}I\left&space;\{&space;y^{(i)}=j&space;\right&space;\}&space;]log\frac{e^{\theta_j^T&space;x^{(i)}}}{\sum_{l=1}^{K}e^{\theta_l^T&space;x^{(i)}}}" title="l(\theta)=-\frac{1}{m}[\sum_{i=1}^{m}\sum_{j=1}^{K}I\left \{ y^{(i)}=j \right \} ]log\frac{e^{\theta_j^T x^{(i)}}}{\sum_{l=1}^{K}e^{\theta_l^T x^{(i)}}}" />

其中<img src="https://latex.codecogs.com/gif.latex?I(x=y)" title="I(x=y)" />为指示函数，即x=y时值为1，x不等于y时值为0

m表示样本数

如上式所示只有当第i个样本的分类<img src="https://latex.codecogs.com/gif.latex?y^{(i)}" title="y^{(i)}" />=第j类时，值才为1，否则值为0，连乘变连加得到上式

加上l2正则项则为

<img src="https://latex.codecogs.com/gif.latex?l(\theta)=\left&space;(&space;-\frac{1}{m}[\sum_{i=1}^{m}\sum_{j=1}^{K}I\left&space;\{&space;y^{(i)}=j&space;\right&space;\}&space;]log\frac{e^{\theta_j^T&space;x^{(i)}}}{\sum_{l=1}^{K}e^{\theta_l^T&space;x^{(i)}}}\right&space;)&plus;\frac{\lambda&space;}{2}\sum_{i=1}^{K}\sum_{j=0}^{n}\theta_{ij}^2" title="l(\theta)=\left ( -\frac{1}{m}[\sum_{i=1}^{m}\sum_{j=1}^{K}I\left&space;\{&space;y^{(i)}=j&space;\right&space;\}&space;]log\frac{e^{\theta_j^T&space;x^{(i)}}}{\sum_{l=1}^{K}e^{\theta_l^T&space;x^{(i)}}}\right )+\frac{\lambda }{2}\sum_{i=1}^{K}\sum_{j=0}^{n}\theta_{ij}^2" />



### 梯度求导

我们只考虑一个样本<img src="https://latex.codecogs.com/gif.latex?(x,y)" title="(x,y)" />，有，

<img src="https://latex.codecogs.com/gif.latex?l(x,\hat{y})=-\sum_{j=1}^{K}I\left&space;\{&space;y=j&space;\right&space;\}ln\hat{y_j}" title="l(x,\hat{y})=-\sum_{j=1}^{K}I\left \{ y=j \right \}ln\hat{y_j}" />

令<img src="https://latex.codecogs.com/gif.latex?a_j=\theta_j^Tx" title="a_j=\theta_j^Tx" />，有

<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;l(x,\hat{y})&space;}{a_j}\\&space;=&space;\sum_{i=1}^{K}\frac{\partial&space;l(x,\hat{y})&space;}{\partial&space;\hat{y_i}}&space;\frac{\partial&space;\frac{e^{a_i}}{\sum_{l=1}^{K}e^{a_l}}&space;}{\partial&space;a_j}\\&space;=-\sum_{i=1}^{K}\frac{I\left&space;\{&space;y=i&space;\right&space;\}}{\hat{y_i}}\frac{e^{a_i}\cdot&space;I\left&space;\{&space;i=j&space;\right&space;\}\cdot(\sum_{l=1}^{K}e^{a_l})-e^{a_i}\cdot&space;e^{a_j}}{(\sum_{l=1}^{K}e^{a_l})^2}\\&space;=\sum_{i=1}^{K}\frac{I\left&space;\{&space;y=i&space;\right&space;\}}{\hat{y_i}}\frac{e^{a_i}\cdot&space;e^{a_j}}{(\sum_{l=1}^{K}e^{a_l})^2}-\sum_{i=1}^{K}\frac{I\left&space;\{&space;y=i&space;\right&space;\}}{\hat{y}}\frac{e^{a_i}\cdot&space;I\left&space;\{&space;i=j&space;\right&space;\}\cdot(\sum_{l=1}^{K}e^{a_l})}{(\sum_{l=1}^{K}e^{a_l})^2}\\&space;=\sum_{i=1}^{K}\frac{I\left&space;\{&space;y=i&space;\right&space;\}}{\hat{y_i}}\hat{y_i}\hat{y_j}-\sum_{i=1}^{K}\frac{I\left&space;\{&space;y=i&space;\right&space;\}}{\hat{y_i}}\hat{y_i}I\left&space;\{&space;i=j&space;\right&space;\}\\&space;=\hat{y_j}-\sum_{i=1}^{K}I\left&space;\{&space;y=i&space;\right&space;\}I\left&space;\{&space;i=j&space;\right&space;\}\\&space;=\hat{y_j}-I\left&space;\{&space;y=j&space;\right&space;\}" title="\frac{\partial l(x,\hat{y}) }{a_j}\\ = \sum_{i=1}^{K}\frac{\partial l(x,\hat{y}) }{\partial \hat{y_i}} \frac{\partial \frac{e^{a_i}}{\sum_{l=1}^{K}e^{a_l}} }{\partial a_j}\\ =-\sum_{i=1}^{K}\frac{I\left \{ y=i \right \}}{\hat{y_i}}\frac{e^{a_i}\cdot I\left \{ i=j \right \}\cdot(\sum_{l=1}^{K}e^{a_l})-e^{a_i}\cdot e^{a_j}}{(\sum_{l=1}^{K}e^{a_l})^2}\\ =\sum_{i=1}^{K}\frac{I\left \{ y=i \right \}}{\hat{y_i}}\frac{e^{a_i}\cdot e^{a_j}}{(\sum_{l=1}^{K}e^{a_l})^2}-\sum_{i=1}^{K}\frac{I\left \{ y=i \right \}}{\hat{y}}\frac{e^{a_i}\cdot I\left \{ i=j \right \}\cdot(\sum_{l=1}^{K}e^{a_l})}{(\sum_{l=1}^{K}e^{a_l})^2}\\ =\sum_{i=1}^{K}\frac{I\left \{ y=i \right \}}{\hat{y_i}}\hat{y_i}\hat{y_j}-\sum_{i=1}^{K}\frac{I\left \{ y=i \right \}}{\hat{y_i}}\hat{y_i}I\left \{ i=j \right \}\\ =\hat{y_j}-\sum_{i=1}^{K}I\left \{ y=i \right \}I\left \{ i=j \right \}\\ =\hat{y_j}-I\left \{ y=j \right \}" />

# Accuracy_score

|          | Guessed Positive   | Guessed Negative |
| -------- | ------------------ | ---------------- |
| Positive | True Positive(TP)  | False Negative   |
| Negative | False Positive(FP) | True Negative    |

准确率Accuracy:

How many did we classified correctly?

= (TP+TN)/总数

准确率不适用的类型

## 补充

# Matric的使用


# 参考
<div id="refer-anchor-1"></div>

- [1] [cs229]

<div id="refer-anchor-2"></div>

- [2] [西瓜书]

<div id="refer-anchor-2"></div>

- [3] [李航] 统计学习导论

仅供自己学习使用

