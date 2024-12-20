### Configuração de projeto com JBOSS no VS Code

- Instalar os plugins necessários:
  - Java Extension Pack
  - Maven for Java
  - JBoss Toolkit
- Baixar uma versão do WildFly (Desnecessário caso for feito o download ao criar o novo servidor)
- Na aba Servers (No ícone de explorer) do VSCode, clicar em "Create New Server". Informar se deve ser feito o download do WildFly ou se ele já se encontra em algum diretório (Neste caso, informar o caminho). 
- Caso necessário, editar as opções do servidor, clicando com o botão direito e selecionando Edit Server.Para configurar a versão do Java incluir a propriedade *vm.install.path*. Também pode ser necessário incluir o parâmetro "rsp-ui.rsp.java.home": "/usr/lib/jvm/java-11-openjdk-amd64", indicando o caminho do java
- Para testar se o Wildfly está funcionando, clicar com o botão direito sobre o server criado e selecionar *Start server*
- Utilizar o Maven para gerar o arquivo .war. Isso pode ser feito com o plugin Maven for java (Aba abaixo de servers) ou via linha de comando:  
```mvn clean package```
- Será gerada uma nova pasta *target* com um arquivo .war. Clicar com o botão direito sobre o arquivo e selecionar *Run on server* e escolher o Server Wildfly criado anteriormente.
- Para acessar a aplicação, a url será composta por: localhost:8080/<artifactId>/<caminho_definido_no_arquivo_web.xml>/<rotas_da_aplicacao>

### Sintaxe

#### Leitura / Escrita no terminal
```java
import java.util.Scanner;

public class LeituraEscrita {
  public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    System.out.println("Informe seu nome");
    String nome = scan.nextLine();
    System.out.println("Seu nome é: " + nome);
  }
}
```

#### Tipos primitivos
```java
/* booleano */
boolean varBool = true;

/* numéricos */
byte varByte = 20;
short varShort = 20;
int varInt = 20;
logn varLong = 20;

/* Ponto flutuante */
float varFloat = 123.3f;
double varDouble = 1.2323;
```
#### Operadores 

```java
/* Aritiméticos */
+ - * / % ++ -- += -=

/* Lógicos */
& | ^ && || !

/* Relacionais */
== != < > <= >= 
```

#### Estruturas condicionais (IF, SWITCH)

```java
if (a > b) {
  // DO Something
} else if (b > c) {
  // DO Something
} else {
  // DO Something
}

switch (a) {
  case 1:
    // Do something
    break;
  case 2:
    // Do something
    break;
  default:
    break;
}
```

#### Estruturas de repetição (FOR, WHILE, DO WHILE)

```java
/* FOR */
for (int i=0; i<10; i++) {
  System.out.println(i);
}

/* FOR EACH */
int[] arrSample = {1, 2, 3};
for (int i :  arrSample) {
  System.out.println(i);
}

/* DO WHILE */
int i = 0;
do {
    System.out.println(i);
    i++;
} while(i < 10);

/* WHILE */
int i = 0;
while(i < 10) {
    System.out.println(i);
    i++;
} 
```

#### Definição de classes, instancia de objetos

