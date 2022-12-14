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

where $P_{123}$ is the cyclic permutation. For arbitrary observable $O$ , we have $OP = PO$, it should be invariant to permutation operators.

Two special combinations of $\psi$ and its permutations are realized in nature: 

1. Totally symmetric: Bose-Einstein statistics, Boson, integer spin
2. Totally antisymmetric: Fermi-Dirac statistics, Fermion, half-inter spin

For a realistic wave function of a multi-particle system (identical particles), we have

$$
P_{ij}\psi(\dots,i,\dots,j,\dots)=
\pm
\psi(\dots,i,\dots,j,\dots)
$$

Label the basis states of an $N$-particle system

$$
\ket{i_1,\dots,i_N} = 
\ket{i_1}\cdots\ket{i_N}
$$

Symmetrized/Anti-symmetrized states

$$
\ket{n_1,n_2,\dots} = 
S_\pm \ket{i_1,\dots,i_N} = 
\frac{1}{\sqrt{N!}}
\sum_p (\pm1)^p
\ket{i_1,\dots,i_N}
$$

*Example.* 2-particle system

$$
S_+\ket{1,2} = 
\frac{1}{\sqrt{2}}
(\ket{1,2} + \ket{2,1})\\
S_-\ket{1,2} = 
\frac{1}{\sqrt{2}}
(\ket{1,2} - \ket{2,1})
$$

If the first-state in a 3-particle system occurs 2 times, then

$$
S_+\ket{1,2,1} = 
\frac{1}{\sqrt{3!}}
(\ket{1, 2, 1} + \ket{2, 1, 1} + \ket{1,1,2} + \ket{1,2,1}
+ \ket{2,1,1} + \ket{1,1,2})
= \frac{2}{\sqrt{3!}}(\ket{1,2,1} + \ket{2,1,1} + \ket{1,1,2})
$$

If the $$i$$th state occurs $n_i$ times ($n_i$ is called the occupation number), we need to include an extra normalization factor

$$
\frac{1}{\sqrt{\prod_i n_i!}}S_+\ket{i_i,\dots,i_N}
$$

Naturally, $\sum_i n_i = N$.

Define a complete and orthogonal set of states for arbitrary particle number $N$.
Completeness:

$$
\sum_{n_1,n_1,\dots}\ket{n_1,n_2,\dots}\bra{n_1,n_2,\dots} = 1
$$

Orthogonality: 

$$
\braket{n_1,n_2,\dots|n_1',n_2',\dots} = \delta_{n_1n_1'}\delta_{n_2n_2'}\cdots
$$

Name the vector space as the Fock space.

Creation and annihilation operator

$$
a_i^\dagger \ket{\dots,n_i,\dots} = \sqrt{n_i+1}\ket{\dots,n_i+1,\dots}
$$

where the extra factor $\sqrt{n_i+1}$ comes from $(n_i+1)!/n_i!$ (`check definition of annihilation operator` ). Hence

$$
a_i\ket{\dots,n_i,\dots} = \sqrt{n_i}\ket{\dots,n_i-1,\dots}
$$

$[a_i, a_j]=0$, $[a_i^\dagger, a_j^\dagger]=0$.

For $i\neq j$ we have $[a_i,a_j^\dagger]=0$.

$$
a_ia_j^\dagger
\ket{\dots,n_i,\dots,n_j,\dots}
=
\sqrt{n_j+1}\sqrt{n_i}\ket{\dots,n_i-1,\dots,n_j+1,\dots}
= 
a_j^\dagger a_i
\ket{\dots,n_i,\dots,n_j,\dots}
$$

For $i=j$, we have $[a_i,a_i^\dagger]=1$.

Define the vacuum state

$$
\ket{0} = \ket{0,\dots,0}
$$

1-particle

$$
a_i^\dagger \ket{0} = \ket{0,\dots,1,\dots}
$$

2-particle

$$
\frac{1}{\sqrt{2!}}(a_i^\dagger)^2 \ket{0} = 
\ket{0,\dots,2,\dots}
$$

Multi-particle state

$$
\ket{n_1,n_2,\dots} = 
\frac{1}{\sqrt{n_1!n_2!\cdots}}
(a_1^\dagger)^{n_1}(a_2^\dagger)^{n_2}\cdots\ket{0}
$$

