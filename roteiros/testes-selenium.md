# Roteiro: Testes Automatizados com Selenium IDE

Neste roteiro vamos aprender a criar testes automatizados de interface (também chamados de testes *end-to-end*) usando o **Selenium IDE**, uma ferramenta gratuita que funciona como uma extensão do navegador Firefox (também disponível para Chrome).

A grande vantagem do Selenium IDE é que ele permite **gravar** as interações do usuário (cliques, digitação, navegação) e **reproduzir** essas ações automaticamente, sem que você precise escrever código. É uma excelente porta de entrada para o universo dos testes automatizados.

---

## Objetivos de Aprendizagem

Ao final deste roteiro, você deve ser capaz de:

* Instalar e configurar o Selenium IDE no Firefox.
* Gravar um teste automatizado a partir de interações reais com um site.
* Adicionar asserções (verificações) ao teste.
* Executar, salvar e organizar casos de teste em uma *suíte*.
* Compreender a diferença entre testes manuais e testes automatizados.

---

## Pré-requisitos

* Navegador **Mozilla Firefox** instalado (versão recente).
* Conexão com a internet.
* Conhecimento básico de HTML (saber o que é um campo de formulário, um botão, um link).

---

## Passo 1 — Instalação do Selenium IDE no Firefox

1. Abra o Firefox.
2. Acesse a página oficial de extensões: <https://addons.mozilla.org/firefox/addon/selenium-ide/>
3. Clique em **"Adicionar ao Firefox"** e confirme a instalação.
4. Após a instalação, um pequeno ícone do Selenium (em vermelho, com a letra "Se") aparecerá na barra de ferramentas do Firefox, no canto superior direito.
5. Clique no ícone para abrir o Selenium IDE em uma nova janela.

> **Dica:** se o ícone não aparecer, vá em `Menu → Extensões e Temas → Extensões` e verifique se o Selenium IDE está habilitado.

---

## Passo 2 — Conhecendo a Interface

Ao abrir o Selenium IDE pela primeira vez, você verá uma janela de boas-vindas com algumas opções. Escolha **"Create a new project"** e dê um nome ao projeto, por exemplo: `testes-aula-es`.

A interface principal possui os seguintes elementos:

* **Barra de URL base**: define qual o site que será testado.
* **Painel de testes**: lista os casos de teste do projeto.
* **Tabela de comandos**: cada linha representa uma ação (`Command`, `Target`, `Value`).
* **Botões de controle**: gravar (ícone vermelho), executar todos, executar um, pausar, etc.

---

## Passo 3 — Escolhendo um Site para Testar

Para esta atividade, sugerimos o seguinte site de demonstração, criado especificamente para a prática de testes automatizados:

**🔗 <https://the-internet.herokuapp.com/>**

Esse site oferece diversas páginas simples e estáveis para exercitar testes: formulários, login, *checkboxes*, *dropdowns*, mensagens dinâmicas, entre outros. É ideal para iniciantes porque os elementos da página possuem identificadores bem definidos (`id`, `name`, `class`), o que facilita a gravação.

Outras opções, caso queira explorar:

* <https://www.saucedemo.com/> — loja virtual fictícia com usuários de teste já cadastrados.
* <https://demoqa.com/> — coleção de componentes web variados.

> **Importante:** evite testar sites reais (Google, Facebook, lojas comerciais). Eles possuem mecanismos antibot e mudam frequentemente, o que quebra os testes.

---

## Passo 4 — Gravando o Primeiro Teste (Login Válido)

Vamos automatizar um teste de login bem-sucedido na página <https://the-internet.herokuapp.com/login>.

Credenciais válidas (informadas pelo próprio site):

* **Usuário:** `tomsmith`
* **Senha:** `SuperSecretPassword!`

### Procedimento

1. No Selenium IDE, defina a **Base URL** como `https://the-internet.herokuapp.com`.
2. Clique no botão vermelho **"Start recording"** (canto superior direito).
3. Uma nova aba do Firefox será aberta. Navegue até `/login`.
4. Preencha o campo **Username** com `tomsmith`.
5. Preencha o campo **Password** com `SuperSecretPassword!`.
6. Clique no botão **Login**.
7. Aguarde a página de sucesso carregar.
8. Volte ao Selenium IDE e clique em **"Stop recording"** (mesmo botão vermelho).
9. Dê um nome ao teste: `login-valido`.

Você verá que o Selenium gravou automaticamente comandos como `open`, `type`, `click`. Cada linha é uma instrução que será reproduzida na execução.

### Conferindo os comandos gerados

Ao gravar, o Selenium IDE às vezes escolhe um *locator* (campo **Target**) frágil — por exemplo um `xpath` ou `css` longo — e o comando `type` acaba **falhando na execução** com erro do tipo *"element not found"* ou digitando no campo errado.

