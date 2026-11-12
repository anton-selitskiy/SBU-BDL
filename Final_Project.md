# ESE 670 Final Project

## Goal

The project asks you to take one method or combination of methods from the course and either put it to work on a problem you care about or find out, by careful experiments, when and why it works. You choose the problem; the method must come from the course: Bayesian inference and uncertainty, sampling (MCMC, Langevin, HMC), diffusion models, flow matching, optimal transport, or bridges.

By the end you should be able to show three things:

- that you understand the method well enough to state its assumptions and explain its result;
- that you can implement or adapt it and make it run reliably;
- that you can judge its output honestly: with a baseline, a metric that fits the question, and the failures as well as the successes.

## Two tracks

Pick one track. Both are graded on the same rubric; they differ in where the main contribution lies.

|  | Track A: application | Track B: analysis |
| --- | --- | --- |
| Question | Can this method solve my problem, and how well? | When does this method work, fail, or beat another one, and why? |
| Main contribution | A working pipeline on real data from a domain of your choice | Controlled experiments that isolate one factor at a time |
| Data | Real data: images, audio, signals, measurements, your own research data | Synthetic data with known ground truth first, then one real dataset to check that the finding holds |
| Evaluation | Domain metric against at least one baseline | Error against the known truth, as a function of the factor you vary |
| Typical result | "Flow matching restores clipped audio better than an L2 regressor at the same size" | "DDIM needs 3 times fewer steps than DDPM only when the data has well-separated modes" |


## Example ideas

Your own idea is the most welcomed.

**Track A: applications**

- **Uncertainty in a prediction model.** E.g., stochastic gradient Langevin dynamics (SGLD) and/or Bayesian NN on a regression or classification task from your field; calibration (When the model says “80% confident”, is it right about 80% of the time) or sorts test inputs by predicted uncertainty.
- **Conditional generation on a small domain dataset.** A class- or attribute-conditional diffusion or flow-matching model (spectrograms, sensor signals, medical or satellite patches), with classifier-free guidance. 
- **Inverse problems.** Super-resolution, inpainting, denoising or audio bandwidth extension, trained on paired data: condition on the degraded input, or start from it as in bridge matching.
- **Translation between two domains.** Unpaired translation with minibatch-OT flow matching or a Schrödinger bridge (two image styles, two speakers, two sensor types).
- **Generative data augmentation.** Train a small generator and measure whether its samples improve a downstream classifier.
- **Optimal transport** for generated speech detection.

**Track B: analyses**

- **Samplers versus cost.** DDPM, DDIM, RK2, DPM-Solver or reflow: error against the number of network evaluations, on data where the truth is known (the homework mixture is a good start). You could be also inerested in continuous normalizing flow (CNF) - the neural ODE.
- **Couplings and straightness.** Independent versus minibatch-OT pairs versus reflow: path straightness, few-step quality and training cost as the batch size or dimension grows.
- **Guidance.** What classifier-free guidance does to diversity and fidelity as the scale grows; compare with the exact tilted distribution where it can be computed.
- **Memorization.** When does a diffusion model copy its training data (or text on the images)? Vary the dataset size and model size, and measure the distance to the nearest training example.
- **Attention maps.** Like in Diffusion Transformers.
- **Likelihoods.** Exact ODE likelihood versus the ELBO of the same diffusion model; how far apart are they, and does the gap depend on the schedule?

Individual projects by default. 

- **AI tools.** Allowed for coding help and writing polish. You are responsible for every line and every claim, and the report says how you used them.

## Deliverables and timeline

Four deliverables, each building on the last.

| Due | Deliverable | What it contains |
| --- | --- | --- |
| Nov 23, 2026 | Proposal (1 page) | Track, question, method, data, baseline, metric, compute estimate, and what a negative result would look like |
| Nov 30, 2026 | Checkpoint (10 min meeting) | A first result, even a small one; any change of plan |
| Dec 7, 2026 | Presentation (15 min + questions) | In person or zoom |
| Dec 8, 2026 | Report | 2-3 pages, IEEE conference format |


## Grading

The project is graded out of 30 points. A clean negative result, honestly analyzed, can earn full marks.

| Component | Points | What earns them |
| --- | --- | --- |
| Proposal | 5 | A clear, answerable question; a realistic plan; a baseline and a metric chosen in advance |
| Checkpoint | 5 | Working baseline and a first experiment on time |
| Presentation | 10 | Clear story in 15 minutes; answers to questions |
| Report and code | 10 | Well written, honest about limitations, figures reproducible from the repository |
| **Total** | **30** |  |


- **Office hours.** Write me with any questions, ideas appear in conversations.
