# Itarget HUB — Especificação Tecnica

## Dependencias

| Pacote | Versao | Proposito |
|---|---|---|
| react | ^19.0.0 | Framework UI |
| react-dom | ^19.0.0 | Renderizacao DOM |
| vite | ^6.0.0 | Bundler |
| @vitejs/plugin-react | ^4.4.0 | Plugin React para Vite |
| tailwindcss | ^4.0.0 | Estilizacao utilitaria |
| @tailwindcss/vite | ^4.0.0 | Integracao Tailwind + Vite |
| gsap | ^3.12.0 | Motor de animacao, timelines, ScrollTrigger |
| lucide-react | ^0.460.0 | Iconografia |
| typescript | ^5.6.0 | Tipagem estatica |
| @types/react | ^19.0.0 | Tipos React |
| @types/react-dom | ^19.0.0 | Tipos React DOM |

> **Nota sobre `three`:** O `three` foi listado como dependencia no design, mas nao ha cena 3D, modelo, camera ou renderer Three.js em nenhuma secao. O shader WebGL do hero e um fullscreen quad raw (contexto WebGL nativo), e o efeito de particulas e canvas 2D nativo. Portanto, `three` nao sera incluido — evita ~600KB desnecessarios no bundle.

---

## Inventario de Componentes

### Layout (compartilhados)

| Componente | Fonte | Notas |
|---|---|---|
| Navbar | Custom | Fixed, transparent-to-blur com scroll. Hamburger em mobile. |
| Footer | Custom | 4 colunas de links, copyright. |
| SectionHeader | Custom | Reutilizado em 7 secoes. Inclui eyebrow com TextScramble, titulo e descricao. |

### Secoes (page-level, usados uma vez)

| Componente | Notas |
|---|---|
| HeroSection | Viewport completo, shader WebGL de fundo, floating cards, CTAs. |
| SOPMethodologySection | 3 LayerCards, ProcessFlow (SVG), RuleCards, ObjectivesBar. |
| RACISection | Tabela RACI customizada, legenda, RACIDescriptionCards. |
| InfographicSection | HubDiagram (SVG), DataFlowDiagram, DesvinculacaoBox, DeploymentTimeline. |
| SaaSPlatformSection | PlatformMockup (interface simulada), FeatureHighlights. |
| ActivationFormSection | Preview do formulario com 8 secoes de campos (preview desabilitado). |
| StatsImpactSection | StatCards com contagem animada, QuoteBlock. |
| ModulesOverviewSection | Grid de modulos ativos (4) + futuros (16). |
| CTASection | Titulo, descricao, botao com pulso, texto secundario. |

### Componentes Reutilizaveis

| Componente | Usado em | Notas |
|---|---|---|
| Card | ~15 instancias | Variantes via props: `layer` (borda colorida), `feature` (icon+texto), `form` (sem hover), `stat` (numero grande). |
| Button | ~8 instancias | Variantes: `primary`, `secondary`, `ghost`. |
| LayerCard | SOP (3x) | Especializacao de Card com borda esquerda colorida, badge, glow de cor. |
| FeatureCard | SaaS (3x), RuleCards (4x), RACI cards (3x) | Icone 28-32px + titulo + descricao + tags opcionais. |
| StatCard | Stats (4x) | Numero com gradiente + label + descricao. |
| FormInput | Form preview (~50 campos) | Variantes: text, email, select, textarea, toggle, checkbox, radio, color, file, date. Todos desabilitados no preview. |
| TextScramble | 7+ instancias (eyebrows) | Efeito de terminal: caracteres aleatorios ciclando ate resolver. |
| WaterShader | Hero (1x) | Canvas WebGL raw com fullscreen quad. Shader GLSL completo (vertex + fragment). |
| ParticleWave | Stats (fundo decorativo, 1x) | Canvas 2D com grid de particulas e repulsao por mouse. |
| HubDiagram | Infographic (1x) | SVG central com circulos modulos, paths curvos e tooltips. |
| DeploymentTimeline | Infographic (1x) | Timeline horizontal com 5 milestones, iluminacao sequencial no scroll. |
| ProcessFlow | SOP (1x) | Linha horizontal SVG com 3 nos e setas animadas. |
| FloatingCard | Hero (3x) | Card decorativo com animacao CSS de flutuacao. |