Particle number operator $\hat{n}_i=a_i^\dagger a_i$

$$
\hat{n}_i\ket{n_1,n_2,\dots} = 
n_i\ket{n_1,n_2,\dots}
$$

Fermionic systems: using the Slater determinants

$$
S_-\ket{i_1,i_2,\dots,i_N} = 
\frac{1}{\sqrt{N!}}
\begin{vmatrix}
    \ket{i_1}_1 & \ket{i_1}_2 & \cdots & \ket{i_1}_N\\
    \ket{i_2}_1 & \ket{i_2}_2 & \cdots & \ket{i_2}_N\\
    \vdots & \vdots& \ddots & \vdots\\
    \ket{i_N}_1 & \ket{i_N}_2 & \cdots & \ket{i_N}_N\\
\end{vmatrix}
$$

Note that

$$
S_-\ket{i_1,i_2,\dots} = a_{i_1}^\dagger a_{i_2}^\dagger\ket{0}\quad
S_-\ket{i_2,i_1,\dots} = a_{i_2}^\dagger a_{i_1}^\dagger\ket{0}
$$

Using the antisymmetric property of Fermions, we have

$$
\{a_i^\dagger, a_j^\dagger\} = 0
$$

Creation operator in the two different basis $\ket{i}$ and $ket{\lambda}$.

$$
\ket{\lambda} = 
\sum_i \ket{i}\braket{i|\lambda}
= \sum_i a_i^\dagger\ket{0}\braket{i|\lambda}
$$

therefore 

$$
a_\lambda^\dagger = \sum_i a_i^\dagger \braket{i|\lambda}\quad
a_\lambda= \sum_i a_i\braket{\lambda|i}
$$

under position space $\mathbf{x}$

$$
a_\mathbf{x}^\dagger = \sum_i \braket{i|\mathbf{x}}a_i^\dagger
= \psi^\dagger(\mathbf{x})\quad
a_\mathbf{x} = \sum_i \braket{\mathbf{x}|i}a_i
= \psi(\mathbf{x})
$$

Note that

