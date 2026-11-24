# Kerel hangar fixed for Jolt · 22 Nov 2026

Jolt physics was dropping the Kerel's hangar floor. Turns out one body had a 188k triangle mesh plus 2,638 boxes, more than Jolt can handle in one body. Gave each room's boxes their own body and it works: nobody falls through, and the 100-soldier fight went from 175 ms a frame to 51.
