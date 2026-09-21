# Business Intelligence — Resumo Relâmpago

**Prof. Luiz Gustavo Dias** · 📝 **Avaliação 1: 29/09 (terça)** · Avaliação 2: 24/11

## O que é a matéria
BI = transformar **dados brutos** em **informação** para **apoiar decisões** na empresa. Até a Avaliação 1 o foco é: fundamentos, pipeline, e **quando usar relatório analítico ou dashboard**.

## Os pontos que mais importam
1. **Definição de BI (Dresner, anos 1990):** "conjunto de conceitos e métodos para melhorar a tomada de decisões empresariais através do uso de sistemas baseados em fatos". Termo citado 1ª vez por **Hans Peter Luhn (IBM, anos 1950)**.
2. **Business Analytics (BA):** leitura dos dados **no contexto** + ferramentas para interpretá-los. Componente mais importante: **os dados**.
3. **Dado (Laudon):** fato bruto **antes** de ser organizado. Exemplo "34" sem contexto não diz nada; "Rua Bom Jesus, 34" vira informação.
4. **Cadeia:** Dados → Informações → Conhecimento → Decisões → Ações → Resultados.
5. **Pipeline do BI (ETL):** Fontes → **Extract** (dado bruto) → **Staging/Transform** → **Load** (dado preparado) → **Data Warehouse** → **Analyze** (visual).
6. **Técnicas de preparação (5 degraus):** Requisitos → Dados disponíveis → Medidas → Dimensões → Visuais.
7. **Relatório analítico × Dashboard (Eckerson):** relatório = detalhe/investigação/operacional. Dashboard = resumo/monitoramento/tático-estratégico.
8. **Fluxo de Decisão (5 perguntas):** Objetivo → Público → Tipo de decisão → Nível de agregação → Visualização. ⭐ É o que a atividade de fixação cobra.
9. **Tipo de decisão → formato:** Estratégica = dashboard agregado · Tática = dashboard com **drill-down** · Operacional = **relatório analítico**.
10. **4 autores:** **Inmon** (top-down, fonte única da verdade, integridade) · **Kimball** (bottom-up, fato/dimensão, foco no usuário, self-service) · **Davenport** (cultura analítica, storytelling) · **Few** (design claro, sem poluição visual).

## Como tudo se conecta
```
Dados brutos (OLTP, ERP, CRM, planilhas)
   → ETL (extrai, transforma, carrega)
   → Data Warehouse (fato + dimensões)
   → Camada de visualização
        ├─ Relatório analítico (detalhe, operacional)
        └─ Dashboard (resumo, KPIs, tático/estratégico)
   → Decisão → Ação → Resultado
```

## Estilo do professor
Cobra **aplicação**: dado um pedido de negócio, você decide o formato usando o **Fluxo de Decisão** e justifica com os **autores**. Revisão com exercícios em **22/09**.
