# PHY5410 FA22 Notes

## Time-dependent perturbation theory `TODO: check derivation`
Form of solution

$$
\ket{\psi, t}_I =
\ket{\psi, t_0}_I
+ \frac{1}{i\hbar}\int_{t_0}^t\mathrm{d}t'\ V_I(t')\braket{\psi, t_0}_I
+ \frac{1}{(i\hbar)^2}\int_{t_0}^t \mathrm{d}t'\ 
\int_{t_0}^{t'}\mathrm{d} t''\ V_I(t')V_I(t'')\ket{\psi, t_0}
+ \cdots
$$

Transition probability amplitude

$$
\braket{n,t|\psi,t} = \braket{n|\psi,t}_I = c_i^{(0)} + c_i^{(1)} + \cdots
$$

Where 

$$
\begin{aligned}
    c_i^{(0)} &= 1\\
    c_i^{(1)} &= \lim_{t_0\rightarrow-\infty}
    \frac{1}{i\hbar}\braket{i|V|i}
    \int_{t_0}^t e^{\eta t}\mathrm{d}t\ 
    = \frac{1}{i\hbar\eta}
    \braket{i|V|i}e^{\eta t}\\
    c_i^{(2)} &= \lim_{t_0\rightarrow-\infty}
    -\frac{1}{\hbar^2}\sum_m\int_{t_0}^t\mathrm{d}t'\
    \int_{t_0}^t\mathrm{d}t''\
    \braket{i|V_I(t')|m}\braket{m|V_I(t'')|i}\\
    &= \lim_{t_0\rightarrow-\infty}
    \int_{t_0}^t\mathrm{d}t'\
    e^{i\omega_{im}t'+\eta t'}
    \int_{t_0}^t\mathrm{d}t''\
    e^{i\omega_{mi}t''+\eta t''}\\
    &= -\frac{1}{\hbar^2}\frac{e^{2\eta t}}{2\eta^2}
    |\braket{i|V|i}|^2
    + \frac{1}{i\hbar}\sum_{m\neq i}
    \frac{|\braket{m|V|i}|^2e^{2\eta t}}{2\eta (E_i-E_m + i\hbar\eta)}
\end{aligned}
$$

note that $\omega_{ij}=E_i-E_j$.
Let $c_i=c_i^{(0)} + c_i^{(1)} + \cdots$, (`check` ignoring higher-order terms?) then

$$
\begin{aligned}
    \frac{\dot{c}_i}{c_i} &= \cdots
    = \frac{1}{i\hbar}\braket{i|V|i}
    + \frac{1}{i\hbar}\sum_{m\neq i}
    \frac{|\braket{m|V|i}|^2}{E_i-E_m+i\hbar\eta}\\
    \Rightarrow
    c_i(t) &= Ne^{\frac{\Delta_i t}{i\hbar}}\\
    \Delta_i &= \braket{i|V|i} 
    + \sum_{m\neq i}\frac{|\braket{m|V|i}|^2}{E_i-E_m+i\hbar\eta}\\
    c_i^2(t) &= e^{-2|\Im\Delta_i|t}\sim \text{decay width $\Gamma_i$}
\end{aligned}
$$

as $\eta\rightarrow 0$. Since

$$
\lim_{\epsilon\rightarrow 0}
\frac{1}{x+i\epsilon}
= 
\lim_{\epsilon\rightarrow 0}
\frac{x}{x^2+\epsilon^2} - i\frac{\epsilon}{x^2 + i\epsilon^2}
= \frac{1}{x} - i\pi\delta(x)
$$

## Scattering problem
Wave propagating with (`check what is k`) $\mathbf{k}$.
Wave packet representation, where $a_{\mathbf{k}}$ centered around $\mathbf{k}=\mathbf{k}_0$

$$
\psi_0(\mathbf{x}, t_0) 
= \int\frac{\mathrm{d}^3\mathbf{k}}{8\pi^3}
e^{i\mathbf{k}\cdot\mathbf{x}}
a_{\mathbf{k}}
$$

Need to solve 

