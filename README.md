# Grandi's Series Visualiser

**Author:** CMS1111
**License:** Free for non-commercial use. This work may be forked, modified, and used by anyone, for any purpose other than a for-profit project.

---

## What Is Grandi's Series

Grandi’s series is a classic example of a divergent series in mathematics. Named after the Italian monk and mathematician Guido Grandi (1671–1742), it is the infinite sum:

```
S = 1 - 1 + 1 - 1 + 1 - 1 + ...
```

At first glance it looks trivial: add one, subtract one, repeat. But the series has no conventional sum. It never converges to a fixed value. Depending on where you stop, the partial sum is either 0 or 1, and it switches between them forever. This makes Grandi's series a foundational example of a divergent series.

Mathematicians have nonetheless assigned it a regularised value of 1/2 through Cesàro summation, which averages the partial sums. This is the value most people mean when they say the series sums to one-half, though the series itself stays divergent.

---

## The Expression (-1)^i 

Each term in the series is produced by the expression **(-1)^i**, where `i` is the zero-based index of the term:

| i | (-1)^i | Running total |
|---|--------|---------------|
| 0 | +1     | 1             |
| 1 | -1     | 0             |
| 2 | +1     | 1             |
| 3 | -1     | 0             |
| … | …      | …             |

In Python this reduces to a single conditional:

```python
sign = 1 if i % 2 == 0 else -1
```

Even indices yield `+1`; odd indices yield `-1`. The partial sum is accumulated as:

```python
total += sign
```

This is the complete logic of the series. The visualiser does nothing more than apply this operation once per second and display the result.

---

## The Oscillation

Because no term ever cancels out the accumulation permanently, the partial sum oscillates between **1** and **0** on every step, without end:

```
Step 0  (+1)  ->  S = 1
Step 1  (-1)  ->  S = 0
Step 2  (+1)  ->  S = 1
Step 3  (-1)  ->  S = 0
         ...
```

The partial sum never settles. It does not grow, decay, or drift. This is the defining behavior of a divergent oscillating series, and it is precisely what both versions of this visualiser are built to display.

---

## Why the Color Changes

The display cycles through three colors — **green**, **blue**, **red** — one color per step.

The color carries no mathematical meaning. It is a visual device made necessary by the nature of the series: because the partial sum alternates between only two values (0 and 1), a two-color cycle would itself oscillate in a way that could be confused with the series. The color change provides a perceptual signal that a new step has occurred, making the oscillation legible at a glance. Three colors break that symmetry.

---

## Exploring the Webpage

Open `index.html` in any modern browser, or visit https://cms1111.github.io/grandis-series/

The interface is divided into five sections. Hovering over any section reveals a dark overlay with a detailed explanation of what that section shows:

- **Header** — explains the series and the expression `(-1)^i` used to generate each term.
- **Partial sum display** — the large numeral and sign badge. The overlay explains what the partial sum is and how the sign relates to the current step.
- **i = n** — the zero-based index of the most recently evaluated term. The overlay explains the relationship between the index and the sign.
- **Color / Steps** — the current cycle color and the total number of steps taken. The overlay explains the color cycle.
- **Current sequence** — the last 20 signed terms in order, with the most recent highlighted. The overlay explains how to read the strip.
- **Controls** — Start/Pause and Reset buttons. The overlay explains each control.

Click **Start** to begin the one-second interval. Click **Pause** to suspend it. Click **Reset** to return all state to zero.

---

##  the Python Script

coming soon ... stuff happened, it's broken :(

---

## File Reference

| File            | Description                                      |
|-----------------|--------------------------------------------------|
| `grandi_gui.py` | Python desktop application (Windows 11, tkinter) |
| `index.html`    | Standalone HTML page with hover overlays         |
| `README.md`     | This document                                    |

---

## License

This work may be forked, modified, and used freely by anyone, for any purpose **other than any for-profit project**. No warranty is provided. Attribution to **CMS1111** is appreciated but not required.
