# Biblioteca de Apps

**Um pontinho de encontro na internet para os apps que eu faço — simples, leve e com cara de bloquinho de papel.**

<p align="center">
  <img alt="HTML + CSS" src="https://img.shields.io/badge/feito%20com-HTML%20%2B%20CSS-0fa3b1?style=flat-square">
  <img alt="Sem dependências" src="https://img.shields.io/badge/sem%20depend%C3%AAncias-ff6b5b?style=flat-square">
  <img alt="Site estático" src="https://img.shields.io/badge/site-est%C3%A1tico-0b1f2a?style=flat-square">
</p>

## Sobre

Esta é a vitrine dos meus projetos web: uma página única, em português, que reúne os links dos apps em um cartão incline levemente — a mesma linguagem visual do [To Do List](https://github.com/brunolieps/to-do-list). Não tem JavaScript, framework, build nem backend: é só `index.html` e `style.css`, hospedados como site estático.

## Apps

| App | Status | Acesso |
| --- | --- | --- |
| **To Do List** | Disponível — lista de tarefas PWA, offline, no claro e no escuro | [Abrir app](https://todo-list.bruno-oli-lira.workers.dev/) · [código](https://github.com/brunolieps/to-do-list) |
| **Habit Tracker** | Em breve | Botão desativado na página |

## O que tem hoje

- **Cartão central com os links** — um bloco de papel sobre fundo verde-água, com textura e sombra.
- **Microinteração no hover** — a borda dos links fica coral e o cartão muda de inclinação.
- **Layout responsivo** — largura adaptada à tela, com limite de 400 px.
- **Tipografia Playpen Sans**, carregada do Google Fonts.
- **Zero JavaScript**: a página inteira é HTML + CSS.

## Tecnologias

| Camada | O que é usado |
| --- | --- |
| Estrutura | HTML5 (`lang="pt-br"`, viewport, semântica mínima) |
| Estilo | CSS com custom properties, nesting, `:has` e transições em `cubic-bezier` |
| Fonte | [Playpen Sans](https://fonts.google.com/specimen/Playpen+Sans), via Google Fonts |
| Textura | `src/paper01.png` (papel pautado, reaproveitada do To Do List) |
| Build / dependências | Nenhum |

## Rodando localmente

Não precisa instalar nada:

```bash
git clone https://github.com/brunolieps/app-library.git
cd app-library
python3 -m http.server 8000
```

Depois abra <http://localhost:8000>. Também dá para abrir o `index.html` direto no navegador — a única diferença é que a fonte do Google Fonts exige conexão.

## Publicando

O repositório é público e o site é estático: para publicar, é só habilitar o GitHub Pages em **Settings → Pages → Deploy from a branch → `main` / `/ (root)`**. Não há pipeline de build nem variáveis de ambiente.

Depois de publicar, atualize `og:image` e `twitter:image` no `<head>` para a URL absoluta da imagem (os robôs de redes sociais preferem URLs completas; enquanto isso, os valores relativos funcionam em navegador).

## Favicon e metadados

O favicon é um quadrado verde-água com um cartão de papel inclinado e dois "apps" — coral (disponível) e azul-marinho (em breve). A fonte vetorial está em `icons/favicon.svg`; as versões PNG e o `.ico` foram geradas a partir dela.

O `<head>` traz:

- `description`, `author`, `theme-color` (`#0fa3b1`), `color-scheme` e `robots`;
- Open Graph (`og:title`, `og:description`, `og:image` 1200×630, `og:locale` `pt_BR`);
- Twitter/X (`summary_large_image`);
- links de ícone para SVG, ICO, PNG 16/32 e `apple-touch-icon` 180.

## Estrutura do projeto

```text
.
├── index.html                 # página única com os links dos apps e o <head> completo
├── style.css                  # paleta, cartão de papel e animações
├── icons/
│   ├── favicon.svg            # fonte vetorial do ícone
│   ├── favicon.ico            # fallback para navegadores antigos
│   ├── favicon-16.png         # aba do navegador (telas de alta densidade)
│   ├── favicon-32.png         # aba do navegador
│   └── apple-touch-icon-180.png
└── src/
    ├── paper01.png            # textura usada no cartão e na imagem de compartilhamento
    ├── og-image.png           # preview 1200×630 para redes sociais
    ├── paper02.png            # textura escura (reserva, não usada hoje)
    ├── screenshot-light.png   # captura do To Do List (não exibida aqui)
    └── screenshot-dark.png    # captura do To Do List (não exibida aqui)
```

## Personalizando

As cores ficam no topo de `style.css`, em `:root`:

| Token | Valor | Uso |
| --- | --- | --- |
| `--primary` | `#0fa3b1` | fundo da página |
| `--secondary` | `#f0f4f8` | papel do cartão |
| `--text` | `#0b1f2a` | texto e bordas |
| `--accent` | `#ff6b5b` | hover, seleção e botão ativo |
| `--papertexture` | `src/paper01.png` | textura do cartão |

Para adicionar um app, basta acrescentar uma linha em `.container` em `index.html`:

```html
<a href="https://endereco-do-app.exemplo/">Nome do App</a>
```

O estilo de botão/link já vem da regra `button, a` em `style.css`. Enquanto o app não existe, use `href="#"` e marque **(Em breve)** no texto, como o Habit Tracker.

## Estado atual e limitações

- O **Habit Tracker** ainda não tem link; o botão é apenas um placeholder (`href="#"`).
- O `style.css` foi herdado do To Do List e guarda seletores que esta página não usa (`#list-container`, `#item-list`, `#item-name`, `#darkmodetoggle`, `.ativo`). Eles não afetam a Biblioteca, mas podem ser removidos numa limpeza.
- Não há tema escuro próprio, manifest PWA, service worker, analytics nem testes automatizados.
- A Playpen Sans vem de CDN externa; sem rede, o navegador usa a fonte cursiva do sistema.

## Autor

Feito por **Bruno Lira** — designer gráfico e web. [GitHub](https://github.com/brunolieps) · [Behance](https://behance.net/brunolieps)

Sugestões ou um app novo para a lista? Abra uma [issue](https://github.com/brunolieps/app-library/issues).
