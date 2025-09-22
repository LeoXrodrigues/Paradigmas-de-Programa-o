# Atividades para Casa – Capítulo 8  

## Atividade 1 – Reescrevendo código sem `goto`  

### Código original (com `goto`):
```fortran
i := 1
goto check

loop:
    print(i)
    i := i + 1

check:
    if (i <= 10) then
        goto loop
```

### Versão em Python (usando `while`):
```python
i = 1
while i <= 10:
    print(i)
    i += 1
```

### Versão em Python (usando `for`):
```python
for i in range(1, 11):
    print(i)
```

### Comparação:  
O código com `goto` é menos legível porque exige entender os rótulos e saltos de execução, obrigando o leitor a ficar voltando no código para compreender o fluxo.  
O `while` deixa o raciocínio mais claro, mas ainda exige declarar e atualizar a variável fora do cabeçalho do laço.  
O `for` é a forma mais **prática e moderna**, pois a inicialização, condição e incremento ficam em uma única linha, tornando o código compacto, direto e fácil de ler.  

---

## Atividade 2 – Seleção múltipla em diferentes linguagens  

### Menu em C (usando `switch/case`):
```c
#include <stdio.h>

int fatorial(int n) {
    int fat = 1;
    for(int i = 1; i <= n; i++) {
        fat *= i;
    }
    return fat;
}

int main() {
    int opcao, num;
    do {
        printf("\nMenu:\n");
        printf("1. Calcular o quadrado de um numero\n");
        printf("2. Calcular o fatorial de um numero\n");
        printf("3. Sair\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);

        switch(opcao) {
            case 1:
                printf("Digite um numero: ");
                scanf("%d", &num);
                printf("Quadrado: %d\n", num * num);
                break;
            case 2:
                printf("Digite um numero: ");
                scanf("%d", &num);
                printf("Fatorial: %d\n", fatorial(num));
                break;
            case 3:
                printf("Saindo...\n");
                break;
            default:
                printf("Opcao invalida!\n");
        }
    } while(opcao != 3);

    return 0;
}
```

### Menu em Python (usando `if/elif/else`):
```python
def fatorial(n):
    fat = 1
    for i in range(1, n+1):
        fat *= i
    return fat

while True:
    print("\nMenu:")
    print("1. Calcular o quadrado de um número")
    print("2. Calcular o fatorial de um número")
    print("3. Sair")

    opcao = int(input("Escolha uma opção: "))

    if opcao == 1:
        num = int(input("Digite um número: "))
        print("Quadrado:", num * num)
    elif opcao == 2:
        num = int(input("Digite um número: "))
        print("Fatorial:", fatorial(num))
    elif opcao == 3:
        print("Saindo...")
        break
    else:
        print("Opção inválida!")
```

### Comparação:  
- Em **C**, a estrutura é mais detalhada: exige importação de bibliotecas, declaração de variáveis e uso do `switch/case`, o que aumenta o número de linhas.  
- Em **Python**, o código é mais curto e direto, mas quem nunca programou na linguagem pode estranhar o `elif`, já que em muitas linguagens se usa `else if`.  
- No geral, **Python é mais prático** para esse tipo de menu por causa da sua sintaxe enxuta e expressiva, além de possuir bibliotecas nativas que facilitam operações matemáticas.  

---

## Atividade 3 – Explorando alternativas ao `goto`  

### Código em Python (usando `break`, `continue` e `return`):
```python
def processar_lista(lista):
    for num in lista:
        if num == 0:
            print("Zero encontrado. Encerrando execução.")
            break
        if num < 0:
            continue
        if num % 2 == 0:
            return num * 2

# Exemplo de uso
valores = [3, -2, 5, -7, 4, 0, 6]
resultado = processar_lista(valores)
print("Resultado:", resultado)
```

### Comentário:  
Usando `break`, `continue` e `return`, o código fica **claro, curto e direto**, com cada palavra-chave descrevendo exatamente a intenção do programador.  
Se fosse feito apenas com `goto` e rótulos, seria necessário criar diversos saltos manuais, o que tornaria o fluxo muito menos legível e mais suscetível a erros, principalmente em programas grandes.  
As estruturas modernas de controle deixam o código mais seguro, legível e fácil de manter.  
