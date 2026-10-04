# Phase Transformations, Interactively

An interactive, single-page web demo of phase transformations of pure substances: phase diagrams, the Gibbs free energy as the judge of which phase is stable, the Clausius–Clapeyron relation, the van der Waals model with its Maxwell construction and critical point, and critical exponents and power laws.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 5, Free Energy and Chemical Thermodynamics, Section 5.3). It follows the demo for Sections 5.1 and 5.2 (free energy) and concludes the Statistical Physics 1 series.

## What's inside

**Phases and phase diagrams.** Interactive phase diagrams of water and carbon dioxide on a logarithmic pressure axis, built from the textbook's vapor-pressure tables: choose any temperature and pressure (or click the diagram) to see the stable phase, whether you are on a coexistence line or at the triple point, and the vapor pressure. Notes on water's backward-sloping melting line, dry ice, and helium. The Gibbs free energies of diamond and graphite against pressure, with the crossover at about 15 kbar moving with temperature. First-order and continuous transitions, with the phase diagrams of a type-I superconductor and a ferromagnet.

**The Clausius–Clapeyron relation.** dP/dT = L/(TΔV), with examples for boiling water (3.6 kPa/K) and melting ice (−135 bar/K), and the vapor pressure equation P ∝ e<sup>−L/RT</sup> (Problem 5.35), tested against water's measured vapor pressure on a plot of ln P against 1/T with an adjustable latent heat. The magnetic analogue (Problem 5.47) and what it says about superconductors and ferromagnets.

**The van der Waals model.** The van der Waals equation, its Gibbs free energy, and the critical point V<sub>c</sub> = 3Nb, P<sub>c</sub> = a/27b², k<sub>B</sub>T<sub>c</sub> = 8a/27b (Problem 5.48), in reduced variables (Problem 5.51). An explorer for any T/T<sub>c</sub> shows the isotherm with its unstable region and the equal-area Maxwell construction, the triangular loop of G against P, and the computed vapor-pressure curve ending at the critical point, with the liquid and gas volumes and the latent heat.

**Critical exponents and power laws.** The expansion near the critical point and the van der Waals exponents β = 1/2, δ = 3, and γ = γ′ = 1 (Problem 5.55), against experimental values. A log–log plot of the liquid–gas volume difference, computed from the Maxwell construction, recovers β = 0.50. Scale invariance, Kadanoff's block spins and Wilson's 1982 Nobel Prize, and a caution about reading power laws into data.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The Maxwell construction is solved numerically: the isotherm's volumes at a given pressure come from the analytic roots of the cubic 3pv³ − (p + 8t)v² + 9v − 3 = 0, and the pressure is found by bisection until the two areas are equal. It gives P/P<sub>c</sub> = 0.647 at T = 0.9T<sub>c</sub>, and near T<sub>c</sub> the volume difference and latent heat approach 4√(1 − T/T<sub>c</sub>) and 6Nk<sub>B</sub>T<sub>c</sub>√(1 − T/T<sub>c</sub>), as derived in the lecture.
- The latent heat in the explorer comes from the Clausius–Clapeyron relation with the computed volume difference and the numerical slope of the vapor-pressure curve.
- The water and CO<sub>2</sub> vapor pressures are interpolated log-linearly between the tabulated points; the melting lines are straight lines in temperature against pressure, from their slopes (−0.0074 K/bar for water, about +0.017 K/bar for CO<sub>2</sub>).
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.

## Caveats

- The phase diagrams are schematic outside the tabulated range (ice's other high-pressure phases are not shown).
- The diamond–graphite calculation treats the molar volumes and entropies as constant.
- The van der Waals model is deliberately crude; its critical exponents differ from those of real fluids.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Section 5.3 and Problems 5.35, 5.47, 5.48, 5.51, and 5.55); vapor-pressure data from its tables (Keenan et al. 1978; Lide 1994; Reynolds 1979).
- M. P. H. Stumpf and M. A. Porter, "Critical Truths About Power Laws," *Science* 335, 665–666 (2012).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
