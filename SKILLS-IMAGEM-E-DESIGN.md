# Skills de imagem e design

Quatro skills para melhorar artes, layouts, cores e prompts de imagens fotorrealistas.

| Skill | O que faz | Origem | Licença |
|---|---|---|---|
| **canvas-design** | Cria pôsteres, cards e artes estáticas (PNG/PDF) com direção de arte, composição e mais de 50 fontes incluídas | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/canvas-design) (commit `ca45fc4`) | Apache 2.0 (`LICENSE.txt` na pasta) |
| **theme-factory** | Aplica ou cria temas de cores e fontes em slides, documentos e páginas; 10 temas prontos | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/theme-factory) (commit `ca45fc4`) | Apache 2.0 (`LICENSE.txt` na pasta) |
| **design-taste-frontend** | Direção de arte para sites, landing pages e telas de app, evitando o visual genérico de IA | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) (commit `12af471`), pasta original `skills/taste-skill` | MIT (`LICENSE.txt` copiado para a pasta) |
| **image-master** | Monta prompts fotorrealistas para Gemini, GPT-image, Flux, Midjourney etc. e revisa defeitos típicos de IA | [hoodini/ai-agents-skills](https://github.com/hoodini/ai-agents-skills/tree/main/skills/image-master) (commit `20aebb8`) | MIT, declarada no README do autor (o repositório não tem arquivo de licença) |

## Onde está cada versão

- **`.claude/skills/<nome>`**: cópias originais, sem nenhuma alteração. Use no Claude Code.
- **`claude-ai-uploads/<nome>.zip`**: pacotes para enviar ao claude.ai. A única mudança é a
  `description` do cabeçalho do `SKILL.md`, encurtada para até 200 caracteres (limite citado
  pela página de suporte do claude.ai) e com palavras em português para a skill ser acionada
  em pedidos escritos em português. Instruções, referências, fontes e scripts são idênticos.

A pasta `design-taste-frontend` se chama `taste-skill` no repositório original. Ela foi
renomeada porque o nome da pasta precisa ser igual ao `name` declarado no `SKILL.md`.

## Como ativar em todas as conversas do claude.ai (web, desktop e app)

1. Baixe os quatro arquivos `.zip` da pasta `claude-ai-uploads/`.
2. Abra a página de skills da sua conta: [claude.ai/customize/skills](https://claude.ai/customize/skills)
   (menu **Customize > Skills**).
3. Envie cada `.zip` (sem descompactar) e deixe a skill ativada.
4. Confira se a execução de código está ligada nas configurações: as skills dependem dela.

Depois disso, o Claude carrega a skill sozinho quando o pedido combina com a descrição.

## Como instalar no Claude Code (qualquer projeto)

Copie as pastas para a pasta pessoal de skills (`~/.claude/skills`):

```bash
git clone --depth 1 https://github.com/winterbruno-boop/skilsswinter.git
cp -r skilsswinter/.claude/skills/{canvas-design,theme-factory,design-taste-frontend,image-master} ~/.claude/skills/
```

No Windows (PowerShell):

```powershell
git clone --depth 1 https://github.com/winterbruno-boop/skilsswinter.git
foreach ($s in "canvas-design","theme-factory","design-taste-frontend","image-master") {
  Copy-Item -Recurse "skilsswinter\.claude\skills\$s" "$HOME\.claude\skills\"
}
```

## Observações

- A **design-taste-frontend** rende mais no Claude Code: os scripts de inspeção precisam de
  Node 22+ e Chrome/Edge, e o `assets.mjs` busca fotos de domínio público (Openverse,
  Wikimedia, Met, NASA) na internet, sem chave de API. No chat ela funciona como guia de
  direção de arte.
- A **image-master** não gera imagens: ela entrega o prompt para colar no gerador de sua escolha.
