# Guia de Contribuição – Byte Gourmet

Obrigado por contribuir com o **Livro de Receitas – Byte Gourmet**!

Este documento estabelece os padrões e procedimentos para colaboração, garantindo organização, rastreabilidade e qualidade nas alterações realizadas no repositório.

## 1. Regras Gerais

O projeto utiliza o **GitHub Flow** como fluxo de trabalho, com controle de mudanças por meio de Issues, branches e Pull Requests.

Todos os colaboradores devem seguir estas regras:

- Não realizar commits diretamente na branch `main`.
- Abrir uma Issue antes de iniciar uma alteração.
- Criar uma branch específica para cada tarefa.
- Utilizar commits semânticos.
- Abrir um Pull Request para integrar alterações.
- Participar das revisões dos colegas.
- Verificar o funcionamento dos links e a formatação Markdown.

**Regra obrigatória de governança:**

> Todo PR deve ter no mínimo 3 aprovações antes do merge na main.

## 2. Abertura de Issues

Toda contribuição deve começar com uma Issue no GitHub, descrevendo a alteração proposta.

### Padrão de títulos

| Tipo         | Exemplo                                        |
| ------------ | ---------------------------------------------- |
| Receita      | `[Receita] Pudim de Leite - Sobremesas`        |
| Correção     | `[Correção] Corrigir link da receita de pudim` |
| Documentação | `[Documentação] Atualizar README.md`           |
| Manutenção   | `[Manutenção] Remover arquivo duplicado`       |

### Modelo de Issue

```markdown
## Descrição

Descreva o que precisa ser realizado.

## Critérios de aceitação

- [ ] Requisito 1
- [ ] Requisito 2
- [ ] Requisito 3
```

Sempre que possível, atribua a Issue ao responsável pela implementação.

## 3. Padrão de Branches

Cada alteração deve ser desenvolvida em uma branch criada a partir da `main` atualizada.

### Convenções

| Prefixo    | Finalidade                            | Exemplo                             |
| ---------- | ------------------------------------- | ----------------------------------- |
| `feature/` | Adicionar receitas ou funcionalidades | `feature/sobremesas-pudim-de-leite` |
| `fix/`     | Corrigir erros existentes             | `fix/corrigir-link-menu`            |
| `docs/`    | Atualizar documentação                | `docs/atualizar-readme`             |
| `chore/`   | Realizar manutenção                   | `chore/remover-arquivo-duplicado`   |

**Para adicionar receitas, utilize obrigatoriamente:**

`feature/<categoria>-<nome-da-receita>`

Utilize letras minúsculas, sem espaços ou acentos, separando as palavras com hífens.

### Criando uma branch

```bash
git switch main
git pull origin main
git switch -c feature/sobremesas-pudim-de-leite
```

## 4. Padrão de Commits

As mensagens devem seguir a convenção **Conventional Commits**.

Formato:

`tipo: descrição objetiva da alteração`

### Tipos utilizados

| Tipo        | Finalidade                                 |
| ----------- | ------------------------------------------ |
| `feat:`     | Adição de conteúdo ou funcionalidade       |
| `fix:`      | Correção de erros                          |
| `docs:`     | Atualização de documentação                |
| `chore:`    | Manutenção e organização                   |
| `refactor:` | Reorganização sem mudança de comportamento |
| `test:`     | Adição ou alteração de testes              |

### Exemplos

```bash
git commit -m "feat: adicionar receita de pudim de leite"

git commit -m "docs: atualizar menu com link para pudim de leite"

git commit -m "fix: corrigir link da receita no menu"

git commit -m "chore: remover arquivo duplicado"
```

Prefira commits pequenos, objetivos e relacionados a uma única alteração.

## 5. Padrão das Receitas

Cada receita deve ser criada em um arquivo Markdown individual, dentro da pasta correspondente à sua categoria.

### Estrutura de diretórios

```text
├── README.md
├── CONTRIBUTING.md
├── menu.md
├── saladas/
├── carnes/
├── sopas/
├── massas/
└── sobremesas/
```

Os nomes dos arquivos devem utilizar letras minúsculas e hífens.

Exemplo: `sobremesas/pudim-de-leite.md`

### Estrutura obrigatória

```markdown
# Pudim de Leite

## Ingredientes

- 1 lata de leite condensado
- 1 lata de leite
- 3 ovos

## Modo de Preparo

1. Separe todos os ingredientes.
2. Misture os ingredientes.
3. Prepare conforme a receita.
4. Aguarde ficar pronto e sirva.

---

[Voltar à Categoria](.) | [Voltar ao Menu Principal](../menu.md)
```

