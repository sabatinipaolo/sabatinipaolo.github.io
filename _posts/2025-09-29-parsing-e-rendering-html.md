---
classes: wide
title: "Parsing e Rendering di pagine HTML"
categories:
  - blog
tags:
  - HTML
  - browser 
  - rendering
  - parsing
  - dom construction

permalink: /blog/parsing-e-rendering-html/
---

1. **HTML parsing** → Costruzione DOM
2. **CSS parsing** → Costruzione CSSOM  
3. **JavaScript execution** (se presente)
4. **Render tree** → Combinazione DOM + CSSOM
5. **Layout** → Calcolo posizioni
6. **Paint** → Disegno elementi
7. **Compositing** → Unione finale

##  Curiosità Tecniche

- **Critical Rendering Path**: È la sequenza minima di passaggi per visualizzare il contenuto
- **Repaint/Reflow**: Quando cambia lo stile, il browser ripete layout e paint
- **60 FPS target**: I browser cercano di mantenere 60 frame al secondo per fluidità

Questo processo è estremamente ottimizzato nei browser moderni e avviene in millisecondi! 

## approfondimenti:

[How Browser work](https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work) da developer.mozilla.org

[https://dev.to/anpet9779/how-browsers-work-a-deep-dive-into-the-rendering-pipeline-1gjg](https://dev.to/anpet9779/
how-browsers-work-a-deep-dive-into-the-rendering-pipeline-1gjg)

[https://www.erwinhofman.com/blog/parsing-and-rendering-process-simplified/](https://www.erwinhofman.com/blog/parsing-and-rendering-process-simplified/)