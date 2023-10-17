# Caldera APT Simulation Datasets

This repository contains datasets from two APT simulations conducted using [Caldera](https://caldera.mitre.org/), following the guidelines provided by MITRE [Center for Threat-Informed Defense](https://github.com/center-for-threat-informed-defense/adversary_emulation_library). These datasets are invaluable for researchers and practitioners aiming to study the intricacies of advanced persistent threats in real-world environments.

## Dataset Details

- **Total Records:** 
  - FIN6 Dataset: X million audit log records.
  - APT 29 Dataset: Y million audit log records.

- **Duration of Simulation:**
  - FIN6 Dataset: M hours.
  - APT 29 Dataset: N hours.

- **Target System:** Windows 10 (64-bit).

- **Nature of Records:** The majority of the logs capture benign activities, with only a small fraction representing actual attacker activities.

- **Data Model:** The audit logs are modeled based on MITRE's CAR (Cyber Analytics Repository) and FiveDirections' eCAR data model. More details can be found [here](https://github.com/FiveDirections/OpTC-data/blob/master/ecar.md).

## Ground Truth

For each of the simulations, we've also uploaded the corresponding ground truths. These will be crucial for validation and benchmarking purposes.

## Usage

These datasets can serve multiple purposes:
- **Research:** Ideal for academic and industry research to understand the behavior and patterns of APTs.
- **Training Machine Learning Models:** Given the vast number of logs, these datasets are ideal for training ML models to distinguish between benign and malicious activities.
- **Benchmarking Security Solutions:** Test the efficiency of your Intrusion Detection Systems (IDS) or other security solutions against real-world APT simulations.

--------------------------------------------------------------------------

WE ARE CURRENTLY ANONYMIZING THE DATASET TO REMOVE CERTAIN IDENTIFIABLE KEYWORDS AND IT WILL BE DONE IN THE NEXT FEW WEEKS.

--------------------------------------------------------------------------

## License

Please refer to the LICENSE file for details on usage, reproduction, and distribution.

## Acknowledgements

We would like to acknowledge MITRE and the Caldera team for providing guidelines that made these simulations possible.

---

Feel free to raise issues if you find any discrepancies in the datasets or have any queries regarding the same. Suggestions are always welcome!
