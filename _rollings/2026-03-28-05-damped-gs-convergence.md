---
title: 'The Traps That Wouldn't Equalize'
date: 2026-03-28
permalink: /rollings/2026/03/damped-gs-convergence/
tags:
  - Optics
  - Gerchberg-Saxton
  - Convergence
  - Numerical Methods
  - Holography
---

The traps that wouldn't equalize
======

Two symmetric optical traps. Same target intensity. The Gerchberg-Saxton algorithm running for 100 iterations. And yet one trap was bright, the other dim, oscillating back and forth forever without converging.

![GS algorithm and phase scaling](/images/rollings/gs_phase_overflow.svg)

The problem
------

The standard weight update rule from Di Leonardo et al. (2007) is aggressive:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Original weight update (undamped):</strong><br/>
w_j<sup>(n+1)</sup> = w_j<sup>(n)</sup> × ⟨|V|⟩ / |V_j<sup>(n)</sup>|<br/>
<span style="color:#5a9ac0;font-size:13px;">If trap j is too bright → weight decreases. Too dim → weight increases.</span>
</div>

The issue: with only two traps, the correction overshoots. Trap A gets too much weight, trap B too little. Next iteration, the opposite happens. The uniformity metric oscillates around 0.85 without improving.

The fix
------

A damping exponent γ ∈ (0, 1] that controls the correction rate:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Damped weight update (γ = 0.5):</strong><br/>
w_j<sup>(n+1)</sup> = w_j<sup>(n)</sup> × (⟨|V|⟩ / |V_j<sup>(n)</sup>|)<sup>γ</sup><br/>
<span style="color:#5a9ac0;font-size:13px;">γ=1.0 → original (aggressive, oscillates)<br/>
γ=0.5 → half-strength corrections (stable, monotonic convergence)</span>
</div>

With γ=0.5, uniformity converges monotonically from ~0.85 to ~0.97 over 30+ iterations instead of oscillating. The key insight: making half-strength corrections each step prevents the overshoot-undershoot cycle.

The phase_scale sweet spot
------

Also found the right value for the phase_scale parameter. Three regimes:

| phase_scale | Fringes | Result |
|-------------|---------|--------|
| π | < 1 | Mask looks flat, no visible pattern |
| 10 × 2π ≈ 63 | 8-15 | Clear, beautiful blazed grating patterns |
| 2π × N/4 ≈ 800 | 100+ | Mask looks like noise, unresolvable |

The sweet spot at 10 × 2π gives enough spatial frequency to see the holographic structure while keeping patterns visually interpretable. Also tightened tolerance to 10⁻⁸ and enforced minimum 30 iterations before checking convergence.

![Fourier optics principles](/images/rollings/dinhot_fourier_optics.svg)

Small changes, big difference. Three numbers: γ=0.5, phase_scale=10×2π, min_iterations=30. [Optical tweezers on GitHub](https://github.com/fsantibanezleal/CEFOP_DinHot).
