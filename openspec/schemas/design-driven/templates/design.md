<!--
## Preparation

Before filling out this template:

1. **Read relevant domain-specific designs** or documents under `specs/[domain]/design.md` to align on existing conventions and patterns.
2. **Review any additional visual and design assets** provided by the user, such as Figma nodes and styles (via Figma MCP tools if available) or images uploaded by the user, to ensure accurate implementation of the design specifications.
3. **Do not infer replacement scope** from similar names or existing implementations. Unless the user explicitly identifies an existing component as a reference or replacement target, keep the proposal scoped to the files and references they named.
4. **Do not broaden file discovery** beyond the files explicitly named by the user plus the minimum design references required by the workflow.
-->

# Main Components

<!--
Each screen gets two consecutive code blocks:
1. The high-level JSX skeleton showing how sub-components compose together.
   - Use HTML comments to annotate sections and reference Figma nodes when available.
   - Mark reused and new pieces directly in the JSX layout comments using `[REUSED]` and `[NEW]`.
   - Do NOT include styles, classes, or props in the JSX tags; keep them clean and focus purely on layout structure and conditional rendering.
2. The TypeScript signature: imports (annotated new/existing), exported interfaces,
   and the function declaration.
   - Do NOT import sub-components from the same file. If a sub-component is local to that file, represent it with its local signature only in the `Components` section, not as a self-import.

Repeat the pair for every screen in the design.
-->

```tsx
// relative/path/to/Screen.tsx
<>
  <Header />
  <main>
    <section>
      {/* Header and section details - [REUSED] */}
      <ChildComponent />

      {/* Render only when search results are available - [NEW] */}
      {hasSearchResults && <ResultsList />}
    </section>
  </main>
</>
```
```tsx
// relative/path/to/Screen.tsx
import type { ChildProps } from "../components/Child"  // [NEW]
import type { ExistingProps } from "../components/Existing"  // [REUSED]

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
- Mark reused and new pieces directly in the JSX layout comments using `[REUSED]` and `[NEW]`.
- Each block starts with a path comment, then alternates between layout skeleton
  and signature as needed.
- If multiple sub-components live in the same file as the main component, show them here as local sub-components and do not add self-imports in `Main Components`.
- Keep JSX skeletons clean by omitting styles, classes, or props in the tags.
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
    {/* Content area - [REUSED]*/}
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
      {/* Another region - [NEW]*/}
      <NewComponent />
    </div>
  </header>
  <div>
    {/* Content area - [REUSED]*/}
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

## Tokens

<!--
List the design tokens that should be reused, extended, or created for this
change. Group them by category when relevant (for example: colors, typography,
spacing, radius, shadows). Use this section for semantic token decisions, not
raw one-off values hidden inside the prose of other sections.
-->

Colors:

- `token-name`: <!-- purpose/value -->

Typography:

- `token-name`: <!-- purpose/value -->

## Component Tree

<!--
Create a mermaid diagram of the components used for this screen or component and indicate if those components already exists on the codebase.
Also indicate if they are organisms, molecules or atoms.
-->

## Found Patterns

<!--
Record patterns or conventions noticed in the explicitly reviewed implementation 
files while preparing this design. Do not copy or restate patterns seen before
on specs/[domain]/design.md here. If a previously read global design document 
already describes the same pattern, omit it from this section.
-->

- <!-- pattern observed in reviewed code -->