### Regras de documentação

- Utilizar títulos e subtítulos Markdown.
- Organizar os ingredientes em listas.
- Numerar as etapas do modo de preparo.
- Adicionar os links de navegação.
- Atualizar o `menu.md` ao adicionar uma receita.
- Verificar se os links funcionam no GitHub.

## 6. Pull Requests

Após concluir as alterações, envie sua branch ao repositório remoto.

```bash
git push -u origin feature/sobremesas-pudim-de-leite
```

Abra um Pull Request no GitHub com:

- **Base:** `main`
- **Compare:** branch utilizada para desenvolver a alteração

### Modelo de Pull Request

```markdown
## O que foi feito

Descreva as alterações realizadas.

## Por quê

Explique o motivo da contribuição.

Closes #N

## Checklist

- [ ] Alterações relacionadas à Issue
- [ ] Arquivos Markdown formatados
- [ ] Links verificados
- [ ] Commits seguindo o padrão
- [ ] Revisores solicitados
```

Substitua `#N` pelo número da Issue correspondente.

A palavra-chave `Closes` permite o fechamento automático da Issue quando o PR é integrado à branch padrão.

## 7. Code Review

Todos os Pull Requests devem passar por revisão antes da integração.

### Regras obrigatórias

1. O autor solicita a revisão dos colegas.
2. Os revisores analisam as alterações na aba **Files changed**.
3. Os revisores verificam a formatação Markdown, os links e o cumprimento da Issue.
4. Correções necessárias devem ser solicitadas por comentários.
5. O autor realiza os ajustes na mesma branch e atualiza o PR.
6. O merge somente pode ocorrer após pelo menos **3 aprovações formais de integrantes diferentes**.

### Tipos de revisão

| Opção             | Significado           |
| ----------------- | --------------------- |
| `Comment`         | Registrar observações |
| `Request changes` | Solicitar correções   |
| `Approve`         | Aprovar formalmente   |

Comentários não substituem aprovações.

Após realizar correções solicitadas, o autor deve enviar novos commits para a mesma branch, responder às observações e solicitar uma nova revisão quando necessário.

## 8. Resolução de Conflitos

Conflitos podem acontecer quando dois colaboradores modificam o mesmo trecho de um arquivo, especialmente o `menu.md`.

Para atualizar a branch de trabalho:

```bash
git switch feature/sobremesas-pudim-de-leite
git fetch origin
git merge origin/main
```

Se houver conflitos:

1. Identifique os arquivos afetados utilizando `git status`.
2. Abra os arquivos e localize os marcadores de conflito.
3. Preserve as alterações corretas de todos os colaboradores.
4. Remova os marcadores de conflito.
5. Salve e valide o arquivo.
6. Registre a resolução com um commit.

```bash
git add menu.md
git commit -m "fix: resolver conflito no menu"
git push
```

Nunca envie arquivos contendo marcadores de conflito não resolvidos.

## 9. Merge e Limpeza

Após a conclusão das revisões e o registro das 3 aprovações obrigatórias, o Pull Request poderá ser integrado à `main`.

O merge deve ser realizado pelo GitHub, respeitando as regras de proteção da branch principal.

Após a integração:

1. Exclua a branch remota pelo GitHub.
2. Atualize a `main` local.
3. Exclua a branch local, após confirmar a integração.

```bash
git switch main
git pull origin main
git branch -d feature/sobremesas-pudim-de-leite
```

Caso a integração tenha sido realizada por _Squash and merge_, a exclusão local com `-d` poderá ser recusada. Depois de confirmar que o PR foi efetivamente integrado, utilize `git branch -D` se necessário.

## 10. Checklist Final de Contribuição

Antes de concluir um Pull Request, confirme:

- [ ] Issue criada e vinculada ao PR.
- [ ] Branch criada conforme a convenção.
- [ ] Commits semânticos e objetivos.
- [ ] Arquivos Markdown corretamente formatados.
- [ ] Links de navegação funcionando.
- [ ] `menu.md` atualizado, quando aplicável.
- [ ] Nenhum conflito pendente.
- [ ] Três aprovações formais registradas.
- [ ] Merge realizado na `main`.
- [ ] Branch remota removida após o merge.

---

**Equipe Byte Gourmet**

Projeto acadêmico da disciplina de Engenharia de Software 1 – Gerência de Configuração de Software.
