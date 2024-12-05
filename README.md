# AI Lab

## Run
```
docker-compose up -d
docker-compose logs -f -n 100
```
- Open WebUI：http://localhost:8080
- Chroma：http://localhost:8000/docs
- n8n：http://localhost:5678

## Ollama
### Pull Model
> https://ollama.com/search
```
podman exec -it ollama ollama pull llama3.2

podman exec -it ollama ollama list
```

### Pull Embedding Model
> https://ollama.com/search?c=embedding
```
podman exec -it ollama-embed ollama pull nomic-embed-text
podman exec -it ollama-embed ollama pull mxbai-embed-large

podman exec -it ollama-embed ollama list
```

## Open WebUI
- Create Admin
  - admin@bp.ai / bpai123
- Disable Arena model
- Disable embedding model
- Modify embedding url
  - http://ollama-embed:11434

## n8n
- Create Admin
  - admin@bp.ai / Bpai1234

## CUDA
### Podman GPU Support
> https://podman-desktop.io/docs/podman/gpu

### Docker GUP Support
> https://docs.docker.com/compose/how-tos/gpu-support/

## AWS EC2
### Install GPU Deiver
> https://docs.aws.amazon.com/zh_tw/AWSEC2/latest/UserGuide/install-nvidia-driver.html
> Bug fix：https://github.com/amazonlinux/amazon-linux-2023/issues/538

### Install Docker
> https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-docker.html
```
sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker ec2-user
docker ps
```

### Install NVIDIA Container Toolkit
```
sudo dnf config-manager --add-repo https://nvidia.github.io/libnvidia-container/stable/rpm/nvidia-container-toolkit.repo
sudo dnf install -y nvidia-container-toolkit
docker run --rm --gpus all nvidia/cuda:11.0.3-base-ubuntu20.04 nvidia-smi
```

### Install Docker Compose
> https://docs.docker.com/compose/install/standalone/
```
curl -SL https://github.com/docker/compose/releases/download/v2.30.3/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```
