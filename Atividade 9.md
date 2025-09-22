# Exercícios – Capítulo 9: Subprogramas  

## Exercício 1 – Passagem de Parâmetros por Valor e por Referência  

Considere o seguinte pseudocódigo de uma função que tenta dobrar o valor de um número:

```text
procedure dobrar(x)
    x := x * 2
end
```

### Implementações em C  

#### Versão por valor
```c
#include <stdio.h>

int dobrarValor(int num) {
    return num * 2;
}

int main() {
    int num = 10;
    int resultado = dobrarValor(num);

    printf("Valor inicial: %d\n", num);
    printf("Resultado da função por valor: %d\n", resultado);
    printf("Valor original após chamada: %d\n", num);

    return 0;
}
```

#### Versão por referência (usando ponteiros)
```c
#include <stdio.h>

void dobrarReferencia(int *num) {
    *num = (*num) * 2;
}

int main() {
    int num = 10;

    printf("Valor inicial: %d\n", num);

    dobrarReferencia(&num);
    printf("Resultado da função por referência: %d\n", num);

    return 0;
}
```

#### Programa principal comparando as duas estratégias
```c
#include <stdio.h>

int dobrarValor(int num) {
    return num * 2;
}

void dobrarReferencia(int *num) {
    *num = (*num) * 2;
}

int main() {
    int num = 10;

    printf("Valor inicial: %d\n", num);

    int resultValor = dobrarValor(num);
    printf("Resultado da função por valor: %d\n", resultValor);
    printf("Valor original após chamada por valor: %d\n\n", num);

    dobrarReferencia(&num);
    printf("Resultado da função por referência: %d\n", num);

    return 0;
}
```

### Questões  

- **Qual a diferença observada entre as duas versões?**  
Na passagem por **valor**, a função recebe apenas uma cópia da variável e não altera o original. Já na passagem por **referência**, a função recebe o endereço de memória da variável e altera o valor diretamente nela.  

- **Por que o valor da variável só se altera na versão por referência?**  
Porque, nesse caso, o parâmetro é um ponteiro para o endereço de memória da variável original, permitindo modificá-la diretamente na memória.  

- **Relação com estratégias de passagem de parâmetros:**  
  - **Por valor:** mais seguro, evita efeitos colaterais indesejados, mas pode ser menos eficiente se a variável for grande (pois faz cópia).  
  - **Por referência:** mais eficiente em termos de memória e performance (não há cópia), mas aumenta o risco de alterações inesperadas no valor original.  

---

## Exercício 2 – Corrotinas em GoLang (primeiro contato)  

As **corrotinas** permitem a execução concorrente de rotinas dentro de um programa. Em Go, isso é feito com a palavra-chave `go`.  

### Código `main.go`  
```go
package main

import (
    "fmt"
    "time"
)

func escrever(texto string) {
    for i := 0; i < 5; i++ {
        fmt.Println(texto, i)
        time.Sleep(time.Millisecond * 500)
    }
}

func main() {
    go escrever("Corrotina")  // executa em paralelo
    escrever("Função normal") // executa no fluxo principal
}
```

### Execução  
```bash
go run main.go
```

### Questões  

- **O que acontece com a ordem das mensagens exibidas?**  
As mensagens aparecem intercaladas de forma não determinística. Às vezes a primeira linha vem da função normal, outras da corrotina. A ordem pode variar a cada execução.  

- **Por que as mensagens da corrotina e da função normal se intercalam?**  
Porque o comando `go escrever("Corrotina")` cria uma goroutine que roda em paralelo com a função principal. O escalonador do Go distribui o tempo de execução entre as duas, alternando qual será executada a cada momento.  

- **Relação com a definição de corrotinas:**  
Corrotinas são subprogramas que podem ser suspensos e retomados, permitindo múltiplas rotinas progredirem alternadamente. Em Go, as goroutines implementam esse conceito: são mais leves que threads tradicionais e podem ser criadas em grande quantidade. O `time.Sleep` no exemplo ajuda a visualizar essa alternância, simulando pausas que permitem ao escalonador intercalar a execução.  

---
