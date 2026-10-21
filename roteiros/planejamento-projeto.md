# Roteiro: Planejamento do Projeto — Requisitos, Sprints e Telas

Neste roteiro, cada equipe vai consolidar o **planejamento do sistema** que está sendo desenvolvido ao longo do semestre. A ideia é sair da aula com três documentos essenciais prontos: requisitos, organização das sprints e telas.

Todos os documentos devem ficar **dentro do repositório do projeto**, em Markdown, e cada entrega é registrada por meio de uma **issue** contendo o link para o arquivo.


## Entrega 1 — Requisitos (`docs/requisitos.md`)

O documento de requisitos é a base de tudo o que vem depois. Ele deve responder: **o que** o sistema faz e **para quem**.

### Conteúdo obrigatório

1. **Visão do produto** (1 parágrafo): qual problema o sistema resolve, para quem, e o que o diferencia.
2. **Público-alvo e papéis**: quem são os usuários (ex.: aluno, bibliotecário, administrador).
3. **Histórias de usuário** no formato:

   > Como *[papel]*, eu quero *[ação]* para *[benefício]*.

   Cada história deve ter um identificador (`H01`, `H02`, ...) e **critérios de aceitação** (condições objetivas para considerar a história pronta).
4. **Priorização de requisitos**: classifique cada história em um dos níveis abaixo.
   * **Essencial** — sem isso o sistema não faz sentido.
   * **Importante** — agrega muito valor, mas o sistema funciona sem.
   * **Desejável** — será feito se sobrar tempo.
   * **Fora do escopo** — não será feito neste semestre (registre explicitamente!).
5. **Requisitos não funcionais**: desempenho, segurança, usabilidade, compatibilidade, etc. Pelo menos 3.

### Quantidade mínima

* **8 histórias de usuário**, sendo pelo menos 4 classificadas como *essenciais*.
* Toda história *essencial* deve ter pelo menos **2 critérios de aceitação**.

### Modelo

```markdown
# Requisitos — <Nome do Sistema>

## 1. Visão do Produto
<parágrafo>

## 2. Papéis de Usuário
| Papel | Descrição |
|-------|-----------|
| Aluno | ... |

## 3. Histórias de Usuário

### H01 — Pesquisar livros (Essencial)
**Como** aluno, **eu quero** pesquisar livros por título ou autor **para** encontrar rapidamente o que preciso.

**Critérios de aceitação:**
- [ ] A busca retorna resultados contendo o termo no título ou no autor.
- [ ] Caso não haja resultados, uma mensagem informativa é exibida.

### H02 — ...

## 4. Priorização de Requisitos
| Prioridade | Histórias |
|------------|-----------|
| Essencial | H01, H02, H03, H04 |
| Importante | H05, H06 |
| Desejável | H07 |
| Fora do escopo | H08 |

## 5. Requisitos Não Funcionais
| ID | Requisito |
|----|-----------|
| RNF01 | O sistema deve responder às buscas em menos de 2 segundos. |
```

---

## Entrega 2 — Planejamento das Sprints (`docs/sprints.md`)

Com os requisitos priorizados, a equipe distribui o trabalho no tempo restante do semestre.

### Conteúdo obrigatório

1. **Calendário das sprints**: duração (sugestão: 2 semanas), datas de início e fim de cada sprint até o final do semestre, e data da apresentação final.
2. **Objetivo de cada sprint** (*sprint goal*): uma frase que resume o que estará funcionando ao final dela.
3. **Backlog da Sprint 1**: quais histórias e tarefas entram na primeira sprint. Para as demais, basta o objetivo: elas serão planejadas em detalhe quando começarem. As histórias *essenciais* devem ficar nas primeiras sprints.
4. **Milestones no GitHub**: cada sprint deve existir como um *milestone* no repositório do projeto, e o documento deve conter o **link** para cada um deles. Todas as issues de uma sprint ficam vinculadas ao milestone correspondente.

### Criando os milestones no GitHub

Um *milestone* agrupa issues que têm uma mesma data de entrega. No projeto, cada sprint será um milestone.

1. No repositório, abra a aba **Issues** e clique em **Milestones** (ao lado do botão de criar label).
2. Clique em **New milestone** e preencha:
   * **Title:** `Sprint 1` (use sempre esse padrão: `Sprint 2`, `Sprint 3`, ...).
   * **Due date:** a data de término da sprint.
   * **Description:** o objetivo da sprint (*sprint goal*).
3. Clique em **Create milestone**. Repita para todas as sprints do calendário.
4. Copie o endereço de cada milestone criado. Ele tem o formato `https://github.com/<usuario-ou-org>/<repositorio>/milestone/<numero>` e é esse link que vai no `sprints.md`.
5. Para vincular uma issue a um milestone, abra a issue e, na barra lateral direita, escolha o milestone em **Milestone**. Também é possível fazer isso em lote na lista de issues: selecione várias e use o menu **Milestone**.

A página de cada milestone mostra uma **barra de progresso** (issues fechadas / total) e a lista de issues abertas e fechadas. Esse será o principal indicador de andamento da sprint nas revisões em aula.

> **Dica:** na lista de issues, o filtro `milestone:"Sprint 1"` mostra apenas as tarefas daquela sprint. No Kanban (GitHub Projects), é possível agrupar ou filtrar os cards por milestone, o que ajuda a visualizar a sprint atual.

### Regras

