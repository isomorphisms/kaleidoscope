# Kaleidoscope — color → mirrors → crystals

A dependency-free browser experiment for [isomorphisms/kaleidoscope](https://github.com/isomorphisms/kaleidoscope). Open [`index.html`](index.html) on a computer or phone, or locally from a downloaded copy. The standalone prototype includes a credited starter-image gallery.

## The progression

1. **Original**: a random watercolor field `f`, which may also be painted on or replaced by an image. Keep this source intact when constructing its symmetric descendants.
2. **Mirror a**: create an image invariant under reflection `Rₐ`.
3. **Mirror b**: start from the **same original**, not from the first symmetric image; independently impose reflection `Rᵦ`.
4. **Compose**: demonstrate `Rₐ² = Rᵦ² = 1` and the rotation `RᵦRₐ`. When the acute mirror angle is `pπ/n` with relatively prime `p,n`, the generated group is `Dₙ`, with `2n` elements. A wedge-fold or full group-orbit average yields an invariant image. With arbitrary angles, the prototype uses a finite-depth approximation rather than pretending closure.
5. **Crystal**: extend color periodically over a square or triangular lattice, then impose a compatible finite dihedral point symmetry. Choose orders 2, 3, 4, or 6.

## Two meanings of “equate the halves”

Let an image be a function `f: ℝ² → RGB`, and reflection about a line be `R`. Two distinct operations both enforce symmetry:

- **Choose one side**: reflect sampling points on the other side into the chosen half-plane. Retains the original pigment without averaging it away.
- **Average matching points**: `(f(x) + f(Rx)) / 2`. This is the linear projection onto images invariant under `R`.

For independent branches, the program always applies each operation to the original `f`. A one-time sequence of averages for two distinct axes generally does **not** enforce both symmetries; for a finite group use its complete orbit average instead.

## From reflections to real crystals

Two nonparallel mirrors through the same point generate rotations and reflections: a rosette, not translations. To obtain translations from reflections alone, allow reflection lines to move away from the common center.

For a unit normal `n`, let `Rₙ,ᶜ(x) = x − 2((x ⋅ n) − c)n`. For parallel mirrors at offsets `c₁` and `c₂`, their composition is:

`Rₙ,ᶜ₂ Rₙ,ᶜ₁(x) = x + 2(c₂ − c₁)n`.

A second independent translation yields a lattice. A more geometric next step is to reflect a painted **fundamental triangle** across its three sides, generating planar affine Coxeter groups:

| Fundamental triangle | Affine group | Point symmetries |
| --- | --- | --- |
| 60°–60°–60° | Ã₂ | order 3 |
| 45°–45°–90° | C̃₂ | order 4 |
| 30°–60°–90° | G̃₂ | order 6 |

Here “point order” means rotational order, not the number of elements in the whole reflection group. Planar lattice rotation orders are restricted to 1, 2, 3, 4, 6. The 5-fold **rosette** is perfectly valid, but a genuinely 5-fold periodic planar crystal is not.

The finite groups in the two-mirror plane are the rank-two dihedral reflection groups `I₂(n)`. In particular `A₂ ≅ I₂(3)`, `B₂ ≅ I₂(4)`, and `G₂ ≅ I₂(6)` as reflection groups; the full `Dₙ` and `E₆/E₇/E₈` ADE families require higher-dimensional reflection arrangements, not just two mirror axes in the plane. Do not conflate the dihedral `Dₙ` notation with type-`Dₙ` Dynkin diagrams.

## Acceptance checks

- Both single-mirror images are derived independently from the original.
- Each single-mirror image is invariant under its chosen reflection.
- With mirror angle `π/n`, the composition is a `2π/n` rotation and the full pattern has `2n` reflection/rotation symmetries.
- Unsnap an angle and check that the UI explicitly reports a finite-depth approximation.
- The crystal view is unchanged by either lattice translation and by its selected point group. A pixel test of the order-4 prototype gave zero mean RGB difference across a horizontal translation by one lattice spacing.
- A fivefold rosette can appear in composition, but the periodic crystal selector deliberately excludes order 5.
- No libraries, build system, or image generator are required for the watercolor/mirror experiment. Loading Klee’s public-domain reference image needs network access; user-imported local images do not.

## Image sources and credit

- [Starter images with artist attributions](images/README.md)
- [Machine-readable source manifest](images/starters.json)
- [Books and lectures](books/README.md)

## Sources and continuation

- [John Baez, *This Week's Finds*, week 62](https://math.ucr.edu/home/baez/week62.html) — two reflections, finite Coxeter groups, and ADE.
- [John Baez, *Coxeter and Dynkin Diagrams* (2026)](https://arxiv.org/abs/2601.02290) — broader reflection groups, lattices, and higher-rank connections.

Next implementation: moveable offset mirrors; affine triangular alcoves and a gallery of `Ã₂`, `C̃₂`, `G̃₂`; then higher-dimensional root systems with honest 2D projection/slicing. The current crystal stage directly periodizes a color field, rather than generating the translations by compositions of offset mirrors.