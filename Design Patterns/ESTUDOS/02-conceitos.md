# Design Patterns — Conceitos (ordem das aulas)

---
## AULA 01 — Revisão de POO

### POO
- **Definição:** paradigma que junta **dados + comportamentos** em **objetos**, criados a partir de **classes** ("planos de construção").
- **Exemplo:** classe `Gato` → objetos `Tom` e `Nina`.

### Classe, objeto, campos, métodos
| Termo | Uma linha | Exemplo |
|---|---|---|
| Classe | planta que define a estrutura | `Cat` |
| Objeto | instância concreta da classe | `Tom: Cat` |
| Campos | dados = **estado** | `name, age, color` |
| Métodos | ações = **comportamento** | `breathe(), eat(), meow()` |
| Membros | campos + métodos | — |
- **UML:** `+` = público, `-` = privado. Nome **em itálico** = classe/método **abstrato**.

### Hierarquia de classes
- **Superclasse** (mãe) × **subclasse** (filha). Filha herda estado e comportamento e só define o que difere.
- **Exemplo:** `Animal` → `Cat` (meow) e `Dog` (bark).

### Pilares da POO ⭐
| Pilar | Uma linha | Exemplo da aula |
|---|---|---|
| **Abstração** | modelar só o que importa para o contexto | `Avião` no simulador (velocidade, altitude) × no app de passagens (poltronas) |
| **Encapsulamento** | esconder detalhes e expor só uma interface | `Aeroporto` aceita qualquer `TransporteAéreo` (Avião, Helicóptero) |
| **Herança** | criar classe nova sobre uma existente → **reuso de código** | `Cat extends Animal` |
| **Polimorfismo** | mesmo método, comportamento diferente em cada subclasse | `makeSound()` abstrato: Cat "Miau", Dog "Au" |
- **Pegadinha:** método **abstrato** não tem corpo na superclasse e **obriga** as subclasses a implementar.

### Relações entre objetos ⭐ (da mais fraca à mais forte)
| Relação | Seta UML | Significado | Exemplo da aula |
|---|---|---|---|
| **Dependência** | `A - - - -> B` (tracejada, seta aberta) | mudança em B pode afetar A; uso **temporário** | Professor - -> Curso (usa materiais) |
| **Associação** | `A ———> B` (linha cheia) | A **conhece** B (geralmente um campo) | Professor → Aluno |
| **Agregação** | `A ◇———> B` (losango vazio) | A **contém** B, mas B **existe sozinho** | Departamento ◇ Professor |
| **Composição** | `A ◆———> B` (losango cheio) | A contém B e **controla o ciclo de vida** de B | Universidade ◆ Departamento |
| **Implementação** | `A - - - ▷ B` (tracejada, triângulo vazio) | A implementa a **interface** B | Cat - -▷ FourLegged |
| **Herança** | `A ———▷ B` (cheia, triângulo vazio) | A **é um** B | Cat ——▷ Animal |
- **Pegadinha 1:** o **losango fica do lado do TODO** (contêiner), não da parte.
- **Pegadinha 2:** composição ⊂ agregação ⊂ associação. A diferença-chave é o **ciclo de vida**.
- **Pegadinha 3:** tracejado = dependência ou implementação; triângulo = herança/implementação.

---
## AULA 02 — Introdução a Padrões de Projeto

### Padrão de projeto
- **Definição:** solução típica para problema comum de projeto; "planta pré-fabricada" que você customiza.
- **Não é** código para copiar; é um **conceito geral**.
- **Padrão × algoritmo:** algoritmo = conjunto **claro de ações**; padrão = **descrição de alto nível**. O mesmo padrão gera códigos diferentes em programas diferentes.

### Partes da descrição de um padrão
**Propósito** (problema + solução, breve) · **Motivação** (explica a fundo) · **Estrutura de classes** (partes e relações) · **Exemplos de código**.

### Classificação ⭐
| Categoria | Faz o quê | Exemplos |
|---|---|---|
| **Criação** | mecanismos de **criar objetos** com flexibilidade e reuso | Singleton, Factory Method |
| **Estruturais** | **montar** objetos e classes em estruturas maiores, flexíveis | (complemento: Adapter, Decorator, Facade) |
| **Comportamentais** | **comunicação** e divisão de **responsabilidades** entre objetos | (complemento: Observer, Strategy) |

### História
- **Christopher Alexander** — primeiro a descrever padrões (*Uma Linguagem de Padrões*; era arquitetura de construções).
- **Gang of Four (GoF)**: Gamma, Vlissides, Johnson, Helm — **1994**, livro com **23 padrões**.

### Por que aprender
Kit de soluções testadas + **linguagem comum** na equipe ("usa um Singleton").

### Características de um bom projeto: reutilização
- **Objetivo:** economizar tempo/custo.
- **Desafios:** acoplamento forte, dependência de classes concretas, operações codificadas diretamente.
- **Níveis de reuso:** **Classes** (baixo: bibliotecas) · **Padrões** (intermediário) · **Frameworks** (alto).

