# Quantum Sparse Solvers: IRLS, Kaczmarz, OMP, and OLS

This repository presents **four canonical sparse recovery algorithms**, written in a **quantum-first, solver-level style**.  
Each algorithm isolates the *true computational bottleneck* and expresses it using **conceptual quantum primitives**, while preserving the exact mathematical structure of the classical method.

The emphasis is on **algorithmic clarity and correctness**, not on runnable quantum benchmarks.

---

## Algorithms Included

### 1. Q-IRLS — Quantum Iteratively Reweighted Least Squares  
**File:** `qirls.py`

A quantum-enhanced formulation of IRLS for sparse regression.

- Classical: weight updates, ε-continuation, problem structure  
- Quantum: linear system solve via **HHL**
- Matches the textbook IRLS formulation exactly

**Quantum bottleneck isolated:**  
\[
(A^T A + \lambda W)x = A^T b
\]

---

### 2. Q-RK — Quantum Randomized Kaczmarz  
**File:** `qrk.py`

A projection-based solver expressed across classical, weighted, and quantum variants.

Includes:
- Classical Randomized Kaczmarz
- IRLS-aware Weighted Kaczmarz
- Quantum inner-product estimation
- Pure Quantum Randomized Kaczmarz loop

**Quantum bottleneck isolated:**  
\[
\langle a_i, x_k \rangle
\]

---

### 3. Q-OMP — Quantum Orthogonal Matching Pursuit  
**File:** `qomp.py`

A greedy sparse recovery algorithm written **quantum-first**, without a classical OMP baseline.

- Quantum oracle for **maximum inner product selection**
- Classical least-squares on the active support
- Residual update identical to classical OMP

No explicit sorting is performed; greedy selection is expressed as a **quantum max-finding primitive**.

**Quantum bottleneck isolated:**  
\[
\arg\max_j |\langle a_j, r \rangle|
\]

---

### 4. Q-OLS — Quantum Orthogonal Least Squares  
**File:** `qols.py`

A global greedy solver with a stronger selection criterion than OMP.

- Quantum oracle evaluates **residual norm after projection**
- Greedy selection minimizes post-projection residual energy
- Classical least-squares only on the selected support

This solver maps especially cleanly to quantum linear algebra.

**Quantum bottleneck isolated:**  
\[
\| P^\perp_{\Lambda \cup \{j\}} b \|_2
\]

---

## Design Philosophy

- Quantum primitives are used **only at true bottlenecks**
- Classical components are retained where unavoidable
- No quantum circuit “theater”
- No forced benchmarking or NISQ claims
- Algorithms read like **theory expressed in Python**

All implementations are:
- silent (no demos or logging)
- minimal
- mathematically faithful
- self-contained

---

## What This Repository Is (and Is Not)

**This is:**
- A solver-level exploration of quantum acceleration points
- A conceptual reference for quantum sparse algorithms
- A clear signal of algorithmic and mathematical maturity

**This is not:**
- A performance benchmark suite
- A NISQ demonstration
- A claim of practical quantum speedup

---

## Intended Audience

- Applied ML and signal processing researchers  
- Quantum algorithms engineers  
- Employers evaluating **algorithmic depth**, not tooling

---

## Summary

This repository provides a **coherent quantum lifting** of four major sparse solvers:

| Solver | Paradigm | Quantum Primitive |
|------|--------|------------------|
| Q-IRLS | Convex / reweighted | HHL (linear solve) |
| Q-RK | Projection-based | Inner product estimation |
| Q-OMP | Greedy (local) | Max inner product search |
| Q-OLS | Greedy (global) | Residual norm estimation |

Together, these form a **complete quantum-aware sparse solver stack**, expressed cleanly and without exaggeration.

---