Para garantir que o teste funcione de forma estável, **confira (e, se necessário, corrija) os Targets** para usar os `id` dos campos. A tabela de comandos do teste `login-valido` deve ficar assim:

| # | Command | Target | Value |
|---|---------|--------|-------|
| 1 | `open` | `/login` | |
| 2 | `type` | `id=username` | `tomsmith` |
| 3 | `type` | `id=password` | `SuperSecretPassword!` |
| 4 | `click` | `css=button[type="submit"]` | |

> **Por que `id=`?** Os campos da página possuem `id="username"` e `id="password"`, que são identificadores estáveis. Já o botão **Login** tem o texto dentro de um ícone (`<i>`), o que faz a gravação registrar um *xpath* esquisito — por isso preferimos `css=button[type="submit"]`.

> **Dica:** para editar um Target, clique na linha do comando; o campo **Target** aparece na parte inferior do Selenium IDE e pode ser digitado manualmente. O botão "Select target in page" (ícone de alvo) também ajuda a escolher um locator melhor.

---

## Passo 5 — Adicionando uma Asserção

Gravar cliques não é suficiente: precisamos **verificar** se o resultado esperado realmente aconteceu. Para isso, usamos *asserções*.

### Procedimento

1. Após o login, vá até a página de sucesso (`/secure`).
2. Localize o texto **"You logged into a secure area!"** na tela.
3. Clique com o botão direito sobre esse texto.
4. No menu de contexto, escolha **Selenium IDE → `assert text`**.
5. Volte ao Selenium IDE: uma nova linha terá sido adicionada, com o comando `assert text` e o texto esperado.

Agora o teste não apenas executa as ações, mas também **valida** se o login funcionou corretamente.

---

## Passo 6 — Executando o Teste

1. Salve o projeto (`Ctrl + S`) em um arquivo `.side` em algum local conhecido.
2. Antes de executar, faça **logout** ou feche a aba do navegador para garantir um estado limpo.
3. No Selenium IDE, clique no botão **"Run current test"** (ícone de *play* simples).
4. Observe: o Firefox executará automaticamente todas as ações que você gravou.
5. Ao final, verifique o resultado no painel inferior:
   * ✅ Verde = teste passou.
   * ❌ Vermelho = teste falhou (veja a mensagem de erro para descobrir o motivo).

---

## Passo 7 — Criando um Segundo Teste (Login Inválido)

Bons conjuntos de teste cobrem tanto o **caminho feliz** quanto os **casos de erro**.

### Tarefa

Crie um novo caso de teste chamado `login-invalido` que:

1. Abra a página `/login`.
2. Preencha o campo de usuário com `usuario_errado`.
3. Preencha a senha com `123`.
4. Clique em **Login**.
5. Adicione uma asserção verificando que a mensagem **"Your username is invalid!"** aparece na tela.

---

## Passo 8 — Organizando em uma Suíte de Testes

Uma **suíte** agrupa vários casos de teste relacionados. No painel à esquerda, mude a aba de **Tests** para **Test Suites**.

1. Crie uma nova suíte chamada `autenticacao`.
2. Adicione os dois testes (`login-valido` e `login-invalido`) à suíte.
3. Clique em **"Run all tests"** para executar a suíte inteira.

---

## Passo 9 — Desafio Final

Escolha outra página do site <https://the-internet.herokuapp.com/> e crie pelo menos **dois testes adicionais**. Sugestões:

* **Checkboxes** (`/checkboxes`): marcar e desmarcar caixas, verificando o estado.
* **Dropdown** (`/dropdown`): selecionar uma opção e verificar o valor escolhido.
* **Add/Remove Elements** (`/add_remove_elements/`): adicionar elementos dinamicamente e verificar a quantidade.
* **Form Authentication** (já feito, mas pode ser estendido com logout).

Cada teste deve conter, no mínimo:

* Pelo menos **uma ação de interação** (clique, digitação, seleção).
* Pelo menos **uma asserção** validando o resultado.

---

## Entrega

Ao final da atividade, entregue:

1. O arquivo `.side` exportado do Selenium IDE com a suíte completa.
2. Um pequeno relatório (1 página) contendo:
   * Quais páginas/funcionalidades foram testadas.
   * Quantos testes foram criados.
   * Quais asserções foram utilizadas.
   * Uma reflexão: *Em quais situações esse tipo de teste é útil? Quais limitações você percebeu?*

---

## Para Refletir

* Por que testes automatizados de interface costumam ser considerados **frágeis**? O que acontece se o desenvolvedor mudar o nome de um botão?
* Por que esses testes são, em geral, mais **lentos** do que testes unitários?
* Em uma pirâmide de testes (unitários → integração → interface), por que os testes de interface ficam no **topo**, em menor quantidade?

---

## Leituras Complementares

* Documentação oficial: <https://www.selenium.dev/selenium-ide/>
* Capítulo sobre testes do livro *Engenharia de Software Moderna*, de Marco Tulio Valente.
