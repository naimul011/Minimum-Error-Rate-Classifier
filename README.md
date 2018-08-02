# Designing a Minimum Error Rate classifier

## Author:

## Naimul Haque

## Roll:

## 14.02.04.080 (B1)

## Submission date: July 27,


```
F
```
## 1 OBJECTIVE

The aspiration of this experiment is to classify
some sample points using the posterior proba-
bilities modeled by **Gaussian distribution** to
calculate the likelihood probabilities. The in-
tention of this type of classifier is to minimize
the error rate during classification. Accordingly,
this classifier takes a decision based on the
most posterior probabilities hence this classifier
is also known as the **Bayes classifier** with
minimum error according to **Bayesian theory**.

## 2 INTRODUCTION

**Minimum error rate classifier** is a classifier
and its aim is to minimize the error rate. We
are given six sample data which needs to be
classified. The likelihood probabilities of a
sample are given by the **Normal Distribution**
or **Gaussian Distribution**. Any Normal
Distribution can be expressed with two
parameter- sigma(σ) and mean(μ).

```
Baysian Classifer:
if p 1 (x)> p 2 (x) then
x∈ω 1
else
x∈ω 2
end if
wherex∈ω 1 andx∈ω 2
```
The likelihood probabilities is the **Gaussian
distribution** here and can be written as:

P(x) =σ√^12 πe−(x−μ)

(^2) / 2 σ 2
Extending this formula for multidimensional
problem:
P(x) =^1
(2π)d^2 Σ^12
e
− 1
2 (x−μ)tΣ
(^12) (x−μ)
wheredis the number of dimension.

## 3 EXPERIMENTAL DESIGN AND IMPLE-

```
MENTATION
```
```
3.1 Plotting the sample points in 2D feature
space
```
```
The sample points are classified into one of the
two classes ω 1 and ω 2 are marked by color
Cyan (c) and magenta(m) respectively. The data
points are plotted in a graph in x 1 and x 2
feature space with their respective class color.
The data points are further marked with
‘Diamond’() for classω 1 and ‘Box’() for class
ω 2.
Figure1 shows the sample data points.
```
```
Figure 1. The points
```
```
To visualize more, the decision boundary
is plotted in the graph by calculating the slope
and constant of the discriminant function
g(x) = 0.
```

**3.2 Drawing decision boundary**

To draw the decision boundary we have to
obtain the equation of the decision boundary
and we know that at decision boundary g1(x)-
g2(x) = 0.

The boundary is shown in figure2.

Figure 2. The boundary

**3.3 Changing parameters**

After changing the mu2 = [2,2] to mu2 =
[10,10]we shift the boundary away from class
ω 2 and all the points are now marked as class
ω 1.
The change of thee model is shown in
figure3.

**3.4 Marking Different Regions**

Different regions are marked in the with
different normal distribution and is shown in
figure1.

```
Figure 3. The transformed graph
```
## 4 RESULT ANALYSIS

```
The distribution is for the feature vectors and
the sample points are plotted in the figure1 in
the 2D feature space.
The minimum error rate classifier minimizes
the error. As soon as we change the parame-
ter of Gaussian distribution the sample values
have shifted to another class because the likeli-
hood probabilities can also be shifted towards
another class.
```
## APPENDIXA

## CODE

```
The MATLAB code :
%Author: Naimul Haque 27th Jul,
2018
clear all;
clc;
x1 = -7:.2:7;
x2 = -7:.2:7;
[X1,X2] = meshgrid(x1,x2);
```
```
mu1 = [1 1];
Sigma1 = [.50 .6; .6 1];
F1 = mvnpdf([X1(:) X2(:)],mu1,
Sigma1);
F1 = reshape(F1,length(x2),length(
x1));
```
```
meshc(X1,X2,F1);
```

axis([-7 7 -7 7 -1.0 .6])
xlabel('x1'); ylabel('x2'); zlabel(
'Probability Density');
hold on;

mu2 = [10 10];
Sigma2 = [.25 .0; 0 .25];
F2 = mvnpdf([X1(:) X2(:)],mu2,
Sigma2);
F2 = reshape(F2,length(x2),length(
x1));

meshc(X1,X2,F2);
axis([-7 7 -7 7 -1.0 .6])
xlabel('x1'); ylabel('x2'); zlabel(
'Probability Density');

caxis([min(F2(:))-.5*range(F2(:)),
max(F2(:))]);

%task 1 and 2
x = [1 1
1 -
4 5
-2 2.
0 2
2 -3];

g = @(Sigma,mu,n) -log(2*pi)-0.5*
log(det(Sigma))-0.5*(x(n,:)'-mu
')'*inv(Sigma)*(x(n,:)'-mu')+log
(0.5);

for n=1:
g1 = g(Sigma1,mu1,n);
g2 = g(Sigma2,mu2,n);

if g1>g
plot3(x(n,1),x(n,2),-1.0,'cd');
else
plot3(x(n,1),x(n,2),-1.0,'ms');
end
end

syms x1 x2;

b = @(Sigma,mu) -log(2*pi) - 0.5*
log(det(Sigma)) - 0.5*([x1;x2]-

```
mu')'*(Sigmaˆ-1)*([x1;x2]-mu') +
log(0.5);
```
```
g1 = b(Sigma1,mu1);
g2 = b(Sigma2,mu2);
```
```
g = g1 - g2;
L3=ezplot(g, [ [-10,10], [-10,10]
]);
```

