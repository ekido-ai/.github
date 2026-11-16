<div align="center">

# Ekido

**Your own small AI model, trained on spare devices. You pay only when it works.**

*From the Japanese* ekiden*, a relay where a sash passes from runner to runner: a training job passes from device to device without losing its work.*

[Live testnet](https://ekido.duckdns.org) · [How it works](https://github.com/ekido-ai/ekido-core#readme) · [Evidence](https://github.com/ekido-ai/ekido-core/tree/main/experiments/results)

</div>

---

### What Ekido does

- **Survives:** when a device drops out mid-training, the job moves to another one from its last checked checkpoint.
- **Refuses bad work:** a quality test, fixed before training starts, checks the result on held-out data. Work that fails is never paid.
- **Settles openly:** each payment leaves a record anyone can check. Today that's an escrow on the Base Sepolia test network, with test money only.

### What has actually run

Every number traces to a raw file in [`experiments/results`](https://github.com/ekido-ai/ekido-core/tree/main/experiments/results).

| | |
|---|---|
| A provider was killed mid-run | noticed in 0.6 s; training resumed elsewhere 65 s later; 8 of 400 steps lost (RTX 3060 Laptop) |
| A replacement returned junk (24.8% vs 89.2%) | refused, and paid 0 |
| One run handed across GPUs | Tesla T4 → RTX 3060 → T4, accuracy 89.6% → 90.6% → 90.5% |
| A real testnet settlement | 0.15 test USDC locked, 0.12 paid, 0.03 refunded (Base Sepolia) |

These are prototype results on a few machines, not production claims. The contracts are unaudited.

### Repositories

| | Repository | What it holds |
|---|---|---|
| 🧩 | [ekido-core](https://github.com/ekido-ai/ekido-core) | Shared library, API contract, design and security docs, the evidence |
| 🧭 | [ekido-coordinator](https://github.com/ekido-ai/ekido-coordinator) | Schedules training across devices: recovery, checkpoints, quality checks, settlement |
| 🏢 | [ekido-platform](https://github.com/ekido-ai/ekido-platform) | Accounts, teams, API keys, quotes, payments and plans |
| ⚡ | [ekido-inference](https://github.com/ekido-ai/ekido-inference) | Serves finished models (Rust) |
| 🖥️ | [ekido-workers](https://github.com/ekido-ai/ekido-workers) | What providers run: the agent, the training runtime, the verifier |
| 🌐 | [ekido-web](https://github.com/ekido-ai/ekido-web) | The web app |
| 📜 | [ekido-contracts](https://github.com/ekido-ai/ekido-contracts) | Escrow and proof-anchoring contracts |
| 🛠️ | [ekido-infra](https://github.com/ekido-ai/ekido-infra) | Servers, deploys, end-to-end tests, the runbook |

### How we build

- **Open code:** what runs on providers' devices and what moves money can be read by anyone.
- **No report, no merge:** every change ships with its tests, its debugging notes and the raw data behind its numbers.
- **Test network only,** until an independent audit.

<div align="center">
<sub>Built in India 🇮🇳 · Python · Rust · TypeScript · Solidity</sub>
</div>
