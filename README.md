# Previsão de Mortalidade Neonatal

Um projeto de machine learning para predizer o risco de morte neonatal (até 28 dias após o nascimento) utilizando dados públicos do SINASC e SIM.

## 📋 Sobre o Projeto

Este projeto utiliza dados públicos do **SINASC** (Sistema de Nascidos Vivos) e do **SIM** (Sistema de Mortalidade) para construir modelos de aprendizado de máquina capazes de prever o risco de morte neonatal. O objetivo é auxiliar profissionais de saúde na identificação precoce de recém-nascidos em situação de risco.

### 👥 Autores
- **Júlia Moraes**
- **Luiz Eduardo**

## 🗂️ Estrutura do Projeto

```
neopredict/
├── data.ipynb              # Análise exploratória e pré-processamento dos dados
├── main.ipynb              # Modelagem e avaliação dos algoritmos
├── sinasc_balanceado.csv   # Dataset balanceado para treinamento
└── README.md              # Documentação do projeto
```

## 🔍 Metodologia

### 1. **Processamento de Dados** (data.ipynb)

#### Datasets Utilizados:
- **SINASC 2023**: Dados de nascimentos
- **SIM 2023**: Dados de mortalidade

#### Principais Etapas:
- **Linkagem de dados**: União dos datasets SINASC e SIM através de chaves compostas
- **Balanceamento**: Criação de dataset equilibrado (1:3 - óbitos:sobreviventes)
- **Limpeza**: Tratamento de valores ausentes e inconsistentes

#### Variáveis Principais:
- **Numéricas**: idade da mãe, peso do bebê, semanas de gestação, etc.
- **Ordinais**: consultas pré-natal, índice de Kotelchuck, escolaridade
- **Categóricas**: tipo de parto, raça/cor, anomalias identificadas

### 2. **Modelagem** (main.ipynb)

#### Pipeline de Pré-processamento:
- **Imputação**: Valores ausentes (média para numéricas, moda para categóricas)
- **Normalização**: StandardScaler para variáveis numéricas
- **Codificação**: OneHotEncoder para variáveis categóricas

#### Modelos Implementados:

##### 🧠 **Redes Neurais**
- **Arquitetura**: 3 camadas densas (100 neurônios cada)
- **Regularização**: Dropout (0.3, 0.2, 0.1) e Early Stopping
- **Otimizador**: SGD com learning rate 0.01
- **Função de Ativação**: ReLU (camadas ocultas), Sigmoid (saída)

##### 🌳 **Árvores de Decisão**
- **Regularização**: Cost Complexity Pruning
- **Otimização**: GridSearchCV com validação cruzada (10-fold)

##### 🎯 **Support Vector Machine (SVM)**
- **Kernel**: RBF (Radial Basis Function)
- **Hiperparâmetros**: C e gamma otimizados via GridSearchCV
- **Validação**: 10-fold cross-validation

## 📊 Métricas de Avaliação

Para cada modelo, são calculadas as seguintes métricas:

- **Ein (Erro no treino)** e **Eout (Erro no teste)**
- **Acurácia**: Proporção de predições corretas
- **Precision, Recall e F1-score**: Métricas específicas para cada classe
- **Matriz de Confusão**: Visualização das predições vs realidade
- **Análise de Overfitting**: Comparação Ein vs Eout

## 🛠️ Tecnologias Utilizadas

```python
# Manipulação de Dados
pandas, numpy

# Visualização
matplotlib, seaborn

# Machine Learning
scikit-learn, tensorflow, keras

# Específicas
- Pipeline, ColumnTransformer (pré-processamento)
- Sequential, Dense, Dropout (redes neurais)
- DecisionTreeClassifier, SVC (modelos clássicos)
- GridSearchCV, cross_val_score (otimização)
```

## 🚀 Como Executar

### Pré-requisitos
```bash
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow
```

### Execução
1. **Análise dos Dados**: Execute [`data.ipynb`](data.ipynb) para exploração e pré-processamento
2. **Modelagem**: Execute [`main.ipynb`](main.ipynb) para treinamento e avaliação dos modelos

### Dados Necessários
- `SINASC_2023.csv`: Dados do SINASC 2023
- `DO23OPEN.csv`: Dados do SIM 2023

> **Nota**: Os arquivos de dados originais devem ser baixados dos sites oficiais do DATASUS.
