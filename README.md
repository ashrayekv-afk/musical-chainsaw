# NKPI 9.1.6 — corneal pattern and follow-up

Release identifier: **9.1.6-pattern-followup**

Complete replacement GitHub upload package. Adds a source-bound, adaptive review
section below the original v9.1.5 natural-eye viewer. This is a descriptive research
visualization, NOT a newly trained or validated progression model.

## Upload these five files

Extract **NKPI_v916_GitHub_Upload.zip** once. Replace the following files in the
repository root (keep the config inside its folder):

```
kcn_dual_calculator_app.py
nkpi_runtime.zip
requirements.txt
README.md
.streamlit/config.toml
```

**Keep nkpi_runtime.zip zipped.** Upload the matching launcher and runtime together.
Do not nest all five items inside an extra folder. Keep the main file set to
`kcn_dual_calculator_app.py` and the existing Python **3.12** deployment setting.
Reboot Streamlit, refresh the browser, and confirm **9.1.6-pattern-followup** in the
footer. Import the original report(s), verify the values and eye/visit assignment,
and calculate. Existing sessions do not migrate to a new patient or source automatically.

## What remains unchanged

Every file under `components/cornea/`, `components/extractor/`, and `models/` is
byte-for-byte identical to v9.1.5. That preserves natural-eye appearance, continuous
visual completion, map colors, whole-surface/map/slice modes, thinnest-point behavior,
C audit, extraction, and NKPI calculations. No simulated patient appears in the app.

## New section: Corneal pattern & follow-up

- **One visit:** linked anterior curvature, posterior curvature magnitude, and
  thickness maps; switch to anterior/posterior elevation plus thickness. Select a
  2 mm-diameter region to inspect supported regional means and point values together.
- **Landmarks:** source-map extrema and reported minimum coordinates where valid.
  Sample extrema are NOT device Kmax or a validated cone center. C remains separate.
- **Spatial context:** optional surrounding-ring average; it is not a stable/healthy
  control. Use 3D point and Locate in 3D link the main imported source's coordinates.
- **Two dates:** confirmed scalar C, Kmax and B histories are available even when
  source files are report images. Image-derived patterns are approximate; the new
  section does not convert them into quantitative regional progression curves.
- **Registered numerical maps:** fixed-region changes on common accepted source
  cells across all acquisitions. Compatible grids, fields, declared registration,
  context and adequate support are required. Elevation also requires the same
  explicit reference key. No automatic scan registration or proprietary decoding.
- **Three or more spatial visits / same-day repeats:** use Advanced → attach
  numerical visit history. This requires the documented JSON schema; ordinary ZIP
  import still supplies first/latest maps. The template has mandatory placeholders
  that must be replaced with verified non-identifying keys, not guessed values.
- **Every acquisition remains visible:** native repeated scans are individual dots;
  visit means and min–max ranges are descriptive, not confidence intervals.
- **Audit:** export source, coordinates, region settings, values and gating reasons.

### Two important source distinctions

A continuous 3D surface may use visual completion. The new calculations NEVER use
those filled surfaces/colors, smoothed geometry or locally recovered report colors.
Only accepted source values enter the new descriptive calculations. Insufficient
source support stays unavailable rather than being called stable.

The original calculator's treatment and quality fields can be unknown. Unknown or
treated context does not become a natural-history comparison: automatic regional
changes are withheld until the numerical history explicitly documents a common
segment. Confirmed scalar observations remain visible without connecting uncertain
treatment dates. Quality-warning acquisitions cannot enter regional changes.
Unknown-quality numerical acquisitions retain an explicit caution.

## Limits and deployment

Not a diagnostic or treatment recommendation. Baseline patterns do not predict
future progression. No significance threshold, new risk score, 95% interval, or
progression probability is calculated. Source-reference declarations and patient
association require human verification. Numerical adapter/export accuracy has not
been independently validated against your clinic's device.

Numerical history stays in the browser session and is cleared on source/input
change or Next patient. Audits are local downloads. Use only de-identified inputs
on an unapproved public deployment. Browser-only processing is not a privacy approval.

## Actual verification for this release

- 29 new mathematical checks and all 23 JavaScript regression suites passed.
- 45 browser checks passed, including baseline/report/numerical routes, repeats,
  source identity, reset, full map controls, mobile layout and Canvas fallback.
- 10 full-component checks passed using the actual HTML/app.js, original viewer,
  and real Python configuration/results. The extractor iframe was stubbed.
- 41 Python tests passed; 24 eye-result comparisons exactly matched v9.1.5 after
  excluding only the UI version. Both eyes produced PDFs in both calculator modes.
- Matching ZIP hash, manifest, secure extraction and frozen-source integrity checked.

Tests ran locally with Python 3.13.5 and Chromium. Python 3.12 is the retained target,
not a new test claim. **A fresh Streamlit server deployment and full OCR import were
not tested here**: Streamlit was unavailable and network installation failed.
All new browser screenshots and numerical fixtures are simulated engineering cases,
not patient measurements. See `docs/PATTERN_LENS.md` and `docs/V916_VERIFICATION.md`
inside the runtime for implementation, schema, and reproducible test details.
