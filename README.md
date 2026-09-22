# Fitts' Law FPS Aim Trainer

**HCI Assignment 1 — Part II**<br>
**Name:** Holy 司大衛<br>
**Student ID:** 115034421<br>
**Live Demo:** https://holy1009.github.io/fitts-law-fps-Holy/

## Scenario
This experiment simulates a competitive FPS aim-training environment (e.g., Valorant, CS2). Professional and high-level players spend hours practicing **aim**. The ability to move the crosshair to a target that may appear anywhere on screen and click it as quickly and accurately as possible.<br>
**User:** Any FPS gamer practicing mouse aiming skills.<br>
**Context:** A training session where targets appear one after another at varying distances and sizes, with no delay between them.

## Innovation
Unlike classical Fitts' Law experiments, this variant adds an **accuracy-scoring system** that mirrors real FPS hitboxes:
| Outcome | Points |
|---|---|
| Inner circle (headshot) | +2 |
| Outer circle (bodyshot) | +1 |
| Miss | −1 |
This lets us measure **2 dependent variables**:
1. **Movement Time (MT)** — classical Fitts' Law
2. **Accuracy points** — does difficulty also affect precision?
The experiment uses **0 ms delay**, reflecting the time critical nature of competitive FPS where every millisecond matters.

## Method
- **100 trials**, randomized order
- **10 (A, W) configurations** × 10 trials each
- **A** = distance from previous target center to current target center (px)
- **W** = target diameter (px)
- **ID** = log₂(A/W + 1) bits
- **MT** = time from target appearance to first click (ms)
- **Points** = accuracy point each trial

### Configurations
| Config | A (px) | W (px) | ID (bits) |
|---|---|---|---|
| 1 | 150 | 120 | 1.17 |
| 2 | 200 | 100 | 1.59 |
| 3 | 300 | 100 | 2.00 |
| 4 | 400 | 100 | 2.32 |
| 5 | 500 | 100 | 2.58 |
| 6 | 600 | 100 | 2.81 |
| 7 | 500 | 50 | 3.46 |
| 8 | 600 | 50 | 3.70 |
| 9 | 700 | 50 | 3.91 |
| 10 | 800 | 50 | 4.09 |

## Experiment Video
[![](https://img.youtube.com/vi/spwWiJX_OE0/0.jpg)](https://www.youtube.com/watch?v=spwWiJX_OE0)

## Results

### Figure 1 — Fitts' Law: Movement Time vs. Index of Difficulty
![Fitts' Law: MT vs ID](GraphMTvsID.png)
**Fitted equation:**<br>
MT = 325.12 + 80.57 × ID<br>
R² = 0.5085

### Figure 2 — Accuracy: Points vs. Index of Difficulty
![Accuracy vs ID](GrapACCvsID.png)
**Fitted equation:**<br>
Points = 1.7633 − 0.0772 × ID<br>
R² = 0.019

## Discussion
**Fitts' Law is validated.** As expected, movement time went up linearly with the index of difficulty (about 80.57 ms per bit). That means the farther away or smaller the target, the longer it took to hit.

**Accuracy, on the other hand, stayed pretty flat.** Unlike MT, accuracy scores didn't really change with difficulty. This tells that I wasn't sacrificing precision for speed. Instead, I naturally slowed down on the harder targets to keep my accuracy up. That slowdown is exactly what shows up in the MT slope.

**Speed–accuracy tradeoff.** Together, these two results tell a story: when targets get harder, users take longer (MT ↑) but maintain accuracy (points ≈ constant). In competitive FPS, this translates to a strategic decision: rush easy shots, slow down on hard ones.

**Limitations.** This was a single-participant test (me), so the results won't generalize to everyone. Different players have different mouse skills, sensitivities, and reaction times. Trial-to-trial noise (fatigue, focus, even my mouse grip) also dragged the R² down. And since I only missed 5 shots out of 100, accuracy was near perfect, which made the accuracy regression pretty insensitive.

## Broader Application
Although designed for FPS aim training, the same interaction applies to any cursor-to-target task under time pressure. A concrete example: **online concert ticket purchasing** with a tight time limit. A target could represent a seat on a digital seating map. Users must select a specific seat from many small, closely positioned options and the size and distance of those seats directly affect how quickly and accurately users can make their selection.

## Files
- `index.html` —  experiment
- `result.csv` — raw trial data (100 rows)
- `GraphMTvsID.png` — Fitts' Law regression
- `GrapACCvsID.png` — Accuracy regression
- `README.md` — report
