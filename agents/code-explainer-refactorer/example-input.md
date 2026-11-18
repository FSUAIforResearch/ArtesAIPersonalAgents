# Example Input: Research Code Explainer & Refactorer

Copy and paste the prompt and legacy Python script below into your ArtesAI **Research Code Explainer & Refactorer** agent:

```text
A former grad student in our ecology lab left this Python script (`sim_pop.py`) with no comments. Please run `/walkthrough` so I understand what it's actually doing and if there are any bugs, and then run `/hpc-ready` so I can run 100,000 simulations on FSU's RCC cluster instead of my laptop.

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

d = pd.read_csv("/Users/kevin/Desktop/ snail_counts_2023.csv")
n0 = d['count'].mean()
r_vals = d['growth'].values

res = []
for i in range(1000):
    p = n0
    for t in range(50):
        r = np.random.choice(r_vals)
        p = p * np.exp(r * (1 - p / 500))
        if p < 2:
            p = 0
    res.append(p)

print("Extinction prob:", res.count(0) / 1000)
plt.hist(res)
plt.show()
```

