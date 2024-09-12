# OpenHands

## Starting up

```bash
docker run -it --pull=always \
    -e SANDBOX_RUNTIME_CONTAINER_IMAGE=ghcr.io/all-hands-ai/runtime:0.9-nikolaik \
  -e SANDBOX_USER_ID=$(id -u) \
  -e WORKSPACE_MOUNT_PATH=$WORKSPACE_BASE \
  -v WORKSPACE_BASE:/opt/workspace_base \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 3000:3000 \
  --add-host host.docker.internal:host-gateway \
  --name openhands-app-$(date +%Y%m%d%H%M%S) \
  ghcr.io/all-hands-ai/openhands:main
```

## Starting with Local Models (Ollama)

```bash
docker run \
    -it \
  --pull=always \
    --add-host host.docker.internal:host-gateway \
    -e SANDBOX_USER_ID=$(id -u) \
  -e LLM_API_KEY="ollama" \
  -e LLM_BASE_URL="http://host.docker.internal:11434" \
  -e LLM_OLLAMA_BASE_URL="http://host.docker.internal:11434" \
    -e WORKSPACE_MOUNT_PATH=$WORKSPACE_BASE \
    -v WORKSPACE_BASE:/opt/workspace_base \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -p 3000:3000 \
    ghcr.io/all-hands-ai/openhands:main
```
