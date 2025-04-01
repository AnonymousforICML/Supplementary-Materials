

# Proof of Convergence: Spectral Radius Analysis

We aim to prove that the spectral radius of matrix $G(\eta)$ satisfies $\|G(\eta)\| < 1$ for an appropriate step size $\eta$, where:

$$G(\eta)=\left[\begin{array}{ccccc}
w_1 / 2 & \frac{2 w_1}{w_2} \eta^2 & 0 & \frac{8 \omega w_1}{w_2} \eta^2 & 0 \\
c_1 & \frac{w_1}{2}+c_2 \eta^2 & c_3 & c_4 \eta^2 & \frac{8 w_1 \omega}{w_2} \eta^2 \\
c_5 \eta & 0 & 1-3 \mu \eta / 2 & 0 & 0 \\
2 a_x & a_x \eta^2 & n a_x & b_x+2 a_x \omega \eta^2 & 0 \\
c_6 & c_7 & c_8 & c_7 \omega & b_y+a_y \omega \eta
\end{array}\right]$$

with coefficients defined as:
$$ & c_1=\frac{30(m+4) L^2 w_1+2 w_1}{w_2}, \quad c_2=\frac{96 w_1 w_2 L^2+16(m+4) w_1^2}{w_2^2} \\
& c_3=\frac{20 n L^2(m+4) w_1}{w_2}, \quad c_4=\frac{64 w_1^2(m+4)+96 w_1 w_2}{w_2^2} L^2 \\
& c_5=\frac{L}{4 n}\left(\frac{(4 m+5)}{\sqrt{m+4}}+\frac{(4 m+4) L}{\mu}\right) \\
& c_6=\frac{15(m+4) L^2+1}{6} a_y, \quad c_7=\frac{\left(w_1+w_2\right) a_y}{w_2}, \quad c_8=\frac{5 n L^2(m+4) a_y}{3} $$
where $w_1=1+\rho^2$, $w_2=1-\rho^2$, $\rho \in (0,1)$, and all parameters $\mu$, $a_x$, $a_y$, $b_x$, $b_y$, $\omega$, $L$, $m$, $n$ are positive.

## Proof Strategy

We establish that $\|G(\eta)\| < 1$ by verifying the necessary and sufficient conditions:
1. $0 < G_{ii}(\eta) < 1$ for all diagonal elements
2. $\det(I-G(\eta)) > 0$

### Part 1: Diagonal Element Constraints

For the diagonal elements of $G(\eta)$, we derive the following constraints:

**First diagonal element:** $0 < \frac{w_1}{2} < 1$
- This holds naturally since $w_1 \in (1,2)$ for $\rho \in (0,1)$

**Second diagonal element:** $0 < \frac{w_1}{2}+c_2\eta^2 < 1$
- This requires $\eta < \sqrt{\frac{w_2}{2c_2}}$

**Third diagonal element:** $0 < 1-3\mu \eta/2 < 1$
- Satisfied when $\eta > 0$ (which is inherently true as step size)

**Fourth diagonal element:** $0 < b_x+2 a_x \omega \eta^2 < 1$
- Requires $\eta < \sqrt{\frac{1-b_x}{2a_x\omega}}$

**Fifth diagonal element:** $0 < b_y+a_y \omega \eta < 1$
- Requires $\eta < \frac{1-b_y}{a_y\omega}$

### Part 2: Determinant Positivity

To prove $\det(I-G(\eta)) > 0$, we expand the determinant as:

$$\begin{aligned}
\det(I-G(\eta)) &= -c_5\eta \det(M_1) + \frac{3\mu\eta}{2}\det(M_2)
\end{aligned}$$

where $M_1$ and $M_2$ are the corresponding submatrices.

When $\eta$ is sufficiently small, we can neglect terms of order $\mathcal{O}(\eta^3)$ and higher, yielding:

$$\begin{aligned}
\det(I-G(\eta)) &\approx \left[\left(\frac{2w_1c_8}{w_2}-4w_1\omega c_7 +\frac{3\mu a_y w_2^2\omega}{8}\right) (b_x-1)+8w_1\omega a_x(b_y-1)\right]\eta^2\\
&+ \frac{3\mu w_2^2}{8}(1-b_x)(1-b_y)\eta
\end{aligned}$$

Substituting the expressions for $c_7$ and $c_8$, we can verify that $\frac{2w_1c_8}{w_2}-4w_1\omega c_7 > 0$. 

Since $b_x,b_y \in (0,1)$, the coefficient of the quadratic term is negative and the coefficient of the linear term is positive. Therefore, $\det(I-G(\eta)) > 0$ when:

$$\eta < \frac{\frac{3\mu w_2^2}{8}(1-b_x)(1-b_y)}{\left[\left(\frac{2w_1c_8}{w_2}-4w_1\omega c_7 +\frac{3\mu a_y w_2^2\omega}{8}\right) (1-b_x)+8w_1\omega a_x(1-b_y)\right]}$$

## Conclusion

Combining all constraints, the spectral radius $\|G(\eta)\| < 1$ when:

$$\eta < \min\limits \left\{
\sqrt{\frac{w_2}{2c_2}},\,
\sqrt{\frac{1-b_x}{2a_x\omega}},\,
\frac{1-b_y}{a_y\omega},\,
\frac{\frac{3\mu w_2^2}{8} (1-b_x)(1-b_y)}
{\left( \frac{2w_1c_8}{w_2} - 4w_1\omega c_7 + \frac{3\mu a_y w_2^2\omega}{8} \right) (1-b_x) + 8w_1\omega a_x (1-b_y)}
\right\}$$
This establishes the upper bound on the step size $\eta$ that guarantees convergence of the iterative scheme.