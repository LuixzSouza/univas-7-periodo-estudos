# DevOps — Comandos, arquivos e passo a passo

---
## 1. Git — comandos da aula
```bash
git clone <url>                        # baixa o repositório
git pull origin main                   # atualiza a main local
git checkout -b <nome-branch>          # cria e entra numa branch nova
git add apresentacoes.md               # prepara o arquivo
git commit -m "Adiciona apresentacao"  # salva localmente
git push origin <nome-branch>          # envia a branch ao GitHub
git checkout main                      # volta pra main
# repositório novo:
git init
git add .
git commit -m "Commit inicial"
git remote add origin <URL.git>
git branch -M main
git push -u origin main
```

### Passo a passo — fluxo de feature com PR (exercício da Aula 01)
1. `git pull origin main` (base atualizada)
2. `git checkout -b joao`
3. edita o arquivo
4. `git add` + `git commit -m "..."`
5. `git push origin joao`
6. abre **Pull Request** joao → main no GitHub
7. responsável faz o **merge**
8. todos: `git checkout main` + `git pull origin main`

---
## 2. Docker

### Dockerfile Java (Aula 02)
```dockerfile
FROM eclipse-temurin:21-jdk-jammy     # imagem base com Java
WORKDIR /app                          # pasta de trabalho
COPY App.jar /app/App.jar             # copia o JAR
ENTRYPOINT ["java", "-jar", "App.jar"]# comando ao iniciar
```
`Manifest.txt`: `Main-Class: App`

```bash
javac -d bin src/*.java                    # compila
jar cfm App.jar Manifest.txt -C bin .      # cria o JAR com manifesto
jar tf App.jar                             # confere conteúdo
docker build -t app-java-simples .         # constrói a IMAGEM (o "." = contexto)
docker run --name app-java-simples app-java-simples   # cria e roda o CONTAINER
docker start -a app-java-simples           # próximas execuções
```

### Dockerfile Node multi-stage (Aula 03)
```dockerfile
# Estágio 1: Build
FROM node:22-alpine AS builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci --omit=dev          # só dependências de produção
COPY . .
# Estágio 2: Produção
FROM node:22-alpine
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/node_modules ./node_modules
COPY --from=builder /usr/src/app ./
EXPOSE 3000
CMD [ "node", "server.js" ]
```
`.dockerignore`: `node_modules`, `npm-debug.log`, `.git`, `.gitignore`

```bash
docker build -t ola-devops .
docker run -p 3000:3000 -d ola-devops    # -p host:container, -d = em segundo plano
```

### Tabela de instruções
| Instrução | Faz |
|---|---|
| `FROM` | imagem base |
| `WORKDIR` | pasta de trabalho dentro da imagem |
| `COPY` | copia arquivos para a imagem |
| `RUN` | executa comando **durante o build** |
| `EXPOSE` | documenta a porta |
| `CMD` / `ENTRYPOINT` | comando executado **quando o container inicia** |
- **Pegadinha:** `RUN` = na construção da imagem; `CMD` = na execução do container.

---
## 3. App Node + teste (Aula 03)
```js
// app.js
const express = require("express");
const app = express();
app.get("/", (req, res) => { res.status(200).send("Olá Mundo DevOps!"); });
module.exports = app;

// server.js
const app = require("./app");
const port = process.env.PORT || 3000;
app.listen(port, () => console.log(`Servidor rodando na porta ${port}`));

// app.test.js (Jest + Supertest)
const request = require("supertest");
const app = require("./app");
describe("API Olá Mundo", () => {
  it('Deve retornar "Olá Mundo DevOps!" na rota /', async () => {
    const response = await request(app).get("/");
    expect(response.statusCode).toBe(200);
    expect(response.text).toBe("Olá Mundo DevOps!");
  });
});
```
```bash
npm init -y
npm install express --save
npm install jest -D
npm install supertest -D
# package.json: "scripts": { "start": "node server.js", "test": "jest" }
npm test      # PASS
npm start     # http://localhost:3000
```
**Pegadinha:** se mudar a mensagem só no `app.js`, o **teste falha** e o pipeline para — tem que mudar no `app.test.js` também (exercício da Aula 05).

