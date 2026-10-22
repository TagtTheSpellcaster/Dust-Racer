# Dust Racer

![Version](https://img.shields.io/badge/version-1.4-blue)
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

## Rolling over

A roll happens when the severity of a feature exceeds the limit of the driving mode. Severity grows with the **square of speed**, like the cornering load, so slowing down reduces it quickly.

| Mode | Corners | Bumps and dips |
| --- | --- | --- |
| **Easy** | All corners flat out | Bounces and loses speed on landing, never rolls the vehicle |
| **Intermediate** | Wide corners flat out | Only the largest features roll the vehicle at full speed (roughly above 78% speed) |
| **Expert** | Even wide corners need a lift | Medium and large features roll the vehicle at full speed (the largest need about 60% speed) |

Hitting trees, walls, tunnel walls, rock walls or bridge edges still destroys the vehicle as in Pole Racer. The speed figures above come from an automated driving test on one circuit, not from extensive human play.

## Running and controls

Open `offroad.html` in a modern browser. Controls, game modes, day/night, minimap (`T`), circuits and scoring are the same as in Pole Racer. Arcade time limits include a 12% allowance for the rougher surface. Best score and settings use their own `localStorage` keys (`dr_*`), separate from Pole Racer.

## Changes after 1.0

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
