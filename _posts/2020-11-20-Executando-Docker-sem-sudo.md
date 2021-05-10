---
layout: post
title:  Executando Docker sem sudo
description: Essa é uma situação bem comum principalmente com quem está iniciando em usar docker, efetuar a instalação e logo nos comandos receber uma mensagem de permissão negada....
date:   2020-11-20 15:01:35 +0300
image:  'images/posts/2020/11/20/docker_sudo.png'
tags:   [docker, linux]
---

Essa é uma situação bem comum principalmente com quem está iniciando em usar docker, efetuar a instalação e logo nos comandos receber uma mensagem de permissão negada.

Esse tutorial pretende auxiliar usuários de linux

Caso não tenha instalado basta seguir essa postagem onde explico como efetuar as instalação: http://cafecodigo.com.br/instalando-docker-no-ubuntu-e-semelhantes

Com o docker instalado, pode tentar buscar qualquer imagem, para isso basta executar o comando:
```bash
 docker search nginx
```
Provavelmente receberá a mensagem de que não tem as permissões necessárias.

Uma forma rápida de resolver isso seria utilizar o comando sudo, porém incluir sudo em todo comando do docker, além de acrescentar mais um fator para se preocupar e digitar sempre que executar, pode causar inconsistências na execução quando seus exemplos se tornarem mais complexos.

A solução mais eficaz é criar um grupo com autorização de adm para o docker e adicionar seu usuário nesse grupo:

Criar um grupo no linux:

```bash
sudo groupadd docker
```

Adicionar seu usuário no grupo criado:

```bash
sudo usermod -aG docker $USER
```

Agora para efetivar as mudanças basta efetuar o logout e o login no seu computador.

Um teste rápido pode ser feito, tentando buscar qualquer imagem docker

```bash
 docker search nginx
 ```

agora ele deve executar o comando sem problemas.


Fonte: https://docs.docker.com/engine/install/linux-postinstall/
