# CLAUDE.md — ollama-endpoints-test

Endpoint test notebook for Ollama running as a native systemd service on the DGX Spark host.

- Base: `http://localhost:11434` (host-bound — no kubectl port-forward needed)
- Ollama is GPU-accelerated on GB10 Blackwell (sm_120 binaries)
- NIM and Ollama share the 128 GB unified memory pool — only one heavy model at a time

Open `notebook.ipynb` in JupyterLab. Inference cells require a model to be loaded first
(`Actions → Ollama Deploy` in miramar-platform-gcp).

SSH tunnel: `ssh -L 11434:localhost:11434 -L 8888:localhost:8888 <user>@spark-79b7.local`
