Components are created at these relative paths:

- packages/ui/src/marketplace/components
- packages/ui/src/marketplace/screens

We use Camel case for components names and files.

Every component must have a component.stories.tsx as we work with storybook.

Creating a screen means that it will use several components depending on the design.

Icons should be importes, created or saved on this relative path:

- packages/ui/src/icons/icons.tsx

For screens, the main content should be constraint to 393px max

<main className="mx-auto w-full max-w-[393px]">