# AT1 - Criar um Perceptron Manual

### Projeto acadêmico de Aprendizado de Máquina com implementação manual de um Perceptron para classificação binária usando dados públicos de Fórmula 1.

## Objetivo

- Construir e avaliar um Perceptron sem bibliotecas de rede neural para investigar se é possível prever:

- Pole position em classificações (qualifying).
- Tendências em dados de corrida por meio de engenharia de atributos.

# Base de Dados

Os dados foram extraídos da plataforma Kaggle e estão disponíveis [aqui](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020)

### Os dados foram importados na pasta `data/raw` e incluem tabelas como:

- qualifying.csv
- lap_times.csv
- races.csv
- drivers.csv
- results.csv

# Estrutura do Projeto

- main.py: entrada simples do projeto Python.
- pyproject.toml: metadados e dependências.
- perceptron_f1.ipynb: análise exploratória e primeiras tentativas de modelagem.
- perceptron_quali_f1.ipynb: foco em classificação de pole position com diferentes abordagens.

# Metodologia

## Pipeline geral aplicado nos notebooks:

- Leitura dos CSVs
- impeza de valores ausentes.
- Definição de target binário.
- Balanceamento de classes por undersampling.
- Normalização Min-Max.
- Split treino/teste.
- Treinamento manual do Perceptron com função degrau.
- Avaliação por acurácia e inspeção de exemplos.

### Destaque da Nova Abordagem

Na etapa final de perceptron_quali_f1.ipynb, a modelagem passa a usar contexto por corrida:

- Cálculo do melhor Q3 por corrida.
- Criação de atributo relativo: q3_relativo = q3 / melhor_q3_da_corrida.
- Criação de atributo de evolução: diferenca = q1 - q3.
- Manutenção de driverId e raceId para interpretar as predições.
- Treino e avaliação do Perceptron com esses novos atributos.

Essa abordagem melhorou significativamente o desempenho no notebook, chegando a aproximadamente 94,67 por cento de acurácia no cenário apresentado.

# Requisitos

- Python >= 3.14
- fastapi[standard]
- matplotlib
- numpy
- pandas
- scikit-learn

## Dependências de desenvolvimento:

- ipykernel
- notebook