* A **Sprint 1** já deve estar detalhada em **tarefas** (não apenas histórias), e cada tarefa deve existir como issue no Kanban, vinculada à história correspondente e ao milestone `Sprint 1`.
* **Nenhuma issue de tarefa fica sem milestone.** Issue sem milestone é trabalho que não foi planejado.
* O milestone é **fechado na revisão da sprint**. Issues não concluídas são movidas para o milestone seguinte, e o motivo é registrado na retrospectiva.
* A última sprint deve reservar tempo para testes, correções e preparação da apresentação. Evite planejar funcionalidades novas para ela.
* Estime a capacidade da equipe com honestidade: horas por integrante por semana × número de integrantes.

### Modelo

```markdown
# Planejamento das Sprints — <Nome do Sistema>

## 1. Equipe e Papéis
| Integrante | Papel na Sprint 1 |
|------------|-------------------|
| ... | Product Owner |
| ... | Scrum Master |
| ... | Desenvolvedor(a) |

## 2. Calendário e Milestones
| Sprint | Início | Fim | Objetivo | Milestone |
|--------|--------|-----|----------|-----------|
| 1 | 22/10/2026 | 04/11/2026 | Usuário consegue se cadastrar e pesquisar livros | [Sprint 1](https://github.com/equipe/projeto/milestone/1) |
| 2 | 05/11/2026 | 18/11/2026 | ... | [Sprint 2](https://github.com/equipe/projeto/milestone/2) |
| 3 | 19/11/2026 | 02/12/2026 | ... | [Sprint 3](https://github.com/equipe/projeto/milestone/3) |
| 4 | 03/12/2026 | 16/12/2026 | Testes, correções e apresentação | [Sprint 4](https://github.com/equipe/projeto/milestone/4) |

Todos os milestones: <https://github.com/equipe/projeto/milestones>

## 3. Backlog por Sprint
### Sprint 1 — [milestone](https://github.com/equipe/projeto/milestone/1)
| História | Tarefas | Responsável | Issue |
|----------|---------|-------------|-------|
| H01 | Criar modelo Livro | ... | #3 |
| H01 | Implementar endpoint de busca | ... | #4 |
| H01 | Criar tela de busca | ... | #5 |

### Sprints seguintes
As Sprints 2, 3 e 4 têm apenas o objetivo definido na tabela acima. O backlog de cada uma será detalhado no planejamento da própria sprint, e esta seção será atualizada nesse momento.

---

## Entrega 3 — Telas (`docs/interfaces.md`)

O documento de telas é uma **lista descritiva** das telas do sistema. Ele é criado hoje e **atualizado a cada entrega de sprint**: conforme as telas forem implementadas, a equipe adiciona os *prints* (capturas de tela) do sistema em funcionamento.

### Conteúdo obrigatório

Para cada tela prevista, informe:

* **Nome** da tela (ex.: `T01 — Busca de Livros`).
* **Histórias atendidas** (ex.: H01, H03).
* **Descrição**: o que o usuário vê e o que pode fazer nessa tela (campos, botões, listas, navegação para outras telas).
* **Sprint** em que a tela está prevista.
* **Print** da tela implementada, adicionado na entrega da sprint em que ela foi concluída.

Hoje, as telas ainda não existem, então a entrega conterá apenas nome, histórias, descrição e sprint. Toda tela associada a uma história *essencial* deve estar listada.

Quem já tiver **wireframes** ou protótipos (papel, Excalidraw, Figma) pode incluí-los junto à descrição. Isso é opcional.

### Prints a cada sprint

Na entrega de cada sprint, a equipe atualiza o `docs/interfaces.md`:

1. Tire um print de cada tela concluída na sprint, com o sistema rodando.
2. Salve as imagens em `docs/img/` com o nome da tela (ex.: `t01-busca.png`).
3. Adicione a imagem abaixo da descrição da tela correspondente.
4. Se a tela mudou em relação ao planejado, atualize a descrição.

### Modelo

```markdown
# Telas — <Nome do Sistema>

| Tela | Histórias | Sprint | Status |
|------|-----------|--------|--------|
| T01 — Busca de Livros | H01 | 1 | prevista |
| T02 — Detalhe do Livro | H01, H02 | 1 | prevista |
| T03 — Meus Empréstimos | H04 | 2 | prevista |

## T01 — Busca de Livros
**Histórias:** H01 · **Sprint:** 1

Tela inicial após o login. Possui um campo de busca por título ou autor e uma lista de resultados com capa, título e autor. Clicar em um resultado abre a tela T02. Se não houver resultados, exibe a mensagem "Nenhum livro encontrado".

<!-- Adicionar na entrega da Sprint 1 -->
![Print da tela de busca](img/t01-busca.png)

## T02 — Detalhe do Livro
**Histórias:** H01, H02 · **Sprint:** 1

...
```

## Leituras Complementares

* *Engenharia de Software Moderna*, Marco Tulio Valente — Cap. 2 (Processos: Scrum, Kanban), Cap. 3 (Requisitos: histórias de usuário) e Cap. 7 (Arquitetura). Disponível em <https://engsoftmoderna.info/>.
* *User Story Mapping*, Jeff Patton — sobre como organizar histórias em um mapa de produto.
* *Software Requirements*, Karl Wiegers e Joy Beatty, 3ª ed., Microsoft Press, 2013 — Cap. 16 (priorização de requisitos).
* Guia do Scrum (versão em português): <https://scrumguides.org/>.
* Documentação do GitHub Projects (Kanban): <https://docs.github.com/pt/issues/planning-and-tracking-with-projects>.
* Documentação do GitHub sobre milestones: <https://docs.github.com/pt/issues/using-labels-and-milestones-to-track-work/about-milestones>.