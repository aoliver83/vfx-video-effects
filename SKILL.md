---
name: vfx-video-effects
description: Use when adding VFX, shaders, particles to Remotion videos.
version: 1.0.0
author: Hermes Agent
license: MIT
---

# VFX Video Effects Stack for Remotion & HyperFrames

## Overview
Use this skill when enhancing video compositions (Remotion or HyperFrames) with visual effects, post-processing filters, particle simulations, shaders, or celebratory overlays. Tailored for dark, institutional fintech and regtech video styles (ACAM212).

## Approved Stack (Tier 1 & 2)

| Library | Type / Efeito | npm | CDN |
|---|---|---|---|
| **Remotion** | Motor central (React → MP4) | `remotion` `@remotion/cli` | - |
| **PixiJS Filters** | CRT, old film, shockwaves, cor | `pixi-filters` | jsDelivr |
| **canvas-confetti** | Confeti controlado | `canvas-confetti` | jsDelivr |
| **drei** | Sparkles, estrelas, vidro (three.js) | `@react-three/drei` | npm only |
| **three-nebula** | Partículas mágicas, vortex | `three-nebula` | jsDelivr |
| **VFX-JS** | Shaders em elementos HTML | `@vfx-js/core` | jsDelivr |
| **fireworks-js** | Fogos de artifício (uso pontual) | `fireworks-js` | jsDelivr |
| **Vanta** | Backgrounds 3D animados (pin versão) | `vanta` | jsDelivr |
| **Rapier** | Física 2D/3D (simulação de dados) | `@dimforge/rapier2d` | npm / WASM |

## Scene Pairing Recipes

1. **Intro Institucional / Identidade**
   - Fundo: Vanta.net (pontos ciano #00e5cc sobre #0a0e17)
   - Luz: drei (sparkles / pontos de luz estelares)
   - Cor: PixiJS Filters (ajuste de tom ciano/verde compliance)

2. **Transições de Cenas**
   - Efeito: PixiJS Filters (shockwave ou CRT scanlines)
   - Elemento: VFX-JS (glitch / bloom em textos de tese regulatória)

3. **Métrica / Destaque de Número**
   - Animação: contador em fonte monospace com cor primária #00e5cc
   - Destaque: canvas-confetti (baixa dispersão, cores da paleta) + three-nebula (partículas sutis)

## Rules & Constraints
- **RegTech / institutional videos (Ativos & Regulação, ACAM212): use at most ONE effect per video, at the reveal.** Allowed: subtle glow/bloom on a stamp or number, one shockwave-type pulse. Forbidden on-brand: confetti, fireworks, Vanta backgrounds, glitch/CRT scanlines — they read as hype and contradict the "zero promessa financeira" positioning. The persistent-world explainer pattern (see `regtech-faceless-video-production`, Concept v2) carries the attention; VFX does not.
- Every library here is browser-side; in the local Playwright→ffmpeg pipeline it must be **seek-deterministic** (driven by a paused GSAP timeline or by a frame counter), otherwise particles differ between runs and QA screenshots never match the final render.
- **Estilo Visual:** Dark background (`#0a0e17`), acentos ciano/verde compliance (`#00e5cc`), sem hype de criptomoeda.
- **Performance:** Prefira shaders leves e componentes React isolados (`useCurrentFrame()`).
- **Verificação:** Valide o resultado executando no Remotion Studio ou renderizando frame de teste.
