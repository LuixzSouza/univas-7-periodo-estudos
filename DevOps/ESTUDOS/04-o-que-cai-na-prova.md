# DevOps — O que cai na prova

> Sem provas antigas nem data informada. Previsão pela ênfase dos slides e pelos exercícios (todos práticos + "explique a utilidade na empresa").

## 🔴 Prioridade ALTA
| Tema | Por que é provável |
|---|---|
| **CI: definição + 5 etapas do pipeline** | Aula inteira; base de todas as aulas seguintes. |
| **Docker: container, imagem, Dockerfile, VM × container** | Aula inteira com tabela comparativa; usado em todas as práticas. |
| **Pilares C.A.M.S e definição de DevOps** | Conceito central da Aula 01; questão teórica clássica. |
| **DevSecOps: SCA × SAST × Container scan** | Aula mais recente; tabela fácil de cobrar e confundir. |
| **Entrega Contínua × Implantação Contínua** | Diferença sutil, explicada explicitamente no slide. |

## 🟡 Prioridade MÉDIA
| Tema | Por que é provável |
|---|---|
| Git: clone/commit/push/pull, branch, **Pull Request** | Aula 01 com exercício em grupo. |
| Leitura de **ci.yml** (`on`, `jobs`, `steps`, `if`, `needs`, `runs-on`) | Aparece em 4 aulas. |
| **Proteção de branch** e status check | Aula 04. |
| O que acontece no **PR** × no **merge** (steps skipped) | Explicado passo a passo nas Aulas 04-06. |
| Benefícios do CI e dos containers (consistência, imutabilidade, portabilidade, escalabilidade) | Listas nos slides. |
| Comandos Docker (`build`, `run -p`, `start`) | Práticas das Aulas 02 e 03. |

## 🟢 Prioridade BAIXA
| Tema | Por que é menos provável |
|---|---|
| Self-hosted runner e docker-compose (detalhes) | Muito operacional. |
| Dockerfile multi-stage e `.dockerignore` | Detalhe de implementação. |
| Jest/Supertest, `app.js` × `server.js` | Detalhe da prática. |
| Criar JAR com manifesto | Passo operacional. |
| Secret/Push protection | Citado rapidamente. |
