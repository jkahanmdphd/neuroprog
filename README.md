# Neuroprognostication Communication Tool

A clinician-facing visual aid for communicating likely neurological outcomes to patients' families. Built for use before family meetings in neurocritical care settings.

**Live tool:** [yourusername.github.io/neuroprog](https://jkahanmdphd.github.io/neuroprog)

---

## What this is

Family meetings in neurocritical care often require clinicians to communicate prognosis under significant uncertainty. A single point estimate ("we think he will remain in a vegetative state") can be misleading — it collapses a genuinely wide distribution of possible outcomes into one number, and it fails to convey the asymmetric uncertainty that characterises most of these conversations.

This tool provides a visual probability distribution across a functional outcome spectrum, ranging from coma through disorders of consciousness (DOC) to the patient's premorbid baseline. The clinician sets three parameters before the meeting:

- **Most likely outcome** — where the peak of the distribution sits
- **Uncertainty spread** — how wide or narrow the range of plausible outcomes is
- **Tail skew** — whether uncertainty extends more toward better or worse outcomes

The tool is designed to be tuned by the treating clinician based on their synthesis of the available clinical information — examination findings, electrophysiology, neuroimaging, biomarkers, and arrest or injury characteristics — rather than algorithmically generated from individual inputs.

---

## What this is not

This is **not a validated prognostic calculator**. The probability distributions are not derived from a fitted statistical model or a specific patient dataset. They are a communication scaffold — a way to visually represent the clinician's gestalt in a form that families can engage with.

The tool should not be used to make clinical decisions, to determine goals of care in isolation, or as a substitute for a thorough multimodal prognostic assessment. All prognostic conversations should be grounded in individual patient data, assessment timepoint, and the nuances of the clinical context.

---

## Outcome scale

The scale runs left to right from worst to best functional outcome, anchored at the right to the **patient's premorbid baseline** — not an idealised full recovery. This is a deliberate design choice: recovery beyond premorbid function is not a realistic ceiling, and framing it otherwise can mislead families.

The outcome bins are:

| Bin | Description |
|-----|-------------|
| Coma | Unresponsive, no sleep-wake cycles |
| UWS | Unresponsive wakefulness syndrome (vegetative state) — eyes open, no awareness |
| MCS | Minimally conscious state — inconsistent but reproducible signs of awareness |
| MCS+ | MCS with command following |
| eMCS | Emerged from MCS — consistent command following, functional communication or object use |
| mRS 4 | Moderately severe disability — unable to walk or attend to bodily needs without assistance |
| mRS 3 | Moderate disability — requires some help, but able to walk without assistance |
| mRS 2 | Slight disability — unable to perform all previous activities but independent |
| mRS 1 | No significant disability despite symptoms — able to perform all usual duties |
| mRS 0 | No symptoms |

The DOC states (Coma through eMCS) are functionally equivalent to **mRS 5** (bedridden, incontinent, requires full nursing care) in terms of the modified Rankin Scale, but are distinguished here because the level of awareness within that functional floor carries significant prognostic and ethical weight.

*Modified Rankin Scale descriptions adapted from Rankin (1957) and van Swieten et al. (1988).*

---

## Using the tool

1. Set the patient's **premorbid baseline** — this becomes the rightmost bin and the ceiling of the distribution
2. Select the **most likely outcome** using the peak slider
3. Adjust **uncertainty spread** — narrow for cases with strong multimodal convergence, wide for early or ambiguous assessments
4. Adjust **tail skew** if uncertainty is asymmetric — for example, skewing toward worse outcomes when poor-outcome predictors are present but not conclusive
5. Use the summary cards and distribution to anchor the family conversation

---

## Technical notes

- Single-file HTML application — no framework, no build step, no backend
- JavaScript probability model uses a skewed normal distribution parameterised by peak, spread, and skew
- Chart rendered with [Chart.js 4.4](https://www.chartjs.org/) via CDN
- Supports light and dark mode via `prefers-color-scheme`
- No data is collected, transmitted, or stored

---

## Limitations and future directions

The current version has several important limitations:

- Distributions are hand-parameterised by the clinician, not derived from population data
- The tool does not currently accept structured clinical inputs (exam findings, SSEP, NSE, EEG, imaging) to generate an evidence-based prior
- The outcome scale is adapted primarily from cardiac arrest and stroke literature; applicability to TBI and other conditions involves additional nuance
- The tool has not been tested in clinical settings or validated against patient outcomes

Future versions could incorporate condition-specific priors derived from validated datasets (TTM/TTM2 trial data, IMPACT-TBI, CARES registry) and allow clinician adjustment from an evidence-based starting point rather than a blank distribution.

---

## Contributing

Feedback from clinicians — particularly around the clinical accuracy of bucket groupings, outcome labels, and the framing of uncertainty — is welcome. Please open an issue or submit a pull request.

---

## Author

Developed by a neurocritical care physician as a communication aid for family meetings. If you use or adapt this tool, please maintain the disclaimer language and the distinction between communication scaffold and validated prognostic instrument.

---

## License

MIT License — free to use, adapt, and redistribute with attribution.
