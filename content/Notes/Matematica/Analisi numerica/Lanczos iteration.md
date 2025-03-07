When we have a symmetric matrix $A$, the [[Arnoldi iteration]] can be greatly optimized, since $V_k^TAV_k = H_k$ and the left side is symmetric, the matrix $H_k$ (which is upper hessember) is now forced to be tri-diagonal.

So when computing the overlaps $h_{ij}$, which for the arnoldi iteration are $k$, we need only the previous.

It is custom to change the notation used in the aronldi iteration:
$$
\alpha_k := h_{k,k} \qquad \beta_k := h_{k+1,k} = h_{k,k+1}
$$
The orthogonal matric is named $Q_k$, the tri-diagonal matrix $T_k$.

The procedure is:
```
function [V, H] = GSlanczos(A, v, k)
	% Inputs:
	% A: n x n symmetric matrix
	% v: n x 1
	% k: number of iterations
	%
	% Outputs:
	% Q: n x (k+1) matrix of Lanczos basis vectors
	% T: (k+1) x k tri-diagonal matrix 
	
	% Initialize variables
	n = size(A, 1);
	V = zeros(n, k+1);
	H = zeros(k+1, k);
	
	% Set initial vector
	V(:,1) = v / norm(v);
	
	% Iterate
	for i = 1:k
		% Compute next vector
		
		w = A * V(:,i);
		
		% Orthogonalize w
		
		for j = 1:i
		
		H(j,i) = V(:,j)' * w; %computing overlap
		
		w = w - H(j,i) * V(:,j); %removing overlap
		
		end
		
		% Normalize w
		
		H(i+1,i) = norm(w);
		
		if H(i+1,i) == 0 %check breakdown
		
		return
		end
		
		V(:,i+1) = w / H(i+1,i);
	end
end
```


## Lanczos method for eigenvalues

It can be showd that the Ritz values of $T_k$, called $\mu_i,\dots\mu_k$ converge to the eigenvalues of $A$.

