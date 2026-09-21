# DevOps — Flashcards

| Pergunta | Resposta |
|---|---|
| O que é DevOps? | União de cultura, práticas e ferramentas para entregar software em alta velocidade. |
| Foco do Dev? | Inovação e velocidade. |
| Foco do Ops? | Estabilidade e segurança. |
| C.A.M.S? | Cultura, Automação, Medição, Sharing (compartilhamento). |
| Frase da Medição? | "O que não é medido não é gerenciado." |
| O que é VCS? | Sistema que registra mudanças e permite recuperar versões. |
| Ferramenta VCS dominante? | Git. |
| commit × push? | commit = local; push = envia ao remoto. |
| O que é branch? | Linha de desenvolvimento isolada da main. |
| O que é Pull Request? | Pedido para mesclar a branch na principal; revisão + gatilho do CI. |
| Problema que o Docker resolve? | "Na minha máquina funciona". |
| O que tem num container? | Código, runtime, bibliotecas, configurações. |
| Docker Hub? | Repositório de imagens (GitHub das imagens). |
| Slogan do Docker? | Construa uma vez, execute em qualquer lugar. |
| Container compartilha o quê? | O kernel do SO do host. |
| Isolamento mais forte: VM ou container? | VM. |
| Inicia mais rápido? | Container (segundos). |
| Dockerfile? | Receita (texto) para construir a imagem; infraestrutura como código. |
| 4 vantagens dos containers? | Consistência, imutabilidade, portabilidade, escalabilidade. |
| Orquestrador citado? | Kubernetes. |
| CI em uma frase? | Integrar código de forma frequente, automática e testada. |
| 5 etapas do pipeline de CI? | Baixa código, instala dependências, testa, build, notifica. |
| Se um teste falha? | O pipeline para. |
| Arquivo do GitHub Actions? | .github/workflows/ci.yml |
| runs-on ubuntu-latest × self-hosted? | Máquina do GitHub × sua máquina (runner). |
| Branch protection faz? | Exige status check (CI) aprovado antes do merge. |
| Onde a imagem é publicada? | GHCR (ghcr.io) – GitHub Container Registry. |
| Quando a imagem é publicada? | Só em push na main (após merge). |
| Entrega Contínua? | Publicar a imagem no registro após o merge. |
| Implantação Contínua? | Implantar automaticamente no servidor. |
| `needs`? | Job só roda se o outro terminar com sucesso. |
| SCA? | Vulnerabilidades nas dependências (npm audit). |
| SAST? | Vulnerabilidades no seu código (CodeQL). |
| Container scan? | Vulnerabilidades na imagem (Trivy). |
| `--audit-level=high`? | Falha só com vulnerabilidade alta ou crítica. |
| Push protection? | Impede dar push de senha por engano. |
| Corrigir dependências? | npm audit fix (ou --force). |
| `docker run -p 3000:3000 -d`? | Porta host:container; -d = segundo plano. |