### Hooks

| Hook | Proposito |
|---|---|
| useScrollReveal | IntersectionObserver para fade-in + translateY com stagger. Usado por praticamente todos os elementos animados por scroll. |
| useTextScramble | Logica do scramble de caracteres aleatorios. Acionado por IntersectionObserver. |
| useWaterShader | Ciclo de vida do contexto WebGL: init, compile shaders, uniforms, render loop, cleanup. |
| useParticleWave | Ciclo de vida do canvas 2D: grid de particulas, repulsao por mouse, render loop, cleanup. |
| useScrollProgress | Retorna progresso normalizado [0,1] de um elemento no scroll (usado pelo DeploymentTimeline). |

---

## Plano de Animacao

| Animacao | Biblioteca | Abordagem | Complexidade |
|---|---|---|---|
| Water Deformation Shader (hero bg) | WebGL raw | Hook `useWaterShader` gerencia todo o pipeline: contexto WebGL, compilacao de shaders, uniformes (`u_time`, `u_res`, `u_mouse`), render loop via `requestAnimationFrame`, cleanup. Fullscreen quad de 2 triangulos. | **Alta** 🔒 |
| Particle Wave (stats bg) | Canvas 2D raw | Hook `useParticleWave`: grid de ~5000 pontos (2000 em mobile), projecao 3D→2D, repulsao radial por mouse, render loop. Canvas com `pointer-events: none`. | **Alta** 🔒 |
| Text Scramble (eyebrows) | Vanilla JS no hook `useTextScramble` | IntersectionObserver dispara ciclo: cada caracter itera por `ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%&*` a 50ms ate resolver em ~1.5s. Executa uma unica vez. | Media |
| Scroll Reveal (global) | CSS transitions + IntersectionObserver | Hook `useScrollReveal` aplica classe que transiciona `opacity: 0, translateY(40px)` para `opacity: 1, translateY(0)`. Stagger via CSS `transition-delay` incremental. | Baixa |
| Process Flow draw (SOP) | GSAP + ScrollTrigger | `gsap.fromTo` no `stroke-dashoffset` do path SVG com `scrub: true`. Linha desenhada da esquerda para direita conforme scroll. | Media |
| Stat numbers count-up | GSAP | `gsap.to` com `snap` e `textContent` interpolado de 0 ate valor final ("70%", "100%", "3x", "0"). Disparado por ScrollTrigger `once: true`. | Media |
| Deployment Timeline sequential light-up | GSAP + ScrollTrigger | Timeline GSAP com `scrub`: cada milestone transiciona de `--color-gray-700` para `--color-accent` em sequencia conforme scroll. | Media |
| Timeline nodes pulse (milestone ativa) | CSS keyframes | Pulsacao de glow no node ativo da timeline. Alterna `box-shadow` entre normal e intensificado. | Baixa |
| Hub diagram flowing dashes | CSS animation | `stroke-dasharray` + `stroke-dashoffset` animado via CSS `@keyframes` nos paths SVG conectando HUB aos modulos. | Baixa |
| Card hover glow | CSS transitions | `transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s`. `translateY(-4px)` + glow no hover. Puramente CSS. | Baixa |
| Floating cards bobbing | CSS keyframes | `@keyframes float` com `translateY(±8px)` em ciclos de 4s, fases diferentes por card (delay negativo). | Baixa |
| CTA button pulse glow | CSS keyframes | `@keyframes pulseGlow` oscilando `box-shadow` entre `--glow-accent` e versao intensificada, 3s infinite. | Baixa |
| Smooth scroll navigation | CSS `scroll-behavior: smooth` | Nativo do CSS, sem JS. Offset de -80px via `scroll-padding-top` no `<html>`. | Baixa |
| Scroll indicator bounce | CSS keyframes | `@keyframes bounce` com `translateY(±8px)`, 2s infinite ease-in-out. | Baixa |
| Navbar background transition | CSS transition | `transition: background 0.3s ease, backdrop-filter 0.3s`. Classe aplicada com base em scroll >100px via estado React. | Baixa |
| SaaS mockup scale-in | CSS transition | `transform: scale(0.95)` → `scale(1)` + `opacity` no scroll entry. | Baixa |
| Form section accent bar | CSS transition | Lateral bar `width: 0` → `width: 4px` via scroll entry, 0.5s. | Baixa |

