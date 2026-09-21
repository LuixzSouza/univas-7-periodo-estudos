# Business Intelligence — Fórmulas, códigos e passo a passo

---
## Diagramas para memorizar
```
PIPELINE:  Fontes → Extract → Staging (Transform) → Load → Data Warehouse → Analyze (visual)
PREPARAÇÃO: Requisitos → Dados disponíveis → Medidas → Dimensões → Visuais
FLUXO DE DECISÃO: Objetivo → Público → Tipo de decisão → Agregação → Visualização
CADEIA:    Dados → Informação → Conhecimento → Decisão → Ação → Resultado
```

## Regra de ouro (decorar)
| Se a decisão é... | Público típico | Agregação | Formato |
|---|---|---|---|
| **Estratégica** | diretoria/executivos | alta (resumo) | **Dashboard agregado** |
| **Tática** | gerentes | média | **Dashboard com drill-down** |
| **Operacional** | analistas/operadores/auditoria | baixa (detalhe, linha a linha) | **Relatório analítico** |

---
## TIPO 1 — Aplicar o Fluxo de Decisão a um pedido (Atividade de Fixação 1) ⭐

### Passo a passo
1. **Objetivo:** o que o pedido quer saber? Procure verbos: "investigar/rastrear/verificar" → detalhe. "Acompanhar/monitorar/comparar/tendência" → resumo.
2. **Público:** quem vai usar? (auditoria/analistas × diretoria/gerência)
3. **Decisão:** estratégica, tática ou operacional?
4. **Agregação:** detalhado (transação por transação) ou resumido (totais, %)?
5. **Formato:** relatório analítico ou dashboard (agregado/drill-down)?
6. **Justifique** com: Eckerson (relatório × dashboard), Few (clareza), Kimball (fato/dimensão), Inmon (dados consistentes), Davenport (decisão baseada em dados).

### Exemplo resolvido — GlobalParts Industries

**Pedido 1 — Auditoria interna quer as compras de abril a junho com todos os campos**
| Pergunta | Resposta |
|---|---|
| 1. Informação | Lista **detalhada** de cada compra (nº pedido, data, unidade, fornecedor, produto, qtd, valor unit./total, prazo, entrega, aprovador) para **investigar divergências**. |
| 2. Para quem | **Equipe de auditoria interna** (analistas). |
| 3. Decisão | **Operacional**: verificar transações específicas e achar causas. |
| 4. Agregação | **Baixa / nenhuma** — nível de transação (alta granularidade). |
| 5. Formato | **Relatório analítico** (tabela, com filtros por período/fornecedor, exportável). |
| Justificativa | Eckerson: relatório serve para **análise detalhada e investigação**. Comparativo: foco em **precisão e rastreabilidade**, leitura longa, grande volume. Inmon: dados íntegros e fiéis à fonte são essenciais para auditoria. |

**Pedido 2 — Diretoria quer acompanhar mensalmente a eficiência de compras**
| Pergunta | Resposta |
|---|---|
| 1. Informação | **Indicadores**: gasto por mês, comparação entre unidades/regiões, top fornecedores, % entregas no prazo, economia, variação mês a mês. |
| 2. Para quem | **Diretoria de Operações** (executivos). |
| 3. Decisão | **Estratégica/tática** (acompanhar desempenho, discutir em reunião executiva). |
| 4. Agregação | **Alta** — totais, médias, percentuais por mês/unidade/fornecedor. |
| 5. Formato | **Dashboard agregado** (KPIs em cartões, linha para evolução mensal, colunas para comparar unidades, ranking de fornecedores), com **drill-down** por região/unidade se quiserem aprofundar. |
| Justificativa | Eckerson: dashboard dá **visão resumida** e **identifica exceções** rapidamente ("situações que mereçam atenção"). Few: pouca carga cognitiva, gráfico certo (linha = tendência, coluna = comparação). Davenport: apoio a decisões gerenciais baseadas em evidência. |

---
## TIPO 2 — Relatório analítico em SQL (Estudo de Caso 1 / dataset d_produto)

### Passo a passo
1. Identifique **fato** (valores) e **dimensões** (descrições).
2. `SELECT` as colunas pedidas.
3. `JOIN` do fato com cada dimensão pela chave.
4. `WHERE` para o período, se pedido.
5. `ORDER BY` conforme o requisito.

### Sintaxe base (complemento — SQL padrão/MySQL)
```sql
SELECT colunas
FROM fato f
JOIN dimensao d ON d.id = f.id_dimensao
WHERE condição
GROUP BY agrupamento      -- só se for resumir
ORDER BY coluna;
```

### Exemplo resolvido — Caso 1 "Beleza Natural" (vendas)
Requisito: Data da Venda, Produto, Categoria, Valor Total, ordenado por data.
```sql
SELECT dt.data          AS "Data da Venda",
       p.nome_produto   AS "Produto",
       p.categoria_produto AS "Categoria",
       v.vlr_total      AS "Valor Total"
FROM f_vendas v
JOIN d_produto p ON p.id_produto = v.id_produto
JOIN d_data   dt ON dt.id_data   = v.id_data
ORDER BY dt.data;
```
> Os nomes de colunas de `f_vendas` e `d_data` são suposições (o script dessas tabelas não está na pasta). `d_produto` é real.

### Exemplo resolvido — consultas no dataset real `d_produto`
```sql
-- Relatório analítico: lista de produtos por categoria e preço
SELECT id_produto, nome_produto, categoria_produto, vlr_uni, qtd_estoque
FROM d_produto
ORDER BY categoria_produto, nome_produto;

-- Visão agregada (tipo dashboard): valor em estoque por categoria
SELECT categoria_produto,
       COUNT(*)                     AS qtd_produtos,
       SUM(vlr_uni * qtd_estoque)   AS valor_estoque
FROM d_produto
GROUP BY categoria_produto
ORDER BY valor_estoque DESC;
```
Conta de verificação (Carnes): 14,90×80 + 39,90×60 + 29,90×75 + 21,90×70 + 9,90×120 = 1192 + 2394 + 2242,50 + 1533 + 1188 = **R$ 8.549,50**.

**Pegadinha:** listar linha a linha = **relatório analítico**. `GROUP BY` com totais = visão **agregada** (base de dashboard).

---
## TIPO 3 — Relacionar autor ↔ ideia
| Frase na questão | Autor |
|---|---|
| "fonte única da verdade", "top-down", "DW corporativo", "integridade" | **Inmon** |
| "fato e dimensão", "Data Marts", "bottom-up", "self-service", "foco no usuário" | **Kimball** |
| "cultura analítica", "storytelling", "Competing on Analytics", "vantagem competitiva" | **Davenport** |
| "evitar sobrecarga visual", "hierarquia visual", "gráfico adequado" | **Few** |
| "reduzir ruído visual" | **Tufte** |
| "relatório × dashboard", "monitoramento de desempenho" | **Eckerson** |
| "termo pela 1ª vez, anos 1950, IBM" | **Luhn** |
| "sistemas baseados em fatos", Gartner | **Dresner** |

---
## TIPO 4 — Escolher o gráfico (Few — complemento nos exemplos)
| Objetivo | Gráfico |
|---|---|
| Tendência no tempo | Linha |
| Comparar categorias/unidades | Colunas/barras |
| Ranking (top fornecedores) | Barras horizontais ordenadas |
| KPI isolado (% no prazo) | Cartão/número grande, com meta |
| Detalhe de transações | Tabela |
