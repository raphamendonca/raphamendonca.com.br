---
layout: post
title:  Introdução ao Apache KAFKA
description: 
date:   2021-011-07 20:00:00 +0300
image:  'images/posts/2021/11/07/apache_kafka.jpeg'
tags: [fundamentos]
---

Ao trabalhar com microsserviços, data science e diversas outras soluções hoje em dia é quase impossível não ter ouvido falar de Kafka, essa plataforma criada para processamento de streams com alta demanda e capacidade de processar dados em tempo real, tem revolucionado a forma como o desenvolvimento e a integração de sistemas tem funcionado.

O [Apache Kafka](https://kafka.apache.org/) foi criado inicialmente dentro do Linkedin e disponibilizado como sofrware opensource em 2011, hoje sob desenvolvimento da Apache Software Foundation e teve seu nome em homenagem a Franz Kafka, autor que um dos responsáveis pelo projeto gostava e quis homenagear. Em 2014 três pessoas da equipe que trabalhava com Kafka dentro do Linkedin decidiram sair e fundar sua propria empresa a [Confluent](https://www.confluent.io/), uma empresa focada em atuar com Kafka, contribuindo para melhoria, oferenendo soluções, treinamentos e muito mais. Alem de disponibilizarem diversos materiais gratuitos sobre o conhecimento em Kafka.

O Kafka é uma ferramenta poderosa na criação de uma solução, projetado para trabalhar com alta demanda, consegue trabalhar com milhões de requisições simultâneamente,
sua estrutura em cluster possibilita toda essa capacidade, tal cluster gerenciado pelo [Zookeeper](https://zookeeper.apache.org/), garante uma coordenação das instâncias, garantindo a resiliência 

O Kafka funciona com uma estrutura onde é possível publicar e ler eventos, através de "producers" ( produtores) e "consumers" (consumidores), esses eventos são enviados para tópicos. Os tópicos podem ser dividios cem partições, essas partições garantem resiliencia e são distribuidas dentro do cluster.

![Kafka Structure](/images/posts/2021/11/07/kafka_structure.png "Kafka Structure")

Os producers enviam as mensagens aos topicos, essas mensagens sao replicadas nas particoes e tribuidas de um identificador. Os consumers leed dos topicos as mensagens que neles foi publicada. O identificador garante a ordem das mensagens para os consumers e que todas as mensagens serão consumidas. 
O Kafka garante que os consumers sejam distribuidos entre as particoes, possibilitando um processamento paralelo e aumentando a performance do processamento. Se uma partição é adicionada ou removida o Kafka redistribui os consumidores. o mesmo para um novo consumidor que seja atribuido. 

Os consumidores são identificados por um nome, a relacao descrita acima representa como um consumidor com um determinado nome ( ou multiplas instancias dele) se comportam.  Se dois consumidores com nomes distindos estiverem ouvindo um mesmo topico, todos os eventos serão processados por ambos os consumidores. Porem dois consumidores com o memso nome, não processarão o mesmo evento. 

Esses eventos possuem uma etrutura chamada Schema Registry e tem uma notação similar a JSON. No site da confluent possui uma descrição mais detalhada de como funciona [Schema Registry doc](https://docs.confluent.io/platform/current/schema-registry/index.html)

O Kafka armazena os eventos da mesma forma que muitas aplicações armazenam logs, no filesystem de forma sequencial, com isso os eventos no Kafka funcionam como um fluxo temporam ( Streams ) Podendo ser processados e trabalhados como tal. Alem de ter uma liguagem de consulta de eventos chamada ksql[KSQÇ](https://www.confluent.io/blog/ksql-streaming-sql-for-apache-kafka/).

Dentre os usos do kafka estão, processamentos assincronos, sistemas de notificação, sincronia entre diferentes sistemas, envio de dados de aplicações para Data Science e muitos outros. 

Existem diversos plugins para enviar e consumir eventos do Kafka implementados em diversas linguagens de programação. Tornando-a uma ferramente muito versátil na integração de sistemas.

Essa é uma explicação simplificada do funcionamento.

Para saber mais sobre o Kafka, a confluent disponibilizou uma serie de videos de fundamentos (em ingles).  Alem de encontrar diversos outros materiais como livros e treinamentos em diversas plataformas de cursos como Alura, Udemy e outros.

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLa7VYi0yPIH2PelhRHoFR5iQgflg-y6JA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Vale a pena dar uma olhada e entender um pouco mais sobre Kafka. 


