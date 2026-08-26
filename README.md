# Context-Aware Wazuh Alert Prioritisation Framework

This repository contains the prototype developed for my MSc Cybersecurity research project at Technological University Dublin.

## Project Overview

The project implements a transparent, post-detection framework for prioritising existing Wazuh alerts.

The framework combines three inputs:

- Wazuh rule severity, represented as the likelihood proxy `L`
- Asset criticality, represented as `A`
- MITRE ATT&CK tactic context, represented as `T`

The final priority score is calculated as:

Priority Score = (2 × L × (A + T)) / 4 × 100

The resulting score is assigned to a LOW, MEDIUM, HIGH or CRITICAL priority band.

## Experimental Evaluation

The prototype was evaluated using six Atomic Red Team experiments executed individually in a controlled laboratory:

1. T1057 – Process Discovery
2. T1136.001 – Create Account: Local Account
3. T1548.003 – Sudo and Sudo Caching
4. T1003.008 – OS Credential Dumping: `/etc/shadow`
5. T1071.001 – Application Layer Protocol: Web Protocols
6. T1486 – Data Encrypted for Impact

Wazuh alerts generated during each experiment were exported separately and processed by the scoring notebook.

## Repository Contents

- `SOC_Alert_prioritisation_final_v2.ipynb` – final scoring and evaluation notebook
- `asset_inventory.csv` – asset-criticality input used by the prototype
- `requirements.txt` – Python dependencies

## Running the Prototype

Install the required Python packages:

```bash
pip install -r requirements.txt
