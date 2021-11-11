
# Goal : (1) To derive the equations for learning parameters of a Gaussian mixture model

---

## Gaussian Mixture Model 


For Given data $x$, GMM represents the probability of x occurring as the sum of several Gaussian probability density functions. 

$$p(x) = \sum^K_{k=1} \pi_k N(x|\mu_k, \Sigma_k) \tag{1} $$

mixing coefficient, $\pi_k$ represents the probability that the k-th Gaussian distribution will be selected. so $\pi_k$ must satisfy follows:

$$0\le \pi_k \le 1 \tag{2}$$
$$\sum^K_{k=1} \pi_k = 1 \tag{3}$$


## 1. Classification using GMM  

Learning GMM means estimating appropriate $\pi_k, \mu_k, \Sigma_k$ for given $X=\{x_1,x_2,..,x_N\}$ 

Classification using GMM is to find out in which Gaussian distrubution a given data $x_N$ was generated. 

For this, responsibility is defined as follows.

$$\gamma(z_{nk}) = p(z_{nk}=1)|x_n) \tag{4}$$


$z_{nk} \in \{0,1\}$ is a binary variable with a value of 1 if the k-th Gaussian distribution of GMM is selected given xn or a value of 0 if not.

That is, when $z_{nk}$ is 1, it means that $x_n$ is generated in the k-th Gaussian distribution.

Classification using GMM is to select the Gaussian distribution with the highest value by calculating the k number of $\gamma(z_{nk})$ given xn.


If the values of all parameters $\pi, \mu, \Sigma$ of GMM are determined through learning, $\gamma(z_{nk})$ can be calculated as follows using Bayes'theorem.

$$\gamma(z_{nk}) = p(z_{nk}=1 | x_n) = \frac{p(z_{nk}=1)p(x_n|z_{nk}=1)}{\sum^K_{j=1}p(z_{nj}=1)p(x_n|z_{nj}=1)} = \frac{\pi_k N (x_n|\mu_k, \Sigma_k)}{\sum^K_{j=1}\pi_jN(x_n|\mu_j,\Sigma_j)} \tag{5}$$

## 2. Learning GMM using Expectation-Maximization algorithm (EM algorithm) 

For estimating parameters,  log-likelihod $\mathcal{L}(X;\theta)$ is defined as 

$$\mathcal{L}(X;\theta) = \ln p(X | \pi, \mu, \Sigma) = \ln\left\{\Pi^N_{n=1}p(x_n|\pi,\mu,\Sigma)\right \} = \sum^N_{n=1} \ln \left \{\sum^K_{k=1} \pi_k N(x_n | \mu_k, \Sigma_k)\right \} \tag{6}$$

Estimating $\pi,\mu,\Sigma$ with maxmized log-likelihood means 

Estimating $\pi,\mu,\Sigma$ when log-like hood is at its maximum has the same meaning as constructing GMM that best represents given data X.

For do this, 
it partial differentiate $\mathcal{L}(X;\theta)$ for $\pi_k, \mu_k, \Sigma_k$.



### 1) $\mu_k$
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  


### 2) $\Sigma_k$ 

.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  

### 3) $\pi_k$  

 $\pi_k$, the last parameter of GMM, must maximize log-likelihood while satisfying the condition of equ.3.
so $\pi_k$ is estimated by using Lagrange multiplier method, Lagrangian $J(X;θ,λ)$ is as follows: 

.  
.  
.  


$\lambda$ is found by partial differentiation of Lagrangean.


.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
$\pi_k$ can be estimated using the calculated $\lambda$.

.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  


For estimating parameters of GMM, 

In **E-step** of EM algorithm,  
$\gamma(z_{nk})$ is calculated by all datas and Gaussian distribution.

And then, In **M-step**of EM algorithm,  
$\pi,\mu,\Sigma$ for all Gaussian distribution are estimated by using  equ.7,8,11

These E-step and M-step are repeated until converging or a certain number of times.