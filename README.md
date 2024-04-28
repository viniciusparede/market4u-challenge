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


Cada objetivo do projeto será destrinchado em cada uma das etapas, algumas etapas em todos os objetivos do projeto são pilares básicos do projeto, por exemplo a coleta dos dados advindo do proprio banco de dados do aplicativo ou até mesmo outras fontes de dados para realizar o enriquemento dos dados

Nesse momento deixo um exemplo de como funcionaria a coleta dos dados e também a analise exploratoria desses dados

### Coleta de Dados
 
 - Obter os dados históricos de vendas de outras lojas, incluindo informações sobre produtos, quantidade vendidas, preços e temporadas (Processo de consulta do banco de dados MySQL)
 
 - Dados demongráficos e de mercado: Incluir informações sobre a população local, renda média, preferências de consumo, e concorrências nas áreas proximas às lojas. Nesse processo o enriquecimento de dados é fundamental, uma vez que o banco não possui todos os dados necessários para se montar um modelo.

### Análise Exploratória de Dados
Exemplo p/ EDA:
 - Análise de tendências: Identificação de quais produtos são mais populares em diferentes regiões ou períodos do ano.
 - Segmentação de clientes: Técnicas de clustering para identificar diferentes segmentos de clientes e suas preferências.
 - Análise de correlação: Relações entre as vendas de diferentes produtos para identificar possíveis combinações ou substituições. 


## Sugetão de Mix de Produtos 
Para resolver o problema de sugerir um mix de produtos para novas lojas e ajustar o mix em lojas existentes com o objetivo de otimizar o desempenho e a satisfação do cliente, pode-se seguir uma abordagem estrutura baseada em analise de dados e modelagem preditiva da seguinte maneira

### Modelo Preditivo 

Esta fase do projeto envolve a implementação de dois modelos preditivos, executados em paralelo, ambos fundamentais para a tarefa de recomendação. Em sistemas de recomendação, geralmente utilizamos dois tipos principais de algoritmos: Sistemas de Recomendação Baseados em Conteúdo e Sistemas de Recomendação Colaborativos. Para o contexto deste projeto, a aplicação de ambos os algoritmos se mostra bastante adequada

Para as novas lojas, iniciaremos com uma análise de clustering baseada em similaridade. É importante destacar que, embora cada loja possua um layout específico, o enriquecimento de dados nos permite identificar lojas similares com base em características específicas. Este processo de clustering é crucial e serve como a fundação para a aplicação subsequente dos algoritmos de recomendação. É essencial garantir que as comparações sejam feitas entre lojas com contextos similares — por exemplo, comparar lojas em São Paulo com outras em São Paulo, ao invés de com lojas na Bahia, devido às diferenças significativas em preferências regionais. Neste sentido, o princípio de "Garbage In, Garbage Out" é particularmente relevante: a qualidade dos insights gerados depende diretamente da qualidade e relevância dos dados utilizados nas comparações.

A seguir, apresentamos a arquitetura dos sistemas desenvolvidos para os dois cenários deste objetivo. As figuras ilustram como os sistemas funcionarão tanto para o mix inicial em novas lojas quanto para ajustes no mix em lojas já ativas, garantindo que as estratégias sejam adaptadas e otimizadas para cada contexto específico.

![Arquitetura - Mix Inicial para Novas Lojas](/images/1.png)

Para as novas lojas, a recomendação baseada em conteúdo é a técnica escolhida. Esse método utiliza características dos produtos e das lojas já existentes para identificar e recomendar um mix de produtos ideal. A ideia é analisar atributos como categoria de produtos, desempenho de vendas em lojas similares, e dados demográficos das áreas ao redor para sugerir produtos que provavelmente terão boa aceitação no novo local. Essa abordagem é particularmente útil para novas lojas sem histórico de vendas, pois permite fazer inferências baseadas nas características dos produtos e comparações com lojas semelhantes em termos de localização e perfil de cliente.

![Arquitetura - Mix para Lojas já Ativas \label](/images/2.png)

