# Zeta Zero Scope

An interactive, single-file HTML visualization of Riemann's explicit formula in action: step forward or backward through real, published nontrivial Riemann zeta zeros and watch the partial sum

```
f(s) = Σ cos(γᵢ · log s)
```

resolve into resonant spikes at the primes and prime powers as more zeros (γᵢ) are added.

## What it shows

Each nontrivial zeta zero ρᵢ = 1/2 + iγᵢ contributes one cosine wave of frequency γᵢ (in log s). Individually these waves look like noise. Summed together, they constructively interfere at exactly the primes and prime powers — a live, hands-on demonstration of why the zeros of ζ(s) are said to "encode" the primes (Riemann's explicit formula).

## Features

- **1,000,000 real zeta zero ordinates**, sourced directly from Andrew Odlyzko's published tables (`zeros6`, rounded to 6 decimal places to fit the file size budget) — not approximated or computed locally.
- **Step forward / backward** through the zero list one at a time (or in configurable batches), with each step exactly adding or subtracting one `cos(γᵢ · log s)` term.
- **Adjustable playback speed** (log-scaled slider, zeros/sec) and a **zeros-per-tick** control for fast-forwarding through the list.
- **User-defined x-axis range** (s-min / s-max; minimum is floored at 1.5), with an auto-scaling y-axis.
- **Jump-to-index** control to skip directly to any zero in the list.
- Live readouts: current zero index, the γ value just added, current f-range, and playback status.
- Fully self-contained — all 1,000,000 zero values, CSS, and JavaScript are embedded in the single HTML file. The only external network dependency is the Google Fonts stylesheet (IBM Plex Sans/Mono); everything else, including the plotting and all interaction logic, works fully offline with a system-font fallback.

## Usage

Open `zeta_zero_scope_v1.0.html` directly in any modern browser (double-click it, or `file://` it, or serve it from any static file server) — no build step, no server required.

- **▶ Play / ❚❚ Pause** — start/stop stepping through the zero list.
- **◀| / |▶** — step one zero backward / forward manually.
- **▶ forward / ◀ backward** — set which direction Play advances in.
- **Jump to #** — go directly to a specific zero index (0–1,000,000).
- **Speed slider** — set how many zeros are added per second while playing.
- **Zeros per tick** — batch multiple zeros per step/tick, for quickly traversing large ranges.
- **x-axis min/max + Apply range** — change the window of s being plotted; the curve is recomputed from scratch for the new range.
- **↺** — reset back to zero terms summed.

## Background

This tool grew out of a conversation exploring an old MATLAB plot (`f = f + cos(log(s)*theta(i))`, found among files in this folder) that empirically demonstrates Riemann's explicit formula. The original generating script was never recovered; this project independently reconstructs the underlying mathematics (Riemann–Siegel Z-function root-finding for computed zeros, then later swapped for Odlyzko's published tables for accuracy and scale) and builds an interactive explorer around it, rather than a static replica of the original plots.

Related files elsewhere in this folder (not part of this tool):
- `zeta_theta_spectrum.cpp` / `zero_skip_demo.cpp` — earlier C++ explorations computing zeta zeros from scratch via the Riemann–Siegel formula, including a "jump-ahead" zero-index estimator and a segmented sieve for locating primes near very large numbers.
- `Riemann-Siegel formula.py` — an unrelated earlier script plotting |ζ(1/2+it)| and the Riemann–Siegel Z-function.

## Data source

Zero ordinates: Andrew Odlyzko, *Tables of zeros of the Riemann zeta function*, https://www-users.cse.umn.edu/~odlyzko/zeta_tables/ (table `zeros6`, first 1,000,000 of 2,001,052 zeros, values rounded to 6 decimal places for this build).

## Version

**v1.0** — initial release: 1,000,000-zero dataset, forward/backward stepping, adjustable speed, user-defined x-axis with a 1.5 floor, 50-division gridlines.

## License

MIT — see [LICENSE](LICENSE).