$$
[\psi(\mathbf{x}), \psi(\mathbf{x})]_\pm = 0\quad
[\psi(\mathbf{x}), \psi^\dagger(\mathbf{x}')]_\pm
= \sum_{ij}
\varphi_i(\mathbf{x})
\varphi_j^*(\mathbf{x}')[a_i, a_j^\dagger]_\pm
= \sum_{ij}
\varphi_i(\mathbf{x})
\varphi_j^*(\mathbf{x}')\delta_{ij}
= \delta^{(3)}(\mathbf{x}-\mathbf{x}')
$$

where $\varphi(\mathbf{x})=\braket{i|\mathbf{x}}$.

The kinetic energy (where $T_{ij}=\braket{i|T|j}$)

$$
\sum_{ij}T_{ij}a_i^\dagger a_j = 
\sum_{ij}\int\mathrm{d}\mathbf{x}\
a_i^\dagger\braket{i|\mathbf{x}}\braket{\mathbf{x}|T|j}a_j
= \int\mathrm{d}\mathbf{x}\ \psi^\dagger(\mathbf{x})
\left(-\frac{\hbar^2}{2m}\nabla^2\right)\psi(\mathbf{x})
$$

$n(\mathbf{x})=\psi^\dagger(\mathbf{x})\psi(\mathbf{x})$ (density operator?)

$$
N = \int\mathrm{d}\mathbf{x}\
n(\mathbf{x})
$$

Time relation of the field operator $\psi$

$$
\psi(\mathbf{x}, t) = 
e^{iHt/\hbar}\psi(\mathbf{x}, 0)e^{-iHt/\hbar}
$$

*Example.* Two-electron interaction

$$
V' = \frac{1}{2}\int\mathrm{d}\mathbf{x}\mathrm{d}\mathbf{x}'\
\psi^\dagger(\mathbf{x})\psi^\dagger(\mathbf{x}')V'(\mathbf{x}, \mathbf{x}')
\psi(\mathbf{x}')\psi(\mathbf{x})
$$

$\psi_\mathbf{k}(\mathbf{x})=e^{i\mathbf{k}\cdot\mathbf{x}}/N$.

$$
\int\mathrm{d}\mathbf{x}\ \varphi_\mathbf{k}^*(\mathbf{x})
\varphi_\mathbf{k}(\mathbf{x}) = \delta_{\mathbf{k}\mathbf{k}'}\quad
\int\mathrm{d}\mathbf{x}\ \varphi_\mathbf{k}^*(\mathbf{x})
\left(-\frac{\hbar^2}{2m}\nabla^2\right)
\varphi_\mathbf{k}(\mathbf{x}) = \delta_{\mathbf{k}\mathbf{k}'}
\mathbf{k}^2\frac{\hbar^2}{2m}
$$

Multi-fermion non-interacting system, Fermi sphere with radius $r$.
$p_F$ is the Fermi momentum

$$
\ket{\phi} = \prod_{|\mathbf{p}|<p_F}\prod_\sigma a^\dagger_{\mathbf{p}\sigma}
\ket{0}
$$

Hence

$$
\braket{\phi|a_{\mathbf{p}\sigma}^\dagger 
a_{\mathbf{p}\sigma}|\phi} = \begin{cases}
    1 & |\mathbf{p}|<p_F\\
    0 & \text{otherwise}    
\end{cases}
$$

$$
N =  \sum_{\mathbf{p},\sigma}n_{\mathbf{p}\sigma}
= \sum_{|\mathbf{p}|<p_F} 2
= \frac{2\cdot\frac{4}{3}\pi p_F^2}{(2\pi \hbar/L)^3}
= V\frac{p_F^3}{3\pi^2\hbar^3}\\
\Rightarrow
n = \frac{N}{V} = \frac{p_F^3}{4\pi^2\hbar^3}
$$

since the momentum is quantized by the smallest momentum $2\pi\hbar/L$, i.e., $|\mathbf{p}|=n\cdot 2\pi\hbar/L$. Fermi energy: $p_F^2/2m$

Generate the first excited state: two interpretations

1. Excite a fermion out of the Fermi sphere: $\ket{\phi_1} = a^\dagger_{\mathbf{k}'\sigma'} a_{\mathbf{k}\sigma}\ket{\phi}$
2. Let $b^\dagger_{\mathbf{k}\sigma} = a_{-\mathbf{k},-\sigma}$ which means the creation of a fermion hole

Single-particle correlation function

$$
G_\sigma(\mathbf{x}-\mathbf{x}') 
= \braket{\phi_0|\psi_\sigma^\dagger(\mathbf{x})\psi_{\sigma'}(\mathbf{x}')}
= \braket{\phi_0|\sum_{\mathbf{p},\mathbf{p}'}\frac{1}{V}
e^{-i\mathbf{p}\cdot\mathbf{x}+i\mathbf{p}'\cdot\mathbf{x}'}
a^\dagger_{\mathbf{p}\sigma}a_{\mathbf{p}'\sigma'}}
$$

Note that if $\mathbf{p}\neq\mathbf{p}'$, $\sigma\neq\sigma'$, the eigenkets will be orthogonal, hence

$$
G_\sigma(\mathbf{x}-\mathbf{x}') 
= 
\frac{\delta_{\sigma\sigma'}}{V}\sum_{\mathbf{p}}
e^{-i\mathbf{p}(\mathbf{x}-\mathbf{x}')}
\braket{\phi_0|a^\dagger_{p\sigma}a_{p\sigma}|\phi_0}
$$

Density-density correlation

$$
\braket{\phi_0|n_\sigma(\mathbf{x})n_{\sigma'}(\mathbf{x}')|\phi_0}
$$

Pair-distribution function, easy to see that it vanishes at $\mathbf{x}=\mathbf{x}'$ in fermion systems

$$
\braket{\phi_0|
\psi_\sigma^\dagger(\mathbf{x})\psi_{\sigma'}^\dagger(\mathbf{x}')
\psi_{\sigma'}(\mathbf{x}')\psi_\sigma(\mathbf{x})
|\phi_0}
= \left(\frac{n}{2}\right)^2g_{\sigma\sigma'}(\mathbf{x}-\mathbf{x}')
\\
= \frac{1}{V^2}\sum_{k,k'}\sum_{q,q'}e^{-i(k-k')\cdot x - i(q-q')\cdot x'}
\braket{\phi_0|a^\dagger_{k\sigma}a^\dagger_{q\sigma}
a_{q'\sigma'}a_{k'\sigma'}|\phi_0}
$$

1. $\sigma\neq\sigma'$, it equals to $n^2/4$
2. If $\sigma=\sigma'$, 2 options: $k'=k$ and $q'=q$, or $k=q$ and $k'=q'$


## Relativistic wave equations
Non-relativistic energy-mass relation: $E\rightarrow i\hbar\partial_t$, $\mathbf{p}=-i\hbar\nabla$

In relativistic energy mass relation, we have the Klein-gordon equation

$$
E^2 = \mathbf{p}^2c^2 + m^2c^4
\rightarrow
-\hbar^2\partial_t^2\psi = (-\hbar^2c^2\nabla^2 + m^2c^4)\psi
$$

where $m$ is the rest mass.

Define the 4-vector (contra-variant vector)

$$
\mathbf{x}^\mu = (ct, \mathbf{x})\in\mathbb{R}^4
\\
p^\mu = (p^0,\mathbf{p})\in\mathbb{R}^4\quad p^0 = \frac{E}{c}
$$

In the Euclidean space

$$
\mathrm{d}s^2 = 
(\mathrm{d}x_1)^2 +
(\mathrm{d}x_2)^2 +
(\mathrm{d}x_3)^2
$$

In Minkowskian space

$$
\mathrm{d}s^2 = 
(\mathrm{d}x_0)^2 -
(\mathrm{d}x_1)^2 -
(\mathrm{d}x_2)^2 -
(\mathrm{d}x_3)^2
$$

$\mathrm{d}s^2>0$: time-like separation; $\mathrm{d}s^2=0$: light-like separation; $\mathrm{d}s^2<0$: space-like separation.
Consider the diagonal metric.
`check: Minkowski metric`

$$
g^{\mu\nu} = \begin{bmatrix}
    1 & & & \\
    & -1 & & \\
    & & -1 & \\ 
    & & & -1
\end{bmatrix}=g_{\mu\nu}\\
\mathrm{p}_{\mu\nu}= g_{\mu\nu}\mathrm{p}^{\mu\nu}\\
\Rightarrow
\mathbf{p}^\mu\cdot\mathrm{p}_\mu = m^2c^2
$$

where $\mathbf{p}_\mu = g_{\mu\nu}\mathbf{p}^\nu$, sum over $\nu$.
Then

$$
\mathrm{d}s^2 = \mathrm{d}\mathbf{x}^\mu\mathrm{d}\mathbf{x}_\mu
$$

Hence $\mathrm{p}^\mu\cdot\mathrm{p}_\mu$ is a Lorentz invariant quantity.

Let

$$
\partial_\mu = \frac{\partial}{\partial x^\mu}
$$

Then the K-G equation can be written to 

$$
\left[
\partial_\mu\partial^\mu + \left(\frac{mc}{\hbar}\right)^2
\right]\psi = 0
$$

Set $c=\hbar=1$ for convenience.

$$
\begin{cases}
    \psi^*(\partial_\mu\partial^\mu + m^2)\psi &= 0\\
    \psi(\partial_\mu\partial^\mu + m^2)\psi^* &= 0
\end{cases}
\Rightarrow
\frac{\partial}{\partial t}\left[
    \frac{i}{2m}\left(
        \psi^*\partial_t\psi - \psi\partial_t\psi^*
    \right)
\right]
+ \nabla\cdot\frac{1}{2mi}(\psi^*\nabla\psi - \psi\nabla\psi^*) = 0\\
\partial_t\rho + \nabla\cdot\mathbf{j} = 0
$$

One problem is that in the relativistic system we have $\rho$ non-real, however in non-relativistic system we should have $\rho\geq 0$.

Let solution to K-G equation be in the following form, another problem is it allows negative energy

$$
\psi = e^{i(Et-\mathbf{p}\cdot\mathbf{x})},\quad
E = \pm\sqrt{\mathbf{p}^2+m^2}
$$

The Dirac equation

$$
i\hbar\partial_t\psi = (-i\alpha^k\partial_k + \beta_m)\psi = H\psi
$$

Note that if we apply another $i\partial_t$ to the Dirac equation we should recover the C-G equation

$$
-\partial_t^2\psi = 
\left[
    \cdots
\right]\psi
$$

Compare to the C-G equation, we have three constraint equations

$$
\begin{aligned}
    \alpha^k\alpha^j + \alpha^j\alpha^k &= 2\delta_{kj}\\
    \alpha^k\beta + \beta\alpha^k &= 0\\
    \beta^2 &= 0
\end{aligned}
$$

Hence $\alpha^k$ and $\beta$ are matrices.
$\alpha^k$, $\beta$ must be Hermitian matrices, then $\alpha_{ii}=\pm 1$,
$\beta_{jj}=\pm 1$. Note that

$$
\alpha^k\beta + \beta\alpha^k = 0
\Rightarrow
\alpha^k = -\beta\alpha^k\beta
\Rightarrow
\mathrm{tr}(\alpha^k) = 0
$$

In 2-dim space, not possible.
In 4-dim space, for example, we can define $\alpha^i$ and $\beta$ as

$$
\alpha=\begin{bmatrix}
    0 & \sigma^i\\
    \sigma^i & 0
\end{bmatrix}\quad
\beta = \begin{bmatrix}
    \mathbf{1} & 0\\
    0 & -\mathbf{1}
\end{bmatrix}
$$

4-dim spinor

$$
\psi=\begin{bmatrix}
    \psi_1\\ \psi_2 \\ \psi_3 \\ \psi_4
\end{bmatrix}
$$

Rewrite the equation

$$
-i\partial_0\psi - i\alpha^i\partial_i\psi + \beta^2 m\psi = 0
$$

Dirac matrices

$$
\gamma^0 = \beta,\ \gamma^i = \beta\alpha^i
\Rightarrow
(-i\gamma^\mu\partial_\mu + m)\psi = 0
$$

Properties of Dirac matrices

$$
\gamma^\mu \gamma^\nu + \gamma^\nu\gamma^\mu = 2g^{\mu\nu}\mathbf{1}
$$

Solution of Dirac equation

$$
i\partial_t\psi = \beta m\psi\text{ for an electron at rest}\\
i\partial_t
\begin{bmatrix}
    \psi_1 \\ \psi_2 \\ \psi_3 \\ \psi_4
\end{bmatrix}
= m\begin{bmatrix}
    \mathbf{1} & 0\\
    0 & -\mathbf{1}
\end{bmatrix}
\begin{bmatrix}
    \psi_1 \\ \psi_2 \\ \psi_3 \\ \psi_4
\end{bmatrix}
$$

Then 

$$
\begin{aligned}
\tilde{\psi}_1 &= e^{-imt}\mathbf{e}_1\\
\tilde{\psi}_2 &= e^{-imt}\mathbf{e}_2\\
\tilde{\psi}_3 &= e^{imt}\mathbf{e}_3\\
\tilde{\psi}_4 &= e^{imt}\mathbf{e}_4
\end{aligned}
$$

easy to show that the 3rd and 4th solutions have negative-energy solutions.

Consider the non-relativistic limit of Dirac equation, we should be able to reproduce the result from classical Schrodinger equation.
Separate $\psi$ to two 2-dim spinors

$$
\psi = 
\begin{bmatrix}
    \varphi \\ \chi
\end{bmatrix}
= e^{-imt}
\begin{bmatrix}
    \varphi_0 \\ \chi_0
\end{bmatrix}
$$

For electrons, the term $\mathbf{\sigma}\cdot\mathbf{B}$ appears naturally according to the Dirac equation (in classical case we need to add this by hand anyway). `check the derivation`

$$
i\partial_t \varphi=
\left[
\frac{\mathbf{p}^2}{2m} - \frac{e}{2m}(\mathbf{L}+2\mathbf{S})\cdot\mathbf{B}
+ \frac{e^2}{2m}\mathbf{A}^2 = e\Phi
\right]\varphi
$$

Magnetic moment $\mathbf{\mu}=\frac{e^2}{2m}(\mathbf{L}+2\mathbf{S})$.

Lorentz transformation. Lorentz boost

$$
\begin{aligned}
\mathbf{x} = A\mathbf{x}\quad
\begin{bmatrix}
    t'\\ z'
\end{bmatrix}
=
\begin{bmatrix}
    B_{11} & B_{12}\\
    B_{21} & B_{22}
\end{bmatrix}
\begin{bmatrix}
    t \\ z
\end{bmatrix}
=
\begin{bmatrix}
    \gamma & -\beta\gamma\\
    -\beta\gamma & \gamma
\end{bmatrix}
\begin{bmatrix}
    t \\ z
\end{bmatrix}
\end{aligned}
$$

where $\gamma=1/\sqrt{1-v^2/c^2}$.
Note that the Lorentz boost can be written in 

$$
\begin{bmatrix}
    \gamma & -\beta\gamma\\
    -\beta\gamma & \gamma
\end{bmatrix} = 
\begin{bmatrix}
    \cosh\alpha & -\sinh\alpha\\
    -\sinh\alpha & \cosh\alpha
\end{bmatrix}
$$

Homogeneous Lorentz transformation: 3 rotations among spatial axes, 3 rotation between 1 spacial axis and time axis, overall 6 degrees of freedom. Inhomogeneous Lorentz transformations: 10 degrees of freedom. `check the number of DOF`

$$
\mathbf{x}^\mu = (t, x, y, z)\quad
{\mathbf{x}'}^\mu = \Lambda^\mu_\nu\mathbf{x}^\nu
$$

$$
\mathrm{d}t' = \gamma\mathrm{d}t - \beta\gamma\mathrm{d}z,\
\mathrm{d}z' = \gamma\mathrm{d}z - \beta\gamma\mathrm{t}
\Rightarrow
\mathrm{d}z = \beta\mathrm{d}t,\
\mathrm{d}t' = \gamma\mathrm{d}t - \beta^2\gamma\mathrm{d}t
= \sqrt{1-\beta^2}\mathrm{d}t
$$

$$
\mathrm{d}s^2 
= \mathrm{d}x^\mu\mathrm{d}x_\mu
= \mathrm{d}x'^\mu\mathrm{d}x'_\mu
= \Lambda^\mu_\nu dx^\nu g_{\mu\rho}\Lambda^\rho_\sigma dx^\sigma
\Rightarrow
\Lambda^\mu_\nu g_{\mu\rho}\Lambda^\rho_\sigma = g_{\nu\sigma}
$$

Assume $\psi'(x')$ and $\psi(x)$ are related by a linear transformation

$$
\psi'(x') = S(\Lambda)\psi(x) = S(\Lambda)\psi(\Lambda^{-1}x')\\
(-i\partial_\mu + m)\psi(x) = 0\Rightarrow
(-i\partial_\mu' + m)\psi'(x') = 0
$$

$$
\left(
-i\gamma^\mu\frac{\partial}{\partial x^\mu} + m
\right)\psi(x) 
= \left(-i\gamma^\mu\frac{\partial}{\partial x'^\nu}
+ m
\right)\psi(x)
= \left(
-i\gamma^\mu\Lambda^\nu_\mu\partial_\nu' + m 
\right)S^{-1}(\Lambda)\psi'(x') = 0\\
\Rightarrow
-iS\gamma^\mu\Lambda_mu^\nu\partial_\nu' S^{-1}\psi'(x') + m\psi'(x')=0\quad
S^{-1}\gamma^\nu S = \Lambda_\mu^\nu \gamma^\mu
$$

Example for a spinor (period $\theta=4\pi$).

$$
S(\Lambda) = 
e^{-\frac{i}{4}\sigma_{\mu\nu}\omega^{\mu\nu}}\quad
\psi'(x') = S(\Lambda)\psi(x)
= (\cos(\theta/2) + i\sigma^{12}\sin(\theta/2))\psi(x)
$$

Derive the most basic form of solutions of Dirac's equation

$$
(-i\gamma^\mu\partial_\mu + m)\psi = 0
$$

In the rest frame

$$
\psi^+(x) = U_0 e^{-imt}\quad
\psi^-(x) = V_0 e^{-imt}
$$

In the moving frame, $k^2=m^2$.

$$
\psi^+(x) = U(k)e^{-ikx}\quad
\psi^-(x) = V(k)e^{ikx}
$$

$U$ and $V$ have to satisfy $(k'-m)U(k)= 0 $ and $(k'+m)V(k)=0$, $k'$ stands for $k$-slash.

$$
U(k) = (k' + m)U_0\quad
V(k) = (k' - m)V_0
$$

$$
U(k) = 
\begin{bmatrix}
    \sqrt{\frac{E+m}{2m}}\chi_\gamma\\
    \frac{\sigma\cdot k}{\sqrt{2m(E+m)}}\chi_\gamma
\end{bmatrix}\quad
V(k) = 
\begin{bmatrix}
    \frac{\sigma\cdot k}{\sqrt{2m(E+m)}}\chi_\gamma\\
    \sqrt{\frac{E+m}{2m}}\chi_\gamma
\end{bmatrix}
$$

Time evolution, start with a positive energy spinor

$$
\psi(t=0, x) \propto 
e^{ip_0\cdot x-x^2/4x_0^2}\begin{bmatrix}
    \varphi\\ 0
\end{bmatrix}
$$

The general solution at time $t$ can be written as

$$
\psi(t, x) = 
\int\frac{d^3}{(2\pi)^3}\sum_\gamma
[
    b(p, \gamma)U_\gamma (P)e^{-ip\cdot x} + 
    d^*(p, \gamma)V_\gamma(p)e^{ip\cdot x}
]
$$

where $b$ and $d^*$ are expansion parameters.

Do Fourier transform `check textbook`

Start from a positive energy state, time evolution will generate negative energy state. Dirac postulated that negative energy are fully occupied. `check Dirac sea`

## Field theory

Find a Lagrangian generating the correct EOM `(Lagrangian density?)`

$$
\mathcal{L} =\mathcal{L}(\phi_i(x), \partial_\mu\phi_i(x))
$$

No longer to be unitary, since the time evolution operator will have exponentially decay factor $e^{-iHt}\rightarrow e^{-i(H-i\delta)t}$.

In non-relativistic case we have $[x_i,p_j]=i\delta_{ij}$.
Define the conjugate momentum

$$
\pi_i = \frac{\partial \mathcal{L}}{\partial \dot{\phi}_i}
$$

Define the action

$$
S = \int d^4 x\ \mathcal{L}
$$

EOM is determined by requiring $\delta S=0$.

$$
\delta S 
= 
\int d^4 x
\left[
    \frac{\partial\mathcal{L}}{\partial\phi_i}\delta\phi_i
    + \frac{\partial L}{\partial (\partial_\mu\phi_i)}\delta(\partial_\mu\phi_i)
\right]
= 
\int d^4 x
\left[
    \frac{\partial\mathcal{L}}{\partial\phi_i}
    - \partial_\mu\frac{\partial L}{\partial (\partial_\mu\phi_i)}
\right]\delta\phi_i + \text{surface term}
= 0
$$

Euler-Lagrange equation

$$
\frac{\partial\mathcal{L}}{\partial\phi_i}
- \partial_\mu\frac{\partial L}{\partial (\partial_\mu\phi_i)}
= 0
$$

Commutation relations

$$
[\phi_i(x, t), \pi_j(x', t)] = 
i\delta_{ij}\delta(x-x')
$$

*Example.* A real scalar field

$$
\mathcal{L} = 
\frac{1}{2}(\partial^\mu\phi\partial_\mu\phi - m^2\phi^2)\quad
\frac{\partial\mathcal{L}}{\partial\phi} = -m^2\phi\quad
\partial_\mu\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)} 
= \partial^\mu\partial_\mu\phi
$$

EL equation becomes KG equation. $\pi=\dot{\phi}$.

$$
[\phi(x, t), \dot{\phi}(x', t)] = 
i\delta(x-x')
$$

$$
\phi(x) = 
\int\frac{d^3k}{(2\pi)^3}\frac{1}{\sqrt{2k^0}}
[a_ke^{-ik\cdot x} + a_k^\dagger e^{ik\cdot x}]
$$

$[a_k,a_{k'}^\dagger]=\delta_{kk'}$. Hence $\phi=\phi^\dagger$.

How to calculate the correlation function $\braket{0|\phi(x)\phi(y)0}$?

$$
\braket{0|\phi(x)\phi(y)0} 
= 
\int_\mathbb{C}
\frac{d^4 k}{(2\pi)^4}\frac{e^{-ik(x-y)}}{k^2-m^2}
\sim
\int\frac{d^3 k}{(2\pi)^3}\frac{1}{2k^0}e^{-ik(x-y)}
$$

Physical situation: positive-energy propagate forward in time. `check Feymann propagator`

