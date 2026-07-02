# Component Conventions

> Project-specific conventions for component design and implementation.
> Edit the values marked with `>>> Editable` to match your project's structure.

## Table of Contents

- [1. Paths](#1-paths)
  - [1.1 Components](#11-components)
  - [1.2 Icons](#12-icons)
  - [1.3 Design Tokens](#13-design-tokens)
- [2. Naming](#2-naming)
  - [2.1 Component & File Naming](#21-component--file-naming)
- [3. Component Rules](#3-component-rules)
- [4. Integrations](#4-integrations)
  - [4.1 Figma](#41-figma)
  - [4.2 Storybook](#42-storybook)

---

## 1. Paths

Relative paths where components, icons, and tokens live in the project.

### 1.1 Components

You MUST always scan the file names in these directories (only names, do NOT read file contents) before designing or implementing a component to identify what can be reused and prevent duplicates. New components and screens must also be created in these directories, unless indicated otherwise.

>>> Editable
- `packages/ui/src/primitives/`
- `packages/ui/src/marketplace/components/`
- `packages/ui/src/marketplace/screens/`

### 1.2 Icons

If the design includes icons, you MUST check these files (or their entry point, aka index.ts) first to reuse existing icons before importing, creating, or saving new ones.

>>> Editable
- `packages/ui/src/icons/icons.tsx`

### 1.3 Design Tokens

You MUST always check/review this file to map styles to existing design tokens before introducing new custom styles.

>>> Editable
- `packages/ui/src/styles/tokens.css`

---

## 2. Naming

### 2.1 Component & File Naming

Convention used for component names and their file names.

>>> Editable
**Convention:** CamelCase

**Example:** ProductCard.tsx

---

## 3. Component Rules

>>> Editable
**Max screen component width:** `"mx-auto w-full max-w-[393px] flex"`

**Notes**: Apply only on `<main>` content

**Example:**

```tsx
<main className="mx-auto w-full max-w-[393px] flex">
```

---

## 4. Integrations

>>> Editable
### 4.1 Figma

When given a Figma node, extract the actual design tokens and CSS properties (colors, spacing, font sizes, border radii, shadows, etc.), not only the visual structure. The goal is to map Figma values to existing design tokens or identify new ones needed.

**Download assets:** Download any visual assets (such as JPGs/PNGs used in the mocks) into the mock assets path defined below unless there are other options (like storybook defaults).

**Mock assets path:**

>>> Editable
 `mock/images/figma`

>>> Editable
### 4.2 Storybook

Every component must have a corresponding Storybook file for visual testing and documentation.

**File pattern:** 

>>> Editable
`<ComponentName>.stories.tsx`

**Example:**

```
ProductCard.tsx
ProductCard.stories.tsx
```