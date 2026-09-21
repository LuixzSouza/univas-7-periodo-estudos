# Design Patterns — Resumo Relâmpago

**Prof. Raffael Carvalho** · Linguagem das aulas: **Java** · Material: 5 PDFs + código da aula 04

## O que é a matéria
Padrões de projeto = **soluções típicas e testadas** para problemas comuns de projeto orientado a objetos. Não é código pronto: é uma **ideia/receita** que você adapta.

## Os pontos que mais importam
1. **Base de POO:** classe (planta) × objeto (instância); 4 pilares: **Abstração, Encapsulamento, Herança, Polimorfismo**.
2. **Relações UML (da mais fraca à mais forte):** Dependência (- - ->) · Associação (——>) · Agregação (◇——>) · Composição (◆——>) · Implementação (- - -▷) · Herança (——▷).
3. **Agregação × Composição:** agregação = parte **existe sozinha** (Departamento ◇ Professor). Composição = parte **morre com o todo** (Universidade ◆ Departamento).
4. **Padrão ≠ algoritmo:** algoritmo = passos exatos; padrão = descrição de alto nível.
5. **3 categorias (GoF, 1994, 23 padrões):** **Criação** (como criar objetos) · **Estruturais** (como montar estruturas) · **Comportamentais** (comunicação/responsabilidades).
6. **Princípios:** Encapsule o que varia · Programe para interface, não implementação · Prefira composição sobre herança.
7. **Singleton (criação):** uma classe com **só uma instância** + **ponto de acesso global**. Receita: **construtor privado** + **campo estático** + **método estático `getInstancia()`**. Alternativa: **enum**.
8. **Factory Method (criação):** superclasse define o **método que cria**; **subclasses decidem qual objeto** criar. Receita: interface Produto → produtos concretos → Criador abstrato com `criarX()` → criadores concretos.
9. **Vantagens/desvantagens** de cada padrão (SRP, Aberto/Fechado, multithread, mais subclasses).

## Como tudo se conecta
```
POO (classes, pilares, relações UML)
   ↓ problemas recorrentes de projeto
Princípios (encapsular o que varia, interface, composição)
   ↓ aplicados em soluções prontas
Padrões de CRIAÇÃO → Singleton (1 instância)  |  Factory Method (subclasse escolhe o objeto)
```

## Estilo do professor
Exercícios **práticos em Java** (implementar o padrão num cenário novo) e **desenhar UML a partir de um texto**. Espere: "implemente X com Factory Method", "identifique as relações", vantagens/desvantagens.
