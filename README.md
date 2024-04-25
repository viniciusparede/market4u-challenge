# Automatização Mix Produtos 

Este projeto visa desenvolver um sistema para automatizar a gestão do mix de produtos nas lojas da Market4U. O objetivo é otimizar o mix inicial para novas lojas e realizar ajustes dinâmicos nas lojas ativas, adaptar as capacidades de estoque dos produtos com base em sazonalidade e demanda, e determinar os melhores momentos para o reabastecimento das lojas para minimizar rupturas de estoque.

Para enfrentar esses desafios, o entendimento profundo dos dados disponíveis e o desenvolvimento de modelos preditivos são essenciais. Por isso, a necessidade da posição de Data Scientist é evidenciada neste documento, que detalha explicitamente a metodologia proposta para o desenvolvimento do projeto. Embora a solução apresentada possa não ser a mais eficaz neste momento inicial, é crucial expor ao avaliador como o problema será abordado caso eu seja escolhido para o cargo. Este documento não apenas delineia os métodos propostos, mas também ilustra a abordagem analítica que será adotada para transformar os desafios em oportunidades de crescimento para a empresa.

[Apresentação do Desafio - Mix de Produtos](https://available-salute-e12.notion.site/Projeto-Automatiza-o-Mix-Produtos-f529cc37aaed4a1bb7a149cf27c1cc53?pvs=4)


## Introdução

A Market4U é uma franqueadora que opera mercados autônomos principalmente em condomínios residenciais. Com a tecnologia como base de seu modelo de negócio, a empresa acumulou uma vasta base de dados sobre suas operações, que agora serão utilizadas para aprimorar a gestão de produtos nas lojas.

### Objetivos do Projeto
 1. **Sugestão de Mix de Produtos:** Propor um mix inicial para novas lojas e ajustar o mix em lojas existentes para otimizar o desempenho e a satisfação do cliente.
 2. **Ajuste de Capacidades de Produtos:**  Modificar as capacidades de produtos baseando-se em tendências de consumo e sazonalidade.
 3. **Otimização de Reabastecimento:** Determinar os momentos ideias para o reabastecimento, evitando rupturas de estoque


## Metodologia

Nesse momento separarei cada um dos objetivos com sua respectiva metodologia, uma vez que, para cada objetivo são diferentes etapas do projeto, é substancial analisar cada item separadamente para abordar problemas de maneira diferente. A metodologia de cada objetivo se baseia na metodologia CRISP-DM. Um padrão já reconhecido na industria para processos que envolvem mineração de dados.

### CRISP-DM

De maneira geral o entendimento do negocio e o entendimento dos dados é a etapa de fundação para o desenvolvimento de qualquer modelo de Machine Learning. Um diagrama que é muito difundido no mundo da ciência dos dados é o modelo CRISP-DM. Basiamente ele separa as tarefas em tornos dos dados. Quando falamos dessas etapas iniciais estamos justamente respondendo as perguntanta sobre O que o negocio precisa e quais os tipos de dados que eu tenho.

Nas primeiras semanas de projeto, deve-se realizar tarefas inicias como análise exploratória dos dados. Essa etapa irá ser de suma importância pois podemos destinguir os atributos, realizar analises univariadas e multivariadas, realizar testes de estatisticos de hipotese e também trabalhar com o enriquecimento dos dados através da criação de multiplas variaveis.

### Ferramentas

O objetivo principal deste projeto não é resolver problemas de Big Data, mas sim a habilidade de utilizar ferramentas adequadas para solucionar desafios específicos, o que é de suma importância. A seguir, listo algumas ferramentas e frameworks essenciais que considero indispensáveis para o projeto. O domínio dessas ferramentas não só agilizará o tempo de desenvolvimento, mas também permitirá que nos concentremos mais na modelagem, que é o cerne do trabalho:

 - **Python:** Principal linguagem de programação na área de dados
 - **MySQL Workbench:** Ferramenta para desenvolvimento e consulta dos dados MySQL
 - **Git:** Essencial para o controle de versões e colaboração
 - **Power BI, Tableau ou Metabase:** Ferramentas de visualização de dados que facilitam a interpretação dos resultados e o compratilhamento de insights com stakeholders não técnicos
 - **Pandas e NumPy:** Indispensáveis para análise de dados
 - **Scikit-learn, XGBoost, TensorFlow, Keras, PyTorch, LightGBM ...** Bibliotecas para machine learning
 - **Docker:** Facilita a criação, implantação e execução de aplicações por meio de contâiners, útil para manter a consistência entre ambientes de desenvolvimento, teste e produção 
 - **AWS, Google Cloud ou Azure:** Oferecem serviços robustos para hospedagem, processamento e armazenamento de dados, além de capacidades de machine learning e analytics. Atualmente, trabalho com Azure, mas estou familiarizado com o fato de que a AWS é a plataforma de nuvem predominante na empresa. A transição para a AWS não deve apresentar problemas significativos, uma vez que muitas das ferramentas e conceitos são semelhantes entre as plataformas

Esta lista apresenta algumas das ferramentas essenciais que todo cientista de dados deve conhecer para iniciar um projeto. Embora tenha incluído as principais, possivelmente deixei de fora algumas ferramentas importantes, como o SQL Alchemy para ORM (mapeamento objeto-relacional) que facilita a consulta a bancos de dados, ferramentas de ETL, Databricks, ou mesmo plataformas avançadas de operações de machine learning, como MLOps. 

Estas são apenas algumas das tecnologias consideradas básicas para o começo de um projeto, mas a lista pode ser expandida conforme a evolução das necessidades do projeto.


Cada objetivo do projeto será destrinchado em cada uma das etapas 

## Sugetão de Mix de Produtos 
Para resolver o problema de sugerir um mix de produtos para novas lijas e ajustar o mix em lojas existentes com o objetivo de otimizar o desempenho e a satisfação do cliente, pode-se seguir uma abordagem estrutura baseada em analise de dados e modelagem preditiva da seguinte maneira

### 1. Coleta de Dados
 
 - Obter os dados históricos de vendas de outras lojas, incluindo informações sobre produtos, quantidade vendidas, preços e temporadas (Processo de consulta do banco de dados MySQL)
 
 - Dados demongráficos e de mercado: Incluir informações sobre a população local, renda média, preferências de consumo, e concorrências nas áreas proximas às lojas. Nesse processo o enriquecimento de dados é fundamental, uma vez que o banco não possui todos os dados necessários para se montar um modelo.

### 2. Análise Exploratória de Dados
Exemplo p/ EDA:
 - Análise de tendências: Identificação de quais produtos são mais populares em diferentes regiões ou períodos do ano.
 - Segmentação de clientes: Técnicas de clustering para identificar diferentes segmentos de clientes e suas preferências.
 - Análise de correlação: Relações entre as vendas de diferentes produtos para identificar possíveis combinações ou substituições. 


### 3. Modelo Preditivo 

Esta fase do projeto envolve a implementação de dois modelos preditivos, executados em paralelo, ambos fundamentais para a tarefa de recomendação. Em sistemas de recomendação, geralmente utilizamos dois tipos principais de algoritmos: Sistemas de Recomendação Baseados em Conteúdo e Sistemas de Recomendação Colaborativos. Para o contexto deste projeto, a aplicação de ambos os algoritmos se mostra bastante adequada

Para as novas lojas, iniciaremos com uma análise de clustering baseada em similaridade. É importante destacar que, embora cada loja possua um layout específico, o enriquecimento de dados nos permite identificar lojas similares com base em características específicas. Este processo de clustering é crucial e serve como a fundação para a aplicação subsequente dos algoritmos de recomendação. É essencial garantir que as comparações sejam feitas entre lojas com contextos similares — por exemplo, comparar lojas em São Paulo com outras em São Paulo, ao invés de com lojas na Bahia, devido às diferenças significativas em preferências regionais. Neste sentido, o princípio de "Garbage In, Garbage Out" é particularmente relevante: a qualidade dos insights gerados depende diretamente da qualidade e relevância dos dados utilizados nas comparações.

A seguir, apresentamos a arquitetura dos sistemas desenvolvidos para os dois cenários deste objetivo. As figuras ilustram como os sistemas funcionarão tanto para o mix inicial em novas lojas quanto para ajustes no mix em lojas já ativas, garantindo que as estratégias sejam adaptadas e otimizadas para cada contexto específico.

![Arquitetura - Mix Inicial para Novas Lojas](/images/1.png)

Para as novas lojas, a recomendação baseada em conteúdo é a técnica escolhida. Esse método utiliza características dos produtos e das lojas já existentes para identificar e recomendar um mix de produtos ideal. A ideia é analisar atributos como categoria de produtos, desempenho de vendas em lojas similares, e dados demográficos das áreas ao redor para sugerir produtos que provavelmente terão boa aceitação no novo local. Essa abordagem é particularmente útil para novas lojas sem histórico de vendas, pois permite fazer inferências baseadas nas características dos produtos e comparações com lojas semelhantes em termos de localização e perfil de cliente.

![Arquitetura - Mix para Lojas já Ativas \label](/images/2.png)

Para as lojas já ativas, o sistema de recomendação de filtragem colaborativa é mais apropriado. Este método analisa padrões de compra e preferências de vários usuários (neste caso, várias lojas da rede) para identificar produtos que possam ser bem-sucedidos em uma loja específica. Utilizando dados de vendas de clientes de múltiplas lojas, o sistema pode sugerir produtos que, embora não tenham sido previamente considerados ou vendidos na loja em questão, demonstraram sucesso em lojas com perfis de consumidores semelhantes. Este modelo é eficaz em ajustar e otimizar o mix de produtos baseado nas experiências compartilhadas de outras lojas, facilitando assim a identificação de oportunidades de vendas cruzadas e a substituição de itens de baixo desempenho por alternativas comprovadas.

### 4. Implementação

### 5. Avaliação de Desempenho 

### 6. Iteração e Ajustes



## Ajuste de Capacidades de Produtos 

### 1. Coleta de dados 

### 2. 

## Otimização do Reabastecimento




[Apresentação do Desafio - Mix de Produtos](https://available-salute-e12.notion.site/Projeto-Automatiza-o-Mix-Produtos-f529cc37aaed4a1bb7a149cf27c1cc53?pvs=4)