# Ford–Johnson (Merge-Insert) Sort Simulator — Minimum Comparison Sorting

This repository contains a single-page HTML app that **simulates the Ford–Johnson “Merge-Insert” sorting algorithm** (often referenced as a *minimum-comparison sorting* method). It visualizes the algorithm **step-by-step**, including pairing, sorting winners, Jacobsthal insertion order, and bounded binary-search insertions—while counting comparisons and comparing them to the theoretical minimum.

Source: `sum4.html`

---

## What it does

The simulator walks through Ford–Johnson sorting in clearly separated phases:

1. **Pair elements**  
   Every two elements are compared to form *(winner, loser)* pairs.

2. **Sort only the winners**  
   Winners are sorted (recursively/ideally) and the simulator accounts for the comparison cost using the information-theoretic lower bound estimate.

3. **Build the main chain**  
   The first loser `a1` is inserted at the beginning **for free** (0 comparisons), because pairing guarantees `a1 < b1`.

4. **Compute Jacobsthal groups and insertion order**  
   Remaining losers `a2..aN` are grouped using Jacobsthal boundaries to minimize comparisons.  
   **Within each group, insertion happens right-to-left.**

5. **Insert losers using bounded binary search**  
   Each loser `a_i` is inserted into the sorted “main chain”, but binary search is limited to the prefix that ends at its paired winner `b_i` (because `a_i < b_i` is guaranteed).

At the end, the app shows:

- **Total comparisons used**
- **Theoretical minimum** `⌈lg(n!)⌉`
- The final **sorted result**

---

## Features

- Manual input: space-separated unique positive integers (**4–100** values)
- Range generator:
  - choose `from`, `to`, and how many numbers to pick
  - generate random / ordered / shuffled selections
- Random generator:
  - choose count and max value
- Step controls:
  - `prev`, `next`, `run all`, `reset`
  - keyboard: **← / →** arrow keys
- Visual panels:
  - array view (chips)
  - pair view (winner/loser columns)
  - main chain view
  - Jacobsthal group table + insertion order
  - binary-search visualization (lo/hi/mid)
  - explanation panel with “deep dive” expandable sections

---

## How to run

### Option A: Open locally
1. Download or clone the repository.
2. Open `sum4.html` in any modern browser.

### Option B: GitHub Pages (optional)
If you enable GitHub Pages for the repository, you can host the page directly from the repo and open it via your Pages URL.

---

## Input rules

- **4 to 100** numbers
- **Unique** positive integers
- Manual entry expects **space-separated** values, e.g.:

```
5 3 8 1 7 2 14 9
```

---

## Notes on the algorithm (as implemented in the simulator)

- The app is designed as a **teaching/visualization tool** and includes:
  - Jacobsthal sequence explanation:  
    \( t_k = \frac{2^{k+1} + (-1)^k}{3} \)
  - Bounded binary-search reasoning:  
    insertion range is limited by the paired winner `b_i`

The page references:

- Knuth, *The Art of Computer Programming*, Vol. 3, §5.3.1 (p.184)

---

## File

- `sum4.html` — the full simulator (HTML + CSS + JavaScript in one file)

---

## License

No license file is included in the repository. If you want, tell me which license you prefer (MIT, Apache-2.0, GPL-3.0, etc.) and I can draft a `LICENSE` file text for you.
