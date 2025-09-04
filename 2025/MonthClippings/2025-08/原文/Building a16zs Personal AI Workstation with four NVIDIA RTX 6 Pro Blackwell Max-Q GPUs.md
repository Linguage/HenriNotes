---
title: "Building a16z’s Personal AI Workstation with four NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs"
source: "https://a16z.com/building-a16zs-personal-ai-workstation-with-four-nvidia-rtx-6000-pro-blackwell-max-q-gpus/"
author:
  - "[[Marco Mascorro]]"
published: 2025-08-22
created: 2025-08-26
description: "In the era of foundation models, multimodal AI, LLMs, and ever-larger datasets, access to raw compute is still one of the biggest bottlenecks for researchers, founders, developers, and engineers. While the cloud offers scalability, building a personal AI Workstation delivers complete control over your environment, latency reduction, custom configurations and setups, and the privacy of running all workloads locally."
tags:
  - "clippings"
---
[![a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-12.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-12.png)

In the era of foundation models, multimodal AI, LLMs, and ever-larger datasets, access to raw compute is still one of the biggest bottlenecks for researchers, founders, developers, and engineers. While the cloud offers scalability, building a **personal AI Workstation** delivers complete control over your environment, latency reduction, custom configurations and setups, and the privacy of running all workloads locally.

This post covers our version of a **four-GPU workstation** powered by the new NVIDIA **RTX 6000 Pro Blackwell Max-Q GPUs**. This build pushes the limits of desktop AI computing with **384GB** of VRAM (**96GB** each GPU), all in a shell that can fit under your desk.

[![a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-13.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-13.png)

## Why Build This Workstation?

Training, fine-tuning, and running inference on modern AI models require massive VRAM bandwidth, high CPU throughput, and ultra-fast storage. Running these workloads in the cloud can introduce latency, setup overhead, slower data transfer speeds, and privacy tradeoffs.

By building a workstation around **enterprise-grade GPUs with full PCIe 5.0 x16 connectivity**, we get:

- **Maximum GPU-to-CPU bandwidth:** No bottlenecks from PCIe switches or shared lanes.
- **Enterprise-class VRAM:** Each RTX 6000 Pro Blackwell Max-Q provides 96GB of VRAM, enabling dense training runs and large model inference without quantization. Each card consumes only 300W of power at peak (Max-Q version).
- **8TB of NVMe 5.0 storage:** 4x 2TB of NVMe PCIe 5.0 x4 modules.
- **256 GB** of total ECC DDR5 RAM.
- **Surprising efficiency:** Despite its scale, the workstation pulls **1650W at peak**, low enough to run on a standard 15-amp / 120V household circuit.
- **Next-gen data GDS streaming:** While we are still in the process of testing this support, this setup should be compatible with the **NVIDIA GPUDirect Storage (GDS)**, which allows datasets or models to stream directly from PCIe 5.0 NVMe SSDs into GPU VRAM, bypassing CPU memory, to reduce latency and maximize throughput.

**We are planning to test and make a limited number of these custom a16z Founders Edition AI Workstations.**

[![Detail of a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-10.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-10.png)

## Core Specifications

Let’s break down the hardware:

- **GPUs:**
	- 4 × NVIDIA RTX 6000 Pro Blackwell Max-Q
	- 96GB VRAM per GPU (**384GB total VRAM**)
	- Each card on a dedicated PCIe 5.0 x16 lane
	- 300W per GPU
- **CPU:**
	- AMD Ryzen Threadripper PRO 7975WX (liquid cooled with Silverstone XE360-TR5)
	- 32 cores / 64 threads
	- Base clock: 4.0 GHz, Boost up to 5.3 GHz
	- 8-channel DDR5 memory controller
- **Memory:**
	- **256GB** ECC DDR5 RAM
	- Running across 8 channels (32GB each)
	- Expandable up to 2TB
- **Storage:**
	- **8TB** total: 4x 2TB PCIe 5.0 NVMe SSDs x4 lanes each (up to 14,900 MB/s – theoretical read speed for each NVMe module)
	- Configurable in RAID 0 for **~59.6GB/s aggregate theoretical read throughput** (we are in the process of testing real throughput).
- **Power Supply:**
	- Thermaltake Toughpower GF3 1650W 80 PLUS Gold
	- System-wide max draw: 1650W, operable on a **standard, dedicated 15A 120V outlet**
- **Motherboard:**
	- GIGABYTE MH53-G40 (AMD WRX90 Chipset)
- **Case:**
	- Off the shelf Extended ATX case with some custom modifications.

[![a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-11.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-11.png)

## Design Highlights

##### Full PCIe 5.0 Bandwidth

Each GPU is connected via its own **dedicated PCIe 5.0 x16**, ensuring maximum data transfer rates between CPU and GPU. Unlike multi-GPU setups that rely on bifurcated lanes, multiplexers, or external bridges, this build guarantees **no compromise on lane allocation or defaulting in lower PCIe versions**.

##### Storage for High-Speed Datasets

The four PCIe 5.0 NVMe SSDs provide read speeds of up to **~14.9 GB/s each (theoretical)**, scaling to **~59 GB/s theoretical in RAID 0**. While we are still in the process of testing full **NVIDIA GPUDirect Storage (GDS)** compatibility, it could allow GPUs to fetch data directly from NVMe drives, enabling direct-memory access (DMA).

##### Power Efficiency & Practicality

The overall system consumes **1650W peak** and fits comfortably into a home or office environment without requiring dedicated circuits or 220V wiring. With built-in wheels, it is designed for effortless transport between locations.

##### Baseboard Management Controller (BMC)

Integrated AST2600, a Baseboard Management Controller (BMC) that serves as a dedicated processor for remote out-of-band server management, operating independently of the host CPU and OS to handle critical monitoring and control tasks.

[![CPU connection diagram of a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-9.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-9.png)

## Use Cases

- **Training and fine-tuning LLMs** with up to **tens of billions of parameters** in full precision.
- **Running dense multimodal inference** across image, text, audio, and video models simultaneously.
- **Experimenting with model parallelism** (tensor, pipeline, or expert-based sharding) across four GPUs.
- **Streaming high-throughput datasets** directly from SSD RAID into GPU memory for reinforcement learning or diffusion-based workloads.

With libraries like vLLM, DeepSpeed, SGLang, etc., this machine serves as a foundation for training and serving custom LLMs, RL training pipelines, multimodal models, autonomous agents, etc., without cloud dependency and with a custom setup and environment.

This RTX 6000 Pro Blackwell workstation represents a **sweet spot between datacenter power and desktop accessibility**; all while staying within the footprint and power draw of a high-end AI Workstation under your desk.

Whether you’re a researcher exploring new architectures, a startup prototyping private LLM deployments, or simply an enthusiast, this build demonstrates an efficient, AI Workstation under your desk.

Some temperature tests:

[![Full Utilization statistics of a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-14.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-14.png)

[![Idle statistics for a16z Personal AI Workstation with 4x NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-15.png)](https://d1lamhf6l6yk6d.cloudfront.net/uploads/2025/08/250821-Building-a-Next-Gen-AI-Workstation-15.png)

- - [X](https://twitter.com/Mascobot)
	- [Linkedin](https://www.linkedin.com/in/marcomascorro/)