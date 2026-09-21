# Gestão de Custos — Fórmulas e passo a passo (com exemplos resolvidos)

## 📌 Folha de fórmulas
| O quê | Fórmula |
|---|---|
| CMV (revenda) | **CMV = EI + C − EF** |
| CPV (indústria) | **CPV = EI + (In + MOD + GGF) − EF** |
| CSV (serviço) | **CSV = Sin + (MO + GDS + GIS) − Sfi** |
| Lucro bruto | **Receita − CPV (ou CMV/CSV)** |
| Custo/hora MOD | **(salários + encargos + benefícios) ÷ horas trabalhadas** |
| Custo de transformação | **MOD + CIF** (sem matéria-prima) |
| Custo de produção (absorção) | **MP + MOD + CIF** |
| Taxa de rateio | **CIF total ÷ total da base** (horas, %, unidades) |
| CIF do produto | **taxa × base do produto** |
| % de rateio por quantidade | **qtd do produto ÷ qtd total** |
| Custo unitário | **custo total do produto ÷ unidades produzidas** |
| Qtd vendida | **produzida − estoque final** (sem estoque inicial) |
| ABC: custo da atividade | **custo do depto × % de dedicação** |
| ABC: custo unit. do direcionador | **custo da atividade ÷ total do direcionador** |
| ABC: custo da atividade p/ produto | **custo unit. do direcionador × qtd do direcionador do produto** |
| ABC: custo por unidade | **custo da atividade do produto ÷ unidades do produto** |

---
## TIPO 1 — CMV (Aula 2)
**Passo a passo:** EI + Compras − EF.

**Exemplo por quantidade:** EI 100, compras 200, EF 125 → **CMV = 100 + 200 − 125 = 175 unidades**.
**Exemplo monetário:** EI R$ 1.000, C R$ 2.000, EF R$ 1.250 → **CMV = R$ 1.750**.

---
## TIPO 2 — CPV e lucro bruto (Aula 2)
**Passo a passo:** 1) some os custos de produção (In + MOD + GGF); 2) some o EI; 3) tire o EF; 4) lucro bruto = faturamento − CPV.

**Exemplo (empresa X):** Faturamento 300.000; EI 150.000; In 50.000; MO 10.000; GGF 30.000; EF 10.000.
```
CPV = 150.000 + (50.000 + 10.000 + 30.000) − 10.000
    = 150.000 + 90.000 − 10.000 = R$ 230.000
Lucro bruto = 300.000 − 230.000 = R$ 70.000
```

---
## TIPO 3 — CSV (Aula 2)
**Exemplo (empresa de limpeza):** Sin 10.000; MO 25.000; GDS 8.000; GIS 5.000; Sfi 30.000.
```
CSV = 10.000 + (25.000 + 8.000 + 5.000) − 30.000 = 48.000 − 30.000 = R$ 18.000
```

---
## TIPO 4 — Custo por hora da MOD (Aula 3)
**Exemplo:** MOD/mês R$ 100.000; 5.000 horas → **100.000 ÷ 5.000 = R$ 20,00/hora**.
**Pegadinha:** some **salário + encargos + benefícios** e desconte **horas ociosas** das horas.

---
## TIPO 5 — Rateio simples de CIF (Aula 4)
**Passo a passo:** 1) taxa = CIF ÷ total da base; 2) multiplique pela base de cada produto; 3) confira: soma = CIF total.

**Exemplo:** CIF R$ 100.000; base hora-produto: A 6.000 h, B 4.000 h (total 10.000).
```
Taxa = 100.000 ÷ 10.000 = R$ 10,00/HProd
A = 10 × 6.000 = R$ 60.000
B = 10 × 4.000 = R$ 40.000     (60.000 + 40.000 = 100.000 ✔)
```

---
## TIPO 6 — Departamentalização (auxiliar → produtivo → produto) (Aula 4) ⭐
**Passo a passo:**
1. Taxa do depto auxiliar = custo ÷ base (horas de manutenção).
2. Distribua aos centros produtivos.
3. Taxa de cada centro produtivo = valor recebido ÷ base dos produtos (hora-produto).
4. Aplique aos produtos e **some** por produto.

