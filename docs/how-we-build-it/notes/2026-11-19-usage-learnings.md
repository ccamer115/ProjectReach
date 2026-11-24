# What actually eats usage · 19 Nov 2026

Dug into where the usage goes. It's mostly agents re-reading a big context every turn, times how many agents are running at once. What helps: a short card per helper instead of the whole history, cheaper models for the housekeeping, and checking 3D models with quick geometry reports before anyone looks at renders.
