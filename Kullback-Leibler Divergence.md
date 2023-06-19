# KL散度
## 信息量
要知道什么是KL散度，首先得先了解信息量的概念
![Alt text](https://raw.githubusercontent.com/Cccccz-x/md/master/image.png)
阿根廷从八强到夺冠的信息量为 $f(\frac{1}{8})=f(\frac{1}{4})+f(\frac{1}{2})$，易理解不论通过哪个路径，都是从八强到夺冠的信息量

而我们又知道 $\frac{1}{8}=\frac{1}{4}\times\frac{1}{2}$

所以需要定义一个信息量满足 $f(x_1 \times x_2) = f(x_1) + f(x_2)$

首先就想到对数函数 $f(x) = ?\cdot \log_?x$

而我们又知道，从八强到夺冠的信息量比从决赛到夺冠的信息量大，即和夺冠概率负相关，但log是正相关，所以系数定为-1

那么信息量公式就为 $f(x)=-\log_?x$，一般以2为底，单位记为bit

## 熵
接下来就要知道什么是熵
![Alt text](https://raw.githubusercontent.com/Cccccz-x/md/master/image-1.png)
熵描述的是一个系统的混乱程度，不确定程度
显然，左边的谁赢谁输更不确定，计算出的信息量加权和为1，右边相对确定，计算出的信息量加权和为0.08

所以就给出熵的定义，即信息量的期望，也即加权平均，权为该事件发生的概率
![Alt text](https://raw.githubusercontent.com/Cccccz-x/md/master/image-2.png)
!!!恍然大悟，原来决策树算法的信息熵公式是这么来的

这里给出完整定义  
若一个离散随机变量X的可能取值为X={x_1,x_2,⋯,x_n}，而对应的概率为p_i=p(X=x_i)，则随机变量X的熵定义为：
$$H(X)=−\sum_{i}^{n} p(x_i)\log p(x_i)$$

## 交叉熵
因为KL散度中涉及交叉熵  
若有两个随机变量P、Q，且其概率分布分别为p(x)、q(x)，则p和q的交叉熵为：
$$H(p,q) = -\sum_i^n p(x_i)\cdot \log q(x_i)$$

机器学习中的交叉熵损失函数:
$$-\sum_i^n y_i\log y_i' + (1-y_i)\log (1-y_i')$$

## KL散度
又被称为：相对熵、互熵、鉴别信息、Kullback熵、Kullback-Leible散度(即KL散度的简写)。在机器学习、深度学习领域中，KL散度被广泛运用于变分自编码器中(Variational AutoEncoder,简称VAE)、EM算法、GAN网络中
![Alt text](https://raw.githubusercontent.com/Cccccz-x/md/master/image-3.png)
把KL散度定义为以P为基准，两个分布的差，图中第二行即为下面定义的公式  
若有两个随机变量P、Q，且其概率分布分别为p(x)、q(x)，则p相对q的相对熵为：
$$D_{KL}(p||q) = \sum_i^n p(x_i) \cdot \log\frac{p(x_i)}{q(x_i)}$$

所以 $D_{KL}(p||q)=H(P,Q)-H(P)$

而由吉布斯不等式知：
![Alt text](https://raw.githubusercontent.com/Cccccz-x/md/master/image-4.png)
所以 $D_{KL}(p||q)\geq 0$ 即正定