**Exemplo:** Manutenção R$ 40.000; 5.000 HManut (Polimento 1.600, Montagem 3.400); 20.000 HProd (A 15.000, B 5.000).
```
1º Taxa manutenção = 40.000 ÷ 5.000 = R$ 8,00/HManut
2º Polimento = 8 × 1.600 = 12.800     Montagem = 8 × 3.400 = 27.200   (total 40.000 ✔)
3º Taxa Polimento = 12.800 ÷ 20.000 = R$ 0,64/HProd
   Taxa Montagem  = 27.200 ÷ 20.000 = R$ 1,36/HProd
4º          Polimento            Montagem             Total
   A   0,64 × 15.000 = 9.600   1,36 × 15.000 = 20.400   30.000
   B   0,64 ×  5.000 = 3.200   1,36 ×  5.000 =  6.800   10.000
                                                  Total 40.000 ✔
```

---
## TIPO 7 — Custeio por Absorção completo (exercício da Aula 4) ⭐⭐
**Dados:** Produção X 2.000 un, Y 600 un · MP: X 60.000, Y 24.000 · MOD: X 24.000, Y 6.000 · MOI 46.000 · Outros CIFs 26.000 · Energia 6.000 · Despesas gerais 20.000 · EF: X 400, Y 100 · Preço: X R$ 200, Y R$ 240 · CIF rateado pelo **% da quantidade produzida**.

**Passo a passo resolvido:**
```
0) Separar custos × despesas:
   CIF = MOI 46.000 + Outros CIFs 26.000 + Energia 6.000 = R$ 78.000
   Despesas gerais 20.000 → FORA do custo (é despesa)

1) % de rateio (quantidades):
   Total = 2.000 + 600 = 2.600
   X = 2.000 ÷ 2.600 = 76,92%     Y = 600 ÷ 2.600 = 23,08%

   CIF X = 78.000 × 2.000/2.600 = R$ 60.000
   CIF Y = 78.000 ×   600/2.600 = R$ 18.000

2) Custo de produção total:
              X          Y
   MP      60.000     24.000
   MOD     24.000      6.000
   CIF     60.000     18.000
   Total  144.000     48.000

3) Custo unitário:
   X = 144.000 ÷ 2.000 = R$ 72,00      Y = 48.000 ÷ 600 = R$ 80,00

4) Quantidade vendida:
   X = 2.000 − 400 = 1.600 un         Y = 600 − 100 = 500 un

5) CPV:
   X = 1.600 × 72 = R$ 115.200        Y = 500 × 80 = R$ 40.000
   CPV total = R$ 155.200
```
**Extra (complemento):** Receita = 1.600×200 + 500×240 = 320.000 + 120.000 = **440.000** · Lucro bruto = 440.000 − 155.200 = **284.800** · Após despesas gerais: 284.800 − 20.000 = **264.800**.
**Pegadinha:** Energia aqui é **CIF** (energia da fábrica). Os números "redondos" (72 e 80) confirmam isso. Despesas gerais **nunca** entram no custo no absorção.

---
## TIPO 8 — Custeio ABC completo (aula ABC) ⭐⭐
**Dados:** PCP 15.000 (Planejar 40%, Controlar 60%) · Compras 22.000 (Aprovar fornec. 30%, Comprar 70%) · Almoxarifado 12.500 (Receber 45%, Movimentar 55%) · Produção 30.000 (Montar 65%, Embalar 35%) · CD 16.000 (Movimentar PA 5.600, Expedir 10.400). Produção: **A 500 un, B 350 un**.

```
Passo 1 — custo por atividade (direcionador de RECURSO = % tempo):
  Planejar 6.000 | Controlar 9.000 | Aprovar 6.600 | Comprar 15.400 | Receber 5.625
  Movimentar mat. 6.875 | Montar 19.500 | Embalar 10.500 | Mov. PA 5.600 | Expedir 10.400

Passo 2 — direcionador de ATIVIDADE e custo unitário:
  Atividade        Direcionador      A      B    Total   Custo unit.
  Planejar         nº produtos      500    350    850   6.000/850  = 7,0588
  Controlar        nº lotes         120     80    200   9.000/200  = 45,00
  Aprovar fornec.  nº fornecedores    5      3      8   6.600/8    = 825,00
  Comprar mat.     nº pedidos       140     60    200   15.400/200 = 77,00
  Receber mat.     nº recebimentos  145     62    207   5.625/207  = 27,1739
  Movimentar mat.  nº requisições    25     15     40   6.875/40   = 171,875
  Montar           h montagem       200    105    305   19.500/305 = 63,9344
  Embalar          h embalagem       75   52,5  127,5   10.500/127,5 = 82,3529
  Movimentar PA    h movimentação   360    180    540   5.600/540  = 10,3704
  Expedir PA       nº expedições    460    320    780   10.400/780 = 13,3333

Passo 3 — custo da atividade por produto (custo unit. × qtd):
  Controlar: A = 45 × 120 = 5.400    B = 45 × 80 = 3.600
  (idem para as outras — tabela abaixo)

Passo 4 — por unidade (÷ 500 para A, ÷ 350 para B):
  Atividade        A (R$)      B (R$)     A/un    B/un
  Planejar        3.529,41    2.470,59    7,06    7,06
  Controlar       5.400,00    3.600,00   10,80   10,29
  Aprovar fornec. 4.125,00    2.475,00    8,25    7,07
  Comprar mat.   10.780,00    4.620,00   21,56   13,20
  Receber mat.    3.940,22    1.684,78    7,88    4,81
  Movimentar mat. 4.296,88    2.578,13    8,59    7,37
  Montar         12.786,89    6.713,11   25,57   19,18
  Embalar         6.176,47    4.323,53   12,35   12,35
  Movimentar PA   3.733,33    1.866,67    7,47    5,33
  Expedir PA      6.133,33    4.266,67   12,27   12,19
  TOTAL POR UNIDADE                     121,80   98,85
```
⚠️ **Typo no slide:** "Hora de Embalagem B = 52,2". Com 52,2 o total seria 127,2; o total 127,5 e o valor 4.323,53 só batem com **52,5**.

