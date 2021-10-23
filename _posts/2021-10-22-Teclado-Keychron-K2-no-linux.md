---
layout: post
title:  Teclado Keychron K2 no linux
description: 
date:   2021-10-23 10:00:00 +0300
image:  'images/posts/2021/10/23/keychron_k2.png'
tags: [linux]
---

Recentemente adquiri um teclado mecanico da Keychron modelo K2. Eu ja queria um teclado melhor que pudesse utilziar no pc, notebook pessoal, do trabalho e outros aparelhos como tablet e o keychron me pareceu uma otima opção. 


Após ver diversos reviews e videos eu finalmente comprei e chegou muito rapido, gostei muito do acabamento, da embalagem e do produto como um todo.

![Teclado mecanico Keychron K2](/images/posts/2021/10/23/keychron_k2.png "Teclado mecanico Keychron K2")

Essa versão possui led RGB o que é bem bacana, é possivel selecionar diversos modos, inclusive um só branco(caso nao queira cores na sua vida).

![Teclado mecanico Keychron K2 com leds acesos](/images/posts/2021/10/23/keycrhon_k2_color.png "Teclado mecanico Keychron K2 com leds acesos")

Esse teclado possui algumas funções interessantes, como selecionar entre Bluetooth ou cabo, alem do modo windos e MAc. No linux utilizo o modo windows por maior compatibilidade.

![Lateral do teclado keychron k2, exibindo botões de seleção](/images/posts/2021/10/23/keycrhon_k2_side.png "Lateral do teclado keychron k2, exibindo botões de seleção")

## Configurando o layout do telcado

### UBUNTU:

Para funcionar no ubuntu eu utilizei o seguinte comando que configura o teclado para US modo ABNT

ps: ainda não consegui de forma efetiva deixar essa configuracao ativa, constantemente preciso re-executar o comando, assim que resolver atualizo esse post

```shell
setxkbmap -model abnt -layout us -variant intl
```

### POP-OS:

O software de idioma e meios de entrada do Pop-OS é bem mais completo e tem mais opções que o do Ubuntu eportanto pude configurar o telcado para uso sem muitos problemas. 

Porém as teclas de funções não estavam funcionando corretamente, somente apresentando o modo Multimidia. Uma pesquisa rapida em portugues me trouxe a um dos videos do Diolinux onde ele comenta dessa configuração no linux. trouxe aqui o passo a passo em portugues da configuração do keychron para as telcas de função.

Abra o terminal e digite o seguinte comando para criar um arquivo no diretorio do sistema. Esse arquivo receberá um script que ajusta a configuração das teclas de função.

```shell
sudo nano /etc/systemd/system/keychron.service
```

Copie o seguinte bloco para dentro do arquivo **keychron.service**

```shell
[Unit]
Description=The command to make the Keychron K2-k4 work with Function keys

[Service]
Type=oneshot
ExecStart=/bin/bash -c "echo 0 > /sys/module/hid_apple/parameters/fnmode"

[Install]
WantedBy=multi-user.target
```

Para salvar o arquivo aperte ctrl+o e depoisa ctrl+x para sair.

Agora é necessário habilitar o script para funcionar. 

```shell
sudo systemctl enable keychron
```

Agora só necessita reiniciar o sistema que as teclas de função devem voltar a funcionar.

Referencias:
- [DioLinux - Github - teclas de funcao keychron no linux](https://github.com/Diolinux/)
- [Arthur Gregorio blog - config teclado ubuntu](https://arthurgregorio.eti.br/blog/hardware/configurar-acentos-para-teclados-em-ingles-no-linux/)