# Atividades Práticas de Laboratório – Capítulos 5 e 6  

**Disciplina:** Paradigmas de Programação  
**Livro:** Conceitos de Linguagens de Programação – Robert W. Sebesta (11ª Edição)  

---

## Capítulo 5 – Nomes, Vinculações e Escopos  

### Atividade 1 – Escopo Estático x Escopo Dinâmico  

**Processo:** Implementar em Python e JavaScript um exemplo de funções aninhadas para analisar escopo.  

#### Python
```python
x = 10

def f():
    print("Valor de x dentro de f():", x)

def g():
    x = 20  
    f()     

g()
```

#### JavaScript
```javascript
var x = 10;

function f() {
    console.log("Valor de x dentro de f():", x);
}

function g() {
    var x = 20; 
    f();        
}

g();
```

**Respostas:**  
- O valor impresso depende do local de definição da função.  
- Tanto Python quanto JavaScript utilizam **escopo estático (léxico)**. Historicamente, o JavaScript permitia construções que simulavam escopo dinâmico, mas atualmente também segue o estático.  

---

### Atividade 2 – Tempo de Vida das Variáveis  

**Processo:** Criar em C uma função com variável automática e estática e chamar três vezes.  

```c
#include <stdio.h>

void contador() {
    int a = 0;        
    static int b = 0; 

    a++;
    b++;

    printf("a = %d, b = %d\n", a, b);
}

int main() {
    contador();
    contador();
    contador();
    return 0;
}
```

**Respostas:**  
- `a` sempre reinicia porque é uma variável **automática**, criada e destruída a cada chamada.  
- `b` acumula valor porque é uma variável **estática**, criada uma vez e persistente durante toda a execução.  
- Isso demonstra a diferença de tempo de vida entre variáveis automáticas e estáticas.  

---

## Capítulo 6 – Tipos de Dados  

### Atividade 3 – Declaração de Tipos e Coerção  

**Processo:** Testar comportamento em Java e Python.  

#### Java
```java
public class TesteTipos {
    public static void main(String[] args) {
        int num = 10;
        
        System.out.println("num + 5 = " + (num + 5));
    }
}
```

#### Python
```python
num = 10
print("num + 5 =", num + 5)

num = "dez"
print("num agora é:", num)

# Isso gera erro:
print(num + 5)
```

**Respostas:**  
- O Java não permite porque é **tipagem estática e forte**.  
- O Python permite reatribuir, pois usa **tipagem dinâmica**.  
- Vantagens da tipagem estática: mais segurança e menos erros em tempo de execução.  
- Vantagens da tipagem dinâmica: mais flexibilidade e rapidez no desenvolvimento.  

---

### Atividade 4 – Arrays e Registros (Structs)  

**Processo:** Criar array e struct em C, e classe com ArrayList em Java.  

#### C
```c
#include <stdio.h>

struct Livro {
    char titulo[50];
    char autor[50];
    int anoPublicacao;
};

int main() {
    int numeros[5] = {1, 2, 3, 4, 5};

    struct Livro livro1 = {"O Senhor dos Aneis", "J.R.R. Tolkien", 1954};

    printf("Array: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numeros[i]);
    }
    printf("\nLivro: %s (%d)\n", livro1.titulo, livro1.anoPublicacao);

    return 0;
}
```

#### Java
```java
import java.util.ArrayList;

class Livro {
    String titulo;
    String autor;
    int anoPublicacao;

    Livro(String titulo, String autor, int anoPublicacao) {
        this.titulo = titulo;
        this.autor = autor;
        this.anoPublicacao = anoPublicacao;
    }
}

public class TesteLivros {
    public static void main(String[] args) {
        ArrayList<Livro> livros = new ArrayList<>();

        livros.add(new Livro("Dom Casmurro", "Machado de Assis", 1899));
        livros.add(new Livro("1984", "George Orwell", 1949));
        livros.add(new Livro("Clean Code", "Robert C. Martin", 2008));

        System.out.println("Títulos dos livros:");
        for (Livro l : livros) {
            System.out.println(l.titulo);
        }
    }
}
```

**Respostas:**  
- Arrays armazenam elementos **homogêneos** (mesmo tipo).  
- Structs/Classes permitem armazenar dados **heterogêneos** (diferentes tipos em uma unidade lógica).  
- Arrays são mais adequados para coleções simples de dados.  
- Structs/Classes são indicadas quando é necessário representar entidades complexas com atributos diferentes.  