Para as lojas já ativas, o sistema de recomendação de filtragem colaborativa é mais apropriado. Este método analisa padrões de compra e preferências de vários usuários (neste caso, várias lojas da rede) para identificar produtos que possam ser bem-sucedidos em uma loja específica. Utilizando dados de vendas de clientes de múltiplas lojas, o sistema pode sugerir produtos que, embora não tenham sido previamente considerados ou vendidos na loja em questão, demonstraram sucesso em lojas com perfis de consumidores semelhantes. Este modelo é eficaz em ajustar e otimizar o mix de produtos baseado nas experiências compartilhadas de outras lojas, facilitando assim a identificação de oportunidades de vendas cruzadas e a substituição de itens de baixo desempenho por alternativas comprovadas.

### Implementação e Avaliação de Desempenho
**Novas Lojas: Teste A/B**
Para novas lojas, o teste A/B é uma abordagem valiosa para avaliar o impacto do modelo de sugestão de mix de produtos. Neste teste, dividimos as lojas em dois grupos: o Grupo A, composto por lojas que operam sem a implementação do modelo, confiando apenas na experiência do franqueado para a seleção do mix de produtos; e o Grupo B, onde o modelo é utilizado para sugerir o mix de produtos. O faturamento de cada grupo será monitorado durante um período específico, permitindo uma comparação direta dos resultados financeiros. A análise estatística será aplicada para testar a hipótese nula de que o modelo não proporciona um desempenho superior, com o objetivo de validar a eficácia do modelo sugerido.

**Lojas Existentes: Teste MVT**
Para lojas já estabelecidas, o teste multivariado (MVT) é recomendado. Esse método permite testar múltiplas variáveis simultaneamente para entender o impacto combinado de diversas alterações no mix de produtos. Essa abordagem facilita uma otimização mais detalhada e direcionada do modelo, explorando várias configurações de produto e suas interações. O faturamento também serve como métrica principal nesse contexto, oferecendo uma visão clara de como diferentes combinações influenciam o desempenho financeiro das lojas.

**Considerações Adicionais**
É crucial ajustar a análise para eventos de sazonalidade e outros fatores externos que possam influenciar o desempenho das lojas. A separação e análise desses eventos são essenciais para garantir que as comparações entre os modelos sejam justas e baseadas em condições operacionais semelhantes. Isso ajuda a isolar o efeito real do modelo de sugestão de mix de produtos sobre o faturamento das lojas.

Ao adotar essas abordagens de teste, as organizações podem não apenas validar a eficácia dos modelos de Machine Learning em diferentes contextos operacionais, mas também refinar continuamente suas estratégias para otimizar os resultados financeiros e a satisfação do cliente.

## Ajuste de Capacidades de Produtos 
A etapa de ajuste de capacidade de produto visa otimizar a gestão de estoque nas lojas, garantindo que a alocação de produtos esteja alinhada com a demanda real e as variações sazonais. Essa fase vislumbra maximizar a eficiência operacional e melhorar a experiência do cliente. Abaixo, detalha-se as principais estratégias e metodologias para implementar esse ajuste de forma eficaz.

Inicialmente, é fundamental realizar uma análise detalhada da demanda histórica por produtos, considerando fatores sazonais e tendências de mercado. Essa análise deve incluir a coleta e avaliação de dados de vendas, promoções anteriores e eventos específicos que possam influenciar o consumo. Utilizar técnicas de análise de séries temporais pode ajudar a identificar padrões e prever demandas futuras com maior precisão. A analise de dados aqui é muito importante para limparmos do modelo preditivo qualquer SKU 

Para o cenário descrito, onde o objetivo é ajustar as capacidades dos produtos com base na sazonalidade e variações na demanda, pode-se implementar um modelo de otimização de estoque combinando técnicas de previsão de demanda com otimização de inventário. 

### Modelo Preditivo 

