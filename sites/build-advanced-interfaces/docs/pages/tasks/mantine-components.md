# Mantine Component Library

## Add Your First Component

!!! abstract "Instructions"
    Set up Mantine in your Next.js app and add your first component.

    Your task:

    - Install `@mantine/core` and `@mantine/hooks`
    - Wrap your app with `MantineProvider`
    - Import and use at least one component (Button, Card, TextInput, or another)
    - Customise it (e.g. change variant, colour, or props)
    - Replace a plain HTML element with the Mantine version

??? code "click to expand"

    ```bash
    # In your Next.js project:
    npm install @mantine/core @mantine/hooks
    ```

    ```tsx
    // app/layout.tsx — wrap your app
    import "@mantine/core/styles.css";
    import { MantineProvider } from "@mantine/core";

    export default function RootLayout({ children }: { children: React.ReactNode }) {
        return (
            <html lang="en">
                <body>
                    <MantineProvider>
                        {children}
                    </MantineProvider>
                </body>
            </html>
        );
    }
    ```

    ```tsx
    import { Button, Card, Text } from "@mantine/core";

    export default function Page() {
        return (
            <div>
                {/* TODO: Replace old UI with Mantine components */}
                {/* TODO: Try different variants and props */}
            </div>
        );
    }
    ```

??? hint "Hint - Click to expand"
    After setting up `MantineProvider`, import components from `@mantine/core`. Try a `Button` with `variant="outline"` or different `color` values. For a `Card`, use it with `shadow="sm"` and `padding="lg"`. Replace a section that was previously plain `<div>` and `<button>` elements.

---

## Build a Mini Interface

!!! abstract "Instructions"
    Now that you have used your first Mantine component, build a more complete mini interface using several components together.

    Your interface should:

    - Use at least **three different** Mantine component types (e.g. buttons, cards, modals, forms, tables, navigation, alerts)
    - Apply components consistently — same styling for similar actions
    - Be accessible — test with keyboard navigation
    - Be polished — good spacing, alignment, and content

    Prepare a short explanation of why you chose each component. Push your work to GitHub.

??? code "click to expand"

    ```bash
    npm install @mantine/core @mantine/hooks @mantine/modals
    ```

    ```tsx
    "use client";

    import { Button, Card, Text, Title, Modal, TextInput, Table, Alert, Stack, Group } from "@mantine/core";
    import { useDisclosure } from "@mantine/hooks";

    export default function MiniInterface() {
        return (
            <Stack>
                {/* TODO: Build a page using multiple Mantine components */}
                {/* TODO: Maintain consistent spacing and styling */}
            </Stack>
        );
    }
    ```

??? hint "Hint - Click to expand"
    Consistent design means: all primary actions use `Button variant="filled"`, all secondary actions use `variant="outline"`, cards have the same shadow and padding. Use Mantine's `Stack` and `Group` to manage spacing. For your explanation, describe what each component adds — e.g. "Card groups related info visually", "Modal handles confirmations without navigating away".
