# Padrão de Renderização — Posts Instagram Orça Comigo

## Especificações (confirmadas pelo board em 2026-05-12)

- **Canvas:** 1080×1080px, fundo #FAFAFA
- **Padding:** PAD_X = 90px (esquerda/direita), MAX_W = 900px
- **Pill:** Inter-SemiBold.ttf 26px, fill teal (52,115,123), texto branco, padding 36×14px, border-radius 50%
- **Hook linha 1:** Inter-Black.ttf, cor DARK (30,45,50) — auto-fit partindo de 92px, reduz de 2 em 2 até max(l1,l2) ≤ 900px
- **Hook linha 2:** mesma fonte e tamanho, cor TEAL (52,115,123)
- **Divider:** 90×6px, cor ORANGE (233,152,111), rounded 3px
- **Body:** Inter-SemiBold.ttf 40px, cor DARK, word-wrap ≤ 900px, line-height 1.4×
- **Footer:** 120px, fundo #ECF8F7 (236,248,247), borda teal 3px no topo
- **Logo no footer:** extrair de `orcacomigo-cdn/assets/orcacomigo-logo.jpg`
  - Crop topo 62% = mascote
  - Remover bg branco: pixels r>235, g>235, b>235 → alpha=0
  - Resize mascote para 56px de altura
  - Crop 60-100% = wordmark, resize para 38px de altura
  - Ambos centralizados horizontalmente, mascote em footer_y+8, wordmark abaixo

## Fontes
- Local: `/paperclip/.fonts/Inter-Black.ttf`, `Inter-SemiBold.ttf`
- Logo CDN: `https://raw.githubusercontent.com/ffelipesimoes/orcacomigo-cdn/main/assets/orcacomigo-logo.jpg`

## Publicação
- IG User ID: 17841477117996019
- API: Graph API v21.0
- FB Token: verificar em ORC-13 comentários (token fornecido pelo board)
- CDN: `ffelipesimoes/orcacomigo-cdn` (GH_TOKEN env var)
- Fluxo: render PNG → upload CDN → create container → sleep 5s → publish → get permalink
