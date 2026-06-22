# agent-toolkit 🧰

The **model-agnostic reusable core** lifted out of the [GLM-5.2 demolition](https://github.com/PhilipJohnBasile/glm52-demolition)
project — the parts that work on *any* LLM base. Zero demolition-specific code, ~140 KB, one hard dependency (`numpy`).

> Built for the **up-path**: instead of fighting a crippled demolished model, point these at a clean right-sized
> base (e.g. Qwen3-Coder-30B) where they actually lift. The methods transfer; the weights never did.

## What's in it

| Dir | Modules | What it does |
|---|---|---|
| **`verify/`** | `verifiers.py`, `verifier_mesh.py` | **The core idea** — compile/test-check generations in Python · Rust · Go · JS · TS · SQL. Verify-first: the compiler steers every line. |
| **`souls/`** | `soul.py` + 9 `*_canon.py` | Heritage-activation: *name a field's masters* (art, design, music, perfumery, science, legacy, security, fullstack, gamedev) to wake latent eliteness. Heal these as swappable LoRA souls. |
| **`flywheel/`** | `hardneg_flywheel.py`, `media_flywheel.py` | Autonomous **verified**-data generators — mine hard negatives, grow the gold set. |
| **`stem/`** | `sci_tools.py`, `repl.py` | SymPy / units / arXiv tools + a stateful Python REPL for tool-using agents. |
| **`vision/`** | `vision.py`, `ane_vision.py` | Image/video reading; Apple-Neural-Engine perception (OCR, classify). *(`vision.py` needs `mlx`.)* |
| **`memory/`** | `memory.py`, `agent_memory.py` | Solution/project memory + cross-session agent memory. |
| **`audio/`** | `sound_verify.py` | Sound/music validation. |

## Install

```bash
pip install numpy            # core
pip install mlx              # optional — only for vision/vision.py on Apple Silicon
```

## Use it on a clean base

```python
from verify.verifiers import verify_domain          # compile/test-check any generation
from souls.soul import activate                      # heritage-activation prompt for a facet
from souls.security_canon import SECURITY_CANON       # the masters list per facet
from flywheel.hardneg_flywheel import mine            # grow verified gold

# 1. serve any base (mlx_lm.server, vLLM, Ollama, …)
# 2. wrap generations in verify_domain(code, lang) → keep only what compiles/passes
# 3. heal the base with the verified gold dataset → mount a soul via the canons
```

**The data** to heal with lives at
[`philipjohnbasile/glm52-demolition-data`](https://huggingface.co/datasets/philipjohnbasile/glm52-demolition-data)
(272K verified examples + per-facet soul gold + calibration).

## Pairs with
- **[merle](https://github.com/PhilipJohnBasile/merle)** — verifier-first coding CLI (model-agnostic via `MERLE_BASE`)
- **[callsieve](https://github.com/PhilipJohnBasile/callsieve)** — local codebase retrieval for agents
- **[vecstore](https://github.com/PhilipJohnBasile/vecstore)** — embeddable vector DB (backs `memory/`)

## License
MIT. Extracted from the GLM-5.2 demolition pipeline (built on `zai-org/GLM-5.2`, MIT — attribute Z.ai).
