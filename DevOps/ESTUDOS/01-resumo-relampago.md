# DevOps — Resumo Relâmpago

**Prof. Raffael Carvalho** · 6 aulas (Intro/Git → Docker → CI → Proteção de branch → CD → DevSecOps) · muito **prático** (GitHub Actions, Docker, Node.js)

## O que é a matéria
DevOps = **cultura + práticas + ferramentas** que unem Desenvolvimento (quer mudar rápido) e Operações (quer estabilidade) para **entregar software rápido e com qualidade**, automatizando tudo num **pipeline**.

## Os pontos que mais importam
1. **Conflito Dev × Ops:** metas opostas → lentidão, "jogar a culpa", retrabalho.
2. **Pilares C.A.M.S:** **C**ultura · **A**utomação · **M**edição ("o que não é medido não é gerenciado") · **S**haring (compartilhamento).
3. **Git:** clone → commit → push → pull; **branch** isola trabalho; **Pull Request** = revisão + **gatilho do CI/CD**. "Sem Git, não há CI/CD eficiente."
4. **Container/Docker:** pacote com código + runtime + bibliotecas + configs → roda igual em qualquer lugar (resolve "na minha máquina funciona"). **Dockerfile** = receita → **Imagem** → **Container**.
5. **VM × Container:** VM tem SO próprio (pesada, minutos); container **compartilha o kernel** (leve, segundos).
6. **CI (Integração Contínua):** integrar código **frequente, automático e testado**. Pipeline: baixa código → instala dependências → **testa** → **build** → **notifica**.
7. **Proteção da branch main:** exige que o **status check** (job `test-and-build`) passe antes do merge.
8. **Entrega Contínua:** artefato (imagem) **publicado** no registro (GHCR) após merge. **Implantação Contínua:** o pipeline **implanta sozinho** no servidor (self-hosted runner + docker-compose).
9. **DevSecOps:** segurança **dentro** do pipeline: **SCA** (dependências – `npm audit`), **SAST** (seu código – CodeQL), **Container scan** (imagem – Trivy). Falha crítica → pipeline para.

## Como tudo se conecta
```
git push / Pull Request
      ↓ (gatilho)
GitHub Actions — Job 1: test-and-build
  checkout → setup node → npm install → npm test → npm audit (SCA)
  → docker build → Trivy (scan) → [se push na main] login GHCR + push da imagem   ← Entrega Contínua
      ↓ needs
Job 2: deploy-to-local (runs-on: self-hosted)
  docker-compose pull → up -d                                                      ← Implantação Contínua
CodeQL (SAST) roda em paralelo em todo push/PR
```

## Estilo do professor
Aulas = **roteiros práticos** + exercício "replique e explique em quais situações isso é útil numa empresa". Espere questões de **conceito + leitura/ordem de comandos e YAML**.