---
## 4. Pipeline completo (`.github/workflows/ci.yml`) — montado a partir das Aulas 03-06
```yaml
name: Pipeline de CI - Olá Mundo DevOps
on:
  push:
    branches: ["main"]
  pull_request:
    branches: ["main"]
jobs:
  test-and-build:                       # JOB 1
    runs-on: ubuntu-latest
    permissions:                        # (Aula 04; conteúdo exato = complemento)
      contents: read
      packages: write
    steps:
      - name: Checkout do Código
        uses: actions/checkout@v4
      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with: { node-version: "22", cache: "npm" }
      - name: Instalar Dependências
        run: npm install
      - name: Rodar Testes
        run: npm test
      - name: Verificar vulnerabilidades de dependências (SCA)   # Aula 06
        run: npm audit --audit-level=high
      - name: Configurar Docker Buildx
        uses: docker/setup-buildx-action@v3
      - name: Logar no GitHub Container Registry                 # Aula 04
        if: github.event_name == 'push' && github.ref == 'refs/heads/main'
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      - name: Extrair Metadados do Docker
        if: github.event_name == 'push' && github.ref == 'refs/heads/main'
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ghcr.io/${{ github.repository }}
          tags: |
            type=sha
            latest
      - name: Build e Push da Imagem Docker
        uses: docker/build-push-action@v5
        with:
          context: .
          file: ./Dockerfile
          push: ${{ github.event_name == 'push' && github.ref == 'refs/heads/main' }}
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
      # Aula 06: dividir em Build → Trivy (scan) → Push (código no GitHub do professor)

  deploy-to-local:                      # JOB 2 (Aula 05)
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'
    needs: test-and-build
    runs-on: self-hosted
    steps:
      - name: Checkout do Código
        uses: actions/checkout@v4
      - name: Logar no GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      - name: Fazer Deploy com Docker Compose
        run: |
          docker-compose pull
          docker-compose up -d --no-build
          docker image prune -f
```

### docker-compose.yml (Aula 05)
```yaml
version: '3.8'
services:
  app:
    image: ghcr.io/SEU-USUARIO/SEU-REPO:latest
    ports:
      - "3000:3000"
    restart: always
    pull_policy: always
```

### Palavras-chave do YAML
| Chave | Significado |
|---|---|
| `on` | **gatilhos** (push, pull_request) |
| `jobs` | trabalhos do pipeline |
| `runs-on` | onde roda (`ubuntu-latest` = máquina do GitHub; `self-hosted` = sua máquina) |
| `steps` | passos em sequência |
| `uses` | usa uma Action pronta |
| `run` | executa comando de terminal |
| `with` | parâmetros da Action |
| `if` | condição para rodar o step/job |
| `needs` | depende de outro job ter **sucesso** |
| `secrets.GITHUB_TOKEN` | token automático do GitHub |

---
## TIPO DE EXERCÍCIO A — "O que acontece no PR e no merge?"
### Passo a passo
1. Veja o **evento**: PR (`pull_request`) ou merge (`push` na main).
2. Aplique os `if`: steps de login/push/deploy só rodam em **push na main**.
3. Veja `needs`: se Job 1 falhar, Job 2 não roda.
4. Veja as verificações de segurança: falha alta/crítica → para.

### Exemplo resolvido
| Situação | Resultado |
|---|---|
| Abro PR dev → main, testes passam | Job 1 roda: testes + audit + build. Login/push **skipped**. Job 2 **não roda**. PR fica **liberado** para merge (proteção de branch). |
| Faço o merge | Gera **push na main** → Job 1 roda de novo **com** login + push da imagem no GHCR → Job 2 roda no runner local → app atualizado em localhost:3000. |
| `npm audit` acha vulnerabilidade **crítica** | Job 1 falha → PR **bloqueado**; nada é publicado. |
| Trivy acha CRITICAL na imagem após merge | push para o GHCR **não acontece**; Job 2 **não roda**. |
| Mudo a mensagem só no `app.js` | `npm test` falha → pipeline para. |

## TIPO DE EXERCÍCIO B — Classificar a verificação de segurança
| Problema encontrado | Tipo |
|---|---|
| biblioteca `express` com CVE conhecida | **SCA** |
| concatenação de SQL no `app.js` (SQL Injection) | **SAST** |
| pacote vulnerável no sistema da imagem `node:22` | **Container scan** |
| senha/token no código enviado ao GitHub | **Secret/Push protection** |

## TIPO DE EXERCÍCIO C — "Em que situação isso é útil numa empresa?" (resposta-modelo)
- **Docker:** equipes com ambientes diferentes; subir a mesma versão em dev/homologação/produção; mudar de nuvem sem reconfigurar.
- **CI:** muitos devs mexendo no mesmo código; detectar bug em minutos; manter a main sempre estável.
- **CD:** lançar correções várias vezes ao dia sem deploy manual; reduzir erro humano no deploy.
- **DevSecOps:** empresas com dados sensíveis (bancos, saúde, LGPD); impedir que vulnerabilidade chegue à produção.
