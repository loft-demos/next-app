# syntax=docker/dockerfile:1.6
FROM vllm/vllm-openai:latest

ARG MODEL_ID=Qwen/Qwen2.5-3B-Instruct
ENV HF_HOME=/root/.cache/huggingface
ENV MODEL_DIR=/models

# Download weights at build time (public models = no token needed)
RUN mkdir -p ${MODEL_DIR} \
 && python -m pip install --no-cache-dir "huggingface_hub>=0.23" \
 && python -c "from huggingface_hub import snapshot_download; snapshot_download(repo_id='${MODEL_ID}', local_dir='${MODEL_DIR}/${MODEL_ID}', local_dir_use_symlinks=False)"

# vLLM OpenAI-compatible server listens on 8000 by default
EXPOSE 8000
