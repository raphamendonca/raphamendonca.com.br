---
layout: post
title:  Programação Orientado a Objeto
description: Programar criando representações de estruturas do mundo real, criando objetos e asism trabalhar com essas representações no seu código.
date:   2021-06-15 09:00:00 +0300
image:  'images/code_background.png'
tags: [fundamentos]
category: tech
---

A Programação Orientada a Objetsos, ou POO, é uma das formas de como é possível escrever seu código para resolver um problema. 
Sua principal característica é organizar modelos de objetos reais em classes e com essas classes é possível criar diversos objetos, daí que vem o nome Orientação a Objetos.

### Historia
A POO teve seu uso popularizado na decada de 90, porém foi concebida muita tempo antes, em 1967 com a linuagem de programação focada em simulações _Simula 67_. Tendo sua definição como POO oficializada nos anos 70.

Ficou bem popular com o C++ e subsequente com o JAVA, e outras linguagens começaram a adotar sua estrutura.

Suas principais características é permitir a criação de objetos para serem utilizados no decorrer da programação. Porém conta com alguns pilares sendo eles Herança, Encapsulamento e Polimorfismo

### Objetos

Objetos são representações de coisas/modelos do mundo real. Como todas as coisas do mundo real, elas possuem caratecteristicas que as define e ações que conseguem executar.

Por exemplo um smartphone, quase todo mundo tem um, portanto podemos dizer que existem diversas instancias* e smartphones por ai.

Todos os smartphones tem um conjunto e características que o definem como um smarphone:
- Tela
- Processador
- Memoria
- Sistema operacional
- Camera
- Fabricante
- Modelo

Isso para a POO são os atributos desse objeto.
Alem dos atributos todos os smartphones possuem certas funcionalidades por exemplo:
- ligar
- acessar internet
- instalar aplicativos
- tirar foto

Essas ações são para a POO os metodos desse objeto.

Esse conjunto de atributos e metodos, compoem o que chamamos e classe. As classes são os 'moldes' que definem como os objetos serão criados.

Instancia é a criação esse objeto. Cada smartphone criado é uma instancia do objeto Smartphone.
Portanto cada instancia apesar e ter a mesma estrutura podem ter informações diferentes.(Iphone, MotoG, Galaxy, etc.)

Ex de codigo em Java da estrutura de um objeto:

``` java
public class Smartphone{
    String sistemaOperacional;
    Integer camera;
    String fabricante;
    String modelo;
    String processador:
    Integer memoria;
    String sistemaOperacional;

    public Ligacao ligar(Integer numero){
        ...
    }
    public void InstalarAplicativos(String aplicativo){
        ...
    }
    public void TirarFoto(){
        ...
    }
}
``` 

### Encapsuladmento

O encapsulamento é a possibilidade de ocultar determinados atributos ou a possibilidade de editar um atributo de um determinado objeto.

Se considerarmos o exemplo dos smartphones cada fabricante pode querer restringir como seus smartphones efetuam a instalação de aplicativos. impossibilitando que seja possível instalar aplicativos de uma loja diferente. Com isso ela pode ocultar onde é definido a busca por aplicativos.
Esse metodo fica oculto e niguem que tiver um smartphone podera alterar isso.

A mesma situação pode ser aplicada para atributos, um atributo pode ser oculto para alteração. ou ate mesmo para consulta sendo utilizado somente de forma interna no objeto.

``` java
public class Smartphone{
    private String sistemaOperacional;
    private String fabricante;
    //demais atributos
    private Integer armazenamento;

    public String getSistemaOperacional(){
        return sistemaOperacional;
    }
    public String getSistemaOperacional(){
        return sistemaOperacional;
    }
    public Integer getArmazenamento(){
        return armazenamento;
    }
    public setArmazenamento(Integer sdCard){
        armazenamento += sdCard
    }

    public void instalarAplicativos(String aplicativo){
        buscarLoja()
    }
    private void buscarLoja(){
        ...
    }
}

``` 
No exemplo acima o objeto smartphone permite que seja consultado seus valores, porém só permite que seja alterado seu armazenamento. Da mesma forma que o metodo buscar loja é interno ao objeto e não é possível acessa-lo de forma externa, somente pelo metodo InstalarAplicativos


