# Machine learning and AI exam project

In this project we wanted to solve two problems. 

- Estimating the price of a new listing to AirBNB
- Provide recommendations to customers based on preferences such as budget, amount of days, bedrooms etc.

The project is split into 2 parts. Machine learning and AI.

With machine learning we create models that can solve these 2 problems. 

With AI we are going to let the AI model "Llama3" solve these 2 problems.

We will then compare the results from our machine learning models and the AI solutions.

The data used to make our models is based on the dataset found [here](https://www.kaggle.com/datasets/thedevastator/airbnb-prices-in-european-cities). We will combine data from all cities into a single file. Then prepare the data to fit our needs depending on the problem. See the [data folder](./data/) for raw data and modified data

## Machine learning
We are going to use supervised learning (linear regression) to predict the price and unsupervised learning for recommendations (Kmeans).

[Predicting prices with linear regression](./ML/Linear%20regression.ipynb)

[Clusters with Kmeans](./ML/KMeans.ipynb)

[Recommendations from user input](./ML/UserInput.ipynb)

## AI
In this section we will try 2 approaches. One where we do not assist the AI and one where we do. The assistance will be done with **RAG** (retrieval-augmented generation)

[Predicting prices with AI](./AI/Supervised_Linear_Regression_llama_API.ipynb)

[Recommendations with AI](./AI/Ollama_Unsurpervised_API.ipynb)



## Requirements and guide to set up local AI

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

### Open Web UI in docker

#### Step 1: Create a Project Folder

Open your terminal and run:

```powershell
mkdir ollama-webui
cd ollama-webui
```

#### Step 2: Create a docker-compose.yml File
In the same Terminal window, run:
```powershell
notepad docker-compose.yml
```
Paste the following into Notepad and save it:
```
version: '3.8'

services:
  ollama:
    image: ollama/ollama
    container_name: ollama
    volumes:
      - ollama:/root/.ollama
    ports:
      - "11434:11434"
    restart: unless-stopped

  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    container_name: open-webui
    ports:
      - "3001:8080"
    environment:
      - OLLAMA_BASE_URL=http://ollama:11434
    depends_on:
      - ollama
    restart: unless-stopped

volumes:
  ollama:

```
#### Step 3: Start Both Containers

```powershell
docker compose up -d
```

#### Step 4: Access the Interface
Open your browser and go to: http://localhost:3001


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
- `/ML/`: ML model notebooks
- `/AI/`: Ollama Api notebooks
- `README.md`: Setup and instructions

---

## Technologies used
- Anaconda Notebook
- Docker
- Open WebUI
- Ollama
- ChatGPT
- GitKraken
