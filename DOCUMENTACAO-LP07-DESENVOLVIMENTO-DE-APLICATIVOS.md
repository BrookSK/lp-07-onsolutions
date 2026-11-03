# Documentação Técnica — LP07 Desenvolvimento de Aplicativos

## 1. Objetivo da landing page
Apresentar o serviço de **Desenvolvimento de Aplicativos para iPhone e Android** da
ON Solutions Brasil e converter o visitante em lead através do WhatsApp, com mensagem
pré-montada e enriquecida pelos desafios que o visitante selecionar e pela origem do anúncio.

## 2. Arquivo de referência
`07-lp-desenvolvimento-de-aplicativos.html` (fonte de verdade; conteúdo reproduzido fielmente).

## 3. URL de destino
`https://onsolutionsbrasil.com.br/lp/desenvolvimento-de-aplicativos/`

O arquivo foi implementado em `lp/desenvolvimento-de-aplicativos/index.html`, de forma que,
servido por um servidor estático, resolve exatamente nesse caminho de URL.

## 4. Estrutura das seções (ordem original preservada)
1. Header (`.top`)
2. Hero (`.hero`)
3. Identificação dos problemas — `#dores`
4. Benefícios — `#beneficios`
5. Clientes e indicadores — `#clientes`
6. Como funciona — `#como-funciona`
7. Conversa gratuita — `#oferta`
8. FAQ — `#duvidas`
9. CTA final — `#conversa`
10. Footer (`.foot`)
11. Botão fixo de WhatsApp (`.sticky`)

## 5. Conteúdo implementado
Todos os textos foram copiados literalmente da referência (selo, título/subtítulo do Hero,
4 opções de desafios, 4 cards de benefícios, 3 indicadores, 3 passos, bloco da conversa,
3 perguntas do FAQ, CTA final, footer). Nenhum texto comercial de outras LPs foi reutilizado.

## 6. Componentes utilizados
- Header fixo translúcido com blur e comportamento hide/show na rolagem.
- Card de prévia do WhatsApp (composição visual, sem chat real).
- Botões de desafio selecionáveis (`.pain`, `aria-pressed`).
- Cards de benefícios com ícones SVG inline.
- Bloco de indicadores (`.stats`).
- Carrossel contínuo de logotipos (`.marquee` / `.track`).
- Passos numerados (`.steps2`).
- Bloco de oferta em degradê (`.offer`).
- FAQ com `<details>`/`<summary>`.
- Barra fixa de WhatsApp (`.sticky .cta`).

## 7. Identidade visual
Paleta (variáveis CSS em `:root`): `--ink #0B1220`, `--navy #0F172A`, `--bg #F5F8FB`,
`--line #E2E8F0`, `--text #0F172A`, `--soft #52627A`, `--mint #5EEAD4`, `--teal #0D9488`,
`--tealD #0F766E`, `--wa #25D366`, `--waD #1EBE5B`.
Tipografia **Poppins** (400/500/600/700/800) via Google Fonts. Gradientes escuros azul/verde,
destaques verde-menta, cards arredondados, bordas discretas, sombras suaves — idênticos à referência.

## 8. Responsividade e breakpoints
Breakpoints definidos no CSS: **340px, 380px, 400px, 430px e 860px** (desktop).
Mobile em coluna única; a partir de 860px: Hero em 2 colunas, benefícios 4 colunas,
passos e indicadores 3 colunas, oferta 2 colunas. `body` tem `overflow-x:hidden`.
A barra fixa usa `env(safe-area-inset-bottom)` e o footer reserva `84px` extras de padding
inferior para não ser encoberto pela barra.

## 9. Funcionamento dos desafios
Cada botão `.pain` alterna `aria-pressed` entre `true`/`false` (selecionar/desmarcar, múltiplos).
Visual: fundo branco + borda discreta quando não selecionado; fundo verde-claro (`#F0FFF6`),
borda verde e ícone de confirmação quando selecionado. A cada mudança a função `sync()`:
- recalcula a mensagem do WhatsApp;
- atualiza todos os botões `[data-wa-main]` e a prévia (`[data-bubble]`);
- atualiza o texto auxiliar (`[data-hint]`).
Ao mudar o hash da URL, as seleções e o hint são resetados.

## 10. Mensagem padrão e dinâmica do WhatsApp
- **Padrão:** `Olá, vim do site e gostaria de saber mais sobre os serviços de Aplicativos Mobile.`
- **1 desafio:** acrescenta ` Meu maior desafio hoje: [desafio].`
- **2+ desafios:** acrescenta ` Meus maiores desafios hoje: [d1]; [d2]; ....`
- Sem seleção → volta à mensagem padrão.
- Texto auxiliar: vazio (0), "Pronto! Agora toque..." (1), "Você marcou N. Isso tem solução..." (2+).

