# Plugins da IDVL para o Claude Code

A "loja" de plugins da IDVL: ferramentas que você instala **uma vez** no Claude Code e que passam a valer em **todos** os seus projetos.

| Plugin | O que faz |
|---|---|
| [**Guia vivo**](plugins/guia-vivo/README.md) | Painel ao lado da conversa com o método dos 5 passos, o tamanho da tarefa, o progresso da especificação, um checklist do projeto e dicas no momento certo. Também bloqueia tentativas do Claude de ler arquivos de senhas, chaves e certificados. |

> Para começar um projeto novo já com tudo configurado, use o **[projeto modelo](https://github.com/Escribaup/projeto-modelo)**. Os projetos criados a partir dele já ativam o Guia vivo sozinhos.

---

## Instalar o Guia vivo

Este repositório é **público**: não precisa de login no GitHub para instalar.

### No terminal
Na caixa de mensagem do Claude Code, digite:

```
/plugin install guia-vivo --marketplace Escribaup/claude-plugins-idvl
```

Quando ele perguntar se quer adicionar o marketplace, digite `y` e aperte Enter. Depois, escolha **usuário** (vale para todos os seus projetos; as outras opções valem só para um projeto).

Ou, direto no terminal, fora do Claude Code:

```
claude plugin install guia-vivo --marketplace Escribaup/claude-plugins-idvl
```

### No aplicativo Claude para computador (aba Code)
1. Clique no **+** ao lado da caixa de mensagem e depois em **Plugins**.
2. Clique em **Add marketplace** e digite `Escribaup/claude-plugins-idvl`.
3. Escolha **Guia vivo**, clique em **Add plugin** e escolha **usuário**.

> Não encontrou a opção **Add marketplace**? Faça uma vez a instalação pelo terminal (acima). Depois disso, o Guia vivo aparece no aplicativo também.

### No navegador (claude.ai/code) e no app do celular
Essas sessões rodam na nuvem, num "ambiente" que é preparado do zero a cada sessão. Lá o comando `/plugin` não existe (aparece "/plugin isn't available in this environment"), mas dá para instalar o Guia vivo pelo **script de configuração do ambiente**, uma vez só:

1. Numa sessão na nuvem, toque no nome do ambiente no topo da conversa (por exemplo, **Default**) e depois em **Edit**.
2. Em **Setup script**, acrescente estas duas linhas no final:
   ```
   claude plugin marketplace add Escribaup/claude-plugins-idvl || true
   claude plugin install guia-vivo@plugins-idvl || true
   ```
3. Salve. A partir da **próxima sessão** nesse ambiente, o Guia vivo já vem instalado.

Se preferir, peça numa sessão na nuvem: *"Adicione o Guia vivo ao script de configuração deste ambiente"*. O Claude propõe a mudança e você aprova.

### Depois de instalar
Abra um projeto e digite `/guia`. No aplicativo, o painel abre sozinho.

---

## Atualizar

Quando sair uma versão nova, rode no terminal, fora do Claude Code:

```
claude plugin marketplace update plugins-idvl
claude plugin update guia-vivo@plugins-idvl
```

Depois, **feche e abra o Claude Code de novo**. Para ver a versão instalada: `claude plugin list`.

## Já tinha instalado pelo endereço antigo (`projeto-modelo`)?

O Guia vivo mudou para este repositório. Faça a troca uma vez, no terminal:

```
claude plugin uninstall guia-vivo@projeto-modelo
claude plugin marketplace remove projeto-modelo
claude plugin install guia-vivo --marketplace Escribaup/claude-plugins-idvl
```

Depois, feche e abra o Claude Code de novo.

---

## Para quem mantém este repositório

- **Cada plugin fica em `plugins/<nome>/`** e é listado em `.claude-plugin/marketplace.json`.
- **Nome interno do marketplace:** `plugins-idvl` (é o que aparece em `guia-vivo@plugins-idvl`). O Claude Code não aceita nomes que pareçam marketplaces oficiais, por isso ele é diferente do nome do repositório.
- **Publicar uma versão nova:** faça as mudanças e **aumente o número de `version`** no `plugin.json` do plugin (por exemplo, de `0.5.0` para `0.6.0`). Sem isso, quem já instalou pode não receber a mudança. Avise a equipe para seguir "Atualizar".
- **Proteja a branch `main`:** em **Settings › Branches**, exija revisão antes de juntar mudanças. O código destes plugins roda no computador de todos que os instalaram.
- **Testes:** `claude plugin test plugins/guia-vivo` e `claude plugin validate .` antes de publicar.
