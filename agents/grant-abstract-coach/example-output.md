# Example Output: Grant & Abstract Coach

Below is an example of what your ArtesAI **Grant & Abstract Coach** will generate when given the prompts in [`example-input.md`](./example-input.md):

---

## Example A Output: NSF Project Summary, Panel Review, & Broader Impacts Coaching

### 1. 5-Part Abstract Architecture Audit

| Element | Status | Diagnostic Notes on Your Current Draft |
| :--- | :--- | :--- |
| **1. Hook & Unmet Need** | **Strong** | Your opening sentence (*"audio recorders collect thousands of hours of recordings that nobody has time to listen to"*) immediately establishes the practical bottleneck of passive acoustic monitoring (PAM). |
| **2. Knowledge Gap** | **Strong** | Your second sentence clearly explains *why* current ML models fail in Florida pine flatwoods (wind, cicadas, overlapping calls, and scarce training labels). |
| **3. Central Hypothesis / Innovation** | **Needs Tightening** | *"We want to explore using self-supervised audio foundation models..."* names a tool class, but does not state a testable hypothesis or what is algorithmically new about your approach. |
| **4. Concrete Research Aims** | **Needs Tightening** | Your three steps (`First... Second... Third...`) give a clear sequence, but use weak verbs (*"explore"*, *"study"*) and omit quantitative targets (how many hours of audio, how few labeled examples, and what baseline models you will beat). |
| **5. Societal / Broader Impacts** | **Needs Major Work** | Your final sentence (*"train two graduate students and put our code on GitHub"*) describes standard baseline research execution rather than a dedicated NSF Broader Impacts strategy. |

---

### 2. NSF 1-Page Project Summary Compliance & Coaching (`/nsf-summary`)

#### A. Mandatory NSF PAPPG Heading Check
- 🚨 **Compliance Blocker**: Your draft is written as a single undivided paragraph. Under the **NSF PAPPG**, a 1-page Project Summary **must** contain three separate, explicitly labeled sections—**`Overview`**, **`Intellectual Merit`**, and **`Broader Impacts`**—or the proposal may be returned without review.
- **Length Check**: Your draft is currently **154 words** (~1/3 of a page), giving you ~300–350 words of room to expand your technical aims, Intellectual Merit, and Broader Impacts to fill the 1-page budget.

#### B. How to Map & Revise Your Existing Sentences
1. **What to Put Under `Overview`**:
   - Keep your first two sentences as the opening problem statement, and keep your three `First / Second / Third` sentences as **Aim 1, Aim 2, and Aim 3**.
   - **Verb & Specificity Upgrades to Make in Your Own Words**:
     - In sentence 3, replace *"we want to explore using"* with a direct objective or central hypothesis (e.g., state how separating structured insect noise from transient calls allows adaptation with `[N]` labeled examples per species).
     - In *"First, we will collect audio data from 20 wetland sites..."*, specify how many seasons/months of deployment and what expert annotations you will produce.
     - In *"Third, we will study how hydroperiod changes affect calling phenology"*, replace *"study"* with a measurable verb (*quantify*, *model*, or *test*) and name the hydrological variables you will link to calling onset/duration.
2. **What to Put Under `Intellectual Merit` (Currently Missing as a Separate Section)**:
   - Write 3–5 sentences explaining **how** this work advances both machine learning (e.g., few-shot domain adaptation under high-amplitude non-stationary biological noise) and wetland ecology (continuous phenological tracking of imperiled subtropical amphibians).
   - State the quantitative evaluation metric (e.g., macro F1-score or precision/recall at low label counts) you will use to validate Aim 2.
3. **What to Put Under `Broader Impacts` (Replace Final Sentence)**:
   - Move *"put our code on GitHub"* into open-science dissemination, and expand this section to 120–150 words using the coaching frameworks in Section 4 below.

---

### 3. Reviewer Critique Simulator (`/review`)

#### Reviewer 1: The Tired Generalist
- **Major Strength**: The problem is immediately relatable—any panelist can understand why loud cicadas and wind in a Florida wetland break off-the-shelf audio classifiers.
- **Major Confusion**: You write *"overlapping calls from rare species like the frosted flatwoods salamander and ornate chorus frog."* Because Ambystomatid salamanders (`Ambystoma cingulatum`) are largely non-vocal in field acoustic monitoring compared to frogs (`Pseudacris ornata`), an ecology panelist will immediately question whether you are claiming to detect salamander calls directly.
- **Revision Coaching Prompt**: Revise that phrase in your opening to clarify whether you are acoustically monitoring **indicator chorus frog guilds** that share ephemeral breeding ponds with the federally listed frosted flatwoods salamander.

