# Qualidade e Métricas de Software

## Coesão

A função abaixo possui um problema de coesão, isto é, ele implementa mais de uma funcionalidade. Como você resolveria este problema?

```java
float sin_or_cos(double x, int op) {
  if (op == 1)
    "calcula e retorna seno de x"
  else
    "calcula e retorna cosseno de x"
}
```

## LCOM

Considere a seguinte classe Java:

```java
class ContaBancaria {

  private double saldo;
  private double limite;
  private String titular;

  public void depositar(double valor) {
    saldo += valor;
  }

  public void sacar(double valor) {
    saldo -= valor;
  }

  public void atualizarLimite(double novoLimite) {
    limite = novoLimite;
  }

  public void imprimirTitular() {
    System.out.println(titular);
  }

}
```
### Tarefa:

* Liste todos os pares de métodos da classe, formando o conjunto M(C).
* Para cada método, determine o conjunto de atributos acessados (A(f)).
* Para cada par de métodos (f₁, f₂), calcule a interseção entre A(f₁) e A(f₂).
* Identifique quais pares de métodos não compartilham atributos em comum (interseção vazia).
* Calcule o valor de LCOM da classe.

## Acoplamento

## Exercício — Cálculo de CBO (Coupling Between Objects)

Considere a seguinte classe Java:

```java
class PedidoService extends RepositorioBase implements Logavel {

  Cliente cliente;

  Pagamento processarPedido(Produto produto) throws FalhaPagamentoException {
    NotaFiscal nota;
    ...
  }

  void registrarLog() {
    Logger logger = new Logger();
    try {
      ...
    }
    catch (ErroLogException e) { ... }
  }

}
```

### Tarefas

1. Identifique todas as classes das quais PedidoService depende.

2. Para cada dependência, indique por qual motivo ela ocorre, considerando os critérios:
* chamada de método
* acesso a atributo
* herança
* declaração de variável, parâmetro ou retorno
* exceções (lançadas ou capturadas)
* criação de objetos
* Liste todas as dependências identificadas (sem repetir classes).
* Calcule o valor de CBO(PedidoService).