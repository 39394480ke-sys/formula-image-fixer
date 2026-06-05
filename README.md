# Formula Image Fixer

A narrow Codex Skill for fixing formulas before AI image generation.

This is not a general study-notes generator. It is a small formula preflight tool for prompts and visuals that contain math, physics, engineering, or STEM formulas.

It helps prevent AI-generated images from turning formulas into code-like text, broken pseudo-math, or garbled symbols.

## What It Fixes

Bad:

```text
sigma = M*y/I
```

Good:

```latex
\[
\sigma=\frac{My}{I}
\]
```

Bad:

```text
E = stress / strain
Mmax = PL/4
dx/dt = Ax + Bu
```

Good:

```latex
\[
E=\frac{\sigma}{\varepsilon}
\]

\[
M_{\max}=\frac{PL}{4}
\]

\[
\frac{\mathrm{d}x}{\mathrm{d}t}=Ax+Bu
\]
```

## Use Cases

- AI-generated study-note images
- STEM knowledge cards
- Xiaohongshu educational visuals
- PPT illustrations with formulas
- Materials mechanics, circuits, control systems, mechanics, physics, and engineering formula cards

## Install

Copy this folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R formula-image-fixer ~/.codex/skills/formula-image-fixer
```

Then invoke it with:

```text
Use $formula-image-fixer to repair the formulas in this image prompt before generation.
```

## Example Prompt

```text
Use $formula-image-fixer.

Prepare this content for AI image generation:

Title: bending stress formula
Formula: sigma = M*y/I
Style: clean STEM knowledge card

Make the formula LaTeX-safe, centered, and add a short symbol explanation.
```

## Core Rules

1. Convert all plain-text or code-like formulas into LaTeX.
2. Use `\frac{}{}` for fractions.
3. Use correct subscripts, superscripts, Greek letters, derivatives, integrals, sums, matrices, and vectors.
4. Put important formulas in display math blocks.
5. Do not mix formulas inside long paragraphs.
6. Add brief symbol explanations under core formulas.
7. Keep the image style clean: textbook, whiteboard, or STEM knowledge card.
8. Avoid formula乱码, fake code text, decorative formula clutter, and tiny unreadable equations.

## Repository Contents

```text
formula-image-fixer/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── assets/
    └── formula-safe-prompt-template.txt
```

## License

MIT
