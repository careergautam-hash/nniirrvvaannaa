import numpy as np

def elephant(t, params):
    a_x, b_x, a_y, b_y = params
    x = sum(a * np.cos(k * t) + b * np.sin(k * t) for k, (a, b) in enumerate(zip(a_x, b_x)))
    y = sum(a * np.cos(k * t) + b * np.sin(k * t) for k, (a, b) in enumerate(zip(a_y, b_y)))
    return x, y

# Example parameters for elephant shape
a_x = [50, 18, 12, -14, 40]
b_x = [-30, 8, -10, -60, -20]
a_y = [0, 0, 0, -60, 0]
b_y = [0, 8, -10, 0, 20]

params = (a_x, b_x, a_y, b_y)
t = np.linspace(0, 2 * np.pi, 1000)
points = [elephant(tt, params) for tt in t]

# Convert to SVG path
svg_path = "M " + " ".join(f"{x + 200},{y + 200}" for x, y in points)
svg = f'''
<svg width="400" height="400">
  <path d="{svg_path}" stroke="black" fill="none"/>
</svg>
'''

with open("elephant.html", "w") as f:
    f.write(svg)