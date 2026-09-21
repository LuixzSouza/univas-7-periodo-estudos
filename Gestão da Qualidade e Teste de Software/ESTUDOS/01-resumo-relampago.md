# Gestão da Qualidade e Teste de Software — Resumo Relâmpago

**Prof. Flávio Belizário da Silva Mota** · 8 aulas (0 a 7) + 3 atividades · Avaliação: 2 provas de 25 pts + exercícios 10 + seminário 20 + trabalho 20

## O que é a matéria
Como **definir, medir e garantir** a qualidade do software — do **produto** (o que é entregue) e do **processo** (como é feito). A parte de **testes** (unidade, integração, interface) está na ementa, mas **ainda não tem aula**.

## Os pontos que mais importam
1. **Qualidade** = conformidade com requisitos + satisfazer necessidades (ISO 9000). **Produto × Processo**: "bons processos aumentam a probabilidade de bons produtos".
2. **4 perspectivas:** desenvolvedor (código limpo) · usuário (uso fácil, sem falhas) · cliente (prazo, orçamento, ROI) · auditor (normas).
3. **McCall (1977):** 3 grupos — **Operação**, **Revisão** e **Transição** do produto.
4. **ISO 25010:** **Qualidade em uso (5)** + **Qualidade de produto (8)**: adequação funcional, eficiência de desempenho, compatibilidade, usabilidade, confiabilidade, segurança, manutenibilidade, portabilidade.
5. **Fatores humanos + 10 Heurísticas de Nielsen** (visibilidade do status, prevenção de erros, consistência...).
6. **Métricas:** diretas × indiretas; produto × processo × projeto; cuidado com **métricas de vaidade**. **GQM**: Goal → Question → Metric, meta no modelo de **Basili**.
7. **CMM (SEI):** 5 níveis — **1 Inicial, 2 Repetível, 3 Definido, 4 Gerenciado, 5 Otimizado** + áreas-chave de cada nível.
8. **CMMI:** integra disciplinas; **por Estágios** (maturidade 1–5 da organização) × **Contínuo** (capacidade 0–5 de cada processo).
9. **SQA:** Planejamento → **Garantia (QA, foca no processo)** → **Controle (QC, foca no produto)**. Técnicas **estáticas** (auditoria, inspeção, walkthrough, revisões, avaliação, Seis Sigma) × **dinâmicas** (testes).

## Como tudo se conecta
```
O que é qualidade? (definições, perspectivas)
   ↓ modelar
Modelos de qualidade do PRODUTO: McCall, ISO 25010, fatores humanos/Nielsen
   ↓ medir
Métricas + GQM (medir com propósito)
   ↓ melhorar o PROCESSO
CMM → CMMI (níveis de maturidade/capacidade)
   ↓ gerenciar no dia a dia
SQA: Plano de Qualidade + QA (processo) + QC (produto/testes)
```

## Estilo do professor
Sempre usa um **caso (ClínicasPA)** e dá a cada grupo uma **perspectiva**. Cobra **aplicação**: montar GQM, **diagnosticar nível CMM por evidências**, escolher técnicas de SQA e justificar. Espere questões de **caso + justificativa**.
