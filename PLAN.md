PLAN

## Infrastructure
- Development Environment (Laptop)
    - MacOS
    - Virtual Machines
        - Qemu
        - Apple Virtualization.Framework
        - UTM
            - Templates?
- Bare Metal ("Servers")
    - How do we automate provisioning?
    - What are the "sane" defaults?
    - Do we need multiple profiles?
- Virtual Machines
    - Default OS?
        - Ubuntu -> how do we do automated install?
            - Can we just import a .img on creation?
        - RHEL -> needs subscription
        - Fedora
        - Rocky
    - Cloud "like" management -> see Cloud Manager
    - IPXE?
    - Automated install / kickstart type thing?
    - Cloud Image by default
        - User data?
- Micro Cloud
- Kubernetes
- Pods (Dev/Workspaces/PROD)

## Tooling (Develop or implement)
- Cloud Manager
    - Console
    - Images
    - IP addresses
        - How do we manage this? Default "nat", and "bridge" as a "public IP"?
        - How do we manage a pool?
        - Subnetting?
    - VNC connection
    - Organize by Projects?
    - Does it handle VMs *and* kubernetes clusters?
- Code Storage
- Code Pipelines
- Validation
- Deployment
- Inventory
- Running models
    - Llama.cpp
    - vLLM
    - oLlama
    - LMStudio

## Programming Languages
- C
- C++
- Python
- Lisp

## Model Training & Inference, Agent-based "tools" (is tools the right word?)
- Inference
- Training
- Agents
    - Tools
    - Workflows

## Frameworks & Libraries
- CUDA
- PyTorch
- TinyGrad

## Applications
- Stock Market Simulator
    - Start small
        - One stock, up and down (somewhat random or do we track a real one?)
        - One trader, reads changes (events?)
        - One strategy, up 5% sell, down 5% buy