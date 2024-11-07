### Configuração de projeto com JBOSS no VS Code

- Instalar o complemento Server Connector
- Baixar o MAVEN, extrair os arquivos e adicionar o caminho para o diretóri /bin ao PATH
- Baixar a versão do JBOSS e extrair para um diretório do sistema a ser apontado posteriormente
- Criar um novo server apontando para o diretório do JBOSS
- Executar o build da aplicação com o comando `mvn clean package`
- Clicar com o botão direito sobre o server criado e selecionar "Publish server (full)"
- Inicializar o servidor.

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

  
}

/* Instância do objeto */

Carro meuCarro = new Carro();

```
