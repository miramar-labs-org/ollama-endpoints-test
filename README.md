# ollama-endpoints-test

JupyterLab notebook tests for all **Ollama** API endpoints on the DGX Spark host.

## Prerequisites

- Ollama running on DGX host (always-on systemd service)
- A model loaded (`Actions → Ollama Deploy` in miramar-platform-gcp)
- SSH tunnel open:
  ```sh
  ssh -L 11434:localhost:11434 -L 8888:localhost:8888 <user>@spark-79b7.local
  ```

## Endpoints tested

| Endpoint | Description |
|---|---|
| `GET /api/ps` | Models currently loaded in VRAM |
| `GET /v1/models` | Models available on disk |
| `POST /v1/chat/completions` | OpenAI-compatible chat completion |
| `POST /v1/chat/completions` (tools) | Tool / function calling |
| `POST /v1/embeddings` | Embeddings |

Base: `http://localhost:11434` (Ollama host service — no port-forward needed)

## Model quick reference

| Tag | tok/s | Tool use | Best for |
|---|---|---|---|
| `gpt-oss:20b` | **58** | ✅ | Speed, coding |
| `qwen3:32b-q4_K_M` | ~9 | ✅ | Workhorse |
| `llama3.3:70b-instruct-q4_K_M` | ~4 | ✅ | General, agentic |
| `deepseek-r1:70b` | ~4 | CoT | Reasoning, math |

## Reference

- [Ollama API docs](https://github.com/ollama/ollama/blob/main/docs/api.md)
- [miramar-platform-gcp ENDPOINTS.md](https://github.com/miramar-labs-org/miramar-platform-gcp/blob/main/dgx/minikube/nemo/ENDPOINTS.md)
