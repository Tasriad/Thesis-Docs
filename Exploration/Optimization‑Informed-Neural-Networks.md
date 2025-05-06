### Focus

Leverage deep‑learning alone to solve _constrained nonlinear optimization problems_ (CNLPs)—including variational inequalities, complementarity problems and standard CNLPs—without calling traditional optimization or ODE solvers.

### Problem definition

Existing neurodynamic approaches map a CNLP to an ODE whose equilibrium is the optimum, but they still rely on costly numerical integration and specialised optimisation software. This limits speed, requires hand‑tuned solvers, and only yields a final answer after full time‑stepping.

### Solution approach (in a nutshell)

1. **Reformulate** the CNLP as an initial‑value ODE via a suitable neurodynamic scheme (guaranteed global convergence).
    
2. **Replace the integrator** with a neural network

   $$
   y(t; w) = y_0 + (1 - e^{-t})N(t; w)
   $$

   that is trained to satisfy the ODE over a time window

   $$
   [0, T]
   $$

   using an analytically computed residual loss and a time‑decay weight.
    
3. **Predict the optimizer**: the network’s endpoint

   $$
   P(y(T; w))
   $$

   (projected onto feasibility) serves as the solution estimate, and an _epsilon metric_ (either objective value or projection error) guides early‑stopping and model selection.
    

Because the network provides a feasible estimate at every training iteration, OINN can deliver increasingly accurate answers earlier and, in tests, was faster than six classical integrators on stiff problems while matching or improving solution quality.