## 11. Integração com WhatsApp
- Número: `5511972243329`; base: `https://wa.me/5511972243329`.
- Link gerado por `waLink()` com `encodeURIComponent` no texto.
- Todos os links de WhatsApp recebem `target="_blank"` e `rel="noopener"`.
- Posições de clique identificadas: `topo-telefone`, `topo`, `barra-fixa`.

## 12. Rastreamento e parâmetros de origem
- `ON_TRACKING = { gtmId:"", ga4Id:"", gadsId:"", gadsConversionLabel:"" }` — **vazios**;
  nenhum script de rastreamento é carregado enquanto os IDs estiverem vazios.
- `ON_APPEND_ORIGIN = true`.
- Captura `utm_term`/`kw`, `utm_campaign` e `gclid`; quando presentes, anexa a origem à mensagem.
- Eventos: `whatsapp_click` (dataLayer) e `generate_lead` (gtag), além de `conversion`
  se Google Ads estiver configurado. Listener único em captura evita disparos duplicados.

## 13. Imagens e logotipos utilizados
Na referência as imagens são Base64 inline (favicon, logo ON em 2 lugares, 6 logos de clientes
em `<img>` e "Central RZ" como texto).

**Estado atual:** os blocos Base64 estão como **placeholders** (`src=""`/`href=""`) marcados com
`data-logo`, conforme combinado com o cliente, que enviará as imagens originais para colagem final.
Ver `LOGOTIPOS-PENDENTES.md`. As dimensões, `alt`, proporções e o carrossel foram preservados;
ao colar o Base64 original, as imagens ficam idênticas à referência.

## 14. Metadados e SEO
`lang="pt-BR"`, charset UTF-8, viewport com `viewport-fit=cover`, `theme-color #0B1220`.
Title: `Desenvolvimento de Aplicativos | ON Solutions Brasil`.
Description: `Aplicativos bonitos, rápidos e conectados à sua operação.`
Canonical: `https://onsolutionsbrasil.com.br/lp/desenvolvimento-de-aplicativos/`.
Robots: `noindex,follow`. Nenhuma configuração de SEO foi alterada por iniciativa própria.

## 15. Arquivos criados e modificados
- **Criado:** `lp/desenvolvimento-de-aplicativos/index.html` (a landing page completa).
- **Criado:** `DOCUMENTACAO-LP07-DESENVOLVIMENTO-DE-APLICATIVOS.md` (este documento).
- **Criado:** `LOGOTIPOS-PENDENTES.md` (guia de substituição das imagens).
- Nenhuma outra LP ou componente compartilhado foi modificado (não existiam no repositório).

## 16. Testes executados e resultados
- **Integridade estrutural (via busca no arquivo):** confirmadas as 7 seções com os IDs corretos
  (`#dores`, `#beneficios`, `#clientes`, `#como-funciona`, `#oferta`, `#duvidas`, `#conversa`),
  header, hero, footer e barra fixa; documento bem-formado de `<!DOCTYPE html>` a `</html>`.
- **Placeholders de logo:** confirmados 1 favicon + 2 `on-solutions` + 6 logos de clientes + texto Central RZ.
- **Conteúdo textual:** conferido 1:1 com a referência.
- **Limitação de ambiente:** o terminal desta sessão não executa comandos (retorna sempre
  código -1), portanto **não foi possível** rodar um servidor estático, validador de HTML ou
  testes de navegador nesta sessão. A verificação feita foi estática (leitura/busca no arquivo).

## 17. Problemas encontrados e soluções
- **Terminal inoperante:** impossibilitou servir a página e validar via ferramentas. Verificação
  feita por inspeção estática do arquivo.
- **Ferramentas de escrita rejeitam Base64 muito longo em linha única:** confirmado que strings
  Base64 contínuas e muito grandes interrompem a gravação. Solução acordada com o cliente:
  construir todo o site com placeholders e inserir os logotipos (Base64) ao final, enviados por ele.

## 18. Pendências existentes
1. **Colar os logotipos Base64** nos placeholders `data-logo` (ver `LOGOTIPOS-PENDENTES.md`).
2. **Validação em navegador** (visual e responsividade em 340/380/400/430/860px e desktop),
   que não pôde ser executada nesta sessão por limitação do terminal.
3. Definir os destinos reais dos links do footer (LGPD / Política de privacidade), hoje `#`
   como na referência.
