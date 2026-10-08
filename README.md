# Operatory 624

A 3D escape room for reviewing DEN 624 Periodontology I. Players are locked in an operatory after hours. Each of seven workstations releases one digit of the exit code once its cases are solved. Plan on about 15 minutes.

Everything is in `index.html`. It needs no build step and no install. Three.js and the fonts load from public CDNs, so the browser needs internet access.

## Playing

- Open `index.html` in a browser. To host it, turn on GitHub Pages for this repository (Settings → Pages → deploy from the branch root), or drop the file onto any static host.
- Drag to look around. Walk with W/A/S/D or the arrow keys, or click the floor. Click a glowing station to open it, or use the station bar at the bottom of the screen, which also works on phones and with a keyboard.
- Stations can be done in any order. A wrong answer adds 15 seconds and a hint adds 30. After two misses, the player can reveal the answer and move on.
- Every answer shows the reasoning from the slides. After escaping, a debrief shows time, first-try accuracy by objective, and a review sheet of every missed case. **Copy results** produces a short text summary students can submit.

## What each station covers

All content comes from `Perio Doc.pdf`.

| # | Station | Objective / lecture | Cases |
|---|---------|---------------------|-------|
| 1 | X-ray Lightbox | Objective 1: Radiographic Features | 3 |
| 2 | Bone Model | Objective 2: Bone Morphology & Trabecular Changes | 3 |
| 3 | Charting Terminal | Objective 3: Periodontal Disease Classification (plus the staging and grading slides) | 4 |
| 4 | Case File Cabinet | Objective 4: Differential Interpretation | 3 |
| 5 | Clinical Atlas | Diagnosis and Classification Part I; 1999 vs 2017 classification | 3 |
| 6 | Microscope Bench | Role of Dental Biofilm in Pathogenesis | 3 |
| 7 | Instrument Tray | Instruments Utilized in Periodontal Therapy; Mirror and Finger Rests | 4 |

Objectives 1–4 are the Lesson Objectives from the Radiographic Interpretation lecture, the only formal objectives in the document. Stations 5–7 cover the other lectures in the PDF.

The PDF's text for Objective 2 mentions caries, but no slides cover caries; the slides under that heading cover alveolar bone morphology and trabecular changes. Station 2 follows the slides.

## Editing questions

The questions live in the `STATIONS` array near the top of the first `<script>` in `index.html`. Each question has a `type`:

- `mcq`: `options` and the index of the correct `answer`
- `multi`: `options` and an `answer` array of correct indexes
- `num`: a numeric `answer`, a tolerance `tol`, and a `unit`
- `match`: `pairs` of `[prompt, answer]`; the answers are shuffled into a lettered bank
- `compose`: `rows`, each with a `label`, `options` and the index of the correct `answer`
- `order`: `items` listed in the correct order; the game shuffles them

Every question also has a `hint` and an `explain` (shown after it is answered). The code digits and the door's slot order are randomized each game, so students cannot share a code.
