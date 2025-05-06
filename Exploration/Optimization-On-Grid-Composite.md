**Focus**  
Maximise the fracture‑toughness of 11 × 11 grid‑composite “digital materials” by learning how configuration and early‑stage stress fields influence crack growth, then automatically designing tougher layouts.

**Problem definition**  
Toughness depends on complex crack initiation + propagation, so each candidate geometry normally needs expensive full‑range FEM simulation. Exhaustively evaluating the astronomically large design space (≈10³⁴ patterns) is impractical, and previous ML surrogates extrapolated poorly, so optimisation stalled at stiffness/strength rather than toughness.

**Solution approach**

1. Generate an initial FEM dataset (10⁵ random patterns) recording both toughness and grid‑wise stress fields.
    
2. Train a **hierarchical DNN**  
    • _Feature‑generator_: multi‑kernel CNN maps configuration → initial stress field.  
    • _Toughness‑predictor_: ResNet‑style CNN ingests configuration + predicted stress to estimate toughness, giving much better out‑of‑distribution accuracy.
    
3. Embed this surrogate in an **active genetic algorithm**: crossover+mutation propose 1.2 M children per generation; surrogate filters the top 125, which are then verified with FEM and added to retrain the predictor.
    
4. After 28 generations (FEM run on only 3 500 cases ≈ 3.5 % of search space) the best design boosts toughness by ~60 % while also increasing stiffness and strength; result is confirmed by 3‑D‑printed tensile tests and DIC strain maps.