# Airbnb Price Analysis with Local AI (Part 1 & 2)

This project is our final exam solution for the Machine Learning & AI course. It consists of two parts:

- **Part 1**: Traditional Machine Learning (Unsupervised & Supervised)
- **Part 2**: Integrating Local AI via **Ollama** and **LLaMA 3** for natural language interaction with our dataset

Part 2 builds directly on the results and data preparation from Part 1.

---

## Objective

- Perform unsupervised (KMeans) and supervised (Linear Regression) learning on Airbnb pricing data across European cities.
- Enable natural language insights via a **locally hosted LLaMA 3 model** using **Ollama**.
- Showcase the difference between traditional ML and AI-assisted analysis using a local LLM.

---

## Requirements

### Software
- **Operating System**: Windows 10/11 or macOS
- **Python**: 3.9+
- **Docker Desktop**: Version 4.30.0 or newer *(unless installing Ollama natively)*

### Python Packages
Install required packages:
```bash
pip install requests pandas ipykernel
```

---

## Set Up Ollama (Two Options)

### Option 1: Native Install
1. Download Ollama from [https://ollama.com/download](https://ollama.com/download)
2. Install it on your local system (Windows/macOS)

### Option 2: Run via Docker
To run Ollama in a container, you need Docker Desktop:

1. Download Docker Desktop from the official site: https://www.docker.com/products/docker-desktop
2. Use version 4.30.0 or later to ensure compatibility with the latest Ollama images.

You can check your Docker version with:

```bash
docker --version
```
3. Follow the installation guide for your operating system (Windows/macOS) provided on Docker's website.
4. After installation, make sure Docker is running in the background before starting Ollama.

```bash
docker pull ollama/ollama
docker run -d -p 11434:11434 --name ollama ollama/ollama
```

> This starts the Ollama API server at `http://localhost:11434`

---

## Download the LLaMA 3 Model

Once Ollama is running, pull the model:
```bash
ollama pull llama3
```

---

## How to Run the Project

Run the notebooks in this order:

1. **Data preparation & ML**
   - `Data_handling.ipynb`
   - `UserInput.ipynb`
   - `KMeans.ipynb`
   - `Linear regression.ipynb`

2. **AI Interaction via LLaMA 3**
   - `Ollama_Unsupervised_API.ipynb`
   - `Supervised_Linear_Regression_llama_API.ipynb`

These demonstrate:
- Traditional clustering & prediction
- AI-powered data explanation via local LLM

---

## Notes

- All AI interactions occur **locally** via `http://localhost:11434`
- The project works fully **offline** after setup
- Use Docker if you don't want to install Ollama directly

---

## Project Structure Overview

- `/Data/`: Cleaned, clustered, and labeled datasets
- `/Data/airbnb-prices-in-european-cities/`: Raw city pricing data
- 
- `*.ipynb`: Project notebooks (ML models, Ollama API use)
- `README.md`: Setup and instructions
