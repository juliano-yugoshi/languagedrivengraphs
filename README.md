# Language-Driven Graphs for Short Video Similarity

# !\[Project Banner](figures/result\_graph\_legend\_fixed.png)

# \*Gráfico final comparando a coesão semântica de grafos de similaridade construídos a partir de descrições humanas, descrições geradas por IA (LLM) e features visuais puras (CLIP).\*


 Visão Geral do Projeto

# Este repositório contém o código, os dados processados e os resultados da pesquisa que compara a eficácia de diferentes modalidades na construção de grafos de similaridade para vídeos curtos. Utilizando o dataset \*\*MSR-VTT\*\*, o projeto constrói e avalia três tipos de grafos:

1. Grafo Visual: Baseado na similaridade de cosseno entre embeddings visuais extraídos com CLIP.

2. Grafo de Descrição Humana: Baseado na similaridade semântica (SBERT) entre as descrições fornecidas por humanos no dataset.

3. Grafo de Descrição Gerada por IA: Baseado na similaridade semântica (SBERT) entre descrições geradas por um LLM, especificamente o `smol-vlm-2.0`.


# Fluxo de Trabalho e Execução


# O processo é dividido em dois Jupyter Notebooks, projetados para serem executados em sequência no \*\*Google Colab\*\*.


# Notebook 1: `01\_Data\_Preprocessing\_and\_Feature\_Extraction.ipynb` (Opcional)

# &nbsp;   Este script realiza o pré-processamento completo a partir dos dados brutos do MSR-VTT. \*\*Você só precisa executá-lo se quiser replicar a extração de features do zero.


# Notebook 2: `02\_Graph\_Analysis\_and\_Evaluation.ipynb` (Principal)

# &nbsp;   Este script realiza a análise central. Ele carrega os dados e as features, constrói os grafos, avalia a coesão semântica e gera o gráfico final de resultados.



# Como Reproduzir os Resultados


# \### Passo 1: Configuração do Ambiente no Google Drive

# 1\.  \*\*Clone o Repositório para sua Máquina Local:\*\*

# &nbsp;   ```bash  

# &nbsp;   git clone https://github.com/anonymous-1-2/languagedrivengraphs.git 

 

2. Gere a Pasta do Projeto no seu Google Drive: Na raiz do seu Google Drive (My Drive), crie a seguinte estrutura de pastas: 
# 

My Drive/  
└── D/
     └── Dataset/


3. Faça o Upload dos Scripts: Faça o upload de todos os arquivos .ipynb, .csv, .xlsx e a pasta figures/ que você clonou do GitHub para dentro da pasta Dataset/ que você acabou de criar no seu Drive. 


4 . Adicione Atalhos para os Dados e Features: Abra os links compartilhados do Google Drive abaixo. Para cada link, em vez de baixar, clique em "Adicionar atalho ao Drive" (ou no ícone de triângulo com um "+") e escolha a pasta My Drive/D/Dataset/ como destino.


# Atalhos Necessários para a Análise - Notebook 2 (Recomendado):


* Keyframes/ (https://drive.google.com/drive/folders/1jiHTEsbit8o5WyVbcNYdRz3I995B8rBs?usp=sharing) 


* MSRVTT\_Features\_ViT\_L\_14\_Aggregated/ (https://drive.google.com/drive/folders/1USB4NbvxpCL\_V-RFfqrClmMlPrWggvfu?usp=sharing)


* MSRVTT\_Features\_ViT\_L\_14\_Sequential/ (https://drive.google.com/drive/folders/1TpshF89NqtFFBqb-IadriWaLu8Eyi5cL?usp=sharing)


# Atalhos para Replicar a Geração de Features (Opcional):


# Se você deseja executar o Notebook 1 do zero, adicione também os atalhos para os dados brutos:

* TrainValVideo.zip (https://drive.google.com/file/d/1rt4YDdhRblFvYpr3xdvHtff4-jqEWO\_6/view?usp=sharing)


* train\_val\_videodatainfo.json 
 

## Passo 2: Execução dos Notebooks

# Opção A: Apenas Análise (Recomendado)

1. Após configurar o ambiente do Drive com os atalhos, abra o notebook 02\_Graph\_Analysis\_and\_Evaluation.ipynb no Google Colab.

2. Ação Importante: No painel à esquerda do Google Colab, clique no ícone de pasta ("Arquivos"). Em seguida, clique no ícone "Fazer upload para o armazenamento da sessão" e selecione o arquivo MSRVTT\_dados\_compilados\_com\_features.xlsx do seu computador. Isso o tornará acessível diretamente no caminho /content/.

3. Execute todas as células do notebook para realizar a análise completa e gerar os resultados finais.


# Opção B: Geração Completa do Zero

1. # Garanta que os atalhos para os dados brutos (TrainValVideo/ e .json) foram adicionados ao seu Drive.

2. Abra o notebook 01\_Data\_Preprocessing\_and\_Feature\_Extraction.ipynb no Google Colab com um ambiente GPU (T4 ou superior).

3. Execute todas as células. Este processo é longo e pode levar muitas horas. As saídas, incluindo o arquivo MSRVTT\_dados\_compilados\_com\_features.xlsx, serão salvas no seu Google Drive.

4. Após a conclusão, prossiga com a Opção A, fazendo o upload do arquivo .xlsx recém-gerado para a sessão do Colab, conforme instruído. 


# Dependências:

As principais bibliotecas são instaladas diretamente nos notebooks através de células de código com o comando !pip install. As dependências chave incluem: transformers, torch, sentence-transformers, networkx, pandas, scikit-learn, matplotlib, seaborn, e tqdm. 

# Autor 
# GitHub: https://github.com/anonymous-1-2