Na modelagem deste projeto, destacamos a elaboração de dois modelos principais para cada fase do projeto:

 1. Criação do modelo de demanda
 2. Criação do modelo de inventário (Problema de otimização)

Na primeira etapa, abordaremos a venda de alguns produtos utilizando análises de séries temporais. Isso permitirá estabelecer um modelo que não apenas prediz a demanda dos produtos, mas também identifica padrões de sazonalidade e classifica os ciclos de venda.

Para isso, utilizaremos um modelo de previsão de demanda que estima a demanda futura para cada SKU, com base em dados históricos e fatores externos, como tendências de mercado e sazonalidade. Modelos como ARIMA, SARIMA e Holt-Winters são adequados para essa tarefa, dada a sua eficácia em capturar padrões sazonais.

Com as previsões de demanda e a classificação dos SKUs em mãos, aplicaremos modelos de otimização de inventário para determinar o nível ideal de estoque para cada SKU. Este passo envolve um problema de otimização, onde podemos incluir restrições específicas que se alinham ao nosso modelo de negócios.

Após desenvolver esta fase, focamos no modelo de otimização. É essencial modelar a demanda de maneira que possamos chegar a uma equação que permita ajustar a capacidade dos produtos, visualmente representada como uma barra que indica a capacidade ao cliente.

Entre os modelos clássicos de gestão de demanda no varejo estão o Modelo de Pedido Econômico de Quantidade (EOQ) e o Modelo de Ponto de Pedido (ROP). O primeiro calcula a quantidade ideal de estoque para minimizar os custos totais de pedido e manutenção, enquanto o segundo determina o momento adequado para reordenar o estoque, baseando-se no nível atual de inventário e no tempo de entrega dos fornecedores. Estes modelos serão adaptados ao desenvolvimento do nosso modelo de negócio, considerando a previsão de demanda, sazonalidade, ciclos de venda e restrições como espaço físico, capital de giro, entre outros fatores logísticos.

A imagem abaixo ilustra a arquitetura do modelo preditivo proposto, integrando variáveis dependentes da previsão de demanda, identificação de ciclos, sazonalidade e suas respectivas restrições, com o objetivo de informar visualmente ao cliente a necessidade de ajustar a capacidade de produtos em sua loja.

![Arquitetura do modelo preditivo](/images/3.png)

### Implementação e Avaliação de Desempenho
**Teste A/B** 
Realização de testes para comparar lojas usando o modelo com lojas controle, permitindo avaliar a eficácia das estratégias de ajuste.

**Métricas de Avaliação:**
Utilização de indicadores como Curva de Ruptura dos itens, Índice de ruptura geral da loja, e performance de vendas dos produtos ajustados para medir o sucesso do projeto.

## Otimização do Reabastecimento

### Modelo preditivo

### Implementação e Avaliação de Desempenho



## Conclusão
Este projeto apresenta desafios significativos e exige uma compreensão profunda dos conhecimentos de negócios. O documento expõe a metodologia de maneira simplificada, oferecendo uma visão inicial de como podemos abordar as etapas. Contudo, é evidente que a viabilidade das técnicas propostas necessitará de estudos aprofundados, reuniões de acompanhamento, e uma análise detalhada do comportamento dos dados, que podem influenciar o projeto de maneiras inesperadas. Cada projeto envolve um alinhamento interno rigoroso, e a comunicação deve ser clara e eficaz para evitar mal-entendidos.

A ciência de dados, em essência, envolve a formulação de uma abordagem ao problema e, crucialmente, o teste dessa abordagem. O conceito de "falhar rápido" é vital aqui; a implementação de modelos de MVP para testar o impacto do projeto é essencial para solidificar nossa posição dentro da empresa.

Independentemente dos resultados das avaliações iniciais, desejo sucesso à Market4u e destaco a contribuição do Henrique (CTO), cujo documento meticulosamente detalhado justifica os objetivos do projeto e delineia estratégias para melhor atender às necessidades da empresa. A escolha do candidato, portanto, deve refletir a capacidade de levar esses planos adiante com competência e inovação.
