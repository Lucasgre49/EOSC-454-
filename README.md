# EOSC-454-
Lucas Green EOSC 454 Project Repository
SimPEG Two-Stage Magnetisation Vector Inversion — UXO Detection
Overview
This project implements a two-stage geophysical inversion pipeline in Python using SimPEG to detect and characterise a buried unexploded ordnance (UXO) body from synthetic total magnetic intensity (TMI) data. The key capability is the recovery of both induced and remanent magnetisation simultaneously — something a conventional scalar susceptibility inversion cannot do.

The Problem
Steel UXO bodies are ferromagnetic. They acquire a remanent magnetisation during manufacture that can point in any direction, completely independent of Earth's current ambient field. A standard scalar inversion assumes all magnetisation is parallel to Earth's field (induced only). Applied to a remnantly charged target this produces inflated susceptibility values, incorrect depth estimates, and no directional information whatsoever. Magnetisation Vector Inversion (MVI) removes this assumption entirely, allowing the full magnetisation vector to be recovered from the data.

Workflow
Stage 1 — Scalar susceptibility inversion

Inverts TMI data for a scalar χ model using model_type='scalar'
Physically misspecified for remnant targets but reliably locates the body in space
Recovered χ is converted to an induced magnetisation amplitude and normalised to spatial focussing weights

Stage 2 — Magnetisation Vector Inversion (MVI)

Inverts the same TMI data for a full [Mx | My | Mz] model using model_type='vector'
Stage 1 focussing weights concentrate the solution near the body location
Remanent direction emerges through the data fit — no prior knowledge of remanence is provided
Outputs: magnetisation amplitude |M|, inclination, and declination maps

Requirements
pip install simpeg discretize matplotlib numpy scipy
Tested with SimPEG 0.25.2 and discretize 0.12.0.

Key Parameters
ParameterValueNotesSurvey receivers101 TMI points50 m east–west profile at z = 1 mEarth field55,000 nT, inc = 70°, dec = 15°Mid-latitude CanadaUXO depth3 mCentre of bodyUXO susceptibilityχ = 0.05 SIMild steelRemanent magnetisation8 A/m, inc = −40°, dec = 200°Strongly off-axisKoenigsberger ratio Q3.66Remanence dominates inductionMesh core cell size0.5 m × 0.5 mAdequate for 3 m depth target

Known Limitations

Single 2D profile — declination recovery is unreliable without multi-azimuth or vector component data
No depth weighting — both stages are biased toward shallow solutions
L2 regularisation — amplitude is systematically underestimated; sparse norm inversion would improve this
Stage 1 physics mismatch — scalar chi values are inflated and physically meaningless for remnant targets; they are used only as a spatial locator


Background
The two-stage approach replicates the operational workflow used in real UXO clearance surveys. The survey operator never knows in advance whether a target is remnantly magnetised, so both inversions are run on the same observed data. Stage 1 is fast and stable; Stage 2 recovers the directional information needed to classify the target. Full quantitative characterisation would require a 3D multi-line survey with vector component measurements and sparse norm regularisation.

