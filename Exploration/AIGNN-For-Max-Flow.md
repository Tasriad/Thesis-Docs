# Algorithm-Informed Graph Neural Network (AIGNN) for Max-Flow

**paper reviewed**: [[AIGNN-for-max-flow.pdf]]

---

**Field of Target**: Leakage Detection and Localization in Water Distribution Networks

---

## 1. Problem Definition

Graph interpolation-based data-driven methods and graph neural network (GNN) models often learn shortcuts that perform well on in-distribution data but fail to generalize to out-of-distribution scenarios.

## 2. Proposed Method: AIGNN

- **Objective**: Transfer the algorithmic knowledge of the Ford–Fulkerson max-flow algorithm to GNN models for pressure estimation in water distribution networks (WDNs).
- **Approach**:
  1. **Training Phase**: Train the AIGNN to emulate the Ford–Fulkerson algorithm on synthetic graph datasets.
  2. **Application Phase**: Deploy two specialized AIGNNs:
     - **Reconstruction AIGNN**: Reconstructs node pressures from current sensor measurements.
     - **Prediction AIGNN**: Predicts future node pressures based on historical measurements.

## 3. Neural Algorithmic Reasoning (NAR) Background

Neural Algorithmic Reasoning (NAR) embeds classical algorithmic computations within a neural architecture, using an **encoder–processor–decoder** stack.

### 3.1 Encoder–Processor–Decoder Paradigm

| Stage               | Core Function                                                                                  | Algorithmic Analogy                                                                                   |
|---------------------|-----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Encoder** \(f\)  | Transforms raw symbolic inputs (graphs, sequences, sets) into dense latent vectors           | Initializes data structures (e.g., distance arrays, queue flags).                                      |
| **Processor** \(P\)| Iteratively updates latents with a shared neural module (GNN or Transformer) for \(T\) steps | Executes loop body: relaxes edges, propagates BFS wave-fronts, updates DP tables, etc.               |
| **Decoder** \(g\)  | Maps final (or intermediate) latents back to the desired output format (node colors, DP scores) | Reads data structures to produce the final answer.                                                    |

_This framework was introduced by Hamrick et al. (2018) and is now the de facto template for NAR research._

### 3.2 Example Applications of NAR

1. **Prim’s Algorithm**: Reconstructing developmental trajectories of single cells from transcriptomic data.
2. **Max-Flow / Min-Cut**: Classifying vessel types in brain connectivity graphs.

## 4. AIGNN in Water Distribution Networks

- **Integration with ChebNet**: Augmenting a standard Chebyshev GNN (ChebNet) using AIGNN embeddings:
  - **ChebNetIN**: Embeddings fed into the input layer.
  - **ChebNetEMB**: Embeddings injected before the final prediction layer.
- **Performance & Generalization**:
  - Outperforms baseline ChebNet without algorithmic infusion.
  - Demonstrates superior out-of-distribution generalization.
  - Embeddings from AIGNN serve as powerful auxiliary information for existing GNN models.

## 5. Why GNNs as the Processor in NAR?

Graph Neural Networks naturally mirror the iterative, message-passing structure of classical graph algorithms (e.g., Bellman–Ford, Ford–Fulkerson), making them well-suited for neural algorithmic execution.

## 6. Supervision via the CLRS-30 Benchmark

- **Scope**: 30 algorithms spanning sorting, searching, dynamic programming, geometry, graph algorithms, and strings.
- **Representation**: Uniform graph-based representation for all algorithms.
- **Hints**: Decomposes algorithmic execution into consecutive steps (hints) for intermediate supervision (Veličković et al., 2022).
- **Benefits**:
  - Better alignment with underlying algorithms.
  - Reduced reliance on dataset-specific shortcuts.
  - Enables multi-task neural reasoners capable of learning multiple algorithms in a single model.

---

## References

1. Hamrick, J. B., et al. (2018). *On the Alignment of Neural Architectures with Classical Algorithms.* _International Conference on Learning Representations (ICLR)_.
2. Veličković, P., et al. (2022). *CLRS-30: A Benchmark for Neural Algorithmic Reasoning.* _Advances in Neural Information Processing Systems (NeurIPS)_.
3. [Additional references related to AIGNN and pressure estimation in WDNs]