#### Reviewer 2: The Methodological Skeptic
- **Tough Question 1 (Aim Interdependence)**: *"If your First step is collecting new audio from 20 sites in the Apalachicola National Forest, is your Second step (building the few-shot domain adaptation method) blocked during Year 1 while sensors are in the field?"*
  - **How to Preempt in Your Draft**: Add one phrase explaining what existing archival recordings or synthetic noise-mixing datasets you will use to start Aim 2 algorithm development in Year 1.
- **Tough Question 2 (Novelty vs. Off-the-Shelf Fine-Tuning)**: *"How does your Second step differ from simply fine-tuning BirdNET or Perch on 20 labeled frog calls?"*
  - **How to Preempt in Your Draft**: Name the specific technical mechanism that separates background insect choruses from target calls (rather than just calling it *"a few-shot domain adaptation method"*).

#### Reviewer 3: The Impact & Feasibility Pragmatist
- **Scope & Feasibility Assessment**: Maintaining 20 acoustic recorders in the Apalachicola National Forest is realistic, provided you briefly mention whether you already have field access/permits or agency collaboration.
- **High-Leverage Coaching Recommendation**: In your Third step, state how your hydroperiod-phenology findings will inform a real conservation management decision (such as prescribed burn windows or wetland restoration).

#### Panel Consensus Summary
- **Current Readiness**: `Competitive with Revisions`
- **Top 3 Revisions for You to Make Next**:
  1. Split your text into the three mandatory NSF PAPPG headings (`Overview`, `Intellectual Merit`, `Broader Impacts`).
  2. Clarify the acoustic distinction between vocal indicator frogs and the frosted flatwoods salamander, and state how Aim 2 starts in Year 1.
  3. Expand your 12-word Broader Impacts sentence using the planning matrix below.

---

### 4. Broader Impacts Coach (`/impacts`)

#### Why Your Current Sentence Needs Expansion
NSF reviewers treat *"train two graduate students and put our code on GitHub"* as baseline research execution expected of every funded grant, not a standalone Broader Impacts plan.

#### 3 Tailored Activity Frameworks to Consider for Your Lab
Choose 2–3 of the directions below that match your lab's actual partnerships and capacity, and fill in the bracketed specifics in your own words:

| Activity Direction | Target Audience & Potential Partner | Concrete Deliverable | Evaluation Metric (What You Should Quantify in Your Draft) |
| :--- | :--- | :--- | :--- |
| **1. Cross-Disciplinary Undergrad Cohort** | FSU Ecology & Computer Science undergraduates (e.g., via FSU UROP) | Field-to-AI training module + student-curated wetland call library | How many undergrads will you mentor per year (`[N]`), and how will you assess their skill gains? |
| **2. Land Manager No-Code Tool & Workshop** | Wildlife biologists at US Forest Service (Apalachicola NF) & Florida FWC | Lightweight GUI plugin (e.g., Raven/Audacity wrapper) + practitioner workshop | Which agency contact will test the tool, and how many hours of manual listening will it save? |
| **3. K-12 Wetland Soundscape Module** | North Florida (Leon/Wakulla/Liberty County) middle or high school classrooms | Interactive spectrogram lesson on local amphibians & wetland hydrology | How many teachers/classrooms (`[N]`) will you reach? |

#### 4-Sentence Structural Blueprint for Writing Your Broader Impacts Section
When you draft your ~120–150 word `Broader Impacts` section, try following this 4-sentence arc:
- **Sentence 1 (Theme)**: State how your project connects wetland biodiversity conservation, interdisciplinary STEM training, and usable tools in North Florida.
- **Sentence 2 (Workforce / Undergraduates)**: Describe how you will cross-train `[N]` undergraduate and graduate students across field ecology and machine learning (naming specific FSU programs like UROP if applicable).
- **Sentence 3 (Practitioner / Community Partner)**: Describe how you will package your detector so non-coding wildlife biologists (e.g., USFS / FWC) or local K-12 educators can use it, including how you will evaluate its adoption.
- **Sentence 4 (Open Infrastructure)**: Specify where the annotated Apalachicola audio benchmark dataset and pretrained model weights will be archived for public reuse.

---

## Example B Output: NIH Summary, Narrative, & Specific Aims Coaching (`/nih-summary`)

