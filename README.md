# Part 1 


# Part 2 - Local AI Analysis with LLaMA 3 (via Ollama)

This project builds on the Airbnb data analysis from Part 1 by integrating a local large language model (LLM) using **Ollama** and **LLaMA 3**. The goal is to enable natural language interaction with the dataset using an AI model running locally or locally via Docker.

## Objective

Use a locally hosted LLM (LLaMA 3) to provide insights or answer questions based on the cleaned Airbnb dataset. The model is hosted using **Ollama** in **Docker Desktop**, enabling offline and private AI interaction.

---

## Requirements

- **Operating System**: Windows 10/11 or macOS
- **Docker Desktop**: Version **4.30.0** or later (Unless running Ollama locally on your computer)  
  [Download here](https://www.docker.com/products/docker-desktop/)
- **Python**: Version 3.9+
- **Python packages**:
  - `requests`
  - `pandas`
  - `ipykernel` (if running from Jupyter)

You can install them with:

```bash
pip install -r requirements.txt
```

## Install Ollama
Follow the instructions at: https://ollama.com/download
Or run the Docker image manually:
```
docker pull ollama/ollama
docker run -d -p 11434:11434 --name ollama ollama/ollama
```

## Download the LLaMA 3 model
Run:
```
ollama pull llama3
```

After setting this up you should be ready to run the model in our project
