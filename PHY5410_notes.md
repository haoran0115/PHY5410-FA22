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

as $\eta\rightarrow 0$.
Since

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
\psi(\mathbf{x}, t_0) 
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

$$
\begin{aligned}
(\nabla^2 + k^2) \psi_{\mathbf{k}}(\mathbf{x}) 
&= \frac{2m}{\hbar^2}V(\mathbf{x}) \psi_{\mathbf{k}}(\mathbf{x})\\
(\nabla^2 + k^2)G(\mathbf{x}) &= \delta(\mathbf{x})\\
\Rightarrow
\psi_{\mathbf{k}}(\mathbf{x}) &= 
e^{i\mathbf{k}\cdot\mathbf{x}}
+ \frac{2m}{\hbar^2}\int\mathrm{d}\mathbf{x} G(\mathbf{x}-\mathbf{x}')
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
`check residue theory for calculating divergent integrals`

$$
\begin{aligned}
G_\pm(\mathbf{x}) &= \frac{i}{4\pi r^2}
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
\phi_{\mathbf{k}} &= e^{i\mathbf{k}\cdot\mathbf{x}}
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
f_\mathbf{k} = -\frac{m}{2\pi\hbar^2}\int\mathrm{d}\mathbf{x}\
e^{-i\mathbf{k}\cdot\mathbf{x}}V(\mathbf{x}')\psi_\mathbf{x}(\mathbf{x}')
$$

$f_\mathbf{k}$ is called the scattering amplitude.