### 1. Audit of Your NIH `Project Summary / Abstract` (Max 30 Lines of Text)
- **Length & RePORTER Check**: Your current draft is **8 sentences (~155 words / ~13 lines)**—well under NIH's 30-line ceiling, leaving you ~15 lines to add critical methodological and quantitative detail.
- **NIA Mission Alignment**: You open with a strong geriatric vulnerability (*"antihypertensive or anticholinergic medications that impair thermoregulation"* in rural adults 65+), which aligns directly with the **National Institute on Aging (NIA)**. Consider explicitly naming NIA's mission in your long-term goal sentence.
- **Sentence-Level Coaching on Your Draft**:
  - **Upgrade *"We want to explore whether..."***: In NIH review, *"explore"* signals a fishing expedition. Replace *"explore whether"* with a testable **Central Hypothesis** (e.g., hypothesize that indoor nocturnal heat load combined with heat-sensitizing medication burden predicts wearable HRV decline prior to symptomatic heat exhaustion).
  - **Add Sample Size & Design Details to Aim 1**: In *"we will study indoor microclimate and wearable HRV across rural older adults over the summer"*, replace *"study"* with *quantify* or *model*, and insert your planned sample size (`N = ?`), monitoring duration (`? weeks`), and statistical approach (e.g., longitudinal mixed-effects models).

### 2. Audit of Your NIH `Project Narrative` (Max 2–3 Sentences)
- 🚨 **Lay-Language Red Flag**: Your current draft sentence—*"This project investigates longitudinal autonomic nervous system parasympatholytic decompensation via heart-rate variability telemetry coupled with thermodynamic microclimate logging in geriatric pharmacotherapy cohorts..."*—is packed with technical clinical jargon (`parasympatholytic decompensation`, `telemetry`, `pharmacotherapy cohorts`).
- **NIH SF424 Rule**: The **Project Narrative** (2–3 sentences max) is read by non-specialists and the public as your **Public Health Relevance Statement**.
- **How to Revise It in Your Own Words**:
  - **Sentence 1 (The Problem)**: Explain in plain everyday words that older adults taking common blood pressure or chronic-disease medications are at high risk for dangerous heat exhaustion inside older, uninsulated rural homes during summer heat waves.
  - **Sentence 2 (What Your Project Does & Why It Matters for Health)**: State simply that by pairing low-cost indoor temperature sensors with wearable heart-rate monitors, your project will create an early-warning tool so community health workers can check on vulnerable seniors and prevent emergency hospital visits.

### 3. Audit of Your `Specific Aims` Structure & Independence
- 🚨 **Critical Study Section Vulnerability ("Domino Effect" Between Aim 1 and Aim 2)**:
  - Look closely at your wording in Aim 2: *"In Aim 2, **using the validated HRV threshold discovered in Aim 1**, we will build a risk score..."*
  - In an NIH study section, making Aim 2 depend on *"the validated HRV threshold discovered in Aim 1"* is a classic **contingent-aim trap**: a skeptical reviewer will argue that if Aim 1 does not yield a single clean HRV threshold, Aim 2 fails before it starts.
  - **How to Decouple Aim 1 and Aim 2 in Your Revision**:
    - Frame **Aim 1** around characterizing the continuous longitudinal relationship between indoor thermal load (daytime peak vs. nighttime recovery), medication tier, and physiological strain markers (HRV and resting heart rate).
    - Frame **Aim 2** around developing and cross-validating a multi-factor heat-risk score that integrates housing thermal characteristics, medication heat-sensitivity profiles, *and* physiological features—and state a fallback (e.g., established clinical heat-strain/heart-rate thresholds from the literature) so Aim 2 succeeds even if HRV alone has modest predictive power.

### 4. Author Revision Checklist (Next Steps for Your Draft)
1. **Rewrite your Project Narrative in 2–3 plain-English sentences** removing `parasympatholytic decompensation` and `pharmacotherapy cohorts`.
2. **Decouple Aim 2 from Aim 1** by removing *"using the validated HRV threshold discovered in Aim 1"* and specifying how Aim 2 can use multi-modal features and literature thresholds independently.
3. **Add quantitative specifics** to your Project Summary (`N` participants, number of summer weeks, specific HRV metrics, and how you will evaluate Aim 2's risk score).
4. **Expand into the 4-Paragraph Specific Aims Page**: (1) Rural heat burden & outdoor-vs-indoor gap → (2) Long-term goal, R21 objective, central hypothesis, & preliminary feasibility → (3) Decoupled Aims 1 & 2 with working hypotheses → (4) Innovation & how this R21 sets up a future R01 intervention trial.
