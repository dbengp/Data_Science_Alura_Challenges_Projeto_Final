# Data_Science_Alura_Challenges_Projeto_Final
Neste proejto, será demonstrado na prática conceitos fundamentais de estatística, essenciais para entender o comportamento dos dados e embasar decisões analíticas.

# **Análise Preditiva de Churn em Telecomunicações**

## **Introdução**

Este projeto de ciência de dados tem como objetivo principal construir e avaliar modelos de Machine Learning para prever o *churn* de clientes em uma empresa de telecomunicações fictícia. O *churn*, ou a evasão de clientes, é um dos maiores desafios para empresas de serviço por assinatura. Prever quais clientes têm maior probabilidade de cancelar seus serviços permite que a empresa tome ações proativas para retê-los.

O projeto passa por todas as etapas de um fluxo de trabalho de ciência de dados: desde a extração e limpeza dos dados até a modelagem preditiva e a avaliação dos resultados.

## **Dicionário de Dados**

O conjunto de dados contém informações sobre os clientes e seus serviços, incluindo:

* customerID: Número de identificação único de cada cliente.  
* Churn: Variável-alvo. Indica se o cliente deixou a empresa (Yes ou No).  
* tenure: Meses de contrato do cliente.  
* InternetService: Tipo de serviço de internet (DSL, Fibra Óptica ou Nenhum).  
* Contract: Tipo de contrato (mês a mês, um ano, dois anos).  
* PaymentMethod: Forma de pagamento.  
* Charges.Monthly: Total de todos os serviços do cliente por mês.  
* Charges.Total: Total gasto pelo cliente ao longo do vida.

*(Para uma lista completa, consulte o arquivo TelecomX\_dicionario.md.)*

## **Etapas do Projeto**

O projeto foi dividido em quatro etapas principais, cada uma com um objetivo claro.

### **1\. Extração e Normalização dos Dados**

Os dados foram fornecidos em um formato JSON com estruturas aninhadas, o que não é ideal para a análise tabular. A primeira etapa consistiu em carregar o arquivo JSON e usar a função pandas.json\_normalize para "achatar" (normalizar) a estrutura, transformando-a em um DataFrame plano, onde cada característica de cliente se tornou uma coluna separada.

### **2\. Pré-processamento e Limpeza dos Dados**

Esta foi a etapa mais crítica, focada em preparar os dados para a modelagem:

* **Remoção de Colunas:** A coluna customerID foi removida, pois é um identificador único e não tem valor preditivo para o modelo.  
* **Tratamento de Valores Nulos e Inconsistentes:** A coluna account\_Charges\_Total, que continha espaços e valores não numéricos, foi convertida para o tipo float. Valores nulos foram preenchidos com a média da coluna.  
* **Limpeza da Variável-Alvo (Churn):** Foram identificados valores inconsistentes ('') na coluna Churn. Essas linhas foram removidas, garantindo que a coluna só contivesse Yes ou No antes de ser mapeada para 1 e 0\.  
* **Codificação de Variáveis Categóricas:** O **One-Hot Encoding** foi aplicado às colunas categóricas restantes. Essa técnica transformou as categorias em colunas numéricas binárias (0 ou 1), o que é necessário para a maioria dos modelos de Machine Learning.

### **3\. Análise e Visualização de Variáveis**

Após a limpeza, foi gerada uma **matriz de correlação** para entender as relações lineares entre todas as variáveis e o Churn. A visualização da matriz de correlação permitiu identificar rapidamente quais características (como tipo de contrato, forma de pagamento ou tipo de serviço) têm a maior influência na decisão do cliente de sair da empresa.

### **4\. Modelagem Preditiva e Avaliação**

Nesta etapa, os dados foram divididos em conjuntos de treino e teste (70%/30%) para treinar e avaliar os modelos. Dois modelos de classificação foram implementados:

* **Regressão Logística:** Um modelo linear, rápido e interpretável. Ele foi treinado dentro de um Pipeline que incluiu a normalização dos dados (StandardScaler), um passo crucial para o bom desempenho deste algoritmo.  
* **Random Forest:** Um modelo baseado em árvores de decisão que geralmente oferece alta precisão e não requer a normalização dos dados.

A avaliação dos modelos foi realizada com base em métricas como **Acurácia, Precisão, Recall e F1-Score**. As **matrizes de confusão** foram visualizadas para entender o tipo de erro cometido por cada modelo (falsos positivos e falsos negativos), o que é particularmente importante em um problema de classes desbalanceadas como o *churn*.

## **Conclusão**

Este projeto demonstrou um fluxo de trabalho completo de ponta a ponta, desde a ingestão de dados complexos até a construção de modelos preditivos. As etapas de limpeza e preparação de dados provaram ser a parte mais desafiadora, mas foram cruciais para o sucesso da modelagem. Os resultados obtidos indicam o potencial de ambas as abordagens para prever a evasão de clientes, fornecendo à empresa insights valiosos para a tomada de decisões estratégicas.
