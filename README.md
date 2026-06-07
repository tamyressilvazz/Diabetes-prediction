# 🩺 Interpretabilidade em Machine Learning para Predição de Diabetes

## 📖 Sobre o Projeto

Este projeto explora técnicas de interpretabilidade aplicadas a modelos de Machine Learning para predição de diabetes.

Utilizando o dataset Diabetes, foi treinado um modelo Random Forest e aplicadas diferentes abordagens para compreender:

* Quais variáveis mais influenciam as previsões;
* Como cada atributo afeta a probabilidade de diabetes;
* Como interações entre variáveis impactam o modelo;
* Como explicar previsões individuais.

O objetivo é tornar modelos complexos mais transparentes e interpretáveis.

---

## 🎯 Objetivos

* Construir um modelo de classificação para diagnóstico de diabetes;
* Avaliar o desempenho utilizando múltiplas métricas;
* Identificar as variáveis mais importantes;
* Analisar o comportamento global do modelo;
* Explicar previsões individuais utilizando técnicas de IA Explicável (XAI).

---

## 📊 Dataset

O projeto utiliza o **Pima Indians Diabetes Dataset**, amplamente utilizado em pesquisas de Machine Learning para diagnóstico de diabetes.

### Variável Alvo

| Classe Original | Classe Numérica |
| --------------- | --------------- |
| tested_negative | 0               |
| tested_positive | 1               |

### Atributos Utilizados

| Variável | Descrição                      |
| -------- | ------------------------------ |
| preg     | Número de gestações            |
| plas     | Concentração de glicose        |
| pres     | Pressão arterial               |
| skin     | Espessura da dobra cutânea     |
| insu     | Insulina                       |
| mass     | Índice de Massa Corporal (IMC) |
| pedi     | Histórico familiar de diabetes |
| age      | Idade                          |

---

## 🛠 Tecnologias Utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-Learn
* LIME

---

## 🌲 Modelo Utilizado

Foi treinado um modelo:

```python
RandomForestClassifier()
```

Divisão dos dados:

* 70% Treinamento
* 30% Teste

---

## 📈 Avaliação do Modelo

As métricas utilizadas foram:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

### Resultados

| Métrica   | Valor |
| --------- | ----- |
| Accuracy  | 0.766 |
| Precision | 0.714 |
| Recall    | 0.556 |
| F1-Score  | 0.625 |
| AUC       | 0.792 |

### Interpretação

O modelo apresentou desempenho satisfatório na identificação de pacientes com diabetes, alcançando aproximadamente 77% de acerto geral e boa capacidade de separação entre as classes.

---

## 🔍 Permutation Feature Importance (PFI)

A técnica PFI foi utilizada para medir o impacto de cada variável no desempenho do modelo.

### Processo

1. Embaralhar uma variável por vez;
2. Recalcular o desempenho;
3. Medir a perda de performance.

### Variáveis Mais Importantes

As análises indicaram maior relevância para:

* `plas` (glicose)
* `mass` (IMC)
* `age` (idade)

Essas variáveis apresentaram maior influência na capacidade preditiva do modelo.

---

## 📊 Partial Dependence Plots (PDP)

Foram gerados gráficos PDP para compreender o efeito médio das variáveis sobre as previsões do modelo.

### Variáveis Analisadas

* IMC (`mass`)
* Insulina (`insu`)
* Idade (`age`)

### Principais Observações

#### IMC

* Quanto maior o IMC, maior a probabilidade prevista de diabetes.
* O crescimento é mais evidente entre IMC 27 e 32.

#### Insulina

* Valores intermediários e elevados aumentam a probabilidade prevista.
* O efeito não é totalmente linear.

#### Idade

* O risco previsto aumenta gradualmente até aproximadamente os 50 anos.
* Após essa faixa ocorre leve redução.

---

## 🔄 PDP 2D — Interação entre Variáveis

Foi analisada a interação entre:

```text
IMC (mass) × Pressão Arterial (pres)
```

### Resultado

O gráfico mostrou que:

* IMC exerce forte influência sobre a previsão;
* Pressão arterial possui impacto complementar;
* Combinações de IMC elevado e pressão arterial moderada estão associadas às maiores probabilidades previstas de diabetes.

---

## 💡 Explicação Local com LIME

Foi utilizado o framework LIME para interpretar uma previsão individual do modelo.

### Classe Prevista

```text
No Diabetes (70%)
Diabetes (30%)
```

### Variáveis que Favoreceram "No Diabetes"

* Idade baixa (`age`)
* Poucas gestações (`preg`)
* Baixa insulina (`insu`)
* Pressão arterial moderada (`pres`)

### Variáveis que Favoreceram "Diabetes"

* Alta glicose (`plas`)
* IMC elevado (`mass`)
* Histórico familiar (`pedi`)

### Conclusão

O LIME permitiu compreender claramente quais características contribuíram positiva ou negativamente para a previsão específica realizada pelo modelo.

---

## 🚀 Como Executar

### Instalar Dependências

```bash
pip install pandas numpy matplotlib scikit-learn lime
```

### Executar o Projeto

```bash
python exercicio_interprelabilidade.py
```

---

## 📂 Estrutura do Projeto

```text
.
├── diabetes.csv
├── exercicio_interprelabilidade.py
└── README.md
```

---

## 📚 Conceitos Aplicados

* Machine Learning
* Random Forest
* Explainable AI (XAI)
* Permutation Feature Importance (PFI)
* Partial Dependence Plot (PDP)
* LIME
* Classificação Supervisionada
* Avaliação de Modelos
* Interpretabilidade de Modelos

---

## 📈 Principais Conclusões

* A glicose foi uma das variáveis mais importantes para previsão de diabetes.
* O aumento do IMC está fortemente associado ao aumento do risco previsto.
* Técnicas de interpretabilidade permitem compreender modelos complexos como Random Forest.
* O uso combinado de PFI, PDP e LIME fornece explicações globais e locais sobre o comportamento do modelo.

---

## 👨‍💻 Autor

Tamyres Silva

Projeto desenvolvido para fins acadêmicos na disciplina de Aprendizado de Máquina, com foco em Interpretabilidade e Explainable Artificial Intelligence (XAI).
