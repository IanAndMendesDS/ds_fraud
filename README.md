# Detecção de Fraudes

# 1.0 Problema de Negócio
A Blocker Fraude Company é uma empresa especializada na detecção de fraudes em transações financeiras feitas através de dispositivos móveis. A empresa tem um serviço chamado “BlockFraud” no qual garante o bloqueio de transações fraudulentas.
O modelo de negocio da empresa é do tipo serviço com monetização feita por performance do serviço prestado, ou seja, o usuário paga uma taxa fixa sobre o sucesso na detecção de fraudes das transações do cliente
Porem Blocker Fraude Company está em fase de expansão no Brasil e para adquirir clientes mais rapidamente, ela adotou uma estratégia muito agressiva. A empresa funciona da seguinte forma:
Com essa estratégia agressiva a empresa assume os riscos em falhar na detecção de fraude e é remunerada na detecção assertiva das fraudes.

Objetivo: Criar um modelo de alta precisão e acurácia na detecção de fraudes de transações feitas através de dispositivos móveis


# 2.0 Premissas de Negócio
- A empresa vai receber 25% do valor de cada trasação detectada como verdadeiramente como fraude.
- A empresa vai receber 5% do valor de cada transição detectada como fraude, porem a transação é verdadeiramente legítima.
- A empresa vai devolver 100% do valor para o cliente, a cada transação detectada como legitica, porem a transação é verdadeiramente uma fraude.


## 2.1 Descrição dos Dados
| Feature | Description |
| -- | -- |
| step | maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).  |
| type | CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER. |
| amount | amount of the transaction in local currency. |
| nameOrig | customer who started the transaction |
| oldbalanceOrg | initial balance before the transaction |
| isFraud | This is the transactions made by the fraudulent agents inside the simulation. |
| newbalanceDest | initial balance recipient before the transaction |
| isFlaggedFraud | The business model aims to control massive transfers from one account to another and flags illegal attempts. |



# 3.0 Estratégia de Solução
Para a resolução do problema foi utilizado a metodologia CRISP-DM
<img width="1080" height="1080" alt="crisp" src="https://github.com/user-attachments/assets/cb4f63aa-904b-4425-8240-c0b545509b6e" />


## 3.1 Fases do CRISP-DM
1. Definição do Problema de Negócio: Identificar stakeholders e objetivos.
2. Compreensão do Negócio: Alinhar expectativas e prototipar soluções.
3. Coleta de Dados: Agregar dados do Kaggle.
4. Limpeza de Dados: Tratar valores ausentes, outliers e inconsistências.
5. Análise Exploratória: Descobrir padrões e criar hipóteses.
6. Modelagem dos Dados: Aplicar transformações estatísticas.
7. Treinamento de Algoritmos: Avaliação de modelos (Holdout, Cross-Validation, Fine-Tuning).
8. Avaliação de Desempenho: Seleção do melhor modelo via MAPE.
9. Deploy da Solução: Publicação da API e um bot no Telegram para acesso do CFO.

## 3.2 Ferramentas Utilizadas
- Python 3.11.9 (Pandas, Numpy Scikit-learn, XGBoost, CATBoost, Matplotlib
- Git/GitHub (Controle de versão
- VSCode


# 4.0 Análise de Dados
Após a limpeza, foram feitas análises estatísticas e testes de hipóteses, para as análises foi utilizado o ydata_profiling.

## 4.1 Isights de Negócios
- Tipos de transções que ocorrem mais fraudes
<img width="2025" height="991" alt="image" src="https://github.com/user-attachments/assets/b83ed0a5-942b-4396-a14d-3cd7b11bc4b0" />


- Periodo do dia que mais ocorrem fraudes
<img width="2025" height="991" alt="image" src="https://github.com/user-attachments/assets/4259ad8c-8723-4c07-ba98-72e63a4d6610" />

As transações fraudulentas, geralmente são aquelas que zeram o valor da conta do cliente

# 5.0 Modelos de Machine Learning

## 5.1 Modelos Testados
- Logistic Regression
- Random Forest
- XGBoost
- CATBoost

# 6.0 Seleção do Modelo
## 6.1 Performance dos modelos
<img width="2120" height="1012" alt="image" src="https://github.com/user-attachments/assets/fba3df74-862b-447a-baff-2a5f7046aa38" />

| Model | Accuracy | Precision | Recall | F1-Score | Balanced Accuracy |
| -- | -- | -- | -- | -- | -- |
| RandomForest Classifier | 0.99 | 0.98 | 0.73 | 0.83 | 0.86 |
| Logistic Regression | 0.99 | 0.98 | 0.72 | 0.83 | 0.75 |
| XGBoost | 0.99 | 0.23 | 0.25 | 0.24 | 0.62 |
| CATBoost | 0.99 | 0.88 | 0.81 | 0.85 | 0.90 |


# 7.0 Resultado de Negócios

Utilizando os resultados do modelo de Logistic Regression como baseline temos que:
### Logistic Regression

- Valor à receber pelo total das transações detectadas verdadeiramente como fraude: 181329405.94
- Valor à receber pelo total das transações detectadas como fraude, mas são legitimas: 374645.22
- Valor à devolver pelo total das transações detectadas como legítimas, mas são fraudulentas: 668537773.78

### CATBoost

- Valor à receber pelo total das transações detectadas verdadeiramente como fraude: 338106023.96
- Valor à receber pelo total das transações detectadas como fraude, mas são legitimas: 1475421.05
- Valor à devolver pelo total das transações detectadas como legítimas, mas são fraudulentas: 41431301.7

### Diferença entre o baseline e o CATBoost

- Valor total à receber (baseline): 181704051.16
- Valor total à devolver (baseline): 668537773.78
- Valor total à receber (CATBoost): 339581445.02
- Valor total à devolver (CATBoost): 41431301.7

### Diferenças Raw
- À receber: 157877393.85199994
- À devolver: -627106472.0799999


# 9.0 Conclusão e Próximos Passos

### Conclusão

Em problemas de classificação um problema muito comum encontrado é o que foi observado nesse projeto que são os dados desbalanceados, ao se tratar com dados desbalanceados temos um problema na hora 
de metrificar os modelos, pois a acurácia se torna uma métrica fantasiosa, tendo em vista que temos muito mais casos de transações que não são fraudes do que transações fraudulentas, existem alguns
métodos para tratar esse problemas, tais como:
- Undersampling
- Oversampling
- SMOTE
- Calibração
Não sou muito fã de SMOTE pois o SMOTE tende a quebrar a calibração do modelo
Assista o video com a explicação: https://youtu.be/6YnhoCfArQo?list=LL
E também podemos usar uma outra métrica chamada de Acurácia Balanceada que ela leva em consideração essas diferenças
Foi utilizado um cross validation estratificado de 5 folds, mantendo a estratificação das samples, ou sejá mantendo um número balanceado de casos positivos e negativos em cada fold.

## Próximos Passos
- Curva de threshold baseado em lucro.
- Model hyperparameters fine-tunning.
- Model deployment
- CI/CD
- Unit Tests

Como só o treino do modelo CATBoost demora cerca de ~30min na minha maquina, para fazer um fine-tunning como um for iria demorar muito, então está como próximos passos.
O deploy do modelo/ técnicas de CI/CD e teste unitários já estão arquitetados, faltando somente o deploy e alguns bugfixes.









