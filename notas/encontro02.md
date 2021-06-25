# Encontro de Monitoria 02 (25/06/2021)
O código foi desevolvido baseado nas dúvidas dos alunos que participaram. Inicialmente utilizamos Scanner para as exceções mas logo depois partimos para a introdução de como usar interface gráfica simples no Java.

## Throw Exception
Vimos no [Encontro 01](https://github.com/izaiasmachado/monitoria-tecnicas-2021.1/blob/main/notas/encontro01.md) sobre try e catch e hoje implementamos nossa própria exceção.

Essa é uma forma simples de implementar funções e tratar erros sem a necessidade de dar um retorno direto durante a codificação. 

É possível ter um try com vários catches para os mais diversos tipos de validação e também para ter mais informações sobre qual foi o erro e porque ele ocorreu. 

## Interface Gráfica
Implementamos dois tipos de interface, uma que recebe texto e outra que imprime. Veja que importamos o `javax.swing`.

## Implementação
Abaixo, temos detalhes da implementação.

### Contas.java
Criamos uma classe Contas que tem id, saldo e métodos padrões. Temos também um método de depósito que lança uma exceção quando não é possível realizar um depósito.
```java
package encontro02;

public class Contas {
    double saldo = 0.0;
    int id;

    public Contas (int id) {
        this.id = id;
    }

    public void depositar (double valor) {
        if (valor <= 0) {
            throw new IllegalArgumentException("Operação inválida, o depósito tem que ser maior que zero."); 
        }

        this.saldo += valor;
    }

    public void setSaldo (double valor) {
        this.saldo = valor;
    }

    public double getSaldo () {
        return this.saldo;
    }
}
```

### Principal.java
Na nossa classe Principal, instanciamos duas contas e definimos uma função que pergunta informações sobre uma conta.
- O primeiro catch verifica se o que o usuário digitou é realmente um número.
- Já o segundo verifica se foi possível realizar o depósito.
- Por fim, o último catch verifica se o usuário clicou no botão de cancelar e mostra uma mensagem.

```java
package encontro02;

import javax.swing.JOptionPane;
// import java.util.Scanner;

public class Principal {
    public static void main (String[] args) {
        Contas obj1 = new Contas(1);
        obj1.setSaldo(0.0);
        perguntarInformacoes(obj1);

        Contas obj2 = new Contas(2);
        obj2.setSaldo(5.0);
        perguntarInformacoes(obj2);
    }

    public static void perguntarInformacoes (Contas obj) {
        // Scanner scanner = new Scanner(System.in);
        // scanner.next();

        try {
            String valorEmTexto = JOptionPane.showInputDialog("Digite o valor para depósito: ");
            double valor = Double.parseDouble(valorEmTexto);
            String texto = (valor > 1) ? "is" : "l";
            obj.depositar(valor);
            double saldoEmConta = obj.getSaldo();
            String mensagem = "Saldo da conta " + obj.id + " eh de " + saldoEmConta + " rea" + texto;
            JOptionPane.showMessageDialog(null, mensagem);
        } catch (NumberFormatException e) {
            String mensagem = "[ERRO]: Formato inválido, tente novamente!";
            JOptionPane.showMessageDialog(null, mensagem);
            perguntarInformacoes(obj);
        } catch (IllegalArgumentException e) {
            String mensagem = "[ERRO]: " + e.getMessage();
            JOptionPane.showMessageDialog(null, mensagem);
            perguntarInformacoes(obj);
        } catch (NullPointerException e) {
            String mensagem = "Depósito cancelado!";
            JOptionPane.showMessageDialog(null, mensagem);
        }
    }
}
```

## Extras
- [Outros Exceptions](https://www.geeksforgeeks.org/types-of-exception-in-java-with-examples/)