---

## Estado e Logica

### WebGL Shader — Ciclo de Vida Imperativo

O WaterShader opera fora do ciclo de renderizacao do React. O hook `useWaterShader` gerencia:
- Inicializacao do contexto WebGL e compilacao dos shaders GLSL no `useEffect`
- Armazenamento de referencias para `uniformLocations` em um `ref`
- Render loop via `requestAnimationFrame` que atualiza `u_time` a cada frame
- Event listeners para `mousemove`/`touchmove` (normalizados para [0,1] com Y-flip) → `u_mouse`
- Event listener para `resize` → atualiza dimensoes do canvas e `u_res`
- Cleanup completo no unmount: cancela rAF, remove listeners, deleta programa/shaders

**Nao usar React state** para uniforms — causaria re-render desnecessario a 60fps. Todos os valores mutaveis ficam em `refs`.

### Canvas 2D Particle Wave — Mesmo Padrao

O `useParticleWave` segue a mesma arquitetura imperativa:
- Array de particulas com posicao 3D (x,y,z) em `ref`
- Mouse position em `ref` para calculo de repulsao radial
- `requestAnimationFrame` loop: aplica wave senoidal + repulsao por distancia + projeta para 2D + desenha pontos
- Cleanup identico ao shader

### Formulario de Ativacao — Preview Estatico

O formulario de ativacao e **exclusivamente um preview visual desabilitado**. Todos os ~50 campos sao renderizados como `<input disabled>` / `<select disabled>` / toggles visualis (nao interativos). Nao ha estado de formulario, validacao, nem submissao. O unico estado local e opcional: scroll-to-top no footer sticky.

### Navbar Scroll Detection

Um unico listener de scroll no `window` (throttled a RAF) determina se `scrollY > 100`, togglando uma classe CSS para background blur. Estado binario simples em um `useState`.

---

## Outras Decisoes-Chave

### Raw WebGL em vez de Three.js / React Three Fiber

O design especifica `three` como dependencia, mas a unica coisa 3D e um fullscreen quad com um fragment shader customizado. Usar Three.js para isso seria overkill de ~600KB. A implementacao usa WebGL raw: 1 canvas, 1 contexto, 1 programa, 1 quad (6 vertices). Mesma abordagem para o canvas 2D de particulas — nada de Three.js.

### GSAP em vez de Framer Motion

O design lista apenas GSAP como dependencia de animacao. Framer Motion nao sera usado. A arquitetura de animacao e: GSAP para timeline-driven e scroll-driven (ProcessFlow, Stats count-up, DeploymentTimeline), CSS transitions/keyframes para tudo interativo/hover/bobbing/pulse, e IntersectionObserver vanilla para triggers de scroll reveal.

### SVG nativo em vez de biblioteca de diagramas

O HubDiagram, ProcessFlow e DeploymentTimeline sao todos SVG inline nativo. Nao ha necessidade de D3, react-flow, ou similar — os diagramas sao estaticos com animacoes CSS/GSAP simples em paths e elementos.

### Nao ha roteamento

E uma single-page application literal: uma unica pagina `index.md` com secoes. Nao ha necessidade de React Router. Os links de navegacao sao ancoras (`#sop`, `#ficha`, etc.) com smooth scroll nativo.
