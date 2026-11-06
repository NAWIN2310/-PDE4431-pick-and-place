# -PDE4431-pick-and-place
coursework part 2 
# PDE4431: Robot Manipulation — Epson Pick-and-Place

Automated multi-station pick-and-place routine programmed in **Epson SPEL+** for Epson industrial manipulators using the **Epson RC+** development environment.

* **Module:** PDE4431 (Robot Manipulation)
* **Institution:** Middlesex University Dubai
* **Student:** Nawin Ganesan
* **Platform:** Epson RC+ 7.0 / SPEL+

---

## Overview

This repository contains the source routines, motion planning architecture, and workcell verification protocols for an automated transfer sequence. The application coordinates the acquisition of workpieces from a datum pickup station and their sequential distribution across three drop targets (`droppoint1`, `droppoint2`, and `droppoint3`).

Rather than relying on a single monolithic script, the project utilizes a modular, function-based structure designed for clarity, debuggability, and maintainability.

---

## Key Automation Features

* **Modular Architecture:** Dedicated subroutines (`pick_up`, `drop_point1`, `drop_point2`, `drop_point3`) orchestrated via a master `main` routine.
* **Digital I/O Handshaking:** Output channel 11 directly controls the pneumatic solenoid valve driving the gripper jaws (`On 11` to clamp, `Off 11` to release).
* **Mechanical Settling Delays:** Deliberate 2-second stabilization pauses (`Wait 2`) allow pneumatic line pressure to equalize and physical oscillations to dissipate before arm translation.
* **Dynamic Clearance Offsets:** Vertical approach and retract waypoints are generated dynamically using `+Z(100)` to ensure clear vertical motion and prevent side collisions with workspace fixtures.
* **Continuous Path (CP) Blending:** Continuous path (`CP`) modifiers appended to transition waypoints enable radius rounding to minimize cycle times and joint shock.

---

## Program Structure & Logic Flow
