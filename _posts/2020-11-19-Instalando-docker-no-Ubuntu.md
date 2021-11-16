---
layout: post
title: Instalar Docker no Ubuntu e semelhantes
description: Neste rápido tutorial vou explicar como eu fiz a instalação no meu computador que utiliza distro baseada no Ubuntu
date: 2020-11-19 10:47
image:  '/images/posts/2020/11/19/docker_ubuntu.png'
tags: [docker, linux]
category: [tech]
---


Neste rápido tutorial vou explicar como eu fiz a instalação no meu computador que utiliza o linux POP OS ( 20.04 )

As distribuições linux tendem a implementar um recurso que ajuda bastante, que é verificar se existe na disponível no gerenciador de pacotes o software que esteja tentando rodar.

Para verificar isso basta tentar rodar o comando ‘docker‘ no Pop OS, se não existir nenhuma instalação do docker atualmente na sua maquina, o SO vai retornar uma mensagem informando o comando possível para efetuar a instalação

``` bash
sudo apt install docker.io
```

Por se tratar de uma distro baseada no Ubuntu, é possível repetir esse mesmo passo para outras distros derivadas do próprio Ubuntu.

Caso esse passo não funcione para você, vou repassar abaixo os passos explicados no site oficial do docker, porém aqui deixarei as explicações em português.

Uma das coisas necessárias é remover qualquer resquício de instalações anteriores e isso pode ser feito com o comando:

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```
Agora o gerenciador apt vai remover as instalações do docker que ele encontrar, se o apt-get retornar que não foi encontrado nada, esta tudo bem para prosseguir.

Para instalação é possível instalar de algumas maneiras, uma delas é configurar o repositório do docker( mais recomendado, por manter melhor as atualizações ou baixar o .deb e efetuar a instalação( as atualizações precisarão ser efetuadas manualmente)

Para configurar o repositório do docker é preciso configurar o apt e o sistema para obter os dados via http
```bash
sudo apt-get update
```
```bash
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
O próximo comando pega a chave GPG do repositório oficial do docker:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Com isso seu computador tera o registro da chave de criptografia correspondente a 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88. Com o comando abaixo é possível visualizar os detalhes da chave

```bash
sudo apt-key fingerprint 0EBFCD88
```
Uma vez que a chave de criptografia esta configurada no apt, é possível adicionar o caminho do repositório do docker.

```bash
sudo add-apt-repository \   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \   $(lsb_release -cs) \   stable"
```

Obs: o comando lsb_release -cs recupera o nome da versão do Ubuntu que esteja utilizando, no caso do Pop-os e outros, vai recuperar a imagem Ubuntu base da sua distro

Sempre que atualizar o apt-repository, é muito importante efetuar o update do apt.

```bash
sudo apt-get update
```

Repositório configurado podemos iniciar finalmente a instalação do docker:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```



A melhor forma é se manter atualizado e tentar seguir os passos do site oficial, apesar de estar em inglês, possui explicações para os principais sistemas operacionais e no caso do linux para as principais distros.
https://docs.docker.com/engine/install/

Referencias:
GPG -> [GNU Privacy Guard]()

