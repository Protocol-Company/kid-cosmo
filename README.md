# Kid Cosmo

**Sovereign Autonomy: Physics oracles for when Earth isn't answering.**

[![HuggingFace](https://img.shields.io/badge/🤗_Datasets-Mars_EDL-blue)](https://huggingface.co/datasets/spectrumroot/mars-edl-golden-path)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## What is Kid Cosmo?

Kid Cosmo is an **MCP-native reasoning engine** for autonomous systems operating in denied environments — GPS blackouts, communication loss, 20-minute latency to Earth. Instead of failing when the cloud link dies, Kid Cosmo runs local physics-grounded decisions.

**The thesis:** Embodied reasoning beats information retrieval when you can't phone home.

---

## The Physics

| Domain | Environment | Latency | Data Available |
|--------|-------------|---------|----------------|
| **Mars** | 0.38g, CO₂ atmosphere | 4-24 min | [178,857 trajectories](https://huggingface.co/datasets/spectrumroot/mars-edl-golden-path) |
| **Orbital** | LEO debris fields | 0.3-2 sec | Coming soon |
| **Ocean** | Underwater autonomy | Variable | Coming soon |

---

## Golden Path Dataset

Our flagship dataset: **1,000 Mars EDL trajectories** including 158 "Golden Path" soft landings with touchdown velocities as low as **0.01 m/s**.

```python
from datasets import load_dataset

# Load the physics
dataset = load_dataset("spectrumroot/mars-edl-golden-path")

# Filter for perfect landings
golden_paths = dataset.filter(lambda x: x["is_success"] == True)
```

**What's in it:**
- 58,620 physics frames
- Position, velocity, atmospheric density at each timestep
- SHA-256 verified trajectories
- Isaac Lab / LeRobot compatible

[**Access the Dataset →**](https://huggingface.co/datasets/spectrumroot/mars-edl-golden-path)

---

## How It Works

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   DARK WINDOW DETECTED                                      │
│   (GPS loss, comms blackout, sensor degradation)            │
│                                                             │
│                         ↓                                   │
│                                                             │
│   LOCAL REASONING ENGINE                                    │
│   (Qwen 2.5 7B on Apple Silicon)                            │
│                                                             │
│                         ↓                                   │
│                                                             │
│   DECISION MANIFEST                                         │
│   {                                                         │
│     "sensory_synthesis": {...},                             │
│     "decision": {                                           │
│       "actuator_command": "BRAKE MAX",                      │
│       "expected_outcome": "Soft landing"                    │
│     }                                                       │
│   }                                                         │
│                                                             │
│                         ↓                                   │
│                                                             │
│   MCP TOOLS (queryable by any AI agent)                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Quick Start

```bash
# Clone
git clone https://github.com/Protocol-Company/kid-cosmo.git
cd kid-cosmo

# Install
pip install -r requirements.txt

# Run MCP server
python domains/underwater/data_interface/mcp_server.py
```

---

## Commercial Licensing

**Datasets:** Available on HuggingFace with commercial licensing options.

**Custom Physics:** Need trajectories for your specific vehicle? Contact us.

**Integration:** Kid Cosmo can be embedded in your autonomy stack.

[**Contact →**](mailto:kruze@protocolcompany.ai)

---

## Links

- [HuggingFace Datasets](https://huggingface.co/spectrumroot)
- [Reasoning Manifest Spec](spec/REASONING_MANIFEST_v1.md)
- [Protocol Company](https://protocolcompany.ai)

---

*"Physics is not a suggestion. It is a geometry."*

**Protocol Company** — Building sovereign autonomy for extreme environments.