```java
/* Declaração da classe */
public class Carro {
  private String marca;
  private String modelo;

  public String getMarca() {
        return marca;
  }
  public void setMarca(String marca) {
      this.marca = marca;
  }
  public String getModelo() {
      return modelo;
  }
  public void setModelo(String modelo) {
      this.modelo = modelo;
  }

  // Metodo com retorno
  public String exibirMarcaModelo() {
      return this.marca + " " + this.modelo;
  }

  
}

/* Instância do objeto */

Carro carro = new Carro();
carro.setMarca("VW");
carro.setModelo("Gol");
System.out.println(carro.exibirMarcaModelo());

/* Relacionamento TEM UM */

Pessoa pessoa = new Pessoa();
Endereco endereco1 = new Endereco();
// Pessoa "tem um" endereço
pessoa.endereco = endereco1;


/* Herança */
// Aluno "É" uma Pessoa

class Aluno extends Pessoa {
  public Aluno() {
    // super executa métodos da classe pai
    super();
  }
}


/* Modificadores de acesso */
// Publico (Todo mundo)
public String todoMundoVe;
// Private (Somente dentro da classe)
private String somenteDentroDaClasse;
// Default (Somente dentro do mesmo pacote)
String somenteDentroDoPacote;
// Protected (Qualquer classe filha)
protected String somenteSeFilha;

/* Poliformismo de Sobreescrita (Classes filhas implementam uma nova versão do método) - Em tempo de execução */

class Pessoa {
  // ...
  public exibirNome() {
    System.out.println(this.nome)
  }
}

class Aluno {
  // ...
  public exibirNome() {
    System.out.println(this.nome + this.sobrenome)
  }
}

/* Poliformismo de Sobrecarga (Mesmo método com assinatura diferente) */

class Aluno {
  // ...
  public calcularMedia(double nota1, double nota2) {
    System.out.println((nota1 + nota2) / 2);
  }

  public calcularMedia(double nota1, double nota2, double nota3) {
    System.out.println((nota1 + nota2 + nota3) / 3);
  }
}

/* Classes e metodos abstratos */
// Classes abstratas não podem ser instanciadas
// Métodos abstratos da classe pai são obrigatórios nos filhos

public abstract class Pessoa {
  public abstract void mostrarEndereco();
}

/* Classes e atributos imutáveis (final) */

// A classe não pode ser herdada
public final class Pessoa {
}

// Atributos imutaveis geralmente são usados para constantes

public class Constantes {
  public static final URL_SITE = "https://meusite.com";
}

/* Interfaces */
// Uma interface nada mais é do que uma classe abstrata com todos os métodos abstratos.
// É uma espepécie de contrato a ser implementado pelas classes filhas.
// No Java não existe herança múltipla, logo uma interface pode ser usada para um classe filha implementar
// métodos de uma outra classe abstrata (interface)

public interface AnimalDomestico {
  void levarNoVeterinario() {}
}

public interface Felino {
  void apararUnhas() {}
}

public class Mamifero {
  public void mamar()
}

public class Gato extends Mamifero implements Felino, AnimalDomestico { 
}

/* Tratamento de exceções */

try {
  int[] vetorTeste = new int[4];
  vetorTeste[4] = 1;
  vetorTeste[3] = 0;
  vetorTeste=[1] = 10 / vetorTeste[3];
} catch (ArrayIndexOutOfBoundsException exception) {
  Sytem.out.println("Exceção ao acessar índice que não existe");
} catch (ArithmeticlException exception) {
  System.out.println("Exceção ao executar cálculo");
} finally {
  System.out.println("Sempre executada após passar pelo try e catch");
}


// É possível agrupar as exceptions em um único catch

try {
  int[] vetorTeste = new int[4];
  vetorTeste[4] = 1;
  vetorTeste[3] = 0;
  vetorTeste=[1] = 10 / vetorTeste[3];
} catch (ArrayIndexOutOfBoundsException | Exception exception) {
  Sytem.out.println("Ocorreu um erro");
}


// Para "repassar a responsabilidade" do tratamento do erro

public double lerNumero throws Exception () {
  Scanner scan = new Scanner(System.in);
  return scan.nextDouble();
}

// Também é possível lançar uma nova exceção em qualquer parte do código

public double lerNumero () {
  Scanner scan = new Scanner(System.in);
  if (true) { // Uma condição qualquer
    throws new Exception("Ocorreu um erro");
  }
  return scan.nextDouble();
}

// Na chamada deste método, é obrigatório incluí-lo em um bloco Try Catch

try {
  double teste = lerNumero();
catch (Exception e) {
  System.out.println("Erro ao ler o número");
}
```




