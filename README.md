# Previsao_de_Churn

## Previsão de Churn - TelecomPlus

Este projeto tem como objetivo prever a rotatividade de clientes (churn) de uma empresa fictícia de telecomunicações chamada **TelecomPlus**, utilizando técnicas de aprendizado de máquina. A previsão de churn é essencial para identificar clientes propensos a cancelar seus serviços e, assim, permitir ações de retenção.

---

## Objetivos do Projeto

- Construir modelos de machine learning capazes de prever com precisão quais clientes estão propensos a churn.
- Avaliar o desempenho de diferentes algoritmos (Regressão Logística e Random Forest).
- Analisar as variáveis mais importantes que influenciam na decisão de cancelamento.

---


## Conjunto de Dados

- **Linhas:** 98.872
- **Colunas:** 18 (incluindo a variável alvo `churn`)
- **Descrição das principais variáveis:**

| Coluna                  | Descrição                                   |
|-------------------------|----------------------------------------------|
| id_cliente              | Identificador único do cliente               |
| idade                   | Idade do cliente                             |
| genero                  | Gênero (masculino/feminino)                  |
| estado_civil            | Estado civil                                 |
| tempo_como_cliente      | Meses como cliente da empresa                |
| tipo_contrato           | Tipo de contrato com a empresa               |
| forma_pagamento         | Forma de pagamento utilizada                 |
| suporte_contatado       | Quantidade de vezes que acionou o suporte    |
| chamados_abertos        | Quantidade de chamados abertos               |
| tempo_medio_atendimento | Tempo médio de atendimento (minutos)         |
| reclamacoes             | Total de reclamações registradas             |
| atrasos_pagamento       | Quantidade de atrasos                        |
| renda_faixa             | Faixa de renda declarada                     |
| produtos_assinados      | Tipos de produtos contratados (categórico)  |
| valor_mensal            | Valor médio mensal pago                      |
| total_gasto             | Valor total gasto até o momento              |
| churn                   | 1 = cliente cancelou, 0 = cliente ativo      |

---

## Etapas do Desenvolvimento

## 1. Análise Exploratória e Limpeza dos Dados
Primeiramente foi realizada uma análise do conteúdo do dataset. Foram analisadas estatísticas descritivas (como média, mediana, desvio padrão e valores extremos), com isso foram identificados valores ausentes, tipos de dados incorretos e inconsistências. Também foi feita a separação entre variáveis numéricas e categóricas, facilitando o tratamento posterior.

## 2. Separação da Variável Alvo
Foi identificado que a variável churn representava o que se deseja prever: se o cliente deixará ou não a empresa. Por isso, ela foi separada como variável (y), enquanto as demais colunas (exceto identificadores como id_cliente, que são únicos para cada cliente) foram utilizadas como a variável (X).

## 3. Divisão dos Dados em Conjuntos de Treinamento e Validação
Para avaliar o modelo, os dados foram divididos em dois conjuntos: 80% para treinamento e 20% para validação. A divisão foi feita de forma estratificada, mantendo a proporção de clientes que cancelaram e não cancelaram.

## 4. Pipeline de Pré-processamento
Foi criado um pipeline de pré-processamento para automatizar as etapas de transformação dos dados antes do treinamento. O pipeline incluiu algumas etapas:

- Para variáveis numéricas:
  Primeiramente houve um tratamento das variáveis numéricas, preenchendo os seus valores ausentes com a mediana dos valores e realizando a normalização dos valores, para   
  que eles fiquem na mesma escala. 

- Para variáveis categóricas:
  Em seguida, houve o tratamento das variáveis categóricas, preenchendo os seus valores ausentes com o elemento mais frequente em cada variável. Além disso, os valores 
  foram transformados em binários (0 ou 1) para facilitação do treinamento. 

  O uso de pipeline garante que as transformações aplicadas no treino sejam replicadas exatamente da mesma forma nos dados de validação e desafio.

## 5. Criação e Treinamento dos Modelos
 Dois modelos foram treinados com pipelines:

- Regressão Logística: modelo linear, simples, usado como uma baseline.

- Random Forest: modelo baseado em múltiplas árvores de decisão, mais robusto, indicado para dados  com variáveis mistas.

  Ambos os modelos foram treinados após o pré-processamento, utilizando o pipeline para garantir um fluxo limpo e seguro.

## 6. Avaliação dos Modelos
 A performance dos modelos foi avaliada no conjunto de validação usando métricas como:

- Acurácia: proporção de acertos totais.

- Precisão, Recall e F1-Score: métricas detalhadas para cada classe.

- Matriz de confusão: para visualizar os erros de classificação.

  Essas métricas permitiram comparar o desempenho dos modelos de forma justa e escolher aquele com melhores resultados.

## 7. Previsão no Dataset de Desafio
Com o melhor modelo selecionado, foi feita a previsão no arquivo de desafio, que contém apenas os dados dos clientes sem a variável alvo. O resultado foi salvo no formato solicitado, apenas com as variáveis (id_cliente e churn), para uma identificação mais fácil dos clientes.


---

## Resultados

| Regressão Logística | Acurácia | Precisão | Recall | F1-score |
|---------------------|----------|----------|--------|----------|
|          0          | 0.72     | 0.74     | 0.89   | 0.81     |
|          1          | 0.72     | 0.64     | 0.39   | 0.48     |

|    Random Forest    | Acurácia | Precisão | Recall | F1-score |
|---------------------|----------|----------|--------|----------|
|          0          | 0.72     | 0.74     | 0.89   | 0.81     |
|          1          | 0.72     | 0.64     | 0.38   | 0.47     |
---




