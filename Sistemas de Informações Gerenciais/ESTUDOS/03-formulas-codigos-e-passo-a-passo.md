# Sistemas de Informações Gerenciais — Passo a passo para estudos de caso

Não há fórmulas nem código. O tipo de exercício é **estudo de caso dissertativo**.

## Modelo de resposta (use sempre)
```
1. PROBLEMA   → o que aconteceu (1–2 frases, com números do caso)
2. CAUSAS     → Pessoas | Organização | Tecnologia
3. IMPACTO    → financeiro, operacional, imagem, clientes, segurança
4. SOLUÇÕES   → 2–3 alternativas + vantagens/desvantagens
5. ESCOLHA    → qual e por quê (a do caso foi boa?)
6. IMPLANTAÇÃO→ o que considerar nas 3 dimensões (treinamento, patrocínio, testes, contingência, por etapas)
```

---
## TIPO 1 — Plano de ação comportamental (Caso "Reunião tumultuada")
**Passo a passo:** diagnóstico → mudar a própria postura → propor regras de reunião → trazer dados objetivos → plano com responsáveis → acompanhamento.

**Exemplo de resposta (resposta minha):**
| Etapa | Ação |
|---|---|
| 1. Autocrítica | Reconhecer minha parte; conversar individualmente com presidente e diretores (ouvir sem julgar). |
| 2. Pauta e regras | Próxima reunião com **pauta única** ("como aumentar as vendas"), tempo definido, moderador, proibido buscar culpados. |
| 3. Dados | Cada área traz números (vendas por região/produto, cronograma da campanha, orçamento aprovado), trocando opinião por fato. |
| 4. Análise de causa | Usar ferramenta objetiva (ex.: 5 porquês/Ishikawa — complemento) para achar causas, não pessoas. |
| 5. Plano de ação | Ações com **responsável, prazo e indicador** (5W2H — complemento). |
| 6. Integração | Workshop de comunicação/feedback; definir papéis e processo de decisão (vice consultado). |
| 7. Acompanhamento | Reunião curta semanal de indicadores; revisar resultados em 30 dias. |

---
## TIPO 2 — Análise de fracasso de projeto de SI (Caso FBI)
**Respostas-modelo às questões do livro:**
1. **Problema/causa/impacto:** FBI não compartilhava informação (sistemas isolados, papel). Causas nas 3 dimensões (ver arquivo 02). Impacto: pode ter contribuído para não detectar o 11/09; US$ 170 mi perdidos; agentes sem informação.
2. **Identificou corretamente?** Em parte: viu o lado **tecnológico** (Trilogy), mas subestimou o **humano** (cultura sigilosa) e o **organizacional** (gestão de projeto, requisitos).
3. **Soluções:** data warehouse único (VCF), infraestrutura nova, software sob medida pela SAIC. **Apropriada?** A ideia sim; a forma não — sob medida, "big bang", sem testes; melhor seria prateleira e por etapas.
4. **Implementação efetiva?** Não: 4 CIOs, 14 gerentes, 1,3 mudança/dia, contrato revisto 26 vezes, sem contingência.
5. **Sentinel terá sucesso?** Mais chance: usa 80–90% prateleira e pode ser feito por etapas; **mas** só se resolver cultura, liderança estável e requisitos congelados.

---
## TIPO 3 — Sistema legado e gestão de risco (Caso Comair)
**Respostas-modelo:**
1. **Problemas:** SBS antigo (Fortran/AIX), sem integração, com limite de 32.768 mudanças/mês. Causa: substituição adiada anos. Impacto: 1.100 voos cancelados, US$ 20 mi, 30 mil passageiros, imagem.
2. **Soluções disponíveis:** Maestro (SBS), SABRE, outros fornecedores, reescrever internamente, **dividir o SBS**/monitorar volume, **sistema reserva**. A escolha (SABRE AirCrews) foi boa, **mas tardia**; faltou medida provisória de risco (conhecer os limites, backup, teste de carga).
3. **Fatores na decisão:** Humanos (costume com SBS, opinião do supervisor); Organizacionais (aquisição Delta, saída do diretor de TI, prioridades concorrentes, custo); Tecnológicos (legado, bug do milênio).
4. **Para o novo sistema:** Humanos — treinar usuários, envolver supervisores; Organizacionais — patrocínio da Delta, líder de TI, gestão de risco, migração das regras de negócio (jornada do piloto); Tecnológicos — testes de carga, integração com outros sistemas, **plano de contingência/redundância**.

---
## Checklist rápido de "lições" para citar em qualquer caso
- Envolver usuários e alta direção (patrocínio)
- Liderança estável de TI
- Requisitos controlados (gestão de mudanças)
- Implantação **por etapas** e com **testes**
- Preferir software de prateleira quando possível
- **Plano de contingência** e conhecimento dos limites do sistema
- Integração de dados (fim dos silos)
