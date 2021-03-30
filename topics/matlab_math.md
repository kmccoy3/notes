
These notes are transcribed from a [MathWorks Reference Sheet](./extra/mathworks_reference.pdf)

# Matrices and Arrays

```matlab
A = [1 2 3;
     4 5 6]
```

* **length(A)** - length of largest array dimension
  ```MATLAB
  L = length(A)
  % L => 2
  ```
* size(A) - array dimensions
  ```matlab
  sz = size(A)
  % sz => [2 3]
    % OR
  [r, c, ...] = size(A)
  % r => 2, c => 3
  ```
* numel(A) - number of elements in array
  ```matlab
  L = length(A)
  % L => 2
  ```
* sort(A) - sort array elements
  ```matlab
  L = length(A)
  % L => 2
  ```
* sortrows(A) - sort rows of array or table
  ```matlab
  L = length(A)
  % L => 2
  ```
* flip(A) - flip order of elements in array
  ```matlab
  L = length(A)
  % L => 2
  ```
* squeeze(A) - remove dimensions of length 1
  ```matlab
  L = length(A)
  % L => 2
  ```
* reshape(A, sz) - reshape array
  ```matlab
  L = length(A)
  % L => 2
  ```
* repmat(A, n) - repeat copies of array
  ```matlab
  L = length(A)
  % L => 2
  ```
* any(A), all(A) - check if any/all elements are nonzero
  ```matlab
  L = length(A)
  % L => 2
  ```
* nnz(A) - number of nonzero array elements
  ```matlab
  L = length(A)
  % L => 2
  ```
* find(A) - indices and values of nonzero elements
  ```matlab
  L = length(A)
  % L => 2
  ```

# Linear Algebra

rank(A) trace(A)
det(A)
poly(A)
eig(A), eigs inv(A), pinv norm(x) expm(A), logm cross(A,B) dot(A,B) kron(A,B) null(A)
orth(A)
tril(A), triu linsolve(A,B) lsqminnorm(A,B) qr(A), lu, chol svd(A) gsvd(A,B) rref(A)

# Descriptive Statistics

sum(A), prod
max(A), min, bounds mean(A), median, mode std(A), var
cumsum(A), cumprod, cummax, cummin
smoothdata(A) histcounts(X) corrcoef(A), cov xcorr(x,y), xcov normalize(A) detrend(x) isoutlier(A)

# Symbolic Math
* Requires Symbolic Math Toolbox

sym x, syms x y z eqn = y == 2*a + b solve(eqns,vars)
subs(expr,var,val) expand(expr) factor(expr) simplify(expr) assume(var,assumption) assumptions(z)
fplot(expr), fcontour, fsurf, fmesh, fimplicit
diff(expr,var,n) dsolve(deqn,cond)
int(expr,var,[a, b]) taylor(fun,var,z0)
