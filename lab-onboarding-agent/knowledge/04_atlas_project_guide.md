# Project Atlas: Starter Guide (FICTIONAL DEMO)

Goal: train a baseline CNN to categorize synthetic microscopy images into Class A, Class B, and Class C.

## Workflow
1. Load images from the synthetic `atlas-demo` folder.
2. Resize each image to 128 × 128 pixels and normalize pixel values to [0, 1].
3. Use the supplied split: 70% training, 15% validation, 15% test.
4. Train a small CNN for 10 epochs using cross-entropy loss and Adam.
5. Report overall accuracy, per-class precision and recall, macro F1, and a confusion matrix.
6. Compare validation and training loss to check for possible overfitting.

## Reproducibility
- Set random seed 42.
- Save training configuration and code commit ID with every run.
- Do not treat this synthetic exercise as evidence of real-world scientific performance.

## Common questions
- Why macro F1? It gives equal weight to each class, including classes with fewer examples.
- Who helps with model bugs? Alex Rivera, the graduate mentor.
- Can we publish these results? This onboarding exercise is not a publication-ready study; talk to Dr. Patel before any public release.
