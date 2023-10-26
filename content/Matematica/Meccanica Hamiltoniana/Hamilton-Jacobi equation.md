# Hamilton-Jacobi equation

Is a general first order PDE of the form
$$
G(Du, u_t, u, x, t) = u_t + H(Du,x)=0
$$
call $y = (\mathbf{x},t)$ a $n+1$ vector, and $\mathbf{p} = (u_{x_1},\dots, u_{x_n}, u_t)$ the equation and $z = u(x,t)$ (this notation is used in the [[Metodo delle caratteristiche|method of characteristic]]) becomes
$$
G(p,z,y)=0
$$
so
$$
D_pG = (D_pH, 1)
$$
$$
D_y G = (D_xH,0)
$$
$$
G_z = 0
$$
so that the characteristic equations are
$$
\begin{cases}
\mathbf{\dot p}(s) = - (D_x H,0) \\
\dot z(s) = \mathbf{p}(s)\cdot (D_pH,1) \\
\mathbf{\dot y}(s) = (D_p H,1)
\end{cases}
$$
these equation for the time component means that we can idenitify the parameter $s$ with the time $t$. For the other coordinates
$$
\begin{cases}
\mathbf{\dot p}(s) = -D_x H \\
\mathbf{\dot x}(s) = D_p 
\end{cases}
$$
which are the _Hamilton equations_. We can ignore $z(s)$ since it doesn't appear in $H$.