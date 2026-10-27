---
name: gsap
description: Use ao criar, editar ou depurar animações com GSAP neste projeto (tweens, timelines, ScrollTrigger e outros plugins). Também quando o usuário pedir animação, transição ou efeito de scroll.
---

# GSAP

O projeto usa `gsap` (npm) com ES modules (`"type": "module"` no package.json). Ponto de entrada: `main.js`.

## Importação

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger"; // só se usar o plugin
gsap.registerPlugin(ScrollTrigger);                 // registre todo plugin antes de usar
```

## Regras

- GSAP anima o DOM: o código precisa rodar no navegador (via bundler como Vite), não em Node puro.
- Prefira propriedades de transform (`x`, `y`, `scale`, `rotation`, `opacity`) a `left`/`top`/`width` — são mais performáticas.
- Para sequências, use `gsap.timeline()` em vez de encadear `delay`s.
- Use `defaults` na timeline para evitar repetir `duration`/`ease`.
- Use `gsap.from()` para animar entrada a partir de um estado, `gsap.to()` para um estado final, `gsap.fromTo()` quando precisar dos dois explícitos.
- Em frameworks (React etc.), use `gsap.context()` (ou `@gsap/react` com `useGSAP`) e faça `revert()` na desmontagem.
- Respeite `prefers-reduced-motion` com `gsap.matchMedia()`.

## Exemplos

```js
// Tween simples
gsap.to(".box", { x: 200, rotation: 360, duration: 1, ease: "power2.out" });

// Timeline
const tl = gsap.timeline({ defaults: { duration: 0.6, ease: "power3.out" } });
tl.from(".title", { y: 40, opacity: 0 })
  .from(".subtitle", { y: 20, opacity: 0 }, "-=0.3")
  .from(".card", { y: 30, opacity: 0, stagger: 0.1 });

// ScrollTrigger
gsap.to(".panel", {
  x: 300,
  scrollTrigger: { trigger: ".panel", start: "top 80%", end: "top 30%", scrub: true },
});

// Movimento reduzido
const mm = gsap.matchMedia();
mm.add("(prefers-reduced-motion: no-preference)", () => {
  gsap.from(".hero", { opacity: 0, y: 50, duration: 1 });
});
```
