# Example Input: Grant & Abstract Coach

Copy and paste either **Example A (NSF Project Summary Coaching)** or **Example B (NIH Project Summary, Project Narrative, & Specific Aims Coaching)** into your ArtesAI **Grant & Abstract Coach** agent:

### Example A — NSF Project Summary, Panel Review, & Broader Impacts Coaching (`/nsf-summary`, `/review`, `/impacts`)
```text
Here is my rough draft of an NSF Project Summary abstract. Please run `/nsf-summary`, `/review`, and `/impacts` to coach me on how to structure and strengthen my text (do not rewrite the abstract for me).

Rough Draft:
Acoustic monitoring is used a lot to study frogs and birds in wetlands, but audio recorders collect thousands of hours of recordings that nobody has time to listen to. Existing machine learning models trained on clean lab or global datasets fail badly when deployed in noisy Florida pine flatwoods and ephemeral wetlands because of wind, cicadas, and overlapping calls from rare species like the frosted flatwoods salamander and ornate chorus frog. In this project, we want to explore using self-supervised audio foundation models that can adapt to noisy wetland environments with very few labeled examples. First, we will collect audio data from 20 wetland sites in the Apalachicola National Forest. Second, we will build a few-shot domain adaptation method that separates background insect noise from target amphibian vocalizations. Third, we will study how hydroperiod changes affect calling phenology. For broader impacts, we will train two graduate students and put our code on GitHub.
```

### Example B — NIH Project Summary/Abstract, Project Narrative, & Specific Aims Coaching (`/nih-summary`)
```text
Here is my draft for an NIH R21 proposal targeting the National Institute on Aging (NIA). Please run `/nih-summary` to audit my draft Project Summary/Abstract, my draft Project Narrative, and my two Specific Aims, and coach me on what to revise in my own words.

Draft Project Summary/Abstract:
Older adults living in rural North Florida face high rates of heat-related emergency room visits during extreme summer heat waves, especially those taking antihypertensive or anticholinergic medications that impair thermoregulation. Right now public heat advisories only use outdoor weather station data, which misses dangerous indoor nighttime heat trapping in older manufactured and uninsulated homes. We want to explore whether pairing low-cost indoor temperature/humidity sensors with wearable heart-rate variability (HRV) bands can detect early physiological heat strain. In Aim 1, we will study indoor microclimate and wearable HRV across rural older adults over the summer to find out if indoor heat correlates with HRV drops. In Aim 2, using the validated HRV threshold discovered in Aim 1, we will build a risk score to guide community health worker check-in calls.

Draft Project Narrative:
This project investigates longitudinal autonomic nervous system parasympatholytic decompensation via heart-rate variability telemetry coupled with thermodynamic microclimate logging in geriatric pharmacotherapy cohorts, establishing a multi-variable predictive algorithm to reduce morbidity.
```