---
## TIPO 9 — ABC com 1 departamento e 2 atividades (Exemplo Atividade ABC) ⭐
**Dados:** Depto Produção R$ 25.000; Fabricação 70%, Inspeção 30%. Horas: A = 300 fab + 150 insp; B = 150 fab + 50 insp. Unidades: A = 400 (fab) / 115 (insp); B = 180 (fab) / 40 (insp).

```
a) Custo por atividade:
   Fabricação = 70% × 25.000 = R$ 17.500
   Inspeção   = 30% × 25.000 = R$  7.500

b) Custo unitário do direcionador (horas TOTAIS de cada atividade):
   Fabricação = 17.500 ÷ (300 + 150) = 17.500 ÷ 450 = R$ 38,89/h
   Inspeção   =  7.500 ÷ (150 +  50) =  7.500 ÷ 200 = R$ 37,50/h

c) Custo da atividade por produto:
                 Fabricação                 Inspeção             Total
   A   300 × 38,89 = 11.666,67     150 × 37,50 = 5.625,00     17.291,67
   B   150 × 38,89 =  5.833,33      50 × 37,50 = 1.875,00      7.708,33
                     17.500,00                   7.500,00     25.000,00 ✔

d) Custo por unidade:
   A fabricação = 11.666,67 ÷ 400 = R$ 29,17     A inspeção = 5.625,00 ÷ 115 = R$ 48,91
   B fabricação =  5.833,33 ÷ 180 = R$ 32,41     B inspeção = 1.875,00 ÷  40 = R$ 46,88
```
⚠️ **Atenção — o gabarito do PDF da professora troca linhas:** no item (c) ele coloca 5.833,32 como "inspeção do A" e 5.625,00 como "fabricação do B" (na verdade são **fabricação do B** e **inspeção do A**). Por isso o item (d) do PDF traz 50,72 (A insp.) e 31,25 (B fab.). O **raciocínio certo** é: *custo unit. da atividade × horas daquele produto naquela atividade*. Na prova, siga a lógica e, se o gabarito divergir, mostre o cálculo. Também: 1.875 ÷ 40 = **46,875**, não 46,85.
⚠️ Também: a tabela do PDF chama o direcionador da inspeção de "Horas de Montagem" (typo).

---
## TIPO 10 — Classificar gastos (objetivas/discursivas)
**Passo a passo:** 1) É produção? sim = custo / não = despesa. 2) Dá pra medir por produto? sim = direto / não = indireto. 3) Muda com o volume? sim = variável / não = fixo.

| Gasto | Custo/Despesa | Direto/Indireto | Fixo/Variável |
|---|---|---|---|
| Matéria-prima | custo | direto | variável |
| Embalagem (produto vendido embalado) | custo | direto | variável |
| Aluguel da fábrica | custo | indireto | fixo |
| Salário do supervisor da fábrica (MOI) | custo | indireto | fixo |
| Operário da linha (MOD) | custo | direto | variável* |
| Energia da fábrica | custo | indireto | (misto; complemento) |
| Depreciação de máquina | custo | direto (conforme slide) / indireto se várias linhas | fixo |
| Salário do RH / financeiro | despesa | — | fixo |
| Comissão de vendedores | despesa | — | variável |
| Juros de empréstimo | despesa | — | — |
\* conforme a discussão da Aula 3 (folha fixa × MOD aplicada variável).
