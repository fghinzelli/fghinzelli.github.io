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

