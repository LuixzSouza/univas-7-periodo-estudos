# Sistemas de Informações Gerenciais — Conceitos (ordem das aulas)

> ⚠️ A pasta só tem **estudos de caso**. Os conceitos teóricos abaixo marcados como **(complemento)** vêm de conhecimento geral de SIG (Laudon/O'Brien), porque os casos exigem esse vocabulário para responder. **Confirme com seu caderno** o que o professor explicou em sala.

---
## Base teórica usada pelos casos (complemento)

### Sistema de Informação
- **Definição:** conjunto de componentes (pessoas, processos, dados, tecnologia) que coleta, processa, armazena e distribui informação para apoiar **decisão e controle**.
- **Pegadinha:** SI **não é só tecnologia** — envolve pessoas e organização.

### As 3 dimensões de um SI ⭐
| Dimensão | Inclui | Exemplo de falha |
|---|---|---|
| **Pessoas (humana)** | treinamento, cultura, resistência, comportamento, habilidades | agentes do FBI sem acesso à internet; diretores brigando |
| **Organização** | liderança, estrutura, processos, política interna, regras | 14 gerentes no projeto do FBI; vácuo de liderança na TI da Comair |
| **Tecnologia** | hardware, software, bancos de dados, redes, integração | 5 sistemas isolados; SBS em Fortran com contador limitado |

### Sistema legado
- **Definição:** sistema antigo ainda em uso, difícil de trocar porque os processos dependem dele.
- **Exemplo:** SBS da Comair; terminais IBM 3270 do FBI.
- **Pegadinha:** "funciona razoavelmente" ≠ "é seguro"; o risco aparece no pico de uso.

### Data warehouse / integração
- **Definição:** repositório único que junta dados de várias fontes para consulta e análise.
- **Exemplo:** Data Warehouse Investigativo do FBI (47 fontes, 100 mi de páginas).

### Software sob medida × de prateleira
| Sob medida | Prateleira (pacote) |
|---|---|
| feito do zero (SAIC escreveu o VCF) | comprado pronto (Sentinel: 80–90%; SABRE) |
| mais caro/arriscado, pode encaixar melhor | mais rápido, testado, menos flexível |

---
## CASO 1 (17/08) — Uma reunião tumultuada
**Situação:** vendas **30% abaixo** do plano. Na reunião, cada diretor culpa outro (finanças, marketing, agência), o vice diz que não é ouvido, discutem "política". Ninguém trata "**o que fazer para aumentar as vendas?**".
**Problema real:** **comportamental/organizacional** — falta de foco, de pauta, de liderança, de dados objetivos; clima de culpa e subjetivismo.
**Ponto-chave do enunciado:** "O problema está com o presidente, **mas também com você**" (diretor de desenvolvimento) → a solução começa por **atitude interativa** de cada executivo.
**Pegadinha:** o texto diz que a **informação não é o principal** agora — o foco é o **comportamento**.

---
## CASO 2 (24/08) — O FBI abandona seu sistema de casos virtual
**Contexto:** após o 11/09/2001, ficou claro que o FBI não compartilhava informações.
**Situação tecnológica:** centenas de aplicativos em várias linguagens, bancos independentes; **5 sistemas de investigação** isolados, cada um com dados em formato diferente; terminais verdes **IBM 3270**; relatórios **impressos, assinados e digitalizados**; IAFIS × IDENT incompatíveis (10 × 2 impressões digitais).
**Projeto Trilogy (2000):** US$ **379 mi** — hardware, rede de **622 escritórios**, e o **VCF (Virtual Case File)**: data warehouse integrando **180 bancos** num portal web.
**O que deu certo:** 21 mil PCs, 3 mil impressoras, 1.500 scanners, rede de alta velocidade, **Data Warehouse Investigativo** (47 fontes).
**O que deu errado (VCF):**
| Dimensão | Causas |
|---|---|
| Pessoas | cultura **sigilosa**; autorizações de segurança levavam **8 meses**; FBI sem pessoal experiente em projetos/contratos/software |
| Organização | **4 CIOs e 14 gerentes**; **1,3 pedido de mudança por dia**; contrato revisado **26 vezes**; bancos mal documentados |
| Tecnologia | SAIC escreveu software do zero (não usou prateleira); sistema **inflexível**; **sem testes nem plano de contingência**; legados sem comunicação |
**Impacto:** US$ **170 mi** gastos, só **1/10** pronto; abandonado em **8/3/2005**; risco à segurança nacional.
**Solução seguinte:** **Sentinel** (maio/2005), 80–90% software de prateleira; Conselho Nacional recomendou implantar **passo a passo**.

---
## CASO 3 (14/09) — Como o sistema de escala de tripulação da Comair entrou em colapso
**Empresa:** Comair (Cincinnati), 7 mil funcionários, 1.100 voos/dia, subsidiária da **Delta**.
**Linha do tempo:**
| Ano | Fato |
|---|---|
| 1984 | escalas com caneta e papel |
| ~1994 | aluga software **SBS** por exigência de regulação |
| 1997 | TI pensa em trocar; SBS com 11 anos, em **Fortran**, só um especialista; recusam o **Maestro** |
| 1998 | Jim Dublikar faz plano de 5 anos com SABRE: trocar o sistema de tripulação |
| fim 1990s | foco no **bug do milênio** |
| 2000 | Delta compra a Comair; Dublikar sai → **vácuo de liderança na TI** |
| 2001 | **greve de 89 dias** (800 voos/dia cancelados, US$ 200 mi) + **11/09** |
| 2002 | demonstrações de fornecedores; nada fechado por **custo** |
| jun/2004 | Delta aprova troca pelo **SABRE AirCrews**, previsto para 2005 |
| 22–25/12/2004 | tempestade → muitas mudanças de escala → SBS atinge o limite de **32.768 mudanças/mês** → pane |
**Impacto:** 1.100 voos cancelados, 30 mil passageiros afetados, **US$ 20 mi** de prejuízo, imagem arranhada; volta só em 29/12; sem **sistema reserva**.
**Após:** SBS dividido em 2 módulos (pilotos e comissários, 32 mil cada) e volume monitorado.
| Dimensão | Causas |
|---|---|
| Pessoas | usuários acostumados ao SBS; supervisor com opinião negativa do Maestro; ninguém sabia do contador |
| Organização | aquisição pela Delta (foco em marketing, não TI); saída do diretor de TI; TI passiva; prioridades (bug do milênio, greve, 11/09); custo |
| Tecnologia | legado em Fortran/AIX; limite de 32.768 (contador de 16 bits — complemento); sem redundância nem teste de carga |
**Pegadinha:** a Comair culpou o **clima**, mas a causa raiz foi o **software legado** e a **falta de gestão de risco**.
