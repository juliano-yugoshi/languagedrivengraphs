## Language-Driven Graphs for Short Video Similarity

![Project Banner](figures/result_graph.png)
*Final results from our paper, showing how Large Language Models (LLMs) create video similarity graphs that prioritize global semantic organization over the strict local purity of visual models like CLIP.*

---

## Overview

> **Authors:** *Juliano Koji Yugoshi¹², Ricardo Marcondes Marcacini¹*  
> ¹Institute of Mathematical and Computer Sciences (ICMC), University of São Paulo (USP)  
> ²Campus de Três Lagoas (CPTL), Federal University of Mato Grosso do Sul (UFMS)  

This repository contains the official code and data for our paper, **"Language-Driven Graphs for Short Video Similarity."**

In this work, we investigate a fundamental question: Do visual and language-based representations of videos create similarity spaces with different structural properties? While visual embeddings (like CLIP) are excellent at capturing appearance, they often fail to connect conceptually related content, a limitation known as the "semantic gap."

Our research introduces a graph-based framework to analyze and compare these spaces. Using the MSR-VTT dataset, we demonstrate that there is a **functional trade-off** between visual and language-based models:
*   **Visual Models (CLIP):** Create locally pure but globally disorganized graphs, excelling at grouping visually identical content.
*   **Language Models (LLMs):** Sacrifice local purity to build globally coherent graphs connected by **narrative bridges**—deep thematic links that transcend rigid categories.

This discovery shows that LLMs create an abstract semantic space that prioritizes thematic reasoning, offering a powerful alternative for applications like content recommendation and semantic search.

### The Power of Narrative Bridges

Our key finding is visualized below. While visual models create dense "hairball" graphs, language-based models build sparser, more meaningful structures.

The LLM graph (right column) connects videos based on their core narrative. For instance, it links a "Music" anchor to other videos of a "stage performance" (ignoring their formal categories) and connects a "People" anchor to videos of "social interaction," a theme primed by the anchor's own description.

![Music Video Neighborhood](figures/neighborhood_analysis_video1118.png)
*Figure 1: Neighborhoods for a "Music" anchor. The LLM graph creates a thematic cluster around "stage performance."*

![People Video Neighborhood](figures/neighborhood_analysis_video2753.png)
*Figure 2: Neighborhoods for a "People" anchor. The LLM graph links videos based on "social interaction."*

---
## Workflow and Execution

The process is divided into two Jupyter Notebooks, designed to be run sequentially in **Google Colab**.

### Notebook 1: `notebooks/01_Data_Preprocessing_and_Feature_Extraction.ipynb` (Optional)

&nbsp; &nbsp; This notebook performs the complete preprocessing pipeline, starting from the raw MSR-VTT data. **You only need to run this if you want to replicate the feature extraction from scratch.**

### Notebook 2: `notebooks/02_Graph_Analysis_and_Evaluation.ipynb` (Main)

&nbsp; &nbsp; This notebook conducts the core analysis. It loads the pre-processed data and features, builds the graphs, evaluates their semantic cohesion, and generates the final results plot.

## How to Reproduce the Results

### Step 1: Google Drive Environment Setup

1.  **Clone the Repository to Your Local Machine:**
    ```bash  
    git clone https://github.com/juliano-yugoshi/languagedrivengraphs.git

2.  **Create the Project Folder in Your Google Drive:**
    In the root of your Google Drive (`My Drive`), create the following folder structure: My Drive/D/Dataset/

3.  **Upload the Project Files:**
Upload all `.ipynb`, `.csv`, `.xlsx` files and the `figures/` folder that you cloned from GitHub into the `My Drive/D/Dataset/` directory you just created.

4.  **Add Shortcuts to Data and Features:**
Open the shared Google Drive links below. For each link, instead of downloading, click **"Add shortcut to Drive"** (or the triangle icon with a `+`) and select the `My Drive/D/Dataset/` folder as the destination.

**Required Shortcuts for Analysis (Notebook 2 - Recommended):**
*   `Keyframes/` ([Link](https://drive.google.com/drive/folders/1jiHTEsbit8o5WyVbcNYdRz3I995B8rBs?usp=sharing))
*   `MSRVTT_Features_ViT_L_14_Aggregated/` ([Link](https://drive.google.com/drive/folders/1USB4NbvxpCL_V-RFfqrClmMlPrWggvfu?usp=sharing))
*   `MSRVTT_Features_ViT_L_14_Sequential/` ([Link](https://drive.google.com/drive/folders/1TpshF89NqtFFBqb-IadriWaLu8Eyi5cL?usp=sharing))

**Shortcuts for Full Feature Generation (Optional):**
If you wish to run Notebook 1 from scratch, also add shortcuts for the raw data:
*   `TrainValVideo.zip` ([Link](https://drive.google.com/file/d/1rt4YDdhRblFvYpr3xdvHtff4-jqEWO_6/view?usp=sharing))
*   `train_val_videodatainfo.json`

### Step 2: Running the Notebooks

**Option A: Run Analysis Only (Recommended)**

1.  After setting up your Drive environment with the shortcuts, open the `notebooks/02_Graph_Analysis_and_Evaluation.ipynb` notebook in Google Colab.
2.  **Important Action:** In the Google Colab file browser (left-side panel), click the "Upload to session storage" icon and select the `MSRVTT_dados_compilados_com_features.xlsx` file from your local machine. This will make it directly accessible at the `/content/` path.
3.  Run all cells in the notebook to perform the complete analysis and generate the final results.

**Option B: Full Generation from Scratch**

1.  Ensure the shortcuts for the raw data (`TrainValVideo.zip` and the `.json` file) have been added to your Drive.
2.  Open the `notebooks/01_Data_Preprocessing_and_Feature_Extraction.ipynb` notebook in Google Colab with a GPU runtime (T4 or higher).
3.  Run all cells. This process is time-consuming and may take several hours. The outputs, including the `MSRVTT_dados_compilados_com_features.xlsx` file, will be saved to your Google Drive.
4.  Once complete, proceed with **Option A**, uploading the newly generated `.xlsx` file to the Colab session as instructed.

## Dependencies

The main libraries are installed directly within the notebooks using `!pip install` commands. Key dependencies include: `transformers`, `torch`, `sentence-transformers`, `networkx`, `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, and `tqdm`.


