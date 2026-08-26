# Orientação a Objetos

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_java)

## Sumário

1. [Classes Java](#classes-java)<br>
    1.1 [Objetos](#objetos)<br>
2. [Pacotes (packages)](#pacotes-packages)<br>
    2.1 [Declarando um pacote](#declarando-um-pacote)<br>
    2.2 [Pacote e estrutura de pastas](#pacote-e-estrutura-de-pastas)<br>
    2.3 [Importando uma classe](#importando-uma-classe)<br>
    2.4 [Nome completo da classe](#nome-completo-da-classe)<br>
    2.5 [Pacote padrão](#pacote-padrão)<br>
    2.6 [Pacotes e controle de acesso](#pacotes-e-controle-de-acesso)<br>
    2.7 [Exemplo de estrutura de packages](#exemplo-de-estrutura-de-packages)<br>


## Classes Java

No paradigma da Orientação a Objetos, o programa é dividido em blocos menores chamados classes, que por sua vez são subdivididos em atributos (valores) e métodos (ações). A partir delas, são criados os objetos.

> [!NOTE]
> Antes do Java 25, cada arquivo `.java` era na verdade uma classe. Isso incluia o arquivo a ser executado, que continha o código-fonte principal. Isso mudou com o Java 25, onde o arquivo principal contém apenas a função `void main()`.<br>
> Já uma classe Java sem ser a principal continua sendo criado da mesma forma que antes: crie um arquivo `.java` e dê o mesmo nome que deseja pôr na classe.

Uma classe Java é feito da seguinte forma, usando como exemplo a classe `Pessoa`:

#### Diagrama de Classes

~~~mermaid
classDiagram
    class Pessoa {
        +String nome
        +int idade
        +double altura
        +cumprimentar() void
    }
~~~

#### Código-fonte da Classe

~~~java
public class Pessoa {
    // atributo
    public String nome;
    public int idade;
    public double altura;

    // método
    public void cumprimentar() {
        IO.print("Olá, meu nome é " + nome);
        IO.print(", tenho " + idade + " anos");
        IO.print(", e " + altura + " metros de altura.");
    }
}
~~~

### Objetos

Para criar um objeto de uma classe, faça como no exemplo abaixo:
~~~java
void main() {
    // cria objeto da classe
    Pessoa usuario = new Pessoa();

    // entrada de dados
    usuario.nome = IO.readln("Informe o nome: ");
    usuario.idade = Integer.parseInt(IO.readln("Informe a idade: "));
    usuario.altura = Double.parseDouble(IO.readln("Informe a altura em metros: "));

    // saída de dados
    IO.println("Nome: " + nome);
    IO.println("Idade: " + idade + " anos");
    IO.println("Altura: " + altura + " metros");
}
~~~

> [!TIP]
> A criação do objeto de uma classe também é chamado de **instância de classe**.

## Pacotes (packages)

Um **pacote** (*package*) é uma forma de organizar classes e interfaces relacionadas. Ele funciona como uma pasta lógica do projeto e ajuda a:

- evitar conflitos entre classes com o mesmo nome;
- deixar o projeto mais organizado;
- controlar o acesso entre classes por meio dos modificadores de acesso.

### Declarando um pacote

A declaração do pacote deve ser a primeira instrução do arquivo `.java`, antes das classes e dos `import`s:

~~~java
package modelo;

public class Pessoa {
    public String nome;
}
~~~

Por convenção, os nomes dos pacotes são escritos em letras minúsculas. Em projetos maiores, é comum usar o domínio invertido da organização, por exemplo `br.com.exemplo.modelo`.

### Pacote e estrutura de pastas

O caminho das pastas deve acompanhar o nome do pacote. Assim, uma classe declarada como `package br.com.exemplo.modelo;` normalmente fica em:

~~~text
src/
└── br/
    └── com/
        └── exemplo/
            └── modelo/
                └── Pessoa.java
~~~
[![Package Java](../img/package-java.svg)](https://www.readmecodegen.com/file-tree/create-folder-structure-online)

Essa correspondência permite que o compilador e as ferramentas do projeto encontrem a classe corretamente.

### Importando uma classe

Para usar uma classe que está em outro pacote, utilize `import`:

#### No Java anterior ao 25
~~~java
package aplicacao;

import br.com.exemplo.modelo.Pessoa;

public class Programa {
    public static void main(String[] args) {
        Pessoa pessoa = new Pessoa();
    }
}
~~~

#### No Java 25+
~~~java
import br.com.exemplo.modelo.Pessoa;

void main() {
    Pessoa pessoa = new Pessoa();
}
~~~

Também é possível importar todas as classes diretamente de um pacote com `*`:

~~~java
import br.com.exemplo.modelo.*;
~~~

Porém, o `*` não inclui classes de subpacotes. Por exemplo, importar `br.com.exemplo.modelo.*` não importa classes de `br.com.exemplo.modelo.dados`.

### Nome completo da classe

O `import` é apenas uma conveniência. Sem ele, a classe pode ser usada pelo nome completo, formado pelo pacote e pelo nome da classe:

~~~java
br.com.exemplo.modelo.Pessoa pessoa = new br.com.exemplo.modelo.Pessoa();
~~~

Essa forma é útil quando existem classes com o mesmo nome em pacotes diferentes.

### Pacote padrão

Se um arquivo não tiver uma declaração `package`, ele estará no **pacote padrão**. Esse recurso pode funcionar em exemplos pequenos, mas deve ser evitado em projetos reais: classes dentro de pacotes nomeados não conseguem importar classes do pacote padrão.

### Pacotes e controle de acesso

Quando nenhum modificador de acesso é informado, o membro ou a classe tem acesso de **pacote** (*package-private*): pode ser acessado por classes do mesmo pacote, mas não por classes de outros pacotes.

~~~java
package modelo;

class CadastroInterno {
    public String codigo;
}
~~~

Nesse exemplo, `CadastroInterno` só pode ser usado por classes do pacote `modelo`. Para permitir o uso em outros pacotes, a classe ou membro precisa de um modificador como `public`.

### Criar um novo package no VSCode

> [!TIP]
> Crie primeiro um novo *package*, e só depois crie uma nova classe Java.

1. Clique com o botão direito do mouse em cima da pasta `src/`;
2. Clique em **New Java Package...**;
3. Informe o nome desejado para o *package*, seguindo o padrão de mercado, e dê `Enter`. Exemplo: `br.com.nome.models`;

#### Para criar um package dentro de outro package

1. Clique com o botão direito do mouse em cima do diretório do package;
2. Dê o nome do do seu package após o ponto depois do último nome do package e dê `Enter`.

#### Para criar uma nova classe dentro do package

1. Clique com o botão direito do mouse em cima do package desejado;
2. Clique na opção **New Java File -> Class...**;
3. Dê o nome da sua classe, começando com letra maiúscula.

### Exemplo de estrutura de packages

#### Diretórios

```
projeto-java/
├── bin/
├── lib/
└── src/
    ├── br/
    │   └── com/
    │       └── models/
    │           └── Pessoa.java
    └── App.java

```
[![Package Class](../img/package-classe.svg)](https://www.readmecodegen.com/file-tree/create-folder-structure-online)

> [!WARNING]
> Dentro da pasta `bin`, tem conteúdo necessário para o funcionamento do seu programa, mas não mexemos nela. A única coisa que importa para o desenvolvedor é o conteúdo da pasta `src/`.