
These notes are transcribed from [MathWorks Reference Sheet](./extra/mathworks_reference.pdf)

# Matrices and Arrays

* length(A) - length of largest array dimension
* size(A)
* numel(A)
* sort(A)
* sortrows(A)
* flip(A)
* squeeze(A)
* reshape(A,sz)
* repmat(A,n)
* any(A), all(A)
* nnz(A)
* find(A)

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
