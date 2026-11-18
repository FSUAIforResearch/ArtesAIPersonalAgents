# Example Output: Lab Onboarding Assistant

Below is an example of what your ArtesAI **Lab Onboarding Assistant** will generate when given the prompts in [`example-input.md`](./example-input.md) (using the fictional Cypress Computational Research Lab knowledge pack):

---

## Example A — First-Week Checklist & Contacts
- **Day 1:** Introduce yourself in `#onboarding`, send **Jordan Lee** (Lab Manager) your university email, read the Lab Overview and Data Handling Policy, and attend a 20-minute introductory meeting with **Alex Rivera** (Graduate Mentor).
- **Day 2:** Ask **Jordan Lee** for read-only access to the training-data folder, install Python 3.11 and Git on your workstation, and clone the lab's demo repository once access is approved.
- **Day 3:** Create a virtual environment, install packages from `requirements.txt`, run the smoke-test script on synthetic sample data, and log any setup issues in the onboarding issue tracker.
- **Day 4:** Read the Project Atlas starter guide, reproduce the example metrics on the demonstration dataset, and discuss data leakage and train/validation/test splits with **Alex Rivera**.
- **Day 5:** Give a 3-minute update at the weekly check-in with **Alex Rivera**, choose an approved starter task, and confirm access to the shared experiment log.

For all dataset or computing access requests, contact **Jordan Lee**. *(Sources: `02_first_week_checklist.md`, `01_lab_overview.md`)*

---

## Example B — Plain-Language Project Explanation
**Project Atlas** teaches a computer program to sort *synthetic* microscopy images into three categories (`Class A`, `Class B`, and `Class C`). It uses a **convolutional neural network (CNN)**—a type of machine learning model that learns to recognize visual patterns (like shapes and textures) from labeled examples.

In the starter workflow, you resize images to `128 × 128` pixels, scale pixel values between `0` and `1`, and split the images into **70% training** (to teach the model), **15% validation** (to check progress during training and watch for overfitting), and **15% test** (saved strictly for final evaluation). You then measure performance using overall accuracy, per-class precision and recall, **macro F1** (which weights all three classes equally even if one class has fewer images), and a confusion matrix. Because the dataset is synthetic for onboarding, it is a training exercise and **not evidence of real-world scientific performance**. *(Source: `04_atlas_project_guide.md`)*

---

## Example C — Unknown Information / Hallucination Test
The lab Wi-Fi password and any change to tomorrow's meeting time are **not documented** in the uploaded lab files (the only documented meetings are Monday `10:00–10:30 a.m.` in Science Building Room 210 and Thursday `2:00–3:00 p.m.` hybrid). Please check the `#onboarding` channel or ask **Jordan Lee** (Lab Manager) to confirm rather than relying on a guess. *(Source: `01_lab_overview.md`)*

---

## Example D — Data Security & Policy Check
**No.** According to the lab's Data & Computing Policy, restricted research data must **never** be uploaded to public AI tools or personal cloud accounts, and must only be stored in approved lab storage. In addition, access to restricted datasets requires prior approval from **Dr. Maya Patel** (PI) and provisioning by **Jordan Lee** after you complete the data-handling orientation. For onboarding exercises, use only the synthetic `atlas-demo` dataset. *(Sources: `03_data_and_security_policy.md`, `02_first_week_checklist.md`)*

---

## Example E — Two-Week Onboarding Plan (`onboarding-plan-builder`)

*(Because no specific start date was provided, this plan uses relative **Day 1–Day 10** labels. Share your start date if you would like an exact calendar schedule.)*

### Week 1: Official Documented Onboarding Checklist

| Day | Task | Contact | Source |
| :--- | :--- | :--- | :--- |
| **Day 1** | Introduce yourself in `#onboarding`, send university email to Jordan Lee, read Lab Overview and Data & Computing Policy, and attend 20-minute intro meeting with Alex Rivera. | Jordan Lee, Alex Rivera | `02_first_week_checklist.md`, `01_lab_overview.md` |
| **Day 2** | Request read-only access to the training-data folder from Jordan; install Python 3.11 and Git; clone the demo repository **after** access is approved. | Jordan Lee | `02_first_week_checklist.md` |
| **Day 3** | Create a Python virtual environment, install `requirements.txt`, run the smoke-test script on synthetic sample data, and record any setup issues in the onboarding issue tracker. | Alex Rivera (for code/setup questions) | `02_first_week_checklist.md`, `01_lab_overview.md` |
| **Day 4** | Read the Project Atlas starter guide, reproduce the baseline metrics on the synthetic demo dataset, and review train/validation/test splits (70%/15%/15%) and data leakage with Alex. | Alex Rivera | `02_first_week_checklist.md`, `04_atlas_project_guide.md` |
| **Day 5** | Give a 3-minute update at the weekly check-in with Alex, select an approved starter task, and verify access to the shared experiment log. | Alex Rivera | `02_first_week_checklist.md` |

### Week 2: Suggestions — Not Official Lab Requirements

| Day | Suggested Task *(Not Mandatory)* | Contact | Source Basis |
| :--- | :--- | :--- | :--- |
| **Day 6** | *Suggestion*: Inspect the `atlas-demo` preprocessing pipeline (`128 × 128` resize and `[0, 1]` normalization) and verify that `random seed 42` is set in your training script. | Alex Rivera | `04_atlas_project_guide.md` |
| **Day 7** | *Suggestion*: Run the 10-epoch baseline CNN (`Adam` + cross-entropy loss) and log the dataset version, code commit ID, configuration, accuracy, per-class precision/recall, macro F1, and confusion matrix in the shared experiment log. | Alex Rivera | `04_atlas_project_guide.md`, `03_data_and_security_policy.md` |
| **Day 8** | *Suggestion*: Plot or compare the training loss vs. validation loss across the 10 epochs to check for overfitting, keeping the 15% test split untouched for final evaluation. | Alex Rivera | `04_atlas_project_guide.md`, `03_data_and_security_policy.md` |
| **Day 9** | *Suggestion*: Work on the starter task approved by Alex on Day 5 and document any model bugs or questions for Thursday's research methods discussion (`2:00–3:00 p.m.`). | Alex Rivera | `01_lab_overview.md`, `02_first_week_checklist.md` |
| **Day 10** | *Suggestion*: Review your Week 2 experiment log entries with Alex and ask Dr. Patel and Jordan if your next task requires approval for additional datasets. | Alex Rivera, Dr. Maya Patel, Jordan Lee | `01_lab_overview.md`, `03_data_and_security_policy.md` |

> **Data-Security Reminder**: Use only the synthetic `atlas-demo` data during onboarding. Do not request or download restricted datasets until you have completed the data-handling orientation and received approval from **Dr. Patel** and provisioning from **Jordan Lee**. Never upload restricted lab data or secrets/API keys to public AI tools, personal cloud accounts, or Git repositories. *(Sources: `02_first_week_checklist.md`, `03_data_and_security_policy.md`)*
