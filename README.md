# 🤖 Projeto: Otimização de Entregas Urbanas com Algoritmos de IA

Este projeto resolve o desafio de logística urbana, utilizando técnicas de Aprendizado de Máquina Não Supervisionado e Algoritmos de Busca para agrupar entregas próximas e otimizar o trabalho dos entregadores.

## 📌 1. Descrição do Problema e Objetivos

O principal desafio é o alto custo e a ineficiência logística na entrega final. Entregadores gastam tempo e combustível excessivos em rotas desorganizadas. O objetivo deste projeto é:
1. Agrupar geograficamente entregas próximas utilizando **Clustering**.
2. Propor uma solução teórica de **otimização de rota** para cada grupo.
3. Reduzir custos operacionais, o tempo de entrega e o impacto ambiental (sustentabilidade).

## 💡 2. Explicação Detalhada da Abordagem Adotada

Nossa solução é dividida em duas fases essenciais para o planejamento logístico:

### Fase 1: Agrupamento Inteligente (Clustering)
Nesta fase, utilizamos **Aprendizado Não Supervisionado** para processar as coordenadas (Latitude e Longitude) dos pontos de entrega. O resultado é a criação de **zonas de entrega coesas**.

### Fase 2: Otimização de Rota por Zona (Busca e Grafos)
Após a definição das zonas, cada grupo é tratado como um **Grafo** (onde as entregas são **nós** e as ruas são **arestas**). A otimização da rota interna é feita através da aplicação teórica de algoritmos de busca, visando o caminho mais rápido entre todos os nós do cluster.

## 🧠 3. Algoritmos Utilizados

| Algoritmo | Tipo | Aplicação no Projeto |
| :--- | :--- | :--- |
| **K-Means** | Aprendizado Não Supervisionado | Responsável por agrupar as coordenadas do `entregas.csv` em *N* clusters (zonas de entrega). |
| **Grafo** | Estrutura de Dados | Representação teórica da rota dentro de cada cluster, essencial para a otimização sequencial. |
| **Busca A\* (A-Star)** | Algoritmo de Busca Heurística | **Aplicação Teórica:** É o algoritmo ideal proposto para ser usado para encontrar o caminho mais curto entre os pontos do grafo, minimizando o custo total da rota. |

## 📊 4. Diagrama do Grafo/Modelo

**Diagrama do Modelo de Agrupamento K-Means**
*(Este diagrama representa as zonas de entrega e os Centróides gerados pelo algoritmo.)*

![Diagrama de Clusters K-Means](docs/diagrama_clusters.png)

## 📈 5. Análise dos Resultados, Eficiência e Limitações

### Análise de Resultados e Eficiência
O sucesso do agrupamento foi avaliado pela **Métrica de Coesão**, que mede a distância média dos pontos ao centroide de seu cluster. O baixo valor da coesão demonstra a alta eficiência do K-Means em criar grupos geograficamente densos, resultando em rotas iniciais já otimizadas. Nossa abordagem se alinha com o sistema **ORION** da UPS, que utiliza otimização e heurísticas para redução massiva de custos.

### Limitações e Sugestões de Melhoria
A principal limitação do projeto é a **implementação da Busca A\***, que está tratada de forma conceitual. Em uma aplicação de produção, o algoritmo A\* (ou um similar, como o *Branch and Bound*) deveria ser totalmente codificado para calcular a rota ideal em tempo real, incorporando dados de tráfego (arestas variáveis).

## 🛠️ 6. Instruções para Execução

1.  **Pré-requisitos:** Certifique-se de ter Python instalado.
2.  **Bibliotecas:** Instale as bibliotecas necessárias:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn scipy
    ```
3.  **Execução:** Execute o arquivo principal a partir da raiz do repositório:
    ```bash
    python src/otimizacao_entregas.py
    ```
    *(Isso irá processar os dados, gerar o agrupamento no console e exibir os gráficos.)*
