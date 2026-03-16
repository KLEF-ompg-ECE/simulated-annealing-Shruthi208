# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :**  P.Shruthi  
**Student ID    :** 2310040061
**Date Submitted:** 15-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
[count_clashes() measures the number of conflicts in the timetable, such as two classes scheduled at the same time for the same room, teacher, or student group. It evaluates how good or bad the timetable is. A value of 0 means there are no clashes, which represents a perfect timetable.]
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
[generate_neighbor() creates a new timetable by making a small change to the current timetable, such as swapping time slots or modifying a class schedule. This helps explore different possible solutions. The new timetable is slightly different from the current one but still based on it.]
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
[This line decides whether the new timetable should replace the current timetable. If the new solution has fewer clashes (delta < 0), it is always accepted. Simulated Annealing sometimes accepts worse solutions with a small probability to help escape local minima and explore better solutions later.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379|
| Clashes at iteration 1 |12 |
| Final best clashes |3 |
| Did SA reach 0 clashes? (Yes / No) | |

**Copy the printed timetable output here:**
```
[ Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
  Total clashes : 3]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
[The number of clashes drops quickly in the early iterations, with the biggest decrease occurring near the beginning where it falls from around 12 to about 6. After that, the improvement becomes slower with small reductions to 5, 4, and finally 3 clashes. Yes, the curve eventually flattens out, showing that the algorithm stabilizes and finds a near-optimal timetable.]
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |8              | 31                   | No                 |
| 0.95        |3              | 135                  | No                 |
| 0.995       |3              | 1379                 | No                 |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[From the three plots, fast cooling (0.80) causes the temperature to drop very quickly, so the algorithm stops exploring early and gets stuck with more clashes. Medium cooling (0.95) allows a little more exploration and improves the solution compared to fast cooling. Slow cooling (0.995) decreases the temperature gradually, giving the algorithm more time to search for better timetables. As a result, slower cooling generally produces a better or more stable solution than fast cooling.]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[The cooling_rate 0.95 and 0.995 gave the best results with 3 final clashes. This is because slower cooling allows the algorithm to explore more possible solutions before settling on a final timetable. It avoids getting stuck too early in a poor solution.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3|Slow cooling allows the algorithm to search longer and produce a better timetable with fewer clashes|
| 2 — Cooling rate | cooling_rate =0.95 |3 |A moderate cooling rate balances exploration and convergence better than very fast cooling. |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[From these experiments, I learned that the cooling rate is very important in Simulated Annealing. If the temperature decreases too quickly, the algorithm stops exploring early and may get stuck with more clashes. Slower cooling allows the algorithm to explore more possible solutions and gradually improve the timetable. Therefore, choosing a proper cooling rate helps the algorithm find better results.]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
