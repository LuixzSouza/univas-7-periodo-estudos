# Design Patterns — Códigos, diagramas e passo a passo

---
## Tabela de setas UML (decorar)
```
Dependência     A - - - - -> B     (usa temporariamente)
Associação      A ——————————> B    (conhece / tem campo)
Agregação       A ◇—————————> B    (contém; B vive sozinho)      ◇ do lado do TODO
Composição      A ◆—————————> B    (contém; B morre com A)        ◆ do lado do TODO
Implementação   A - - - - - -▷ B   (A implementa interface B)
Herança         A ———————————▷ B   (A é um B)
```

## Palavras-chave no texto → relação
| Frase no enunciado | Relação |
|---|---|
| "é um tipo de", "pode ser um" | **Herança** |
| "implementa", "interface com métodos" | **Implementação** |
| "parte essencial/integrante", "não existe fora de", "obrigatoriamente" | **Composição** |
| "pode existir sem", "vinculado a vários", "contém mas é independente" | **Agregação** |
| "possui um responsável", "matriculado", "conhece" | **Associação** |
| "utiliza temporariamente", "usa durante", "recebe como parâmetro" | **Dependência** |

---
## TIPO 1 — Texto → relações → diagrama UML

### Passo a passo
1. Sublinhe os **substantivos** = classes.
2. Para cada par, ache a **frase-chave** (tabela acima).
3. Decida o **lado** do losango (todo) e da seta.
4. Marque **interfaces** com `«interface»` e classes abstratas em itálico.
5. Desenhe.

### Exemplo resolvido — Exercício 1 (Clínica)
| Par | Relação | Por quê |
|---|---|---|
| Paciente → Pessoa | **Herança** | "Pessoa pode ser um Paciente" |
| Médico → Pessoa | **Herança** | idem |
| Paciente ◆ Endereço | **Composição** | "obrigatoriamente", "parte essencial" |
| Clínica ◇ Médico (ou Médico ◇ Clínica) | **Agregação** | "clínica pode existir sem o médico e vice-versa" |
| Médico → Atendimento | **Associação** | "Médico pode realizar atendimentos" |
| Secretaria → Consulta | **Associação** | "agenda Consultas" |
| Consulta → Paciente, Médico | **Associação** | consulta é entre paciente e médico |
| Secretaria - -> Paciente, Médico | **Dependência** | "utiliza **temporariamente**" |
```
            Pessoa
           ▲      ▲
   Paciente        Médico ——> Atendimento
   ◆                ▲ ◇
   ↓                │ └——> Clínica (agregação)
 Endereço           │
Secretaria ——> Consulta ——> Paciente / Médico
Secretaria - - -> Paciente ; Secretaria - - -> Médico
```

### Exemplo resolvido — Exercício 2 (Cursos)
| Par | Relação |
|---|---|
| Professor ——▷ Pessoa ; Aluno ——▷ Pessoa | Herança |
| Pessoa ◆ Endereço | Composição ("parte integrante") |
| ConteudoProgramatico ◆ Modulo | Composição ("não podem existir fora") |
| Curso ◆ ConteudoProgramatico | Composição (complemento: conteúdo pertence ao curso; aceitável também associação) |
| Curso ——> Professor | Associação ("professor responsável") |
| Curso ◇ Aluno | Agregação ("vários alunos matriculados"; aluno existe sem o curso) |
| Aluno - - -▷ UsuarioSistema ; Professor - - -▷ UsuarioSistema | Implementação (`fazerLogin()`, `visualizarPerfil()`) |

---
## TIPO 2 — Implementar Singleton (Java)

### Passo a passo
1. `private static Classe instancia;`
2. Construtor **`private`**.
3. `public static Classe getInstancia()` → se `null`, cria; retorna.
4. Getters/setters e métodos de negócio.
5. No `main`, pegue 2 referências e mostre `ref1 == ref2` → `true`.

### Implementação clássica (slide)
```java
public class Configuracao {
    private static Configuracao instancia;                 // guarda a instância única
    private String urlBanco = "jdbc:mysql://localhost:3306/minhaBase";
    private Configuracao() {}                              // construtor privado
    public static Configuracao getInstancia() {            // lazy initialization
        if (instancia == null) {
            instancia = new Configuracao();
        }
        return instancia;
    }
    public void exibirConfiguracao() { System.out.println("URL do banco: " + urlBanco); }
    public String getUrlBanco() { return urlBanco; }
    public void setUrlBanco(String urlBanco) { this.urlBanco = urlBanco; }
}
// Main
Configuracao config1 = Configuracao.getInstancia();
Configuracao config2 = Configuracao.getInstancia();
config1.setUrlBanco("jdbc:mysql://localhost:3306/outraBase");
config2.exibirConfiguracao();              // mostra outraBase
System.out.println(config1 == config2);    // true
```

### Implementação com enum (slide)
```java
public enum ConfiguracaoEnum {
    INSTANCIA;
    private String urlBanco = "jdbc:mysql://localhost:3306/minhaBase";
    public void exibirConfiguracao() { System.out.println("URL do banco: " + urlBanco); }
    public String getUrlBanco() { return urlBanco; }
    public void setUrlBanco(String urlBanco) { this.urlBanco = urlBanco; }
}
// uso: ConfiguracaoEnum config = ConfiguracaoEnum.INSTANCIA;
```

