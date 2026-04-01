# Prompt: Gerar novo orçamento e documentar fluxo

---

## Prompt

```

Acesse a rota http://fretatech-erp.local/dev/auto-login via Playwright e vá em Novo orçamento. Crie um novo orçamento para o cliente [NOME DO CLIENTE] que seja ida e volta. Você pode escolher o primeiro cliente que aparecer na lista.

Aplique o orçamento com as seguintes informações:
- Origem: [CIDADE DE ORIGEM]
- Destino: [CIDADE DE DESTINO]
- Data de ida: [DD/MM/AAAA]
- Data de volta: [DD/MM/AAAA]
- Hora de ida: [HH:MM]
- Hora de volta: [HH:MM]

Você precisa clicar na cidade no autocomplete, e selecionar o dia no calendário e a hora no select. Depois que tiver preenchido os dados, clique em Fazer pesquisa e depois adicione o veículo e clique em avançar.

Pare na tela de orçamento, não precisa salvar ele. Documente todo o fluxo de criação de orçamento e todos os fluxos possíveis na tela de definir a forma de pagamento. Tire prints de tudo.
```

## Variáveis para preencher

| Variável | Exemplo |
|----------|---------|
| `[NOME DO CLIENTE]` | Maria |
| `[CIDADE DE ORIGEM]` | Formiga |
| `[CIDADE DE DESTINO]` | Divinópolis |
| `[DD/MM/AAAA]` ida | 03/04/2026 |
| `[DD/MM/AAAA]` volta | 05/04/2026 |
| `[HH:MM]` ida | 07:00 |
| `[HH:MM]` volta | 15:00 |

## Detalhes técnicos

- **Rota de login:** `http://fretatech-erp.local/dev/auto-login`
- **Rota do orçamento:** `http://fretatech-erp.local/quote/create`
- **Pasta dos prints:** `images/novo-orcamento/`
- **Documentação:** `documentacao/novo-orcamento.mdx`
- **Padrão de referência:** `documentacao/configuracoes/configurar-emails.mdx`
- **Resolução:** `deviceScaleFactor: 2` (alta resolução)
- **Viewport:** `1920x1080`
- **Seletores importantes:**
  - Labels de tipo de viagem: `label[for="roundtrip"]`, `label[for="onewaytrip"]`, `label[for="hourtrip"]`
  - Roteiro personalizado: `button[service="customtrip"]`
  - Origem: `#triporigin`
  - Destino: `#tripdestination`
  - Autocomplete: `.ft-autocomplete.has-focus .ft-autocomplete__results-box li`
  - Adicionar veículo: `select.add_to_quote`
  - Avançar: `.forward`
  - Parcelas: `#installments`
  - SweetAlerts: usar `dismissAllSwals()` com `.swal2-confirm` click + `.swal2-container` remove
