# Design Patterns — Flashcards

| Pergunta | Resposta |
|---|---|
| O que é POO? | Paradigma que junta dados e comportamentos em objetos criados a partir de classes. |
| Classe × objeto? | Classe = planta; objeto = instância concreta. |
| Estado × comportamento? | Estado = campos; comportamento = métodos. |
| 4 pilares da POO? | Abstração, Encapsulamento, Herança, Polimorfismo. |
| Maior benefício da herança? | Reutilização de código. |
| Nome em itálico no UML? | Classe/método abstrato. |
| Relação mais fraca? | Dependência. |
| Seta da dependência? | Tracejada com seta aberta. |
| Seta da herança? | Linha cheia com triângulo vazio. |
| Seta da implementação? | Tracejada com triângulo vazio. |
| Losango vazio? | Agregação (parte vive sozinha). |
| Losango cheio? | Composição (parte morre com o todo). |
| O que é padrão de projeto? | Solução típica e reutilizável para problema comum de projeto. |
| Padrão × algoritmo? | Algoritmo = passos exatos; padrão = descrição de alto nível. |
| 3 categorias? | Criação, Estruturais, Comportamentais. |
| Quem primeiro descreveu padrões? | Christopher Alexander. |
| GoF? | Gamma, Helm, Johnson, Vlissides — 1994 — 23 padrões. |
| 3 princípios universais? | Encapsule o que varia; programe para interface; prefira composição a herança. |
| Composição = relação? | "Tem um". |
| Singleton faz o quê? | Garante 1 instância + ponto de acesso global. |
| 2 passos do Singleton? | Construtor privado + método estático que devolve a instância. |
| Lazy initialization? | Só cria o objeto na primeira vez que é pedido. |
| Singleton viola qual princípio? | Responsabilidade Única (SRP). |
| Problema do Singleton com threads? | Pode criar mais de uma instância. |
| Singleton com enum: como acessa? | `MeuEnum.INSTANCIA`. |
| Enum pode herdar? | Não (só java.lang.Enum). |
| Factory Method outros nomes? | Método Fábrica, Construtor Virtual. |
| Factory Method faz o quê? | Superclasse define método de criação; subclasses escolhem o objeto. |
| Papéis do Factory Method? | Produto (interface), Produtos concretos, Criador abstrato, Criadores concretos. |
| Exemplo da aula (Factory)? | Logistica → LogisticaViaria (Caminhão) / LogisticaMaritima (Navio). |
| Vantagens do Factory Method? | Menos acoplamento, SRP, Aberto/Fechado. |
| Desvantagem do Factory Method? | Código mais complexo (muitas subclasses). |
| Níveis de reuso? | Classes (baixo), Padrões (médio), Frameworks (alto). |
