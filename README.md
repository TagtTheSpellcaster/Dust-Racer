# Dust Racer

![Version](https://img.shields.io/badge/version-1.17-blue)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Single file](https://img.shields.io/badge/distribution-single_file-lightgrey)

Off-road variant of Pole Racer: same engine, modes, circuits and controls, with 4x4 vehicles, dirt terrain and a bumpy road. Single self-contained `offroad.html`, no dependencies.

## What differs from Pole Racer

| | Pole Racer | Dust Racer |
| --- | --- | --- |
| Vehicle | Open-wheel race car | 4x4 (jeep-like) |
| Surface | Asphalt, lane markings, red/white kerbs | Dirt, sand, gravel, mud; no markings, soft verges, stones and scrub |
| Road profile | Flat | Rough: continuous small undulation plus larger bumps and dips |
| Top speed | 256 km/h | 140 km/h |
| Hazards | Corners, scenery | Corners, scenery, **and bumps/dips that can roll the vehicle** |

## Terrain

* Rises and falls of the road are made visible by shading: slopes facing you are lighter, slopes falling away are darker, and the road edge and ground follow the profile.
* The vehicle follows the ground. When the road falls away faster than free fall, it takes off: the higher the bump and the higher the speed, the higher and longer the jump (at full speed the biggest bumps give about 0.9 s of air time and a few metres of height; at about half speed most bumps no longer launch the vehicle). A compressed suspension adds a small extra kick at take-off.
* **While airborne steering is reduced to 25%**, in every mode. A hard landing costs speed and the vehicle rebounds with one or more smaller hops. A soft shadow on the ground shows where it will land.
* Large bumps and deep dips are placed along every circuit (none inside tunnels or on bridges, none near the start line).

## Hills

The circuits now include long climbs and descents on top of the bumps and dips (gradients up to about 9–10%). Uphill reduces acceleration and the top speed you can hold, downhill increases it, so you accelerate more easily and brake less effectively going down. The effect grows from Easy to Expert (Easy only slows noticeably on the steepest climbs). Hills are flattened on bridges and in tunnels and fade in and out around the start line. Opponents slow down uphill and speed up downhill by a smaller amount. The strength is set by `HILLA` (height) and `hg` per driving mode in the source.

## Rolling over

A roll starts in the air and ends on landing. When the vehicle leaves a **bump** at speed, it can start to tilt sideways in flight if the driver is **steering at the same time** (or the vehicle is being pushed sideways in a corner); the larger the jump, the faster the tilt. On touchdown the accumulated tilt is released: below a threshold the vehicle lands hard (speed loss, wobble) and stays upright, above it the vehicle rolls over. **Dips never roll the vehicle.** Slowing down shortens and lowers the jump, so it reduces the risk quickly.

| Mode | Corners | Bumps and dips |
| --- | --- | --- |
| **Easy** | All corners flat out | Bounces and loses speed on landing, never rolls the vehicle |
| **Intermediate** | Wide corners flat out | Rolls only after a large jump (roughly the biggest bumps at near full speed) combined with steering in the air or at take-off |
| **Expert** | Even wide corners need a lift | Rolls after medium and large jumps while steering; at full speed it can roll even when going straight into the highest bumps of a circuit |

Hitting trees, walls, tunnel walls, rock walls or bridge edges still destroys the vehicle as in Pole Racer. The speed figures above come from an automated driving test on one circuit, not from extensive human play.

## Running and controls

Open `offroad.html` in a modern browser. Controls, game modes, day/night, minimap (`T`), screenshot (`K`, saves a PNG), circuits and scoring are the same as in Pole Racer. Arcade time limits include a 12% allowance for the rougher surface. Best score and settings use their own `localStorage` keys (`dr_*`), separate from Pole Racer.

## Changes after 1.0

* **1.17**: Climbs and descents added; uphill slows the vehicle, downhill speeds it up.
* **1.16**: Screenshot key (`K`).
* **1.15**: Viaduct Run: free-standing waterfall pillars replaced by the same continuous, opaque mountain ranges with animated waterfalls used in Cascade Valley.
* **1.14**: Start-line stands lightened (about 25-30% less drawing time near the start line); the stand banner easter egg removed and replaced by one roadside sign per circuit.
* **1.13**: Easter eggs adjusted.
* **1.12**: A few easter eggs. Find them yourself.
* **1.11**: Cornering drift scaled to 80% of the road game's value (the lower top speed made corners last longer in time); roll-overs made easier to trigger: lower jump thresholds, and lateral push in a corner now counts like steering.
* **1.10**: Warning signs before the sharper corners in Intermediate and Expert modes: 1 to 3 chevrons pointing in the turn direction (yellow, orange, red), based on the speed at which the corner can be held with the current mode's drift. Not shown in Easy. The level is relative, not a speed limit.
* **1.9**: Roll-overs reworked: the tilt builds up in flight (visible on the vehicle) and is discharged on landing; they need a bump jump plus steering (Expert also straight into the highest bumps); dips no longer roll the vehicle.
* **1.8**: Crowd audio reworked: a continuous babble of synthesized voices (formant-filtered, not white noise) that is already audible at the start, swells as the car approaches the start line, peaks with a louder cheer layer when passing at speed, and fades after.
* **1.7**: Scenery sprites (posts, rocks, trees, billboards) are now drawn in depth order together with the road segments, so walls and hills hide what is behind them (fixes posts/rocks/trees showing through the Coast Road wall).
* **1.6**: Coast Road: the rock wall is now fully opaque at distance (reduced haze blending).
* **1.5**: Grandstands with a cheering crowd on both sides of the start line (before and after it); the crowd waves and bobs as the car passes and a cheer sound plays on each pass, in arcade and training.
* **1.4**: Steering while airborne is reduced to 25% instead of being disabled.
* **1.3**: Coast Road: inclined (about 12.5°), more uniform rock wall (same as Pole Racer 1.14).
* **1.2**: Cascade Valley: waterfalls descend from continuous opaque mountain ranges (same as Pole Racer 1.13).
* **1.1**: Cascade Valley reworked as in Pole Racer 1.12 (continuous animated river under four bridges, valley slopes with animated waterfalls).

## Known limitations

* The road profile is a height offset on a flat-curve engine: no banking, no side slopes, and the same height profile is used for every lane.
* Opponents follow the ground but do not bounce or roll.
* Thresholds, bump sizes and time limits are tuned by simulation only; they probably need play-testing.

## License

Copyright (C) the authors of Pole Racer. Licensed under the **GNU Affero General Public License, version 3**, as for Pole Racer. This program is distributed without any warranty. See the [GNU AGPL v3](https://www.gnu.org/licenses/agpl-3.0.html).
