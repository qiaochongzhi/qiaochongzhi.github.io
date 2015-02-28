---
layout: post
title: Modified Fundamental Measure Theory  Calculation process
tags: Density-Functional-Theory
---

## From $\omega$ to $n$

In FMT, Rosenfeld postulates that the excess Helmholtz energy functional of an inhomogeneous hard-sphere mixture, $F^{ex}$, can be expressed in the form of a weight density approximation

$$
  F^{ex}/k_BT = \int \Phi (\textbf{r}) d\textbf{r}
$$

where $K_B$ is Boltzmann constant and $T$ is absolute temperature. The reduced excess Helmholtz energy density $\Phi$ is a function of only the weight averages of the density distribution function $\rho_i(\textbf{r}) $

$$
  n_{\alpha} (\textbf{r}) = \sum_i n_{\alpha ,i} (\textbf{r}) = \sum_i \int \rho_i (\textbf{r}') \omega_i^{(\alpha)} (\textbf{r} - \textbf{r}')d\textbf{r}'
$$

The weight functions $\omega_i^{(\alpha)}(\textbf{r})$ characterize the gemoetry of a hard-sphere: two scalar functions are related to, respectively, the volume and the surface area

$$
  \omega_i^{(3)} (\textbf{r}) = \theta (\sigma_i/2 -r),
$$

$$
  \omega_i^{(2)}(\textbf{r}) = \delta (\sigma_i/2 -r)
$$

and a surface vector function characterize the variance across the particle surface 

$$
   \omega_i^{(V2)}(\textbf{r}) = (\textbf{r}/r)\delta (\sigma_i/2 -r)
$$

Three additional weight function characterizes thr variance across the particle surface

$$
  \omega_i^{(1)}(\textbf{r}) = \omega_i^{(2)}(\textbf{r})/(2\pi \sigma_i),
$$

$$
  \omega_i^{(0)}(\textbf{r}) = \omega_i^{(2)}(\textbf{r})/(\pi \sigma_i^2),
$$

$$
  \omega_i^{(V1)}(\textbf{r}) = \omega_i^{(V2)}(\textbf{r})/(2\pi \sigma_i)
$$

 $\sigma_i$ is the hard-sphere diameter, $\delta (r)$ is the Dirac delta function, and $\theta (r)$ is the Heaviside step function. The vector weighted densities, $$\textbf{n}_{V1}$$ and $$\textbf{n}_{V2}$$, vanish in the limit of a bulk fluid.

## Hard-spheres in slit pores


We first apply the modified FMT to a one-component hard-sphere fluids confinde in slit pores. The external potential due to the slit walls is given by HS potential.

where $H$ stands for pore width, and $z$ is the distance from one of the slit walls. In this case, the weighted densities $n_2$ is

$$
  n_2(\textbf{r}) = \int \rho_i(\textbf{r'}) \omega^{(2)}(\textbf{r}-\textbf{r}')d\textbf{r'}
$$

Now, we defined $r''$:

$$
  \textbf{r}'' = \textbf{r}-\textbf{r}'
$$

so we have:

$$
  n_{2} = -\int \rho_i (\textbf{r}-\textbf{r}'') \omega^{(2)}(\textbf{r}'')d\textbf{r}''
$$

$$
  n_{2} = \int \rho_i (\textbf{r}-\textbf{r}'') \omega^{(2)}(\textbf{r}'')r''^2 dr'' d\cos \theta d \phi
$$

We know that the $\rho$ is only connection with the $z$, We set $y = z + r'' 	\cos \theta$ and $ \int d \phi = 2\pi  $. So we have $r'' d \cos \theta = d y$ :

$$
  n_2 = 2 \pi \int \rho_i (y) \omega^{(2)} (r'') r'' dr'' d y
$$

$$
  n_2 = 2 \pi \int \rho_i (y) \delta (\sigma /2 - r'') r''  d r'' d y
$$

Because $\int \delta (\sigma / 2 -r'') r'' dr''= \sigma /2$

$$
  n_2=\pi \sigma \int \rho_i (y) d y
$$

We set $r'' \cos \theta = z'$, So $y = z + z'$:

$$
  n_2(z) = \pi \sigma \int_{-\sigma/2}^{\sigma/2} \rho_i (z+z') d z'
$$

Now, we calculate the $n_{3}$

$$
 n_{3} = \int \rho_{i}( \mathbf{r'} ) \omega^{(3)} (\mathbf{r} - \mathbf{r'}) d \mathbf{r'}
$$

Because, $\omega^{(3)}$ is the volume area:

$$
 \omega^{(3)}(\mathbf{r}) = \theta (\omega/2 - r) 
$$

$$
 n_3 = \int \rho (\mathbf{r'}) \omega^{(3)} (\mathbf{r} - \mathbf{r'}) d \mathbf{r'}
$$

$$
 \label{eq:n_3-4}
 n_{3} = \int \rho(\mathbf{r'}) \theta (\sigma / 2 - r ) d \mathbf{r'}
$$

So, we can rewrite $n_3$ :

$$
 \label{eq:n_3-5}
 n_{3} = \int_{V} \rho(\mathbf{r}) d \mathbf{r}
$$

$$
 \label{eq:n_3-6}
 n_{3}(z) = \pi \int_{-\sigma/2}^{\sigma /2} \rho(z+z')  \left[ \left(\sigma /2\right)^2 - (z')^2 \right] d z'
$$

Finally, we calculate the $n_{V2}$:

$$
\label{eq:n-v2-1}
n_{V2} = \int \rho (\mathbf{r'}) \omega ^{(V2)} (\mathbf{r} - \mathbf{r'}) d \mathbf{r'}
$$

Because $\omega^{V2} = (\mathbf{r}/r) \delta (\omega/2 - r) $, we can rewritte $n_3$ as

$$
\label{eq:n-v2-2}
 n_{V2}(z) = \int_s e_{(\mathbf{r}-\mathbf{r'})} \rho(\mathbf{r'})  d \mathbf{r'}
$$

$$
  \label{eq:n-v2-3}
  n_{V2}(z) =  \mathbf{e_z} \int \rho (z+z') 2 \pi ( \sigma / 2 ) \sin \theta d\mathbf{z'} 
$$

We know $(\sigma / 2)\sin \theta$ is equal $z'$, so we have


  $$n_{V2}(z) =  2 \pi \mathbf{e_z} \int \rho (z+z') z' d\mathbf{z'} $$


* Yu, Y. X.; Wu, J., Structures of hard-sphere fluids from a modified fundamental-measure theory. *The Journal of Chemical Physics* **2002**, 117, 10156.