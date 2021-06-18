# Encontro de Monitoria 01 (18/06/2021)
Inicialmente foi feita uma apresentação sobre a monitoria e como não houveram dúvidas partimos para a explicação.

O conceito abordado foi o uso de uma classe já pronta chamada Scanner para receber a partir da linha de comando informações do usuário. Importamos a classe com `import java.util.Scanner;` é similar ao include do C.

Após isso, foi explicado como tratar as excessões pelo uso de try e catch. Onde try é o que estamos tentando fazer e catch é quando ocorre uma excessão, ou seja um erro.

No código feito, pedimos para o usuário o número de sua conta e recebemos isso como uma String. Após isso, utilizamos o try para converter essa String em um inteiro e se o que o usuário digitou não for inteiro, é exibida uma mensagem de erro e é perguntado o número da conta novamente. 

Essa é uma forma específica de tratar os erros e você mesmo pode implementar uma função que usa `throws exception`, ou seja indica que houve uma excessão.

Portanto, esse conceito é muito útil para tratar os erros do usuário ou do próprio programa. Imagine um programa que cria um arquivo em um local específico, se não for possível salvar o arquivo é sinal que houve uma excessão e por isso mostramos uma mensagem de erro.

### Principal.java
```java
package encontro01;

import java.util.Scanner;

public class Principal {
    public static void main(String[] args) {
        perguntarInformacoes();
    }
    
    public static void perguntarInformacoes () {
        System.out.print("Digite o número da sua conta: ");            
        Scanner scannerNumeroDaConta = new Scanner(System.in);
        String textoCampoNumeroDaConta = scannerNumeroDaConta.next();
    
        try {
            int numeroDaConta = Integer.parseInt(textoCampoNumeroDaConta); 
            System.out.println("O número da sua conta é " + numeroDaConta);            
        } catch (NumberFormatException e) {
            System.out.println("[ERRO]: Formato inválido, tente novamente!");
            perguntarInformacoes();
        }
    }
}

```