### Princípios universais ⭐
| Princípio | Ideia | Exemplo da aula |
|---|---|---|
| **Encapsule o que varia** | separar o que muda do que é fixo (compartimentos do navio) | tirar o cálculo de imposto do cálculo do pedido |
| **Programe para interface, não implementação** | dependa de abstrações | `Empresa` usa a interface `Empregado` (Desenvolvedor, Tester) |
| **Prefira composição sobre herança** | "tem um" em vez de "é um" | em vez de `CaminhaoEletricoComAutopiloto`, combine `Motor` + `Navegacao` |
- **4 passos para programar para interface:** 1) ver o que uma classe precisa da outra; 2) criar interface com esses métodos; 3) classe concreta implementa; 4) a dependente usa a **interface**.
- **Problemas da herança:** subclasse forçada a implementar métodos inúteis, quebra encapsulamento, acoplamento forte, hierarquias complexas.
- **Pegadinha:** composição permite **trocar comportamento em tempo de execução** (trocar o motor).

---
## AULA 03 — Singleton

### Singleton ⭐
- **Definição:** padrão de **criação** que garante **uma única instância** de uma classe e dá **um ponto de acesso global** a ela.
- **Por quê:** controlar acesso a **recurso compartilhado** (banco de dados, arquivo).
- **Como funciona:** ao pedir um objeto "novo", você recebe o **mesmo** já criado.
- **× variável global:** global pode ser **sobrescrita** por qualquer parte do código; Singleton **controla a criação** e protege a instância.

### Os 2 passos de toda implementação
1. **Construtor privado** → ninguém usa `new` de fora.
2. **Método estático** (`getInstancia()`) → cria na 1ª vez, guarda em **campo estático** e depois sempre devolve o mesmo.

### Vantagens × Desvantagens
| Vantagens | Desvantagens |
|---|---|
| certeza de **uma única instância** | **viola o SRP** (resolve 2 problemas: controlar instância + acesso global) |
| **ponto de acesso global** | pode **mascarar mau design** (acoplamento excessivo) |
| **inicialização tardia** (lazy: só cria quando pedem) | **multithread**: várias threads podem criar várias cópias |

### Classe × Enum (tabela do slide)
| Aspecto | Classe | Enum |
|---|---|---|
| Instâncias | ilimitadas (via `new`) | fixas (definidas no código) |
| Criação | controlada pelo programador | controlada pela **JVM** |
| Herança | pode herdar | **não pode** (só `java.lang.Enum`) |
| Interfaces | pode implementar | pode implementar |
| Runtime | pode criar novos objetos | não cria constantes novas |
| Uso típico | modelos gerais | constantes bem definidas |
- **Pegadinha:** `config1 == config2` dá **true** — as duas variáveis apontam para o **mesmo objeto**. Mudar por `config1` aparece em `config2`.

---
## AULA 04 — Factory Method

### Factory Method ⭐
- **Outros nomes:** Método Fábrica, **Construtor Virtual**.
- **Categoria:** **criação**.
- **Definição:** a **superclasse define um método para criar objetos**, mas **as subclasses decidem qual objeto** concreto criar.

### O problema (logística)
Sistema só com `Caminhao`; depois precisa de `Navio`, `Trem`. Código cheio de `new Caminhao()` → mudar tudo = **acoplamento e retrabalho**.

### A solução
- Criar um **método fábrica** que encapsula o `new`.
- Subclasses **sobrescrevem** e escolhem o produto.
- O cliente só conhece a **interface comum** (`Transporte`).

### Papéis (com o código da aula)
| Papel | No exemplo |
|---|---|
| **Produto** (interface) | `Transporte` → `entregar(origem, destino)` |
| **Produtos concretos** | `Caminhao` (terra), `Navio` (mar) |
| **Criador** (abstrato) | `Logistica` → `criarTransporte()` abstrato + `planejarEntrega()` (lógica comum) |
| **Criadores concretos** | `LogisticaViaria` → `new Caminhao()` · `LogisticaMaritima` → `new Navio()` |
| **Cliente** | `App` escolhe a logística (até por `args[0]`) |

### Como implementar (4 passos)
1. Interface comum dos produtos.
2. Método fábrica na classe criadora.
3. Trocar `new` pelo método fábrica.
4. Subclasses sobrescrevem o método fábrica.

### Vantagens × Desvantagens
| Vantagens | Desvantagens |
|---|---|
| **reduz acoplamento** criador ↔ produtos | código **mais complexo** (muitas subclasses) |
| segue **SRP** (criação separada da regra de negócio) | |
| segue **Aberto/Fechado** (novo produto sem mexer no cliente) | |
- **Pegadinha:** quem decide o **tipo concreto** é a **subclasse criadora**, não o cliente nem a superclasse.
- **Pegadinha 2:** o método fábrica costuma ser `protected abstract` e a lógica comum (`planejarEntrega`) fica **na superclasse**, chamando o método fábrica.

---
> ⚠️ **Observações:** a ementa cita **SOLID** e padrões **estruturais/comportamentais**, mas até agora só há material de **Singleton** e **Factory Method**. SRP e Aberto/Fechado aparecem só como vantagens/desvantagens — sem aula própria de SOLID. Os `.class` do .rar são compilados (não legíveis); os `.java` foram lidos.
