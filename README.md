# 🛒 Previsão de Recompra de Clientes 

## 📘 Descrição do Projeto
Este projeto tem como objetivo prever **a probabilidade de um cliente voltar a comprar** em uma loja online, utilizando técnicas de **aprendizado de máquina supervisionado (Machine Learning)** usando o modelo Radom Forest.  

A análise é baseada em dados transacionais de vendas das lojas do Reino Unido (*clique neste link*) , e busca responder à seguinte pergunta:
“Com base no comportamento passado, quais clientes têm maior chance de realizar novas compras?”

---

## 🎯 Objetivos do Projeto
- **Limpar e preparar** o dataset original (remoção de inconsistências e tratamento de valores faltantes);  
- **Gerar variáveis descritivas** do comportamento dos clientes (Recência, Frequência, Monetário e Quantidade);  
- **Criar um rótulo (target)** indicando se o cliente realizou novas compras após uma data de corte;  
- **Treinar e avaliar um modelo de Machine Learning** para prever a recompra;  
- **Apresentar resultados** através da acurácia, matriz de confusão e probabilidade prevista para novos clientes.

---

## 🧩 Tecnologias Utilizadas
- **Linguagem:** Python  
- **Bibliotecas principais:**
  - `pandas` para Manipulação de dados  
  - `numpy` para Cálculos numéricos  
  - `matplotlib` para Visualização  
  - `scikit-learn` para Modelagem e métricas de ML  

---

## ⚙️ Etapas do Projeto

### 1️⃣ Coleta e Carregamento de Dados
O dataset `Online_Retail.xlsx` foi carregado e inspecionado para entender sua estrutura, dimensões e tipos de variáveis.

### 2️⃣ Limpeza e Pré-Processamento
- Renomeação das colunas para português;  
- Remoção de registros inválidos (`quantidade <= 0` ou `preço <= 0`);  
- Exclusão de linhas sem identificação de cliente;  
- Criação da coluna `PrecoTotal` (quantidade × preço unitário);  
- Conversão de datas e definição da **data de corte** (09/10/2011).

### 3️⃣ Engenharia de Atributos (Feature Engineering)
Os dados transacionais foram agregados por cliente, criando as seguintes métricas:
- **Recência:** dias desde a última compra até a data de referência  
- **Frequência:** número de faturas distintas  
- **Monetário:** total gasto pelo cliente  
- **QuantidadeTotal:** total de itens comprados  

### 4️⃣ Criação do Alvo (Label)
Foi criada a variável binária `voltou`, que indica se o cliente fez uma nova compra **após a data de corte**.

### 5️⃣ Treinamento e Avaliação do Modelo
O modelo escolhido foi o **Random Forest Classifier**, treinado com 70% dos dados e testado com 30%.  
Os dados foram normalizados com `StandardScaler`.

**Métricas apresentadas:**
- Acurácia  
- Matriz de confusão  
- Relatório de classificação (precision, recall e F1-score)

---

## 📊 Resultados Obtidos
O modelo obteve desempenho estável, com **acurácia média de 65%**, mostrando boa capacidade de distinguir clientes propensos a recomprar.

A matriz de confusão e o relatório de classificação foram utilizados para avaliar o balanceamento entre as classes e a precisão das previsões.

---

## 🔮 Predição de Novos Clientes
Para demonstrar o uso prático, foi criada uma **linha de teste** simulando um cliente fictício:

```python
novo_cliente = pd.DataFrame({
    'Recencia': [30],
    'Frequencia': [5],
    'Monetario': [500],
    'QuantidadeTotal': [20]
})
