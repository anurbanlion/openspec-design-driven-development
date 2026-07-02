<!--
## Preparation

Before filling out this template:

1. **Read relevant domain-specific designs** or documents under `specs/[domain]/design.md` to align on existing conventions and patterns.
2. **Review any additional visual and design assets** provided, such as Figma nodes and styles (via Figma MCP tools if available) or images uploaded by the user, to ensure accurate implementation of the design specifications.
-->

# Main Components

<!--
Each screen gets two consecutive code blocks:
1. The high-level JSX skeleton showing how sub-components compose together.
   Use HTML comments to annotate sections and reference Figma nodes when available.
2. The TypeScript signature: imports (annotated new/existing), exported interfaces,
   and the function declaration.

Repeat the pair for every screen in the design.
-->

```tsx
// relative/path/to/Screen.tsx
<>
  <Header />
  <main>
    <section>
      {/* Brief annotation of this region */}
      <ChildComponent />
      <ChildComponent />
    </section>
  </main>
</>
```
```tsx
// relative/path/to/Screen.tsx
import type { ChildProps } from "../components/Child"  // new
import type { ExistingProps } from "../components/Existing"  // existing

export interface ScreenProps {
  items: ChildProps[]
}

export function Screen(props: ScreenProps): JSX.Element
```

## Components

<!--
JSX skeletons and signatures for each sub-component (NOT screens — those belong
in Main Components above).

Rules:
- One code block per FILE. If a file contains multiple sub-components, list them
  all in the same block separated by a "// ComponentName" comment.
- Each block starts with a path comment, then alternates between layout skeleton
  and signature as needed.
-->

```tsx
// relative/path/to/components/Child.tsx
// ComponentNameA (since it may be in Child.tsx but be a separate subcomponent)
<article>
  <header>
    <div>
      {/* Region description */}
      <img />
    </div>
    <div>
      {/* Another region */}
      <p />
    </div>
  </header>
  <div>
    {/* Content area */}
    <ExistingComponent />
  </div>
</article>

// ComponentNameB (since it may be in Child.tsx but be a separate subcomponent)
<article>
  <header>
    <div>
      {/* Region description */}
      <img />
    </div>
    <div>
      {/* Another region */}
      <p />
    </div>
  </header>
  <div>
    {/* Content area */}
    <ExistingComponent />
  </div>
</article>
```
```tsx
// relative/path/to/components/Child.tsx
export interface ComponentNameAProps {}

export function ComponentNameA(props: ComponentNameAProps): JSX.Element

export interface ComponentNameBProps {}

export function ComponentNameB(props: ComponentNameBProps): JSX.Element
```

## Storybook Variants

<!--
List the proposed Storybook stories/variants needed to verify the component.
Use story names and a short note about the state each story represents.
-->

Component A:

- `Default`: <!-- state covered -->

Component B:

- `Default`: <!-- state covered -->

## Local Utils

<!--
List any required utility functions/types that should live in the same file as
the component. Include only signatures and relative path comments.
-->

```ts
// relative/path/to/Component.tsx
export function helper(): void
```

## Component Tree

<!--
Create a mermaid diagram of the components used for this screen or component and indicate if those components already exists on the codebase.
-->

## Found Patterns

<!--
Record patterns or conventions noticed in the explicitly reviewed implementation 
files while preparing this design. Do not copy or restate patterns seen before
on specs/[domain]/design.md here. If a previously read global design document 
already describes the same pattern, omit it from this section.
-->

- <!-- pattern observed in reviewed code -->
