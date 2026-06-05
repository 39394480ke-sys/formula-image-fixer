---
name: formula-image-fixer
description: "Repair and prepare mathematical, physics, engineering, and STEM formulas before AI image generation. Use when Codex is asked to make or improve image prompts, note-card prompts, PPT illustration prompts, Xiaohongshu knowledge-card prompts, or learning-note images that contain formulas. This is a narrow formula-image patch tool: convert plain-text/code-like formulas into clean LaTeX, prescribe formula-safe layout, prevent garbled AI-rendered formulas, and keep formulas readable in generated images. Do not treat this as a general study-note generator."
---

# Formula Image Fixer

## Purpose

Use this skill as a narrow preflight patch before generating formula-heavy images. The job is not to summarize a whole course. The job is to make formulas image-safe.

Fix:
- code-like formulas such as `sigma = M*y/I`
- plain English formulas such as `E = stress / strain`
- malformed subscripts, superscripts, fractions, Greek letters, integrals, sums, derivatives, matrices, and vectors
- prompts that would cause AI image models to draw formulas as ugly text,乱码, or broken pseudo-code

## Core Requirement

All formulas in the final image prompt or rendered image must be standard LaTeX.

- Use `\(...\)` for inline formulas.
- Use `\[...\]` for displayed formulas.
- Use `\frac{}{}` for fractions.
- Use braces for multi-character subscripts and superscripts: `M_{\max}`, `F_y`, `a^2`.
- Use LaTeX Greek letters: `\sigma`, `\tau`, `\theta`, `\omega`, `\varepsilon`.
- Use proper operators: `\int`, `\sum`, `\frac{\mathrm{d}}{\mathrm{d}x}`, `\partial`, `\mathbf{A}`, `\begin{bmatrix}...\end{bmatrix}`.
- Keep equations separate from dense prose when preparing image prompts.

Never ask an image model to invent or redraw formulas from vague prose. Provide exact LaTeX and exact layout instructions.

## Formula Repair Examples

- `sigma = M*y/I` -> `\[\sigma=\frac{My}{I}\]`
- `E = stress / strain` -> `\[E=\frac{\sigma}{\varepsilon}\]`
- `tau = VQ/It` -> `\[\tau=\frac{VQ}{It}\]`
- `Mmax = PL/4` -> `\[M_{\max}=\frac{PL}{4}\]`
- `wn = sqrt(k/m)` -> `\[\omega_n=\sqrt{\frac{k}{m}}\]`
- `x_i = sum a_ij y_j` -> `\[x_i=\sum_j a_{ij}y_j\]`
- `dx/dt = Ax + Bu` -> `\[\frac{\mathrm{d}x}{\mathrm{d}t}=Ax+Bu\]`

## Layout Rules For Image Prompts

When rewriting a prompt for image generation:

1. Put each core formula on its own line or card.
2. Center displayed formulas.
3. Add a short symbol explanation below the formula when useful.
4. Keep derivations step-by-step; do not stack many formulas in one paragraph.
5. Use clear hierarchy: title, formula, symbol explanation, short note.
6. Reduce decorative text; formula clarity has priority.
7. Request a clean textbook, classroom whiteboard, or STEM knowledge-card style.
8. Avoid tiny formulas, dense formula walls, warped perspective, handwritten micro-text, chaotic poster layouts, or decorative formula backgrounds.
9. If using an image model that cannot truly render LaTeX, recommend generating the layout in HTML/SVG/PDF with MathJax/KaTeX/LaTeX instead, then export the image.

## Prompt Patch Template

Use this structure when the user asks for a reusable prompt:

```text
You are a formula-safe image prompt repairer.

Task:
Prepare the following content for AI image generation. Your only job is to make every formula clean, readable, and LaTeX-safe.

Rules:
1. Convert all plain-text or code-like formulas into standard LaTeX.
2. Use \frac{}{} for all fractions.
3. Use proper subscripts/superscripts, Greek letters, derivatives, integrals, sums, matrices, and vectors.
4. Put important formulas in display math blocks.
5. Do not mix formulas inside long paragraphs.
6. Add brief symbol explanations under core formulas.
7. Keep the image style clean: textbook / whiteboard / STEM knowledge card.
8. Avoid formula乱码, fake code text, decorative formula clutter, or tiny unreadable equations.

Input content:
[paste content here]

Output:
A cleaned image-generation prompt with all formulas written in LaTeX and layout instructions that protect formula readability.
```

## Output Format

For most tasks, output:

1. `Formula fixes` - list the repaired formulas.
2. `Image prompt` - a ready-to-copy prompt for the image model or design tool.
3. `Layout notes` - short instructions such as centered formula, symbol explanation, and clean card/board style.

If the user asks for the actual image and formulas must be exact, prefer deterministic rendering with MathJax/KaTeX/LaTeX in HTML/SVG/PDF and screenshot/export it. Do not rely on a generative image model to render exact formulas.