$$
\left[
-\frac{\hbar^2}{2m}\nabla^2 + V(\mathbf{x})
\right]\psi_{\mathbf{k}}(\mathbf{x})
= E_{\mathbf{k}}\psi_\mathbf{k}(\mathbf{x})\quad
E_k = \frac{\hbar^2\mathbf{k}^2}{2m}
$$

Simplify the equation, and use Green's function to solve the equation
`check Green's function`

$$
\begin{aligned}
(\nabla^2 + k^2) \psi_{\mathbf{k}}(\mathbf{x}) 
&= \frac{2m}{\hbar^2}V(\mathbf{x}) \psi_{\mathbf{k}}(\mathbf{x})\\
(\nabla^2 + k^2)G(\mathbf{x}) &= \delta(\mathbf{x})\\
\Rightarrow
\psi_{\mathbf{k}}(\mathbf{x}) &= 
e^{i\mathbf{k}\cdot\mathbf{x}}
+ \frac{2m}{\hbar^2}\int\mathrm{d}\mathbf{x}\ G(\mathbf{x}-\mathbf{x}')
V(\mathbf{x}')\psi_\mathbf{k}(\mathbf{x}')
\end{aligned}
$$

Solve the Green's function by moving to the momentum space

$$
\begin{aligned}
\int\mathrm{d}\mathbf{q}e^{i\mathbf{q}\cdot\mathbf{x}}
(\nabla^2 + k^2)G(\mathbf{x}) &= \int\mathrm{d}\mathbf{q}\
e^{-i\mathbf{q}\cdot\mathbf{x}}\\
(k^2-q^2)G(\mathbf{q}) &= 1\\
\Rightarrow
G(\mathbf{x}) &= \frac{1}{8\pi^3}
\int\mathrm{d}\mathbf{q}\frac{e^{i\mathbf{q}\cdot\mathbf{x}}}{k^2-q^2}
= \frac{i}{4\pi r^2}\int\mathrm{d}q\
\frac{e^{iqr}}{q^2-k^2}
\end{aligned}
$$

$G(\mathbf{x})$ diverges around $q=\pm k$, then
the real-axis integral would be given by the residue
`check residue theory for calculating divergent/contour integrals`

$$
\begin{aligned}
G_\pm(\mathbf{x}) 
&= \frac{i}{4\pi r^2}
\int\mathrm{d}q\ \frac{e^{iqr}}{q^2-k^2\pm i\epsilon}\\
\Rightarrow
q &= \pm (k+i\epsilon)\text{ for } G_+\\
q &= \pm (k-i\epsilon)\text{ for } G_-\\
\end{aligned}
$$

Calculate the integral with $\Im q > 0$ `check`, we get the expression of the Green's function. Retarded Green's function/advanced Green's function.

$$
\begin{aligned}
G_\pm(r) &= -\frac{e^{\pm ikr}}{4\pi r}\\
\Rightarrow
\psi_{\mathbf{k}} &= e^{i\mathbf{k}\cdot\mathbf{x}}
- \frac{m}{2\pi\hbar^2} \frac{e^{ik|\mathbf{x}-\mathbf{x}'|}}{|\mathbf{x}-\mathbf{x}'|}V(\mathbf{x}')\psi_\mathbf{k}(\mathbf{x}')
\end{aligned}
$$

Let $|\mathbf{x}|\gg|\mathbf{x}|$, then

$$
k|\mathbf{x}-\mathbf{x}'| 
= k\sqrt{\mathbf{x}^2-2\mathbf{x}\cdot\mathbf{x}' + {\mathbf{x}'}^2}
\approx
k\sqrt{\mathbf{x}^2-2\mathbf{x}\cdot\mathbf{x}'}
= kr - k\frac{\mathbf{x}\cdot\mathbf{x}'}{r}
$$

Hence

$$
\psi_\mathbf{k} = e^{i\mathbf{k}\cdot\mathbf{x}} 
+ \frac{e^{ikr}}{r} f_\mathbf{k}(\theta,\phi);\quad
f_\mathbf{k} = -\frac{m}{2\pi\hbar^2}\int\mathrm{d}\mathbf{x}'\
e^{-i\mathbf{k}\cdot\mathbf{x}'}V(\mathbf{x}')\psi_\mathbf{x}(\mathbf{x}')
$$

$f_\mathbf{k}$ is called the scattering amplitude.

Rewrite $\psi_0(\mathbf{x}, t_0)$ as the sum of $\psi_\mathbf{k}(\mathbf{x})$ to get the further time evolution of $\psi_0$.

$$
\psi_0(\mathbf{x}, t_0) =
\int\frac{\mathrm{d} \mathbf{k}}{8\pi^3}
\left[
\psi_\mathbf{k} + 
\frac{m}{2\pi\hbar^2}\int\mathrm{d}\mathbf{x} \frac{e^{ik|\mathbf{x}-\mathbf{x}'|}}{|\mathbf{x}-\mathbf{x}'}V(\mathbf{x}')\psi_\mathbf{k}(\mathbf{x}')
\right]
$$

Suppose a sharp incoming wave packet, $k_0\gg |\mathbf{k}-\mathbf{k}_0|$, then
`check why vanishes`

$$
\int\frac{\mathrm{d}\mathbf{k}}{8\pi^3}
a_\mathbf{k}e^{ik|\mathbf{x}-\mathbf{x}'|}\psi_\mathbf{k}(\mathbf{x}')
\approx 
\int\frac{\mathrm{d}\mathbf{k}}{8\pi^3}
a_\mathbf{k}e^{i\frac{\mathbf{k}\cdot\mathbf{k}_0}{k_0}|\mathbf{x}-\mathbf{x}'|}
\psi_{\mathbf{k}_0}(\mathbf{x})
= 
\psi_0(\frac{\mathbf{k}_0}{k_0}|\mathbf{x}-\mathbf{x}'|, t_0) = 0
$$

Therefore we can calculate the time evolution

$$
\psi(\mathbf{x}, t) = 
\int \frac{\mathrm{d}\mathbf{k}}{8\pi^3}
\phi_\mathbf{k}(\mathbf{x}) a_\mathbf{k}
e^{-iE_\mathbf{k}(t-t_0)/\hbar}
$$

*Example:* the scattering cross section $\sigma$ `check this concept`

$$
\mathrm{d}N(\Omega)\propto 
\sigma j_\text{in}\mathrm{d}\Omega
\Rightarrow
\frac{\mathrm{d}\sigma}{\mathrm{d}\Omega}\sim
\frac{\mathrm{d}N(\Omega)}{j_in\mathrm{d}\Omega}
$$

where $j_\text{in}$ is the flux density/intensity of incoming particles.
While

$$
\mathrm{d}_N(\Omega)\sim j_{\text{out}}r^2\mathrm{d}\Omega
$$

Calculate the changing rate of probability density $\psi^*\psi$

$$
\frac{\partial}{\partial t} \psi^*\psi = 
\nabla\cdot \mathbf{j}\quad
\mathbf{j} = \frac{\hbar}{2m i}(\psi^*\nabla \psi - \psi\nabla\psi^*)
$$

Note that

$$
\int \mathrm{d}^3\mathbf{x}\frac{\partial}{\partial t}\psi^*\psi = 
\int \mathrm{d}^3\mathbf{x}\ \nabla\cdot\mathbf{j} = 
\oint \mathbf{j}\cdot\mathbf{n}\mathrm{d}\sigma
$$

Let 

$$
\psi_0 = \int\frac{\mathrm{d}^3\mathbf{k}}{8\pi^3} e^{i\mathbf{k}\cdot\mathbf{x}}a_\mathbf{k}
$$

Let $\psi_0$ centered on $\mathbf{k}_0$ (approximate $\mathbf{k}$ by $\mathbf{k}_0$), therefore we have approximation for $j_\text{in}$ and $j_\text{out}$ `check jout`

$$
\mathbf{j}_\text{in} = \frac{h\mathbf{k}_0}{m}|\psi_0|^2\quad
\mathbf{j}_\text{out}  = \frac{\hbar}{m}
\Im\left(
    \frac{f^*}{r}\psi_0(\hat{\mathbf{k}}_0r,t)^*
    \frac{\partial}{\partial r}\frac{f}{r}\psi_0(\hat{\mathbf{k}}_0r, t)
\right)
$$

Plane wave expansion when $r\rightarrow \infty$

$$
e^{i\mathbf{k}\cdot\mathbf{x}} = 
e^{ik_zz} \approx
\frac{1}{2ik}\sum_{l=0}^\infty
(2l+1)\left[
\frac{e^{ikr}}{r} - \frac{e^{-(ikr-l\pi)}}{r}
\right]P_l(\cos\theta)
$$

Introduce phase shift

$$
\psi_\mathbf{k}(\mathbf{x}) = 
\frac{1}{2ik}\sum_{l=0}^\infty
(2l+1)\left[
\frac{e^{ikr}}{r} - \frac{e^{-(ikr-l\pi+\delta_l)}}{r}
\right]P_l(\cos\theta) = 
\frac{1}{2ik}\sum_{l=0}^\infty
(2l+1)
\frac{e^{2i\delta_l}-1}{2ik}
P_l(\cos\theta)\frac{e^{ikr}}{r}\\
\Rightarrow
f_l = \frac{e^{2i\delta_l}-1}{2ik} 
= \frac{e^{i\delta_l}\sin\delta_l}{k}\sim \frac{\delta_l}{k}
$$

Hence 

$$
\frac{\mathrm{d}\sigma}{\mathrm{d}\Omega} = 
|f_\mathbf{k}(\theta)|^2 = 
\frac{1}{k^2}\sum_{l,l'}(2l+1)(2l'+1)\cdots
\Rightarrow
\sigma = \sum_l \frac{4\pi}{k^2}(2l+1)\sin^2\delta_l
$$

Optical theorem

$$
\sigma = \frac{4\pi}{k}\Im f_\mathbf{k}(\theta=0)
$$

If the potential impact on the all partial wave components is small, then we have the Born approximation

$$
f_\mathbf{k}(\theta) = 
-\frac{m}{2\pi\hbar^2}\int\mathrm{d}\mathbf{x}\
e^{i(\mathbf{k}-\mathbf{k}')\cdot\mathbf{x}}
V(\mathbf{x}) = 
-\frac{m}{2\pi\hbar^2}\tilde{V}(\mathbf{k}-\mathbf{k}')
$$

where $\mathbf{k}'=k\mathbf{x}/r$. If $V(x)=ae^{-\mu r}/r$, then

$$
\tilde{V}(\mathbf{p}) = \frac{4\pi a}{p^2+\mu^2}
\Rightarrow
\tilde{V}(\mathbf{k}-\mathbf{k}') = 
\frac{4\pi a}{|\mathbf{k}-\mathbf{k}'|^2 + \mu^2}
$$

Since

$$
(\mathbf{k}-\mathbf{k}')^2 = 
\mathbf{k}^2 + {\mathbf{k}'}^2 - 2\mathbf{k}\mathbf{k}'\cos\theta
= \left(2k\sin\frac{\theta}{2}\right)^2
$$

For Coulomb potential, we can let $\mu\rightarrow 0$ in the former case, then

$$
\frac{\mathrm{d}\sigma}{\mathrm{d}\Omega} = 
\frac{(Ze^2)}{16E_k^2\sin^4\frac{\theta}{2}}
$$

Example: solid sphere

$$
\delta_l = \arctan\frac{j_l(kr_0)}{n_l(kr_0)}
$$

as $k\rightarrow 0$

$$
\delta_l\sim (kr_0)^{2l+1}
$$


## Identical particles
Permutation operators $P_{ij}$. For a 2-particle system we have a group $\{1, P_{12}\}$. For a 3-particle system we have 

$$
1, P_{12}, P_{13}, P_{23}, P_{123}=P_{13}P_{12}, P_{132}=P_{12}P_{13}
$$

where $P_{123}$ is the cyclic permutation.


