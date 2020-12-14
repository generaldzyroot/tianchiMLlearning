# Logistic 数学推导

## logistic funciton

$\theta$为参数,共有i个观测值,参数的个数为j个



<img src="https://latex.codecogs.com/gif.latex?h_{\theta}(x)=&space;\frac{e^{\theta^T&space;x}}{1&plus;e^{\theta^T&space;x}}=\frac{1}{1&plus;e^{-\theta^T&space;x}}" title="h_{\theta}(x)= \frac{e^{\theta^T x}}{1+e^{\theta^T x}}=\frac{1}{1+e^{-\theta^T x}}" />




<img src="https://latex.codecogs.com/gif.latex?g(z)=\frac{e^z}{1&plus;e^z}&space;=&space;\frac{1}{1&plus;e^{-z}}" title="g(z)=\frac{e^z}{1+e^z} = \frac{1}{1+e^{-z})})" />

当假设y仅有两个取值0,1时

<img src="https://latex.codecogs.com/gif.latex?P(y=1|x;\theta)=h_{\theta}(x)" title="P(y=1|x;\theta)=h_{\theta}(x)" />

<img src="https://latex.codecogs.com/gif.latex?P(y=0|x;\theta)=1-h_{\theta}(x)" title="P(y=0|x;\theta)=1-h_{\theta}(x)" />

似然函数为



<img src="https://latex.codecogs.com/gif.latex?L(\theta)&space;=P(y|x;\theta)=\coprod_{i}P(y^{i}|x^{i};\theta)=\coprod_{i}h_\theta&space;(x^{i})^{y^{(i)}}\coprod_{i}(1-&space;h_\theta&space;(x^{i})^{1-y^{(i)}}" title="L(\theta) =P(y|x;\theta)=\coprod_{i}P(y^{i}|x^{i};\theta)=\coprod_{i}h_\theta (x^{i})^{y^{(i)}}\coprod_{i}(1- h_\theta (x^{i})^{1-y^{(i)}}" />



两边取对数,得
<img src="https://latex.codecogs.com/gif.latex?l(\theta)&space;=logL(\theta)&space;=\sum_{i=1}^{m}y^ilogh_{\theta}(x^{i})&plus;(1-y^{i})logh_{\theta}(1-x^{i})" title="l(\theta) =logL(\theta) =\sum_{i=1}^{m}y^ilogh_{\theta}(x^{i})+(1-y^{i})logh_{\theta}(1-x^{i})" />

对$\theta$求偏导得

<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;l(\theta)}{\partial&space;\theta}\\=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}]\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=[y\frac{1}{g(\theta^T&space;x)}-(1-y)\frac{1}{1-g(\theta^T&space;x)}][g(\theta^Tx)(1-g(\theta^Tx)]\frac{\partial&space;\theta^Tx}{\partial&space;\theta_j}\\&space;=(y-h_{\theta}&space;x)x_j" title="\frac{\partial l(\theta)}{\partial \theta}\\=[y\frac{1}{g(\theta^T x)}-(1-y)\frac{1}{1-g(\theta^T x)}]\frac{\partial g(\theta^T x)}{\partial \theta_j}\\ =[y\frac{1}{g(\theta^T x)}-(1-y)\frac{1}{1-g(\theta^T x)}][g(\theta^Tx)(1-g(\theta^Tx)]\frac{\partial \theta^Tx}{\partial \theta_j}\\ =(y-h_{\theta} x)x_j" />



tips:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=(\frac{1}{1&plus;e^{-\theta^T&space;x}})^{'}\\&space;=\frac{-(e^{-\theta^T&space;x})^{'}}{(1&plus;e^{-\theta^T&space;x})^2}\\&space;=\frac{1}{(1&plus;e^{-\theta^T&space;x})}\frac{e^{-\theta^T&space;x}}{(1&plus;e^{-\theta^T&space;x})}(\theta^Tx)^{'}\\&space;=(g(\theta^T&space;x))(1-g(\theta^T&space;x))(\theta^Tx)^{'}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\&space;=(\frac{1}{1&plus;e^{-\theta^T&space;x}})^{'}\\&space;=\frac{-(e^{-\theta^T&space;x})^{'}}{(1&plus;e^{-\theta^T&space;x})^2}\\&space;=\frac{1}{(1&plus;e^{-\theta^T&space;x})}\frac{e^{-\theta^T&space;x}}{(1&plus;e^{-\theta^T&space;x})}(\theta^Tx)^{'}\\&space;=(g(\theta^T&space;x))(1-g(\theta^T&space;x))(\theta^Tx)^{'}" title="\frac{\partial&space;g(\theta^T&space;x)}{\partial&space;\theta_j}\\ =(\frac{1}{1&plus;e^{-\theta^T&space;x}})^{'}\\ =\frac{-(e^{-\theta^T&space;x})^{'}}{(1&plus;e^{-\theta^T&space;x})^2}\\ =\frac{1}{(1&plus;e^{-\theta^T&space;x})}\frac{e^{-\theta^T&space;x}}{(1&plus;e^{-\theta^T&space;x})}(\theta^Tx)^{'}\\ =(g(\theta^T&space;x))(1-g(\theta^T&space;x))(\theta^Tx)^{'}" /></a>


故

<img src="https://latex.codecogs.com/gif.latex?\theta_j&space;:=\theta_j&plus;\alpha\sum_{i=1}^{m}(y^{i}-h_\theta(x^i))x_j^{i}" title="\theta_j :=\theta_j+\alpha\sum_{i=1}^{m}(y^{i}-h_\theta(x^i))x_j^{i}" />
每计算出一个参数都要遍历这个数据集

# Accuracy_score

|          | Guessed Positive   | Guessed Negative |
| -------- | ------------------ | ---------------- |
| Positive | True Positive(TP)  | False Negative   |
| Negative | False Positive(FP) | True Negative    |

准确率Accuracy:

How many did we classified correctly?

= (TP+TN)/总数

准确率不适用的类型


