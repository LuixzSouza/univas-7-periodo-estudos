# Design Patterns — Questões de treino

---
**1.** Qual a diferença entre um padrão de projeto e um algoritmo?

**2.** Cite as 3 categorias de padrões e o que cada uma resolve. Singleton e Factory Method são de qual?

**3.** Associe a relação ao símbolo UML:
(1) Dependência (2) Associação (3) Agregação (4) Composição (5) Implementação (6) Herança
( ) linha cheia com triângulo vazio ( ) linha tracejada com seta aberta ( ) losango cheio ( ) linha tracejada com triângulo vazio ( ) losango vazio ( ) linha cheia com seta aberta

**4.** Qual a diferença entre agregação e composição? Dê um exemplo de cada.

**5.** Identifique as relações: "Um Pedido é composto por Itens, que não existem sem o pedido. O Pedido pertence a um Cliente. O Cliente é um tipo de Pessoa. A classe GeradorNotaFiscal recebe um Pedido como parâmetro apenas para emitir a nota."

**6.** Quais os 2 passos comuns a toda implementação do Singleton?

**7.** O que imprime?
```java
Configuracao a = Configuracao.getInstancia();
Configuracao b = Configuracao.getInstancia();
a.setUrlBanco("X");
System.out.println(b.getUrlBanco() + " " + (a == b));
```

**8.** Cite 2 desvantagens do Singleton.

**9.** (V ou F)
a) No Singleton, o construtor deve ser público para permitir acesso global.
b) Um enum em Java pode herdar de outra classe.
c) No Factory Method, as subclasses decidem qual objeto concreto será criado.
d) O Factory Method viola o Princípio Aberto/Fechado.

**10.** Explique o problema que o Factory Method resolve usando o exemplo da logística.

**11.** Implemente com Factory Method: interface `Documento` com `abrir()`; classes `Contrato` e `Recibo`; criador abstrato `Editor` com `criarDocumento()` e `editar()`; criadores concretos.

**12.** Explique o princípio "Prefira composição sobre herança" e dê o exemplo da aula.

**13.** Cite os 4 pilares da POO e explique o polimorfismo com um exemplo.

**14.** Um sistema tem uma classe `Log` que grava num único arquivo, usada por todo o sistema. Qual padrão usar e por quê? Qual cuidado ter se houver várias threads?

---
# Gabarito

**1.** Algoritmo = conjunto **claro de ações** para atingir uma meta. Padrão = **descrição de alto nível** de uma solução; o código muda de programa para programa.

**2.** **Criação** (criar objetos com flexibilidade), **Estruturais** (montar objetos/classes em estruturas maiores), **Comportamentais** (comunicação e responsabilidades). Singleton e Factory Method = **criação**.

**3.** (6), (1), (4), (5), (3), (2).

**4.** Agregação: o todo contém a parte, mas a parte **existe sozinha** (Departamento ◇ Professor). Composição: a parte **só existe dentro do todo**; o todo controla o ciclo de vida (Universidade ◆ Departamento).

**5.** Pedido ◆ Item (composição); Pedido → Cliente (associação); Cliente ——▷ Pessoa (herança); GeradorNotaFiscal - - -> Pedido (dependência, uso temporário).

**6.** 1) **Construtor privado** (impede `new` de fora). 2) **Método estático** que cria na 1ª chamada, guarda em campo estático e sempre retorna a mesma instância.

**7.** `X true` — as duas variáveis apontam para o mesmo objeto.

**8.** Viola o SRP; pode mascarar mau design/acoplamento; problemas em multithread (várias instâncias).

**9.** a) **F** — construtor **privado**. b) **F** — enum só estende `java.lang.Enum`. c) **V**. d) **F** — ele **segue** o Aberto/Fechado.

**10.** O código usava `new Caminhao()` direto em vários lugares. Para incluir Navio/Trem teria que alterar tudo (acoplamento). Com Factory Method, `Logistica` define `criarTransporte()`; `LogisticaViaria` cria Caminhão, `LogisticaMaritima` cria Navio; o resto usa só a interface `Transporte`.

**11.**
```java
interface Documento { void abrir(); }
class Contrato implements Documento { public void abrir() { System.out.println("Abrindo contrato"); } }
class Recibo   implements Documento { public void abrir() { System.out.println("Abrindo recibo"); } }

abstract class Editor {
    protected abstract Documento criarDocumento();
    public void editar() {
        Documento d = criarDocumento();
        d.abrir();
        System.out.println("Editando...");
    }
}
class EditorContrato extends Editor { protected Documento criarDocumento() { return new Contrato(); } }
class EditorRecibo   extends Editor { protected Documento criarDocumento() { return new Recibo(); } }
```

**12.** Em vez de herdar ("é um"), monte objetos com partes ("tem um") e delegue comportamento; permite trocar em tempo de execução e evita hierarquias enormes. Exemplo: em vez de `CaminhaoEletricoComAutopiloto`, compor `Motor` + `Navegacao`.

**13.** Abstração, Encapsulamento, Herança, Polimorfismo. Polimorfismo: `Animal.makeSound()` abstrato; `Cat` imprime "Miau" e `Dog` "Au" — a mesma chamada age diferente conforme o objeto.

**14.** **Singleton**: um único recurso compartilhado (arquivo) acessado globalmente. Cuidado: em **multithread** duas threads podem criar 2 instâncias — usar `synchronized` ou **enum** (complemento).
