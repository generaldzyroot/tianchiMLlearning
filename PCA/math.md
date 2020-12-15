# PCA

- 内积与投影
  <img src="https://latex.codecogs.com/gif.latex?A\cdot&space;B=|A||B|cos&space;\alpha" title="A\cdot B=|A||B|cos \alpha" />

  若|B|=1，那么A与B的内积=A向B所在直线投影的矢量长度

- 基

  <img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3,2&space;\end{bmatrix}" title="\begin{bmatrix} 3,2 \end{bmatrix}" />本身并不能精确的表示一个向量，实际上向量<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x,y&space;\end{bmatrix}" title="\begin{bmatrix} x,y \end{bmatrix}" />表示线性组合<img src="https://latex.codecogs.com/gif.latex?x\begin{bmatrix}&space;1,0&space;\end{bmatrix}^T" title="x\begin{bmatrix} 1,0 \end{bmatrix}^T" />+<img src="https://latex.codecogs.com/gif.latex?y\begin{bmatrix}&space;0,1&space;\end{bmatrix}^T" title="y\begin{bmatrix} 0,1 \end{bmatrix}^T" />.**其中基表示<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;1,0&space;\end{bmatrix}" title="\begin{bmatrix} 1,0 \end{bmatrix}" />，<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;0,1&space;\end{bmatrix}" title="\begin{bmatrix} 0,1 \end{bmatrix}" />如果我们要换成新基<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;1,1&space;\end{bmatrix}" title="\begin{bmatrix} 1,1 \end{bmatrix}" />,<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;-1,1&space;\end{bmatrix}" title="\begin{bmatrix} -1,1 \end{bmatrix}" />.首先，我们希望新基的模是1，这样就方便我们直接点乘得到其在新基上的坐标
