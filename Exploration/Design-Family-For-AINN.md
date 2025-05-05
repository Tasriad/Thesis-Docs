### 1  Deep Unrolling / Unfolding

Deep unrolling, also known as algorithm unrolling or unfolding, is a technique that converts an iterative optimization algorithm into a deep neural network architecture.
This approach combines the benefits of both iterative algorithms (interpretability and potentially smaller training data requirements) and deep learning (performance gains and flexibility

mostly been applied on : Biomedical imaging and image processing

---

### 2  Optimizer‑Inspired Backbones

**Optimizer-Inspired Backbones** refer to neural network architectures that are **explicitly designed or structured based on classical optimization algorithms**. This approach is a central idea behind **Algorithm-Informed Neural Networks (AINNs)** and **Deep Unrolling**. Rather than using generic deep architectures like ResNets or Transformers, these models **integrate the steps of optimization algorithms as layers**, making the network architecture interpretable, efficient, and often faster to converge.

mostly been used on : Biomedical imaging, image and video processing.

---

### 3  Neural Algorithmic Reasoning (Graph/DP Executors)

Neural Algorithmic Reasoning (NAR) is a field of machine learning that focuses on building neural networks capable of executing algorithmic computations. It aims to train these networks to mimic the steps of classic algorithms like sorting and shortest path finding. The goal is to enable neural networks to apply algorithms on inputs that generalize beyond the original preconditions defined by the algorithms.

mostly been used on : Graph Algorithms, Generalist Algorithmic Learning, Reinforcement Learning, NLP

---

### 4  Algorithm‑Aware Loss / Hard Constraints

Algorithm-Aware Loss involves designing loss functions that incorporate specific algorithmic behaviors or domain knowledge. This integration ensures that the neural network's learning process is aligned with known principles or desired outcomes
**Examples:**

- **Physics-Informed Neural Networks (PINNs):** These networks embed physical laws, represented by partial differential equations (PDEs), into the loss function. By doing so, the model's predictions are constrained to follow known physical behaviors, improving accuracy and generalization in scientific computing tasks.
    
- **Semantic Loss in NLP:** In natural language processing, semantic loss functions can enforce logical consistency or grammatical rules within generated text, ensuring outputs are not only plausible but also linguistically valid.

Hard Constraints refer to strict conditions that the model's outputs must satisfy. Unlike soft constraints, which are encouraged through penalties in the loss function, hard constraints are enforced explicitly, ensuring that certain criteria are always met.

**Examples:**

- **Safety-Critical Systems:** In applications like autonomous driving or medical diagnostics, hard constraints can enforce safety rules or regulatory standards, ensuring that the model's decisions never violate critical safety parameters.
    
- **Optimization Problems:** When neural networks are used to solve optimization problems, hard constraints can ensure that solutions adhere to feasibility conditions, such as resource limitations or scheduling requirements.

---

### 5  Differentiable Optimisation Layers (Solver‑in‑the‑Loop)

Differentiable Optimization Layers, also known as Solver-in-the-Loop, are components integrated into neural networks where an optimization problem is embedded as a layer, and is fully differentiable—meaning it can be trained end-to-end using gradient-based methods (like backpropagation).
Instead of treating optimization solvers as separate post-processing tools, differentiable optimization layers bring the solver inside the network. The output of this layer is the solution to an optimization problem, and gradients can be propagated through the solver during training.
Because instead of predicting a solution directly, the model predicts parameters of an optimization problem, and a solver computes the solution (which flows downstream). During backpropagation, the solver is treated as a differentiable function—hence, in the loop.



---

### 6  Meta‑learned Algorithm Controllers

Meta-learned algorithm controllers are control systems where the learning algorithm itself is trained to learn how to adapt to different tasks and environments, rather than just learning a single task. This "learning-to-learn" approach allows the controller to quickly adjust to new situations with minimal retraining, leveraging knowledge gained from previous experiences. 

Traditional control systems often require manual tuning and may struggle with adaptability when faced with new or varying conditions. Meta-learned controllers address this by incorporating a learning mechanism that operates on two levels:

1. **Meta-Learner**: Learns a strategy or initialization that enables rapid adaptation to new tasks.
    
2. **Base-Learner**: Applies this strategy to adapt to specific tasks using limited data.
    

This hierarchical learning structure allows the controller to "learn how to learn," facilitating swift adjustments to new control challenges


**Neural Networks (AINNs)** design patterns:

| **Design Family**                              | **Core Idea**                                                                 | **Main Mechanism**                                            | **Primary Benefit**                                          | **Typical Use Cases**                                                              |
| ---------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| **1. Deep Unrolling / Unfolding**              | Turns iterative algorithms into neural network layers                         | Each iteration = 1 layer in a deep net                        | Interpretable layers, fewer parameters                       | Biomedical imaging, compressed sensing, sparse coding                              |
| **2. Optimizer-Inspired Backbones**            | Entire network architecture mimics classical optimization routines            | Architectures structured like solvers (e.g. ISTA, ADMM)       | Inductive bias, interpretable architecture, fast convergence | Image/video restoration, medical imaging, compressed sensing                       |
| **3. Neural Algorithmic Reasoning (NAR)**      | Learns to execute algorithms like sorting, shortest paths, DP                 | Graph neural nets, transformer + executor models              | Generalization beyond training distribution                  | Graph algorithms, combinatorics, NLP, reinforcement learning                       |
| **4. Algorithm-Aware Loss / Hard Constraints** | Embeds constraints or domain knowledge into the loss function or output space | Custom loss functions, constrained optimization formulations  | Enforces correctness, adds structure                         | Physics simulations (PINNs), NLP semantics, safety-critical AI, optimization tasks |
| **5. Differentiable Optimization Layers**      | Embeds optimization problem as a differentiable layer inside the network      | QP/SOCP solvers inside NN with backpropagation through solver | Guarantees feasibility, learns constraint-aware outputs      | MPC, trajectory planning, structured prediction, robotics, computer vision         |
| **6. Meta-Learned Algorithm Controllers**      | Learns to adapt quickly to new tasks via meta-learning                        | Meta-learning loop: base learner + meta learner               | Adaptability across tasks/environments with few samples      | Robotics, adaptive control, tuning controllers in process control and autonomy     |