### Herança

Assim como as coisas do mundo real possuem uma classificação por suas características e muitas coisas compartilham das mesma origem, poranto herdam essas caracteristicas dessa estrutura "pai/mãe". Nos smartphones por exemplo, apersar de parecer que são originarios dos telefones celulares, eles tem muito mais em comum com computadores modernos.
Observando os atributos que definimos aqui:

- Tela
- Processador
- Memoria
- Sistema operacional
- Camera
- Fabricante
- Modelo

Podemos utilizar o mesmo conjunto de atributos para definir um notebook, ou algum outro computador. Pensando no que seria a herança nesse caso. 

- computador
    - Notebook
    - smartphone

exemplificando com código(JAVA)

``` java
public class Computador{
    String sistemaOperacional;
    String fabricante;
    String modelo;
    String processador:
    Integer memoria;
}

public class Notebook extends Computador{
    Integer camera;
    Integer tela;
}

public class Smartphone extends Computador{
    Integer camera;
    Integer tela;
}
```


No codigo acima um computador possui um sistema operacional, fabricante, modelo, processador, memória. Um Notebook é um computador ( definido no java pelo extends na definição da classe), portanto ele possui os mesmos atributos de um computador assim como um smartphone também possui. 

Da mesma forma que os atributos os metodos também podem ser herdados, nesse exemplo 


``` java
public class Computador{
    // atributos
    public void conectaInternet(){
        // implementação
    }
}


public class Smartphone extends Computador{
    // atributos

    public void ligar(){
        // implementação
    }
}
```

Por Smartphone herdar de Computador ele também pode conectar a internet. Mas por ter características particulares ele implementa a funcção de ligar. 

Nesse caso um smartphone pode conectar a internet e ligar, ja um computador pode somente conectar a internet.

#### Interfaces

Outra característica de linguagens POO é possuir interfaces, as interfaces são uma forma de definir caracteristicas de comportamento de classes. 

As classes não podem herdar interfaces, mas interfaces podem herdar outras interfaces. Uma classe pode implementar uma interface, e ao implementar a interface ela precisa implementar todos os métodos definidos na interface. 

No caso dos smartphones eles tem uma caracteristica difernete de computadores mas similar a outros objetos, eles são portateis, assim como um carteira e mochila, Pode se definir então que a interface Portatil possui o metodo carregar

Nesse caso o exemplo
```java
public interface Portatil{
    public void carregar();
}
public class Smartphone extends Computador implements Portatil{
    // atributos
    public void carregar(){
        //implementacao do metodo carregar o Smartphone
    }
}
public class Mochila implements Portatil {
    // atributos
    public void carregar(){
        //implementacao do metodo carregar o mochila
    }
}
```

No exemplo tanto mochila quanto smartphone implementam a interface Portatil, porem cada um tem sua implementação distinta. Até mesmo porque uma mochila e um smartphone são carregados de maneiras diferentes.

### Polimorfismo

O polimorfismo é a possibilidade de criar diferentes implementações para um mesmo método de um objeto.

No caso do computador e smartphone ambos possuem o metodo conectaInternet, porém podem ter implementações diferentes. Um computador pode conectar na internet através de um cabo de rede ou wifi. Ja um smartphone pode conectar através do wifi ou da rede de telefonia(4G, 5G...).


``` java
public class Computador{
    // atributos
    public void conectaInternet(Wifi wifi){
        conectaWifi()
    }
}


public class Smartphone extends Computador{
    // atributos
    public void conectaInternet(Rede4g rede){
        conecta4g()
    }
}
```

Nesse exemplo a implementação de conectar recebendo Wifi é a mesma tanto computador quanto smartphone, mas o smartphone tem a possibilidade de receber uma rede4G para efetuar a conexão. Dessa forma o método sofreu o polimorfismo e possui varias formas de ser utilizado de acordo com sua implementação.


## Padroes De codigo

Dentro de todas as diferentes formas de criar um código existem padroes que otimizam e são considerados boas praticas. Essas praticas possibilitam uma otimização do paradigma, uma melhor manutenção e evolução do codigo.

Mas esse tema será abordado em outro post.