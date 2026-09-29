# NRL — Neural Render Learning

NRL (Neural Render Learning) is an experimental neural rendering project that explores whether a small neural network can learn to represent a virtual 3D-like object without using an explicit 3D mesh.

## Concept

Instead of creating a traditional 3D model, NRL learns a function that maps a viewpoint to visual information.

```text
Rotation X ──┐
Rotation Y ──┼──► Neural Network ──► RGB
Zoom ────────┘
```

Multiple pixel predictions are combined to produce a complete rendered image.

The long-term goal is to investigate whether a neural network can encode the visual representation of an object and generate different views without storing conventional 3D geometry.

## Initial Architecture

```text
Input
  │
  ├── Rotation X
  ├── Rotation Y
  └── Zoom
        │
        ▼
   Linear 3 → 16
        │
      ReLU
        │
   Linear 16 → 16
        │
      ReLU
        │
   Linear 16 → 3
        │
        ▼
      R, G, B
```

### Model Parameters

| Layer     | Parameters |
| --------- | ---------: |
| 3 → 16    |         64 |
| 16 → 16   |        272 |
| 16 → 3    |         51 |
| **Total** |    **387** |

The initial network contains only **387 trainable parameters**.

## Goals

* Experiment with neural representations of virtual objects
* Avoid explicit 3D meshes
* Investigate how small neural networks can encode visual information
* Generate different views from learned representations
* Measure rendering speed during inference
* Study the relationship between model size and visual quality
* Explore the trade-off between model complexity and rendering performance

## Technology

* Python
* PyTorch
* NumPy
* Matplotlib
* CUDA
* PyCharm
* Git
* GitHub

## Hardware

Initial development and testing is performed on:

* NVIDIA RTX 3050 Laptop GPU
* 4 GB VRAM

## Project Structure

```text
NRL/
├── src/
│   ├── model.py
│   ├── train.py
│   └── render.py
├── data/
├── checkpoints/
├── requirements.txt
├── .gitignore
├── README.md
└── LICENSE
```

## Project Status

**Experimental / Early Development**

The project is currently focused on validating the basic neural rendering concept.

The architecture and representation may change as experiments progress.

## Planned Experiments

* Train the initial 3 → 16 → 16 → 3 network
* Test different neuron counts
* Test different activation functions
* Train on increasingly complex objects
* Generate novel viewpoints
* Benchmark GPU inference
* Measure FPS at different resolutions
* Investigate model compression
* Explore larger and deeper architectures
* Study whether additional spatial information is required
* Compare neural representation against traditional 3D approaches

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/NRL.git
cd NRL
```

Create a Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Verify PyTorch and CUDA:

```bash
python -c "import torch; print(torch.cuda.is_available()); print(torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'CPU')"
```

## Experiments

Each experiment should record:

* Network architecture
* Number of parameters
* Training dataset
* Training time
* Loss
* Image resolution
* GPU usage
* Inference FPS
* Visual quality

This will allow different NRL architectures to be compared objectively.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
