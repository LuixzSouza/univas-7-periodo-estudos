# Auditoria de Segurança da Informação — Passo a passo por tipo de exercício

Esta matéria **não tem fórmulas nem código**. Os exercícios são **estudos de caso dissertativos**. Abaixo, os "moldes" para responder.

---
## Diagrama-mestre
```
CICLO DE AUDITORIA
Planejamento → Execução → Coleta de Evidências → Análise → Relatório → Acompanhamento
                                                                            ↺ (volta ao início)

RISCO (complemento):  AMEAÇA  explora  VULNERABILIDADE  →  IMPACTO no C, I ou D
```

---
## TIPO 1 — Caso de auditoria (modelo Aula 01: hospital)

### Passo a passo
1. **Objetivos:** use os 4 objetivos da aula (controles internos, segurança, vulnerabilidades, conformidade) adaptados ao caso.
2. **Tipo de auditoria:** escolha entre Interna / Externa / Operacional / Conformidade / Sistemas e **justifique**.
3. **Como coletar evidências:** logs, entrevistas, documentos, análise de permissões, observação.
4. **3 evidências concretas.**
5. **Análise de risco:** classifique (baixo/médio/alto) = probabilidade × impacto (complemento).
6. **Relatório:** achado → risco → recomendação.
7. **Plano de acompanhamento:** ação, responsável, prazo, como verificar.

### Exemplo resolvido — Hospital com suspeita de acesso indevido a prontuários
| Item | Resposta |
|---|---|
| Objetivos | Avaliar controles de acesso ao prontuário; identificar acessos indevidos e vulnerabilidades; verificar conformidade com LGPD e sigilo médico (complemento). |
| Tipo | **De Sistemas** (controles de acesso de TI) + **De Conformidade** (dados sensíveis de saúde). Pode ser **Interna** (TI do hospital) ou **Externa** (mais independência). |
| Como coletar | Extrair **logs de acesso**; revisar **perfis/permissões**; **entrevistar** usuários e TI; ler a **política de segurança**. |
| 3 evidências | 1) Logs de quem abriu cada prontuário e quando. 2) Lista de usuários × perfis de acesso. 3) Contas ativas de ex-funcionários/senhas compartilhadas. |
| Grau de risco | **Alto**: dados de saúde são sensíveis; vazamento causa dano ao paciente, multa e perda de reputação. |
| Relatório | "Achado: 15 usuários da recepção acessam prontuário completo. Risco: quebra de confidencialidade. Recomendação: acesso por perfil (mínimo privilégio) e revisão trimestral." |
| Acompanhamento | Em 30 dias, reauditar perfis; mensalmente, revisar logs; responsável: gerente de TI. |

---
## TIPO 2 — Identificação de ameaças e vulnerabilidades (modelo Aula 02: e-commerce)

### Passo a passo
1. Leia o cenário e sublinhe os **sintomas** (ex.: "falhas de login", "acesso indevido").
2. **Ameaças** = quem/o que ataca → use a lista da aula (malware, phishing, DDoS, engenharia social, ransomware) + outras se couber.
3. **Vulnerabilidades** = por onde entrou → senha fraca, software desatualizado, permissões, falta de backup.
4. **Problemas para a empresa** (financeiro, legal, imagem).
5. **Problemas para os clientes** (dinheiro, dados, privacidade).
6. **Relatório** curto.
7. **Mitigação** = ligar cada vulnerabilidade a uma medida de proteção.

### Exemplo resolvido — Varejo online com falhas de login e acesso indevido
| Item | Resposta |
|---|---|
| 3 ameaças | Phishing (roubo de senha); ataque de força bruta / uso de senhas vazadas (complemento); malware (keylogger) no computador do cliente; engenharia social no atendimento. |
| Vulnerabilidades | Senhas fracas permitidas; sem bloqueio após tentativas erradas; sem autenticação de 2 fatores; sistema desatualizado; permissões mal configuradas. |
| Problemas p/ empresa | Prejuízo com fraudes/estornos; multas (LGPD); perda de reputação e clientes; processos. |
| Problemas p/ clientes | Compras em nome deles; vazamento de endereço/cartão; perda de dinheiro; golpes futuros. |
| Relatório | Achados + risco (alto) + recomendações priorizadas. |
| Mitigação | Política de senha forte; 2FA; bloqueio por tentativas; atualizações frequentes; criptografia; firewall/antivírus; monitoramento contínuo; campanha anti-phishing. |

---
## TIPO 3 — Classificar violação na tríade CID

### Passo a passo
Pergunte: a informação foi **vista** por quem não devia? → **C**. Foi **alterada**? → **I**. Ficou **inacessível**? → **D**.

### Exemplos resolvidos
| Situação | Princípio violado |
|---|---|
| Hacker publica lista de clientes | Confidencialidade |
| Funcionário altera nota de aluno no sistema | Integridade |
| Servidor cai por DDoS | Disponibilidade |
| Ransomware criptografa arquivos | Disponibilidade (e, se houver vazamento, confidencialidade) |

---
## TIPO 4 — Associar vulnerabilidade → medida de proteção
| Vulnerabilidade | Medida |
|---|---|
| Software desatualizado | Atualizações frequentes |
| Senha fraca | Política de segurança + controle de acesso |
| Falta de backup | Plano de contingência/backup |
| Permissões mal configuradas | Controle de acesso (mínimo privilégio) |
| Dados trafegando abertos | Criptografia |
| Malware | Antivírus e firewall |
