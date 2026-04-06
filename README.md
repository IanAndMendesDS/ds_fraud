# Detecção de Fraudes

# 0.0 Guideline

Projeto para fazer a detecção de transações fraudulentas

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
| Table | Description |
| -- | -- |
| Feature |  |
| Feature |  |


# 3.0 Estratégia de Solução
Para a resolução do problema foi utilizado a metodologia CRISP-DM

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


# 4.0 Análise de Dados


## 4.1 Isights de Negócios


# 5.0 Modelos de Machine Learning


# 6.0 Seleção do Modelo


# 7.0 Resultado de Negócios



# 8.0 Deploy em Produção


# 9.0 Conclusão







