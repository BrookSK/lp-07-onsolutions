# Logotipos pendentes — LP07

O site está 100% construído em `lp/desenvolvimento-de-aplicativos/index.html`.
Faltam apenas as imagens Base64, que estão como **placeholders** (`src=""` / `href=""`)
identificados pelo atributo `data-logo`.

## O que substituir

Para cada elemento abaixo, cole a string completa da referência
(`data:image/png;base64,iVBOR...`) dentro das aspas de `src` (ou `href` no favicon).

| `data-logo`         | Onde aparece                     | Atributo a preencher | Observação |
|---------------------|----------------------------------|----------------------|------------|
| `favicon`           | `<head>` (link rel="icon")       | `href=""`            | PNG 48x48 da referência |
| `on-solutions`      | Header (marca) **e** card de chat | `src=""`            | **Mesma imagem** nos 2 lugares (logo ON) |
| `braziliana`        | Carrossel de clientes            | `src=""`             | |
| `quatri-automacao`  | Carrossel de clientes            | `src=""`             | |
| `brooks-construtora`| Carrossel de clientes            | `src=""`             | |
| `crosshr`           | Carrossel de clientes            | `src=""`             | |
| `multilife-care`    | Carrossel de clientes            | `src=""`             | |
| `mafedo-engenharia` | Carrossel de clientes            | `src=""`             | |

> **Central RZ** não é imagem — é texto (`<span class="wm">Central RZ</span>`),
> exatamente como na referência. Não precisa de Base64.

## Resumo
- 1 favicon
- 1 logo ON Solutions (reutilizado em 2 `<img data-logo="on-solutions">`)
- 6 logos de clientes em `<img>`
- 1 cliente em texto (Central RZ)

Depois de colar as imagens, nenhuma outra alteração é necessária — HTML, CSS e JS já estão fiéis à referência.
