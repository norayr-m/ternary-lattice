# Ternary Simplex Lattice

**Fractal tetrahedral lattice with ternary (base-3) state logic.**

Proof-of-concept for neuromorphic biological simulation architecture. Ternary nodes on a self-similar tetrahedral topology, projected from 4D through 3D rotation onto a 2D screen.

---

## The Architecture

### Ternary Logic (Base-3 Radix)

Standard binary: 2 states (0, 1). Ternary: 3 states (-1, 0, +1).

In biological neural networks, synapses operate in three distinct modes: excitatory (+1), inhibitory (-1), and resting (0). Forcing this onto binary silicon wastes compute cycles simulating the third state. A ternary gate handles all three natively.

Base-3 is the most efficient integer radix — the closest integer to Euler's number *e* ≈ 2.718. Radix economy is minimized at base *e*; base 3 requires fewer total gates than base 2 for equivalent computation.

### Tetrahedral Topology (sp3 Geometry)

Each node connects to exactly 4 neighbors — the 109.5° bond angles of sp3 hybridization (methane geometry). This maps directly to a GPU `vec4` register. The lattice is built recursively: each node spawns 3 children (excluding the incoming edge), producing a fractal simplex.

The 4-neighbor constraint means strictly local routing. No long-range interconnects. This is the thermal advantage: the chip doesn't melt.

### The Trisitor Gate

```
if |resonance| < threshold:
    state = 0        // Resting
else:
    state = sign(resonance)   // +1 (Excitatory) or -1 (Inhibitory)
```

One line of math. The `sign()` function IS the gate. The threshold IS the gate voltage. A polyphonic spatial wave sweeps through the 3D lattice; each node snaps to ternary state based on local resonance.

### 2.5D Fabrication Path

The fractal tetrahedral lattice projects naturally onto stacked 2D layers — the same Manhattan Projection used in 3D NAND Flash (300+ layers). Print the same 2D mask with offset, connect vertically with Through-Silicon Vias (TSVs). Self-similarity means one mask pattern at every scale.

Modern Gate-All-Around (GAAFET/RibbonFET) transistors with multi-threshold voltage doping can hold three stable states in a single vertical structure: +V (excitatory), 0V (resting), -V (inhibitory).

---

## What You See

- **Blue nodes** (+1): Excitatory — firing
- **Red nodes** (-1): Inhibitory — suppressing
- **Dark nodes** (0): Resting

Blue edges = excitatory pathways (both endpoints at +1). Red edges = inhibitory pathways (both at -1). The lattice rotates in 3D with perspective projection; depth sorting provides spatial rendering.

---

## Run

Open `index.html` in a browser. No dependencies. Single self-contained HTML file.

---

## Connection to the Distributed Reconstruction Theorem

```
R(f) = Σ φᵢ · Cᵢ(Πᵢ f)    where ‖R(f)‖ > ‖f‖
```

Each node is an observer with a local projection. The ternary state is the compressed boundary measurement. The tetrahedral topology defines the observer graph. The aggregate reconstruction across the lattice exceeds what any single node holds — the >1 result emerging from distributed local transitions.

**Paper:** N. Matevosyan, C. Anoian, A. Petrosyan — *Distributed Reconstruction from Incomplete Boundary Projections with Non-Trivial Internal Completion* (2026)

---

All visualizations and demonstrations were co-authored with Claude (Anthropic) and Gemini (Google).

## Authors

Norayr Matevosyan & A. Petrosyan

## License

MIT
