# Talk plan — Lorentzian Lagrangians paper (with Davide Manini)

Living record of the planning sessions. It will be the basis for the prompts that build the slides.
Status: **Session 1 (2026-09-29) in progress.** Many structural decisions made (see §5); items marked *(open)* are still waiting on answers.

Source material:
- Paper: `claude/Electromagnetic.tex` + `claude/Electromagnetic.bbl` in this project (current version, received 2026-09-29). The GitHub repo RotemAssouline/lorentzian-lagrangians is private and not reachable from these sessions.
- Companion (technical) paper: `claude/Localization.tex` + `claude/Localization.bbl`, *L¹ Localization for extended-real-valued Lagrangians and the electromagnetic Monge problem* (Assouline–Manini, received 2026-09-29). **Also an allowed source of slide wording** under the hard rule (it's Rotem's own text); its intro has concise phrasings of displacement interpolations and monotonicity.
- Style references (both Reveal.js, readable):
  - `lagrangian-cd` — "Curvature-Dimension for Autonomous Lagrangians", Geometric Structures seminar, SISSA, April 2026 (~57 slides).
  - `magnetic-bm` — "Magnetic Brunn-Minkowski inequalities", Séminaire d'Analyse, IMT, May 2026 (~43 slides).


> ## ⚠️ HARD RULE FOR BUILDING THE SLIDES (Rotem, 2026-09-29)
> **Do NOT generate ANY new text. Use only precise phrasings that appear in the paper** (the EM paper, or the companion paper `Localization.tex`). Slides use short statements and bullets, so the paper's wording may be *compressed* (cut down, shortened), but **no AI-written content**. Every word on a slide must be traceable to the paper (or to a source Rotem designates).
> **Opening slides (ℝⁿ OT/DC, Riemannian theorem, McCann's theorem):** the paper barely covers these, so **Rotem writes that text himself** when building the slides in Claude Code. Claude builds the slide structure/placeholders there and does not draft the wording. Plain-language glosses written in this plan file (e.g. "no overtaking", "each particle's own clock") are *planning notes only*: they must NOT appear on slides unless the paper says them.

---

## 1. What the reference talks already establish (house style)

Observed in the two example decks; assume these carry over unless we decide otherwise.

- **Tech:** Reveal.js 4.6 from jsDelivr, white theme, MathJax 2 via RevealMath, plugins Markdown/Highlight/Notes. `hash: true`, `transition: 'fade'`, progress bar on, default slide numbers off (custom TOC-style indicator instead), controls bottom-right, mouse-wheel navigation.
- **Typography:** Alegreya Sans for text (fonts bundled locally in `fonts/`), Alegreya available too.
- **Title slide:** title / "Rotem Assouline (IMJ-PRG)" / seminar name / institution / month-year.
- **Arc of both talks:**
  1. Brunn–Minkowski in ℝⁿ, built up with a picture of A₀, A_λ, A₁ over several fragment steps.
  2. Question mark: what is A_λ on a manifold? → geodesic interpolation.
  3. Riemannian BM under Ric ≥ 0 (CEMS '01, Sturm '06), weighted/distorted versions, list of extensions (mms, Finsler, sub-Riemannian, Lorentzian).
  4. Motivating non-Riemannian example (horocyclic BM on the hyperbolic plane / ℂHᵈ, pictures).
  5. The new object (Tonelli Lagrangians / magnetic geodesics) with examples and pictures.
  6. Ricci curvature: intuitive meaning (volume of a small blob flowing along parallel geodesics), interactive flow simulations (euclidean plane, sphere, hyperbolic plane — `flow0/flowsph/flowhyp.html`), then the generalized Ricci and Bochner formula.
  7. Main theorem(s) stated as equivalences.
  8. Examples (Kähler, Sasakian, S^{2d+1}, Heisenberg, closed potentials on the flat torus with an interactive simulation).
  9. Proof via L¹ localization / needle decomposition (Part I: transport rays + mass balance; Part II: CD on needles via Bochner).
  10. "Thank you!", with backup slides after it (e.g. Sasakian definition, extra proof sketch).
- **Interactive content:** iframes to simulations in `online_simulations/` (flows, magnetic, electric, n-body, flat torus, GDI).
- **Section divider slides** with a single title (e.g. "Magnetic geodesics", "Magnetic Ricci curvature", "On the proof").
- Heavy use of fragments to build theorems and pictures step by step.

## 2. The events

Three talks with the same underlying material, all given by Rotem alone:

| When | Where | Audience |
|---|---|---|
| **Oct 20, 2026** (Tue, 11 AM, Warren Weaver Hall 1314) | NYU Courant — Convexity Seminar | convex geometry |
| **Oct 26, 2026** (Mon, 14:30–15:15, last talk of the day) | Tel Aviv University — *A Day of Convexity & High-Dimensional Geometry* (with the Israeli GAFA seminar), Schreiber 309 | convex geometry / high-dim geometry |
| **Dec 8, 2026** | Fields Institute, Toronto — Applied Mathematics Colloquium (invited by Robert McCann) | Lorentzian geometry + OT people, plus a broad analysis audience |

**What the seminar sites say about the rooms (checked 2026-09-29):**
- *NYU Convexity Seminar* (organizers Deane Yang, Gaoyong Zhang, Shay Sadovsky, Nestor Guillen): convex geometry and anything involving convexity: differential geometry, PDE, probability, GMT, optimization, functional/harmonic analysis. So it's broad, with some geometric analysts and OT-literate people likely present.
- *TAU Day of Convexity*: five speakers (Assouline, Faifman, Friedland, Hershkovits, Sadovsky); Rotem closes the day. Slot is **45 min**, not 50. It's a high-dimensional/convex geometry crowd at the end of a long day.
- *Fields Applied Math Colloquium*: monthly, broad applied math/analysis. The 2025–26 speakers were mostly differential geometry + GR (Lorentzian spectral geometry, static Minkowski inequality, gravitational radiation, spatial infinity) plus Boltzmann, minimal surfaces, math biology. Typical slot ~1 hour. The room will be comfortable with Lorentzian geometry and GR language but not necessarily with OT.

- Slot lengths: ~50 min per Rotem; **TAU is 45 min** per the event page; Fields slots are typically ~1 hour.
- **Approach (decided 2026-09-29): build one base talk first; adapt it per venue later** (e.g. TAU's 45 min, Fields' different background). Planning sessions focus on the base talk until it's settled.

## 3. The paper

**Title:** *Displacement convexity in electromagnetic optimal transport on Lorentzian manifolds* (Assouline–Manini). Source: `Electromagnetic.tex` — **current version received 2026-09-29 16:38** (amsart; Rotem at MIT, Davide at Vienna; 2376 lines). It replaces an older draft. The intro now has subsections: OT in an EM field / Displacement convexity / Magnetic fields and point charges in Minkowski / Detecting the sign of the charge by varying the charge-to-mass ratio / On the proof. Examples section: Minkowski + EM waves only. Appendix: Kaluza–Klein only (Lorentz–Randers appendix gone). Bibliography: `Electromagnetic.bbl` (received 2026-09-29), use it for citations on slides. Key refs for the opening: McCann '97 (convexity principle), McCann '20 (Camb. J. Math., DC ⟺ strong energy condition), Cavalletti–Mondino '20/'24, Sturm '06, Lott–Villani '09, Klartag '17 (needles). A companion paper, **[AM26] Assouline–Manini, “ℓ¹ localization for extended-real-valued Lagrangians and the electromagnetic Monge problem”, in preparation**, holds the needle decomposition and the existence of interpolations for small charge-to-mass ratio.

**In Rotem's words:** an extension of the equivalence between Ricci lower bounds and displacement convexity of entropy in OT to OT taking place in an electromagnetic field, with the transported mass charged.

**Scope decision:** the talk is about electromagnetism only. It is not pitched as a general "Lorentzian Lagrangians" framework.

**Content inventory (Claude's reading, for reference when choosing what goes in):**
- *Setting:* globally hyperbolic spacetime (M,g), potential A, field F = dA. A charged test particle follows the Lorentz force equation ∇_γ̇ γ̇ = F♯γ̇. The cost is the free-time minimal action; minimizers are unit speed and minimize ∫(−|γ̇| − A(γ̇)). With A = 0 this is the ℓ₁ Lorentzian cost.
- *Curvature:* Ric_F = Ric + δF + ¼⟨F,F⟩ − ½F², a function on future unit timelike vectors. It is gauge invariant and equals the Kaluza–Klein Ricci curvature at a null lift.
- *Physical reading (Remark 2.x):* for an observer V in 4D, **Ric_F(V) = Ric(V,V) − ρ_V + ½|B_V|² − |E_V|²**. Gravity and the magnetic field focus; the charge density and the electric field defocus. This is probably the most talk-friendly formula in the paper.
- *Mechanism:* Riccati/Raychaudhuri for the velocity field V = −∇u − A♯ of a Hamilton–Jacobi solution. The rotation ω is no longer zero: it equals ½ of F restricted to V^⊥. The result is an electromagnetic Bochner inequality V div V + (div V)²/(n−1) + Ric_F(V) ≤ 0, sharp pointwise.
- *Main theorem:* for any relatively open B ⊆ SM (interpolations with endpoints in 𝒫_A, i.e. no action-minimizing null geodesics between the supports; same as 𝒫_≪ in Minkowski), Ric_F ≥ k on B ⟺ entropy is k-displacement convex along every monotone displacement interpolation whose velocities stay in B. There is a weighted version, and it recovers McCann's ℓ₁ strong-energy-condition characterization when A = 0. The localization to B is needed because in n ≥ 3 with Ric = 0 and F ≠ 0, Ric_F is unbounded below on SM (boosted observers see huge E).
- *Displacement convexity* uses the duration function ℓ (proper time of each particle), which in general differs from the cost.
- *Proof:* the needle decomposition from the companion paper, plus the Bochner inequality on each needle.
- *Examples / corollaries:*
  1. **Source-free magnetic field in Minkowski:** entropy is displacement convex whenever all particles move slower than **c/√2** relative to the observer ∂_t in whose frame the field is purely magnetic. "Speed relative to an observer Z" is now defined in the intro. The threshold is the same for every such field and is sharp.
  2. **Coulomb field of a point charge:** displacement convexity with an explicit k(Q, r₁, σ) = −(Q²/r₁⁴)(1 + σ²/2) holds on {r > r₁, v_⊥ < σ} iff |q₀| ≤ Q, so DC "reads off" the magnitude of the charge. New remark: with Q = 0 this recovers Minkowski DC, and any nonzero point charge breaks DC.
  3. **Sign of the charge density (Ricci-flat), current version:** assume J = −δF is *timelike* on the closure of a precompact U, and fix an observer field Z. Then J is future-directed (resp. past-directed) iff there are σ ∈ (0,1) and s₀ > 0 such that for all −s₀ < s ≤ 0 (resp. 0 ≤ s < s₀), entropy is DC along every monotone interpolation for charge-to-mass ratio s that stays in U with speeds < σ relative to Z. **Framing in the paper: DC detects the sign of the charge density in its rest frame** (no longer "causal currents").
  4. **Electromagnetic waves** (pp-waves, geometric optics): Ric_{sF} = |α(θ)|²(κ − s²/2)k². Gravity of the wave's energy competes with its electric push, and for any real particle the latter wins by ~10³⁶–10⁴².
  5. ~~**Reissner–Nordström**~~ — **removed from the current version of the paper** (Rotem, 2026-09-29). Do not use.
- *Charge-to-mass ratio s* is a free probe parameter: rescaling F ↔ rescaling the test charge. Under Einstein–Maxwell only the Lorentz-force terms scale with s; the gravitational part does not.

## 4. Main message / takeaway

Rotem's guiding message: *"Some properties of electromagnetic fields can be read off from displacement convexity of transported test particles."* It **guides how Rotem speaks; it does not appear on any slide** (decided 2026-09-29). The three examples (c/√2, point charge magnitude, sign of charge density) are its illustrations.

## 5. Structure

Build from scratch. The earlier talks are inspiration, not templates.

**Talk title:** *Displacement convexity in electromagnetic optimal transport on Lorentzian manifolds* (same as the paper).

**Title slide:** title / "Rotem Assouline (MIT)" / "joint work with Davide Manini (Universität Wien)" / seminar name / institution / month-year (the last three change per venue).

**Opening (decided 2026-09-29):**
- No Brunn–Minkowski at all.
- Start with **displacement convexity**, built up in three stages:
  1. in ℝⁿ;
  2. on Riemannian manifolds (link to Ricci ≥ 0);
  3. on Lorentzian manifolds.
- Then move to the electromagnetic setting. *(how the transition is made: open)*
- **Time budget for the whole three-stage opening: ~7 minutes** (so roughly 2–3 min per stage).
- **Riemannian stage:** state Ric ≥ 0 ⟺ displacement convexity of entropy, plus **one sentence** that other Ricci lower bounds give correspondingly modified (K-)displacement convexity. This mirrors the older decks, which state the Ric ≥ 0 theorem and then add a line like "Ric ≥ k ⟹ distorted version; in fact ⟺".
- **Lorentzian stage:** state McCann's theorem (displacement convexity ⟺ strong energy condition, Ric ≥ 0 on timelike vectors). This gives the gravitational baseline that the EM result extends (A = 0 case). **State it in McCann's original ℓ_q form (0 < q < 1)**, not the ℓ₁ version recovered by the paper. **Stays in the opening** as background, stated without precise Lorentzian definitions; those come at the start of the EM part (decided 2026-09-29).
- **Remark on the cost switch:** **explicitly remark on the switch** away from McCann's ℓ_q setup and why it happens. The paper's reason: with the free-time cost, minimizers are forced to unit speed and minimize ∫(−|γ̇| − A(γ̇)); for A = 0 this is ℓ₁. **Placement: after the main theorem** (decided 2026-09-29), using the paper's sentence that for A = 0 the theorem recovers the ℓ₁ version of the strong-energy-condition characterization, plus its note that the cost corresponds to ℓ₁ rather than ℓ_r.
- **Displacement interpolations for the EM cost (revised 2026-09-29):** the probabilistic formulation is **dropped** (monotonicity can't be stated cleanly with it, since an "almost surely" version is vacuous). Instead:
  1. A displacement interpolation is given by an **assignment x₀ ↦ (v, ℓ)**: each starting point gets an initial unit timelike velocity v = V₀(x₀) and a duration ℓ = ℓ(x₀) (proper time of that particle). The particle follows the Lorentz-force trajectory from x₀ with velocity v for proper time λℓ, and μ_λ is the push-forward of μ₀; the endpoint map must be an optimal transport map. μ̇_λ = law of the velocities at stage λ. **Picture** of this assignment.
  2. **Monotone:** if the particles from x and y share a worldline with x behind y by τ ≥ 0, then ℓ(x) ≤ τ + ℓ(y), i.e. no overtaking. **Picture** of this.
  - Both on the same slide (or tight pair of slides) and **quick: this is standard OT**, don't linger.
  - The duration ℓ is introduced here.
  - Notation: **no probabilistic notation**. The k-term is written −(k/2)λ(1−λ)∫ℓ² dμ₀, as in the paper.
- **Action / cost (decided 2026-09-29):** formulate everything with the **parametrization-invariant action** 𝒮₁[γ] = ∫(−|γ̇| − A(γ̇)) over future-directed timelike curves; the cost c(x,y) is its infimum. Then **mention** (a remark, not a definition) that minimizers are also free-time minimizers of the convex Lagrangian L(v) = −(1/r)|v|^r + 1/r − 1 − A(v), r ∈ (0,1), and are unit-speed. The explicit L need not be the centerpiece.
- **Introducing the field:** stay geometric. Write F = dA and the Lorentz force equation ∇_γ̇ γ̇ = F♯γ̇, without discussing observers. **E and B come later**: observer-relative definition right after Ric_F, coordinate form in the Minkowski part (revised 2026-09-29).
- **Ric_F and the main theorem:** define Ric_F = Ric + δF + ¼⟨F,F⟩ − ½F². **Mention the Kaluza–Klein interpretation**: Ric_F(V) = Ric of the KK metric g̃ = g − (dφ − A)² on M × S¹ at the null lift Ṽ = V + (1 + A(V))∂_φ. **Do not** put on slides why KK doesn't give the theorem for free (measures live on M, no obvious lift); Rotem answers that orally if asked. *(Exact placement/format, a line on the Ric_F slide or a fragment: open.)* Then **state the main theorem immediately, in two steps**: first Ric_F ≥ 0 on B ⟺ displacement convexity, then (Reveal auto-animate to a near-identical slide) Ric_F ≥ k on B ⟺ k-displacement convexity with the −(k/2)λ(1−λ)∫ℓ² dμ₀ term. Same pattern as `magnetic-bm` (Ric_Ω ≥ 0 slide → Ric_Ω ≥ k slide). The general statement is (Ric_F ≥ k on B ⟺ k-displacement convexity along monotone interpolations with velocities in B). **Afterwards**, explain where Ric_F comes from via the Raychaudhuri equation for a flow of charged particles.
- **Why the set B:** a **dedicated slide** explains that with Ric = 0 and F ≠ 0 (n ≥ 3), Ric_F is unbounded below on SM, because fast observers see arbitrarily strong fields. This is why the theorem is localized to a set B of velocities. **Placed after the post-theorem remarks slide**, before the Raychaudhuri explanation. **The proof opens as a click-to-open popup on this slide** (revised 2026-09-29, replacing the backup-slide idea): reuse the mechanism from `magnetic-bm` (the Sasakian definition): `.def-trigger` span with `data-def="…"`, `<template id="def-…">`, `.def-overlay` modal with MathJax re-typeset, closes on click/Esc. Content: the paper's proof of Lemma `lem: RicFunbounded` (null w with F♯w not parallel to w; v_r = u/r + rw; Ric_F(v_r) = −½r²F²(w) + O(r) → −∞), in the paper's wording, compressed. **Trigger is hidden** (looks like ordinary text; only the cursor changes), as in `magnetic-bm`.
- **Raychaudhuri slide(s):** show the **full kinematic decomposition** of ∇V (expansion θ, shear σ, rotation ω, plus the V♭⊗F♯V term) and the Raychaudhuri equation on the slide, but Rotem will **not walk through it in detail**. Presumably the new point (ω = ½ F restricted to V^⊥, nonzero because of the field) gets a light visual emphasis. *(Level of emphasis: open.)*
- **Proof of the main theorem** goes **at the end of the talk**, after the examples (before "Thank you!"). Content (decided 2026-09-29):
  1. **Go quickly over how needle decomposition works**, with attributions to earlier works, **as in both previous talks** (`lagrangian-cd` / `magnetic-bm` "On the proof" slides: L¹ OT / transport rays + mass balance, Evans–Gangbo, Caffarelli–Feldman–McCann, Feldman–McCann; Klartag's needle decomposition; extensions Ohta, Cavalletti–Mondino, Milman, Braun–McCann, Assouline '24). Take the citation list from the bibliographies (`Electromagnetic.bbl`, `Localization.tex`), and the step structure from the older decks: rays → change of variables → needle densities e^{−ψ} → Bochner gives the CD bound on each needle.
  2. **Then the novelty:** the Lagrangian here is **extended-real-valued** (= +∞ outside the future cone) and **not superlinear** (the |v|^r term with r ∈ (0,1)), so it's not Tonelli and earlier needle decompositions don't apply. The companion paper [AM26] extends Klartag's needle decomposition to such Lagrangians. Its proof idea (companion paper §1.3): locally replace L by a Tonelli Lagrangian agreeing with L in the direction of the transport rays, apply the Tonelli needle decomposition of [Ass24], then glue the local decompositions. The Hamilton–Jacobi clause of that theorem + the EM Bochner inequality give the needle CD bound.
  - For the novelty part, show **only the two obstacles and the key idea** (local Tonelli regularizations + gluing). The companion paper's needle theorem is **not** stated in full. *(Number of slides for part 1: open.)*

**Running outline so far** (50-min base talk: opening ≈ 7 min, proof ≈ 5–7 min, so ≈ 36–38 min for items 4–8; **applications (item 8) ≈ 10–15 min**, leaving ≈ 21–28 min for items 4–7):
1. Displacement convexity in ℝⁿ (OT map → interpolation → DC).
2. Riemannian manifolds: DC ⟺ Ric ≥ 0.
3. Lorentzian manifolds: McCann's theorem (ℓ_q form). *(1–3 ≈ 7 min)*
4. EM part begins with **a little Lorentzian geometry** (signature, timelike/null/causal, time orientation, future-directed, SM, x ≪ y, global hyperbolicity; decided 2026-09-29). **"Globally hyperbolic" is defined in gray parentheses right after the term.** Neither paper defines it, so under the hard rule **Rotem supplies that definition text**. The other terms use the paper's §2.1 wording. **Then basic electromagnetism**: A, F = dA, Lorentz force equation; the parametrization-invariant action and cost; displacement interpolations as x₀ ↦ (v, ℓ) with monotonicity (pictures).
5. Ric_F definition (+ Kaluza–Klein line) → **observer definition of E and B** (paper §2 remark: E_V = F♯V, B_V = (⋆F)♯V are the electric and magnetic fields measured by the observer V, n = 4) **together with the observer formula Ric_F(V) = Ric(V,V) − ρ_V + ½|B_V|² − |E_V|²** (ρ_V = −δF(V), charge density measured by V; same remark in the paper). **Order confirmed: after the Ric_F definition, before the theorem** → main theorem in two steps (k = 0, then k) → **short remarks slide**, modeled on the post-theorem remarks slide in `lagrangian-cd`: A = 0 recovers the ℓ₁ version of McCann's characterization (cost is ℓ₁ rather than ℓ_r). **Nothing else on it for now**; gauge invariance of Ric_F is not mentioned (decided 2026-09-29).
6. Then the slide: why B (Ric_F unbounded below on SM).
7. Raychaudhuri: **goes straight to the EM version** (no gravity-only warm-up). **Do not reuse** the geometric explanation of Ricci from `lagrangian-cd` (blob flowing along parallel geodesics, V div V = −Ric, flow simulations). It **starts by introducing the Hamilton–Jacobi equation** |du + A| = 1 (du + A past-directed) and V = −∇u − A♯, which solves the Lorentz force equation; then the full kinematic decomposition shown, not walked through → EM Bochner inequality V div V + (div V)²/(n−1) + Ric_F(V) ≤ 0 for V = −∇u − A♯, |V| = 1. **Only the inequality**, not the equality/sharpness clause (decided 2026-09-29).
8. *(≈ 10–15 min)* Minkowski specialization: E and B **in coordinates** (paper §4.1: F = dt∧(Eˣdx + Eʸdy + Eᶻdz) − Bˣdy∧dz + Bʸdx∧dz − Bᶻdx∧dy); **Maxwell's equations are not shown**; "source-free" (δF = 0) and "current J = −δF" are used by name without definition, and Rotem explains orally if asked), **the general Minkowski formula for Ric_F is not shown**; each example shows only its own short Ric_F formula (formulas **as in the current version**: magnetic: Ric_F(v) = ½(|B|² − |B×𝐯|²); electric (Coulomb): Ric_F(v) = −|E|² − ½|E×𝐯|²; Ricci-flat: Ric_{sF}(v) = −s·J(v) − s²(½F² − ¼⟨F,F⟩)(v). For reference, the paper's general Minkowski formula is Ric_F(v) = ½|B|² − |E|² − ½|E×𝐯|² − ½|B×𝐯|² + vᵗ⟨E×B,𝐯⟩ − ρvᵗ + ⟨j,𝐯⟩). Then the three featured examples:
   - source-free magnetic field, c/√2 threshold. **State only the corollary** (DC for speeds < 1/√2 relative to the observer in whose frame F is purely magnetic; same bound for every such field; sharp), not a general-k version (the current paper no longer has general-k magnetic/electric theorems; only the corollaries). Why 1/√2: speed < 1/√2 ⟺ |𝐯| < 1 for unit v, so |B×𝐯| ≤ |B||𝐯| < |B|. The fact that speed is conserved in a pure magnetic field (so the bound at μ̇₀ propagates) is **not on the slide**; oral answer if asked. Sharpness of 1/√2 is **not stated separately**: the slide shows Ric_F(v) = ½(|B|² − |B×𝐯|²), from which it is apparent (𝐯 ⊥ B with |𝐯| > 1 gives Ric_F < 0);
   - detecting the size of a point charge (Coulomb). **State fully on the slide** (current version's Theorem: region U_{r₁} = {r > r₁}, set B_{r₁,σ} of velocities with transverse speed v_⊥ < σ, k(Q,r₁,σ) = −(Q²/r₁⁴)(1+σ²/2), equivalence |q₀| ≤ Q ⟺ k-DC along monotone DIs with μ̇_λ(B_{r₁,σ}) = 1). Rotem **skims** it aloud; the slide carries all details. **Include the paper's remark** after it (for Q = 0, (i)⇒(ii) recovers the ℓ¹ version of DC for timelike OT in Minkowski; (ii)⇒(i) shows any nonzero background point charge breaks DC), in the paper's wording, compressed. The other remark (ℝ×(ℝ³∖{0}) not globally hyperbolic → smooth extension of A) is **left out**;
   - **Charge-to-mass ratio slide (its own slide, before the next theorem):** multiplying F by s has the same effect on the equations of motion as multiplying the test particles' charge by s; "displacement interpolations for the charge-to-mass ratio s"; existence/uniqueness of the monotone DI for small |s| (paper intro §1.4 wording).
   - detecting the sign of the charge density (Ricci-flat, timelike current, small charge-to-mass ratio). **Full statement on the slide** (all hypotheses: Ric ≡ 0, precompact U, J timelike on Ū, observer Z, σ ∈ (0,1), s₀), as with Coulomb. The paper's remark (J need not be timelike; same-sign massive charges ⟹ J timelike or zero) is **said aloud, not on the slide**.
   *Observer formula*: **decided** (2026-09-29), shown right after Ric_F together with E_V, B_V (see item 5).
   **No other examples.** Electromagnetic waves are left out of all versions (decided 2026-09-29); Reissner–Nordström is gone from the paper.
9. Proof *(5–7 min)*: needle decomposition, quick with attributions → novelty (extended-real-valued, non-superlinear Lagrangians; companion paper).
10. "Thank you!" — directly after the proof. **No summary / open-questions slide for now** (decided 2026-09-29).
11. **Backup slides after "Thank you!":**
   - Weighted version: reference measure 𝔪 = e^{−ψ}Vol_g, Ric_{F,𝔪} = Ric + Hess ψ + δ_𝔪F + ¼⟨F,F⟩ − ½F², δ_𝔪F = δF + ι_{∇ψ}F; same equivalence (paper's Theorem DC).
   - (Not included: Bochner equality clause, Kaluza–Klein appendix computation. The unboundedness proof is a popup on the B slide, not a backup slide.)

**The ℝⁿ stage:** define, in order, (a) the optimal transport map, (b) the displacement interpolation, (c) what displacement convexity says. The aim is to let newcomers catch up without boring experts. Keep it brisk and precise. Figures for this stage (and figures in general) are **deferred to a later session**.

The rest is *(open)*.

## 6. Reuse from earlier decks

Rotem doesn't mind recycling in general. Decided so far:
- **Not reused:** Brunn–Minkowski prelude (no BM at all); the geometric "what Ricci is" explanation and flow simulations from `lagrangian-cd`.
- **Reused as a model:** the needle-decomposition / "On the proof" slides and their attributions (compressed, quick).
- Style/tech setup (Reveal config, fonts, fragments, auto-animate pairs like Ric_Ω ≥ 0 → ≥ k, hidden-trigger popups) carries over.
- **No section divider slides for now** (decided 2026-09-29), unlike the older decks.

## 7. Pictures, simulations, new visuals

Deferred to a later session.

## 8. Things to avoid / leave out *(open)*


## 8a. Citations per slide (decided 2026-09-29)

**Rule:** only works in `Electromagnetic.bbl` (EM) or `Localization.bbl` (Loc). Format as in the older decks: *Author(s) 'YY* in the slide text, **with the year taken from the bib** (published version where the bib has one). Where the older decks used a different year or a work that isn't in either bib, the bib wins; conflicts are listed at the end. Bib keys are in `[brackets]`.

**1. Title slide:** none (joint work with Davide Manini).

**2. Opening (Rotem writes the text; citations to attach):**
- *ℝⁿ displacement convexity:* McCann '97 [mccann1997convexity] (EM).
- *Riemannian Ric ≥ 0 ⟺ DC:* Cordero-Erausquin, McCann & Schmuckenschläger '01 [CorderoErausquinMcCannSchmuckenschlaeger01], von Renesse & Sturm '05 [RenesseSturm05], Sturm '06 [St06-2, St06], Lott & Villani '09 [LoVi09] (all Loc; Sturm/LV also EM). This is the list the companion paper uses for this characterization.
- *"Other lower bounds" line:* same citations.
- *McCann's theorem (ℓ_q, strong energy condition):* McCann '20 [McCann20] (EM, Loc).

**3. Lorentzian basics / EM setup:**
- Lorentzian geometry background: **no citation** (O'Neill '83 left out, decided 2026-09-29).
- Lorentz force equation as Euler–Lagrange equation: none needed on the slide.
- **Include** (decided 2026-09-29): existence of connecting solutions of the Lorentz force equation, **Minguzzi & Sánchez '06** [MinguzziSanchez06] (EM, Loc). The other Minguzzi / Caponio–Minguzzi items are not on this slide.

**4. Action and cost:**
- ℓ₁ rather than ℓ_r (belongs to the post-theorem remark, item 9 below): Cavalletti & Mondino '20 [CavallettiMondino20], Braun & McCann '24 [BraunMcCann24], Suhr '18 [Suhr18] (EM).
- **Include** with the Lagrangian remark (decided 2026-09-29): **McCann '18** [McCann18] and **Braun, Gigli, McCann, Ohanyan & Sämann** [BraunGigliMcCannOhanyanSaemann24 / BraunGigliMcCannOhanyanSaemann26], an analytical-mechanics approach to Lorentzian OT with a similar Lagrangian. Year: the EM bib has the '24 arXiv version, the Loc bib the published Comm. AMS '26. By the published-version rule use **'26** (confirmed by Rotem). Beran et al. '24 left out.

**5. Displacement interpolations + monotone:**
- Monotone (canonical) interpolation "cf.": Feldman & McCann '02 [FeMc02, FeMc02b], Bernard & Buffoni '06 [BernardBuffoni06] (EM).
- Existence and uniqueness of the monotone DI: Assouline & Manini '26 [AssoulineManini] (companion, in preparation).

**6. Ric_F (+ Kaluza–Klein line):**
- KK relation: Choquet-Bruhat '09 [ChoquetBruhat09], Williams '15 [Williams15] (EM). KK null geodesics ↔ Lorentz force: Minguzzi '03 [Minguzzi03].
- Riemannian analogue of Ric_F (if mentioned): Assouline '26 [Assouline26] (Magnetic BM) (EM). Tonelli-Lagrangian Ricci: Lee '13 [lee2013displacement], Ohta '14 [Ohta+2014], Yang '23 [Yang23], Assouline '24 [Assouline24] (EM).

**7. Observer slide (E_V, B_V, observer formula):** none in the paper.

**8. Main theorem (two steps):** Assouline & Manini '26 (this paper). No other citation on the slide.

**9. Remarks slide (A = 0):** McCann '20 [McCann20], Cavalletti & Mondino '20 [CavallettiMondino20] (EM), exactly as in the paper's sentence.

**10. Why B (+ popup):** none (the paper's own lemma).

**11. Raychaudhuri / Bochner:** none in the paper for the Raychaudhuri equation itself. For local HJ solutions: Assouline '24 [Assouline24], if mentioned.

**12. Minkowski examples:**
- c/√2 and Coulomb: none (the paper's results).
- Charge-to-mass ratio slide: existence/uniqueness for small |s|: Assouline & Manini '26 [AssoulineManini], based on Minguzzi & Sánchez '06 [MinguzziSanchez06] (EM). Dirac-measure case: Caponio & Minguzzi '04 [CaponioMinguzzi04] (Loc).
- Sign of charge density: none.

**13. Proof section:**
- *Needle decomposition, quick overview (structure from older decks):*
  - L¹ OT / transport rays / mass balance: Evans & Gangbo '99 [EvGa99], Caffarelli, Feldman & McCann '02 [CFM], Feldman & McCann '02 [FeMc02]; also Bernard & Buffoni '06 [BernardBuffoni06], Figalli '07 [Figalli07], Fathi & Figalli '10 [FathiFigalli] (Loc).
  - Needle decomposition: Klartag '17 [Kl17] (EM, Loc), inspired by localization in convex geometry: Gromov & Milman '87 [GrMi87], Kannan, Lovász & Simonovits '95 [KaLoSi95] (Loc).
  - Extensions: Finsler, Ohta '18 [Ohta18] (Loc); metric measure spaces, Cavalletti & Mondino '17 [CavallettiMondino17] (EM, Loc); sub-Riemannian, Milman '21 [Milman21] (Loc); Lorentzian, Cavalletti & Mondino '20 [CavallettiMondino20], Braun & McCann '24 [BraunMcCann24] (EM); Tonelli Lagrangians, Assouline '24 [Assouline24].
  - Bochner → CD on needles, "as in previous works": Klartag '17, Ohta '17 [Ohta17], Cavalletti & Mondino '20, Assouline '24 (EM).
- *Novelty:* Assouline & Manini '26, companion paper (*L¹ Localization for extended-real-valued Lagrangians and the electromagnetic Monge problem*); reduces to the Tonelli needle decomposition of Assouline '24 [Assouline24].

**14. Backup: weighted version:** Bakry & Émery '85 [BakryEmery85]; Lott & Villani '09, Sturm '06 (EM) for the CD(K,∞) analogy, if mentioned.

**Conflicts with the older decks — bib wins (confirmed by Rotem 2026-09-29):**
- Evans–Gangbo: decks say '00 → bib '99. Caffarelli–Feldman–McCann: decks '01 → bib '02. Klartag: decks '14 → bib '17.
- Lovász–Simonovits '93 (decks) is **not in either bib** → use Kannan, Lovász & Simonovits '95 [KaLoSi95].
- Ohta Finsler needles: decks '15 → bib Ohta '18. Cavalletti–Mondino mms: decks '15 → bib '17. Milman sub-Riemannian: decks '19 → bib '21. Braun–McCann: decks '23 → bib '24.
- Cavalletti–Mondino Lorentzian: EM bib has both '20 (arXiv) [CavallettiMondino20] and '24 (Camb. J. Math.) [CavallettiMondino24]; the paper cites '20 in the places above. Keep the paper's choice unless Rotem says otherwise.
- The two bibs key the companion papers differently: EM [AssoulineManini] = Localization paper; Loc [AssoulineManini26] = EM paper. Both are "in preparation, 2026".

## 9. Decisions log

| Date | Decision |
|---|---|
| 2026-09-29 | Talk is about the EM paper only; built from scratch, older decks as inspiration. |
| 2026-09-29 | Build a single base talk; venue-specific modifications later. |
| 2026-09-29 | ~50 min slots. No Brunn–Minkowski; open with displacement convexity in ℝⁿ → Riemannian → Lorentzian. |
| 2026-09-29 | First delivery NYU Oct 20 (convex geometry); then TAU (convex geometry); then Fields Dec 8 (Lorentzian + OT). |

## 10. Open questions queue

**How to run these sessions:** ask Rotem one question at a time, not in batches.

Queued (not yet asked one-by-one):
- What can be assumed of the convex-geometry audience (OT/DC yes? Lorentzian no?), and how much time to spend building the Lorentzian side.
- Open from Brunn–Minkowski, or from physics?
- One deck with a Fields switch vs. two decks; slot lengths.
- Does the talk peak at the "reading off" examples or at the main equivalence?
- Should Ric_F(V) = Ric − ρ + ½|B|² − |E|² be the memorable centerpiece?
- Which examples are most striking / which to drop.
- How much physics to teach (observer-dependence of E and B, Lorentz force, charge-to-mass ratio as a probe).
- Proof: Raychaudhuri/Bochner computation vs. needle decomposition vs. one-slide sketch.
- Status of the companion paper by Oct 20; present or just cite.
