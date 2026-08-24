# Lógica de Programação Aplicada a Java

## Sumário

1. [Algoritmo](#algoritmo)
2. [Instalação do Java](#instalação-do-java)
3. [Preparando o VSCode para o Java](#preparando-o-vscode-para-o-java)<br>
    3.1 [Extensões obrigatórias](#extensões-obrigatórias)<br>
    3.2 [Extensões recomendadas](#extensões-recomendadas)<br>
    3.3 [Sugestão de tema para o Java](#sugestão-de-tema-para-o-java)<br>
4. [Novo Projeto Java](#novo-projeto-java)<br>
    4.1 [Executando o projeto](#executando-o-projeto)<br>
    4.2 [Java 25](#java-25)<br>
5. [Comentários](#comentários)
6. [Variáveis](#variáveis)<br>
    6.1 [Exibindo valores de uma variável](#exibindo-valores-de-uma-variável)<br>
    6.2 [Concatenando valores](#concatenando-valores)<br>
7. [Estruturas de decisão](#estruturas-de-decisão)<br>
    7.1 [if...else](#ifelse)<br>

## Algoritmo

> [!NOTE]
> **Algoritmo** é o nome que se dá a solução de um problema, qualquer um que ele seja. É constituído de uma série de instruções passo-a-passo, que visam alcançar um determinado objetivo. Como exemplos, podemos pegar qualquer tutorial disponível na Internet, como este mesmo. Uma receita de bolo também pode ser considerado um algoritmo.

## Instalação do Java

> [!IMPORTANT]
> O Java que o usuário instala para rodar sites de banco e aplicativos é o **JRE** (**Java Runtime Environment**). Esse programa é necessário para rodar aplicações Java, pois dentro dele tem o **JVM** (**Java Virtual Machine**), mas só ele não é o suficiente para desenvolver programas Java.<br>
> Para programar, você precisará do **JDK** (**Java Development Kit**), que pode ser baixado da página de downloads da [**Oracle**](https://www.oracle.com/br/java/technologies/downloads/). Caso não tenha o JRE instalado na sua máquina, você pode baixar e instalar o JDK diretamente que automaticamente irá instalar também o JRE e o JVM.

> [!CAUTION]
> Ao baixar o JDK, procure sempre baixar a última versão **LTS** (**Long-Term Suport**).<br>
> Nem sempre essa versão será a última, pois a Oracle sempre lança uma atualização do Java a cada 6 meses, mas a versão LTS geralmente é a mais estável, e a que tem o maior e mais duradouro suporte por parte da Oracle.

## Preparando o VSCode para o Java

> [!TIP]
> É interessante que antes de começar a configurar o VSCode para o desenvolvimento, crie um Perfil específico para trabalhar com a linguagem Java:
> 1. Vá no menu **Arquivo -> Preferências -> Perfil -> Perfis**.
> 2. Clique no botão **Novo Perfil**.
> 3. Escolha um nome, mude o ícone, e depois clique em **Criar**.
> 4. Somente após isso que você deve instalar as extensões que desejar.

### Extensões obrigatórias

- Extension Pack for Java (pacote com extensões essenciais)
- Lombok Annotations Support for VS Code
- Code Generator For Java
- Database Client

### Extensões recomendadas

- Comment Anchors
- Error Lens
- VSCode icons

### Sugestão de tema para o Java

- One Dark Pro

## Novo Projeto Java

> [!WARNING]
> Um projeto Java não é igual ao de outras linguagens. Não basta simplesmente criar uma pasta e um arquivo `.java`. O programa Java precisa obrigatoriamente obedecer certos padrões de arquitetura, como veremos a seguir.

Para criar novo projeto Java no VSCode:
1. Abra o Explorador de Arquivos do VSCode (`Ctrl+Shift+E`);
2. Clique com o botão direito do mouse na área vazia do Explorador do VSCode e escolha a opção **New Java Project...**;
3. No alto da janela do VSCode, irá aparecer uma lista de opções. Escolha **No build tools** para o seu primeiro projeto Java;
4. Irá abrir uma janela do Explorador de Arquivos do Windows. Escolha a pasta onde deseja salvar o seu projeto, e clique no botão **Select the project location**;
5. No alto da janela do VSCode, irá aparecer uma caixa de digitação. Informe o nome desejado do seu projeto e aperte `Enter`.
6. Uma nova janela do VSCode irá se abrir já dentro do diretório do seu projeto. Confira abaixo a estrutura de pastas que deve estar aparecendo no Explorador do VSCode:
```
nome_do_projeto_java/
├── .vscode/
│   └── settings.json
├── lib/
├── src/
│   └── App.java
└── README.md

```
[![Projeto Java Inicial](../img/projeto_java_inicial.svg)](https://www.readmecodegen.com/file-tree/create-folder-structure-online)

### Executando o projeto

O que importa aqui é a pasta `src/`, mais precisamente o arquivo dentro dela: o `App.java`. Ele é o arquivo principal do seu projeto, e o que deverá ser executado. Ao abrir, você encontrará o seguinte código:
~~~java
public class App {
    public static void main(String[] args) throws Exception {
        System.out.println("Hello, World!");
    }
}
~~~

O diagrama de classes do programa é esse:
~~~mermaid
classDiagram
    class App {
        +main(String[] args) void
    }
~~~

O fluxograma do programa é esse:
~~~mermaid
flowchart TD
    A([Início]) --> B@{ shape: curv-trap, label: "Hello, World!" }
    B --> C([Fim])
~~~

Para executar o projeto:
- Use a tecla de atalho `Ctrl+F5`;
- Ou aperte o botão **Run** no alto à direita da janela do VSCode;
- Ou acesse o terminal (o VSCode tem um terminal integrado que pode ser acessado com `Ctrl+J`) e siga os passos abaixo:
    1. Entre na pasta `src/` com o comando `cd src`;
    2. Compile o programa pelo comando `javac App.java`;
    3. Execute com `java App`.

O processo para executar com linha de comando pode ser visto abaixo:
~~~
cd src
javac App.java
java App
~~~

### Java 25

> [!NOTE]
> A partir do Java 25, os comandos da linguagem mudaram, embora a forma antiga de se programar ainda tenha sido preservada.<br>
> Neste guia, para cada programa, veremos dois códigos-fonte: um anterior ao java 25 e outro que roda no java 25+.<br>
> Abaixo segue o exemplo de código-fonte do mesmo **Hello World**:
~~~java
void main() {
    IO.println("Hello, World!");
}
~~~

> [!CAUTION]
> Em Java, os comandos são encerrados com ponto-e-vírgula (`;`).

## Comentários

Uma linha de comentário é uma linha de código que é desconsiderada pelo interpretador durante a execução do seu programa. Os comentários servem como uma anotação do que o desenvolvedor fez em determinado trecho de código, para que o mesmo possa se lembrar do que fez no futuro.

Para inserir uma linha de comentário em um código-fonte Java, use `//`:
~~~java
// Esta é uma linha de comentário
~~~

Para inserir múltiplas linhas de comentário em um código-fonte Java, use `/*` para iniciar e `*/` para finalizar:
~~~java
/*
Este é um comentário
de múltiplas linhas
*/
~~~

> [!WARNING]
> Comentários são considerados uma boa prática de desenvolvimento, mas não abuse. Sempre comente seus códigos com parcimônia.

## Variáveis

> [!TIP]
> Para o guia de Lógica de Programação, iremos usar a nova sintaxe do Java 25, e quando avançarmos para o guia de Orientação a Objetos, iremos usar a sintaxe do Java clássico.

Uma variável é um elemento do programa que reserva um espaço na memória do computador para guardar um valor que você ainda não sabe qual é, daí o nome.

Exemplo:
~~~java
void main() {
    // declaração de variáveis
    String nome = "Alex Machado";
    int idade = 41;
    double altura = 1.72;
    boolean programador = true;
}
~~~

> [!IMPORTANT]
> Java é uma linguagem fortemente tipada. Ou seja, é necessário informar o tipo de variável ao declará-la.

### Exibindo valores de uma variável

Para exibir o valor de uma variável, chame o nome declarado da variável em uma saída de dados, como no comando `System.out.println()`, ou no caso do Java 25, chamando a biblioteca `IO.println()`:
~~~java
void main() {
    // declaração de variáveis
    String nome = "Alex Machado";
    int idade = 41;

    // saída de dados
    IO.println(nome);
    IO.println(idade);
}
~~~

O fluxograma desse programa é esse:
~~~mermaid
flowchart TD
    A([Início]) --> B[/Entrada:<br>String nome<br>int idade/]
    B --> C@{ shape: curv-trap, label: "nome<br>idade" }
    C --> D([Fim])
~~~

> [!NOTE]
> O padrão de nomenclatura para variáveis em Java é o ***camelCase***, em que uma variável começa com inicial minúscula, e se tiver uma segunda palavra no nome da variável, ela fica junta, com a inicial maiúscula. Exemplo: `String nomeCompleto;` é um nome de variável válido.

> [!IMPORTANT]
> Para nomear uma variável, você pode escolher o nome que desejar, desde que siga algumas regras:
> - Não pode ter espaço
> - Não pode ter acento
> - Não pode ter `ç`
> - Não pode ser uma palavra reservada pelo sistema. Exemplo: não posso chamar uma variável de `switch`
> - Não pode ter duas variáveis com nomes iguais, a não ser que elas sejam variáveis locais ao invés de globais
> - Pode ter numerais no nome da variável, mas ela não pode começar com um numeral. Exemplo: `num1` pode, mas `1num` não pode

> [!WARNING]
> O Java é uma linguagem *sensitive case*, ou seja, ele diferencia letras minúsculas das maiúsculas. Exemplo: uma variável chamada `nome` é diferente de uma variável chamada `Nome`, que é diferente de uma variável chamada `NOME`.

> [!NOTE]
> Em Java, nós temos várias variáveis primitivas. Seus nomes sempre começam com inicial minúsculas. Abaixo seguem as mais usadas:
> - `char`: valores do tipo caractere único
> - `int`: valores numéricos do tipo inteiro
> - `double`: valores numéricos do tipo decimal
> - `boolean`: valores numéricos do tipo decimal

> [!CAUTION]
> Em Java, o `String` não é uma variável primitiva, mas sim uma classe embutida na biblioteca padrão do Java, e é por isso que ela começa com inicial maiúscula, e não minúscula como as variáveis primitivas.

### Concatenando valores

Concatenar significa juntar dois ou mais valores diferentes. Você pode (e deve) concatenar variáveis com strings normais. Você faz isso com o sinal de mais (`+`). Veja abaixo:
~~~java
void main() {
    // declaração de variáveis
    String nome = "Alex Machado";
    int idade = 41;

    // saída de dados
    IO.println("Nome: " + nome + ".");
    IO.println("Idade: " + idade + " anos.");
}
~~~

> [!TIP]
> Em Java, para fazer uma entrada de dados por parte do usuário, é neessário instanciar uma classe da biblioteca Java, o que se faz necessário aprender Orientação a Objetos para fazer o *input*.<br>
> Por esse motivo, a entrada de dados só será ensinada na próxima parte do guia, voltado para **Orientação a Objetos**.

## Estruturas de decisão

Servem para ensinar ao computador a tomar decisões com base em condicionais.

### if...else

Duas decisões podem ser tomadas pelo computador com base em uma condição: Verdadeiro ou Falso.

Exemplo: para fazer o computador decidir se o usuário é maior ou menor de idade:
~~~java
void main() {
    // declaração de variáveis
    int idade = 41;

    // estrutura de decisão
    if (idade >= 18) {
        IO.println("Usuário é maior de idade.");
    }
    else {
        IO.println("Usuário é menor de idade.");
    }
}
~~~

Fluxograma:
~~~mermaid
flowchart TD
    A([Início]) --> B[/Entrada:<br>int idade/]
    B --> C{idade é maior ou igual a 18?}
    C -- Sim --> D@{ shape: curv-trap, label: "Usuário é maior de idade." }
    C -- Não --> E@{ shape: curv-trap, label: "Usuário é menor de idade." }
    D --> F([Fim])
    E --> F([Fim])
~~~

> [!TIP]
> **Obs**: caso a estrutura do *if...else* só tenha uma única linha de código, não há a necessidade de chaves (`{}`) para delimitar o bloco:
> ~~~java
> void main() {
>    int idade = 41;
>
>    if (idade >= 18) IO.println("Usuário é maior de idade.");
>    else IO.println("Usuário é menor de idade.");
> }
> ~~~