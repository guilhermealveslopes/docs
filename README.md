# Guia de contribuição — Documentação Fretatech

Este guia documenta o fluxo completo para criar e manter a documentação da Fretatech.

## Primeiros passos

Para ter acesso à documentação clone o projeto em sua máquina.
Em seguida você pode rodar o servidor do mintlify localmente para visualizar seu trabalho.

## Servidor local via npx

```bash
npx mint dev
```
O servidor roda em `http://localhost:3000` com hot-reload.

**OBS:** eu usei essa opção pra rodar o meu servidor local.

## Servidor local via CLI
Você pode também optar por instalar o pacote do mintlify em sua máquina. 
Instale o [Mintlify CLI](https://www.npmjs.com/package/mint) para visualizar suas alterações localmente. Para instalar, use o seguinte comando:

```
npm i -g mint
```

Execute o seguinte comando na raiz da documentação, onde o `docs.json` está localizado:

```
mint dev
```

O servidor roda em `http://localhost:3000` com hot-reload.
Para mais informações, visite a documentação oficial do Mintlify: [Documentação Mintlify](https://www.mintlify.com/docs/quickstart)

## Fluxo de documentação

### 1. Criar a página `.mdx`

Crie o arquivo dentro de `documentacao/` seguindo a estrutura de pastas existente. As pastas seguem o menu do painel:

```
documentacao/
├── gestao/
│   ├── comercial/       # Serviços, pedidos, orçamentos
│   └── motoristas/      # Recibos, cadastros
├── modulos/             # ANTT, emissão, parametrização
└── configuracoes/       # Motor de reservas, emails
```

Toda página precisa do frontmatter:

```mdx
---
title: "Nome da página"
sidebarTitle: "Nome na sidebar (opcional)"
description: "Descrição curta da página."
---
```

### 2. Capturar screenshots

Configuração padrão para os prints:

| Propriedade          | Valor      |
|----------------------|------------|
| Resolução da tela    | 1920x1080  |
| devicePixelRatio     | 2          |

Isso garante imagens nítidas e consistentes em todas as páginas.

### 3. Salvar as imagens

Salve os prints em `images/` dentro de uma subpasta que corresponda à seção da documentação:

```
images/
├── servicos/
├── servico-detalhes/
├── recibos-motorista/
└── novo-orcamento/
```

### 4. Referenciar imagens na página

Use o componente `<Frame>` para envolver as imagens:

```mdx
<Frame>
  <img src="/images/nome-da-secao/nome-do-print.png" alt="Descrição da imagem" />
</Frame>
```

- O caminho da imagem deve começar com `/images/`.
- Sempre preencha o `alt` com uma descrição útil.

### 5. Registrar a página na navegação

Adicione o caminho da nova página em `docs.json`, dentro do grupo correspondente:

```json
{
  "group": "Comercial",
  "pages": [
    "documentacao/gestao/comercial/servicos",
    "documentacao/gestao/comercial/nova-pagina"
  ]
}
```

> A página só aparece no site se estiver registrada aqui.

### 6. Verificar localmente

1. Rode `npx mint dev`
2. Acesse `http://localhost:3000` e navegue até a nova página
3. Confira se as imagens carregam corretamente
4. Confira se a navegação na sidebar está correta

### 7. Publicar

Faça push para a branch `main`. O deploy é automático via GitHub App do Mintlify.

## Estrutura de uma página

Siga este padrão ao escrever uma página de documentação:

```mdx
---
title: "Nome da funcionalidade"
description: "Descrição curta."
---

# Título principal

Parágrafo introdutório explicando o que a página/funcionalidade faz.

<Frame>
  <img src="/images/secao/visao-geral.png" alt="Visão geral" />
</Frame>

## Seção

Texto descritivo.

<Frame>
  <img src="/images/secao/detalhe.png" alt="Detalhe" />
</Frame>
```

## Componentes Mintlify úteis

| Componente | Uso |
|---|---|
| `<Frame>` | Envolver imagens |
| `<Steps>` + `<Step>` | Guias passo a passo |
| `<Card>` + `<CardGroup>` | Cards de funcionalidades |
| `<Info>`, `<Tip>`, `<Warning>` | Caixas de destaque |
| `<Accordion>` | Seções colapsáveis |

## Convenções

- Imagens organizadas em subpastas dentro de `images/`.
- Nomes de arquivos e pastas em **kebab-case** (ex: `servico-detalhes.mdx`).
- Use `**negrito**` para nomes de botões, campos e abas da interface.
- Use travessão (—) em listas descritivas no lugar de dois pontos.