### Exemplo resolvido — Exercício 2 (contador global com enum)
```java
public enum Contador {
    INSTANCIA;
    private int valor = 0;
    public void incrementar() { valor++; }
    public void decrementar() { valor--; }
    public void exibir() { System.out.println("Contador: " + valor); }
}
public class MainContador {
    public static void main(String[] args) {
        Contador a = Contador.INSTANCIA;
        Contador b = Contador.INSTANCIA;
        a.incrementar(); a.incrementar(); b.decrementar();
        b.exibir();                     // Contador: 1
        System.out.println(a == b);     // true → mesma instância
    }
}
```
**Pegadinha (complemento):** a versão clássica **não é thread-safe**. Soluções: `synchronized` no `getInstancia()` ou usar **enum**.

---
## TIPO 3 — Implementar Factory Method (Java)

### Passo a passo (receita dos slides)
1. **Interface do produto** com o método comum.
2. **Produtos concretos** implementam a interface.
3. **Criador abstrato** com `protected abstract Produto criarX();` + método de **lógica comum** que chama `criarX()`.
4. **Criadores concretos** (`extends`) sobrescrevem `criarX()` retornando `new ProdutoConcreto()`.
5. **Main** escolhe o criador (ex.: por `args[0]`) e chama a lógica comum.

### Exemplo resolvido — Exercício de Pagamento (código real da aula)
```java
interface Pagamento { void processar(double valor); }

class Cartao implements Pagamento {
    public void processar(double valor) { System.out.println("[Cartão] Processando pagamento de R$ " + valor); }
}
class Boleto implements Pagamento {
    public void processar(double valor) { System.out.println("[Boleto] Gerando boleto de R$ " + valor); }
}
class Pix implements Pagamento {
    public void processar(double valor) { System.out.println("[Pix] Pagamento instantâneo de R$ " + valor); }
}

abstract class ProcessadorPagamento {
    protected abstract Pagamento criarPagamento();          // Factory Method
    public void realizarPagamento(double valor) {           // lógica comum
        System.out.println(">> Iniciando processamento...");
        Pagamento p = criarPagamento();
        p.processar(valor);
        System.out.println(">> Pagamento concluído.\n");
    }
}
class ProcessadorCartao extends ProcessadorPagamento { protected Pagamento criarPagamento() { return new Cartao(); } }
class ProcessadorBoleto extends ProcessadorPagamento { protected Pagamento criarPagamento() { return new Boleto(); } }
class ProcessadorPix    extends ProcessadorPagamento { protected Pagamento criarPagamento() { return new Pix(); } }

public class MainPagamento {
    public static void main(String[] args) {
        ProcessadorPagamento escolhida = escolherPagamentoPorArg(args);
        escolhida.realizarPagamento(150.0);
    }
    private static ProcessadorPagamento escolherPagamentoPorArg(String[] args) {
        if (args != null && args.length > 0) {
            String tipo = args[0].toLowerCase();
            if (tipo.startsWith("cartao")) return new ProcessadorCartao();
            if (tipo.startsWith("boleto")) return new ProcessadorBoleto();
            if (tipo.startsWith("pix"))    return new ProcessadorPix();
        }
        return new ProcessadorCartao();   // padrão
    }
}
```
Saída com `java MainPagamento pix`:
```
>> Iniciando processamento...
[Pix] Pagamento instantâneo de R$ 150.0
>> Pagamento concluído.
```

### Exemplo resolvido — Atividade em sala 1 (Notificações)
```java
interface Notificacao { void enviar(String mensagem); }
class Email implements Notificacao { public void enviar(String m) { System.out.println("[Email] " + m); } }
class SMS   implements Notificacao { public void enviar(String m) { System.out.println("[SMS] " + m); } }
class Push  implements Notificacao { public void enviar(String m) { System.out.println("[Push] " + m); } }

abstract class ServicoNotificacao {
    protected abstract Notificacao criarNotificacao();
    public void notificar(String mensagem) {
        Notificacao n = criarNotificacao();
        n.enviar(mensagem);
    }
}
class ServicoEmail extends ServicoNotificacao { protected Notificacao criarNotificacao() { return new Email(); } }
class ServicoSMS   extends ServicoNotificacao { protected Notificacao criarNotificacao() { return new SMS(); } }
class ServicoPush  extends ServicoNotificacao { protected Notificacao criarNotificacao() { return new Push(); } }

public class MainNotificacao {
    public static void main(String[] args) {
        String canal = args.length > 0 ? args[0].toLowerCase() : "email";
        ServicoNotificacao s = switch (canal) {
            case "sms"  -> new ServicoSMS();
            case "push" -> new ServicoPush();
            default     -> new ServicoEmail();
        };
        s.notificar("Sua consulta é amanhã");
    }
}
```
**Atividade 2 (Relatórios)** é idêntica trocando os nomes: `Relatorio.gerar(conteudo)` → `RelatorioPDF/Excel/HTML`; criador `GeradorRelatorio` com `criarRelatorio()` e `processarRelatorio(conteudo)`.

### Diagrama genérico do Factory Method
```
        «abstract» Criador                     «interface» Produto
   + operacaoComum()  ──usa──>                  + metodo()
   # criarProduto(): Produto  (abstrato)            ▲       ▲
        ▲             ▲                          ProdutoA  ProdutoB
  CriadorA          CriadorB
  criarProduto()    criarProduto()
  → new ProdutoA()  → new ProdutoB()
```
