# 🚢 Challenge Kaggle: Análise Preditiva do Titanic

![Kaggle](https://img.shields.io/badge/Kaggle-Titanic-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)
![Pandas](https://img.shields.io/badge/Pandas-2.x-blueviolet.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange.svg)

---

## 🎯 Visão Geral do Projeto

Este repositório contém a solução completa para o desafio "Titanic: Machine Learning from Disaster" do Kaggle. O objetivo principal é construir um modelo de machine learning que prevê a sobrevivência de passageiros a bordo do RMS Titanic. 

Este projeto documenta o fluxo de trabalho de ponta a ponta, desde a análise exploratória e limpeza dos dados até a engenharia de atributos, treinamento, otimização de modelos e submissão final. O trabalho resultou em uma pontuação de **0.77990**, posicionando a submissão entre os **top 20-25%** dos competidores.

---

## 🧊 O Desafio

O naufrágio do RMS Titanic é um dos eventos mais notórios da história. Em 15 de abril de 1912, durante sua viagem inaugural, o navio colidiu com um iceberg e afundou, resultando na morte de 1502 dos 2224 passageiros e tripulantes.

O desafio consiste em usar um conjunto de dados contendo informações sobre 891 passageiros (dados de treino) para construir um modelo preditivo. Em seguida, esse modelo é usado para prever o destino de outros 418 passageiros (dados de teste).

---

## 📁 Estrutura do Repositório
- **`Challenge_Kaggle_Titanic.ipynb`**: O notebook Jupyter contendo todo o código, análises e a narrativa do desenvolvimento do projeto, do início ao fim.
- **`submission_*.csv`**: Pasta contendo os diferentes arquivos de submissão gerados durante o ciclo de experimentação. O arquivo correspondente à melhor pontuação foi o `submissao_com_bins.csv`.

---

## 🗺️ Metodologia e Fluxo de Trabalho

O projeto foi desenvolvido de forma iterativa, seguindo as melhores práticas de um pipeline de ciência de dados.

### ✔️ 1. Análise Exploratória e Limpeza de Dados
A primeira etapa consistiu em uma imersão nos dados para entender sua estrutura e identificar problemas.
- **Identificação de Nulos:** Constatou-se a ausência de dados significativos nas colunas `Age` (Idade) e `Cabin` (Cabine).
- **Tratamento Estratégico:**
    - `Age`: Os valores ausentes foram preenchidos com a **mediana**, uma medida robusta a outliers.
    - `Embarked`: Os poucos valores ausentes foram preenchidos com a **moda** (o porto de embarque mais comum).
    - `Cabin`: Devido ao alto volume de dados faltantes (>75%), a coluna foi inicialmente descartada para simplificar o modelo base.

### ✨ 2. Engenharia de Atributos (Feature Engineering)
Esta foi a etapa mais crucial para o sucesso do modelo. Várias features novas e informativas foram criadas para enriquecer o dataset e fornecer mais "sinais" para o algoritmo.
- **Título (Title):** Extraído da coluna `Name` (ex: `Mr.`, `Mrs.`, `Master.`), servindo como um forte indicador de status social, idade e sexo. Títulos raros foram agrupados para evitar ruído.
- **Tamanho da Família (FamilySize) e Está Sozinho (IsAlone):** Criadas a partir da soma de `SibSp` (irmãos/cônjuges) e `Parch` (pais/filhos). Isso permitiu capturar o efeito do tamanho do grupo familiar na sobrevivência.
- **Faixas de Idade e Tarifa (Binning):** As variáveis contínuas `Age` e `Fare` foram agrupadas em categorias (ex: "Criança", "Adulto"; "Tarifa Baixa", "Tarifa Alta"). Esta técnica ajuda modelos lineares a capturarem relações não-lineares de forma mais eficaz.
- **Transformação Categórica:** Colunas textuais como `Sex` e `Embarked` foram convertidas para um formato numérico através de mapeamento e One-Hot Encoding.

### 🧠 3. Modelagem e Experimentação
Uma abordagem sistemática foi utilizada para selecionar o melhor modelo.
- **Baseline Inicial:** Um modelo de **Regressão Logística** foi treinado com os dados básicos, alcançando um score de **0.76794**.
- **Competição de Modelos:** Vários algoritmos (`Random Forest`, `SVM`, `Decision Tree`) foram comparados. A Regressão Logística se manteve como a mais estável e com melhor performance inicial.
- **Diagnóstico de Overfitting:** O `Random Forest`, em suas configurações padrão, demonstrou ser propenso a overfitting neste dataset, resultando em pontuações mais baixas no conjunto de teste. Esta foi uma descoberta chave do projeto.
- **Técnicas Avançadas:** Foram realizadas tentativas com `GridSearchCV` para otimizar o Random Forest e com `VotingClassifier` (Ensemble), mas os resultados não superaram o modelo de Regressão Logística alimentado com as features bem construídas.

---

## 🏆 Resultados e Conclusão Final

O projeto culminou em múltiplas submissões, onde cada iteração testava uma nova hipótese.

- **Melhor Pontuação:** **0.77990**
- **Posição no Ranking:** **#3058** (entre dezenas de milhares de equipes)
- **Modelo Campeão:** **Regressão Logística**
- **Features Decisivas:** A combinação de `Title`, `FamilySize`, `IsAlone`, e os *bins* de `Age` e `Fare`.

💡 A principal conclusão deste projeto é que uma **engenharia de atributos cuidadosa e inteligente foi mais impactante do que a complexidade do modelo**. A capacidade de extrair e moldar informações relevantes dos dados brutos foi o verdadeiro diferencial para construir um modelo preditivo robusto e eficaz.

---

## 🛠️ Tecnologias Utilizadas
- **Linguagem:** Python 3
- **Bibliotecas:**
    - `Pandas` para manipulação e análise de dados.
    - `Numpy` para operações numéricas.
    - `Scikit-learn` para pré-processamento, modelagem e avaliação.
- **Ambiente:** Google Colab

---

## 🚀 Como Executar
1.  Clone este repositório.
2.  Faça o upload do notebook (`Challenge_Kaggle_Titanic.ipynb`) para o Google Colab ou abra-o em um ambiente Jupyter local.
3.  Certifique-se de que os arquivos `train.csv` e `test.csv` estejam no caminho especificado no notebook.
4.  Execute as células em sequência para reproduzir a análise e os resultados.

---

## 👨‍💻 Autor
- **Luiz Marques**
