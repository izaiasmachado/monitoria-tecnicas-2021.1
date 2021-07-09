# Encontro de Monitoria 03 (02/07/2021)

## Assuntos Abordados
- Função Rand
- Operador Ternário
- Métodos da String
- Funções Matemáticas

## Implementação
### Principal.java
```java
package encontro03;
import java.util.Scanner;

public class Principal {
    public static void main(String[] args) {           
        Scanner scanner = new Scanner(System.in);
        String valorEmTexto = scanner.next();
        // String segundoAngulo = scanner.nextDouble();
        
        // Operador ternário
        // String mensagem = (ehMenor) ? "Realmente eh menor" : "Nao eh nao";
        // Boolean ehMenor = menor(4, 4);
        // System.out.println("Eh menor? " + mensagem);

        try {
            Double valor = Double.parseDouble(valorEmTexto); 
            // System.out.println(valor);
            
            Double valorAbsoluto = Math.abs(valor);
            System.out.println(valorAbsoluto);

            int maior = Math.max(4, 8);
            System.out.println("O maior eh: " + maior);

            String frase = "  estou vendo agora";
            System.out.println(frase.toUpperCase());            
            System.out.println(frase.length());
            System.out.println(frase.trim());
            System.out.println(frase.replace("vendo", "ouvindo"));

            double rand = Math.random(); // Lower Bound: 1 - Upper Bound: 5
            System.out.println(rand);
        } catch (NumberFormatException e) {
            System.out.println("[ERRO]: Formato inválido, tente novamente!");
        }
    }

    public static Boolean menor(int a, int b) {
        return (a < b);
    }
}
```