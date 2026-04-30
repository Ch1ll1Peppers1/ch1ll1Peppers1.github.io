---
author: Luis Mario Ramirez Cruz
pubDatetime: 2025-12-31T20:58:52.737Z
modDatetime: 2026-04-22T09:25:46.734Z
title: Making the most out of your college experience
tags:
  - college_advice
description: Based on my personal experience and the help of multiple people, here is my advice as a first-gen student who knew little about the college experience.
---

Hello! I went to the University of California, Santa Cruz from 2023-2027, where I double majored in Biology & Computer Engineering. I was the first of my family to start college at a US institution and I had little to no advice to start, here is a collection of things I wish I knew before I started school.

## Freshman Year

Freshman Year is a 


Some of my advice:

__Make sure to have an academic plan done__: When I went my freshman year with my engineering advisor I was told to not make a plan since classes offered every year change and it made no sense for me to do this. I am so glad I didn't follow this advice, I would recommend everyone to make a plan. There are probably some templates available in your major's website but do whatever works for you, now do this being totally conscious that your plan _will_ change. Having a plan even if it will definitely have to change means that the classes you need are not this abstract idea that is in the air, but they are something that you know, it helps you prioritize which classes to take and to understand what pace you need to graduate on time.

There are a lot of resources that make this easy, my way of creating my schedule was to look at all my upper division classes and seeing what where their prerequisites. You will notice that there are some classes that are key to opening up most of the upper divisions and this are the classes you want to be prioritizing. The more flexibility that you have on later quarters when choosing your classes, the easier it will be for you to adjust your schedule in the future.

Another way for you to create your schedule is to look at what the schedule of classes in the past has been. There is always change, but most of your lower division classes have a fairly consistent cycle (if it has been offered on spring for the past 5 years, more likely than not it will keep being offered on spring). Another thing to consider is the professors that will be teaching your classes. I had some friend that loved taking hard professors because they believed that it made them stronger students. I personally believe that your transcript will have the exact same class with a grade regardless of who your teacher was, if you can you should try to make your life easier. A good way to get an idea is to look at historical grade spreads of the teacher in places like <a href="https://slugtistics.com/"> Slugtistics</a> or Rate my Professor. I've personally found that grades tend to be a better reflection of the teachers difficulty than Rate my Professor.

__Make use of your free time__: Freshman year more likely than not is the year that your classes will have the lowest stakes and your schedule will have the most free time, make use of it. This can be done in many ways: join a club

__For UCSC Students: Bcycles__

__For UCSC Students: STEMDIV__

__Scholarships__
_For more detail look at #scholarships_


<figure>
  <img
    src="https://images.pexels.com/photos/22690748/pexels-photo-22690748/free-photo-of-close-up-of-complicated-equations-written-on-a-blackboard.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"
    alt="Free Close-up of complex equations on a chalkboard, showcasing chemistry and math symbols. Stock Photo"
  />
  <figcaption class="text-center">
    Photo by <a href="https://www.pexels.com/photo/close-up-of-complicated-equations-written-on-a-blackboard-22690748/">Vitaly Gariev</a>
  </figcaption>
</figure>

## Table of contents

## Instructions

In this section, you will find instructions on how to add support for LaTeX in your Markdown files for AstroPaper.

1. Install the necessary remark and rehype plugins by running:

   ```bash
   pnpm install rehype-katex remark-math katex
   ```

2. Update the Astro configuration to use the these plugins:

   ```ts file=astro.config.ts
   // ...
   import remarkMath from "remark-math";
   import rehypeKatex from "rehype-katex";

   export default defineConfig({
     // ...
     markdown: {
       remarkPlugins: [
         remarkMath, // [!code ++]
         remarkToc,
         [remarkCollapse, { test: "Table of contents" }],
       ],
       rehypePlugins: [rehypeKatex], // [!code ++]
       shikiConfig: {
         // For more themes, visit https://shiki.style/themes
         themes: { light: "min-light", dark: "night-owl" },
         wrap: false,
       },
     },
     // ...
   });
   ```

3. Import KaTeX CSS in the main layout file

   ```astro file=src/layouts/Layout.astro
   ---
   import { SITE } from "@config";

   // astro code
   ---

   <!doctype html>
   <!-- Other elements  -->
   <meta property="og:image" content={socialImageURL} />

   <!-- [!code highlight:4] -->
   <link
     rel="stylesheet"
     href="https://cdn.jsdelivr.net/npm/katex@0.15.2/dist/katex.min.css"
   />

   <body>
     <slot />
   </body>
   ```

4. As the last step, add a text-color for `katex` in `typography.css`.

   ```css file=src/styles/typography.css
   @plugin "@tailwindcss/typography";

   @layer base {
     /* other classes */

     /* Katex text color */
     /* [!code highlight:3] */
     .prose .katex-display {
       @apply text-foreground;
     }

     /* ===== Code Blocks & Syntax Highlighting ===== */
     /* other classes */
   }
   ```

And _voilà_, this setup allows you to write LaTeX equations in your Markdown files, which will be rendered properly when the site is built. Once you do it, the rest of the document will appear rendered correctly.

---

## Inline Equations

Inline equations are written between single dollar signs `$...$`. Here are some examples:

1. The famous mass-energy equivalence formula: `$E = mc^2$`
2. The quadratic formula: `$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$`
3. Euler's identity: `$e^{i\pi} + 1 = 0$`

---

## Block Equations

For more complex equations or when you want the equation to be displayed on its own line, use double dollar signs `$$...$$`:

The Gaussian integral:

```bash
$$ \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi} $$
```

The definition of the Riemann zeta function:

```bash
$$ \zeta(s) = \sum_{n=1}^{\infty} \frac{1}{n^s} $$
```

Maxwell's equations in differential form:

```bash
$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \mathbf{B} &= 0 \\
\nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
\nabla \times \mathbf{B} &= \mu_0\left(\mathbf{J} + \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}\right)
\end{aligned}
$$
```

---

## Using Mathematical Symbols

LaTeX provides a wide range of mathematical symbols:

- Greek letters: `$\alpha$`, `$\beta$`, `$\gamma$`, `$\delta$`, `$\epsilon$`, `$\pi$`
- Operators: `$\sum$`, `$\prod$`, `$\int$`, `$\partial$`, `$\nabla$`
- Relations: `$\leq$`, `$\geq$`, `$\approx$`, `$\sim$`, `$\propto$`
- Logical symbols: `$\forall$`, `$\exists$`, `$\neg$`, `$\wedge$`, `$\vee$`
