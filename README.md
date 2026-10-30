# Pendulum Lab

Browser-based simulations of the simple pendulum. Plain HTML, CSS and JavaScript, with no build step and no dependencies.

| Page | What it does |
| --- | --- |
| `index.html` | Landing page |
| `lab.html` | Ideal pendulum: RK4 integration of θ̈ = −(g/L) sin θ − bθ̇ next to the small-angle model, live period measurement, and an amplitude sweep checked against the exact period T = 4√(L/g)·K(k), k = sin(θ₀/2) |
| `experiment.html` | Experiment Bench: a non-ideal pendulum (finite spherical bob, quadratic air drag, pivot friction, ±1° release scatter) timed with a hand-operated stopwatch and swing counter. Trials go into a table, and any two quantities can be plotted with a least-squares fit (g from T² vs L, power law from ln T vs ln L, amplitude correction from T vs θ₀², …) |

## Physics model (Experiment Bench)

The bob is a solid sphere of radius r on a massless string of length L, with pivot-to-centre distance d = L + r:

```
I θ̈ = −m g d sin θ − f·(½ ρ_air C_d π r²) d³ θ̇|θ̇| − I·b θ̇
I   = m (d² + 2r²/5)
```

`f` is the air-drag factor (1 = real air) and `b` is the linear friction coefficient (s⁻¹), both set in the page.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

The included workflow `.github/workflows/pages.yml` publishes the site to **GitHub Pages** on every push to `main`.
Enable it once under **Settings → Pages → Build and deployment → Source: GitHub Actions**.
The site then appears at `https://<your-user>.github.io/<repo-name>/`.
