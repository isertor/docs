# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **Mintlify documentation site** for Atlas, a restaurant management platform. The repository contains MDX documentation files organized by topic, with configuration managed through `docs.json`.

## Mintlify documentation. Refer to https://www.mintlify.com/docs for up-to-date documentation on Mintlify, its syntax and supported features/components.

## Architecture

### Documentation Structure

The content is organized into main sections defined in `docs.json`:

- **Get started**: Onboarding guides (`get-started/`)
- **Merchant Portal**: Core platform features (`merchant-portal/`)
  - Orders (admin orders, editing, refunds)
  - Stocks
  - Customers
  - Reports (`reports/`)
  - Marketing tools (discounts)
  - Menu builder (menus, POS layouts)
  - Outlet settings (operating hours)
- **Hardware**: Device setup guides (`others/printers.mdx`)
- **Integrations**: Third-party connections (`configuring-atlas/`)
  - Revel POS integration
  - Deliveroo integration

### File Conventions

- All documentation files use `.mdx` format (Markdown with JSX)
- Frontmatter includes `title` and `description` fields
- Images are stored in `/images/` directory
- Navigation structure is defined in `docs.json` under the `navigation` object

### Key Configuration Files

- **docs.json**: Mintlify configuration including theme, navigation, branding
  - Theme color: `#FF3279` (primary)
  - Font: Poppins
  - Navigation tabs: Guides, Integrations, API docs (external)

## Content Guidelines

### Documentation Patterns

1. **Info blocks**: Use for audience targeting

   ```mdx
   <Info>
     **Who is this article for?**

   - Atlas users with Admin permissions...
     </Info>
   ```

2. **Steps component**: For sequential instructions

   ```mdx
   <Steps>
     <Step title="Step title">Content here</Step>
   </Steps>
   ```

3. **CardGroup**: For navigation/overview pages
   ```mdx
   <CardGroup cols="1">
     <Card title="Title" icon="icon-name" horizontal href="path">
       Description
     </Card>
   </CardGroup>
   ```

### Title Conventions

- All titles use **sentence case** (not title case)
- Discount-related content uses escaped dollar signs: `\$` when needed
- Accordion titles also use sentence case

### Image Management

- Screenshot files use CleanShot format with timestamps
- Images referenced in MDX should be in `/images/` with descriptive filenames
- Use WebP format for optimized images when possible

## Working with Navigation

To add new pages to navigation:

1. Create the `.mdx` file in the appropriate directory
2. Update `docs.json` navigation structure
3. Add the file path (without extension) to the relevant `pages` array

Example:

```json
{
  "group": "Orders",
  "icon": "bag-shopping",
  "pages": ["merchant-portal/admin-orders", "merchant-portal/editing-order"]
}
```

## Git Workflow

- Main branch: `main`
- Current branch: `master` (note: different from main)
- Recent commits show documentation edits made through Mintlify web editor
- Commit messages typically describe content changes (e.g., "Fix promo code blank behavior and escape dollar signs")

## Common Tasks

### Editing existing documentation

1. Locate the `.mdx` file in the appropriate directory
2. Maintain frontmatter structure (title, description)
3. Follow existing Mintlify component patterns
4. Ensure sentence case for all titles

### Adding new documentation pages

1. Create `.mdx` file in appropriate directory
2. Add frontmatter with title and description
3. Update `docs.json` navigation
4. Use appropriate Mintlify components (Steps, Info, Card, etc.)

### Managing navigation structure

- Edit the `navigation.tabs` array in `docs.json`
- Each tab contains groups, each group contains pages
- External links use `href` instead of `pages`
- Icons use Font Awesome icon names

## Mintlify-Specific Components

The documentation uses these Mintlify components:

- `<Info>`: Informational callouts
- `<Steps>` and `<Step>`: Step-by-step instructions
- `<Card>` and `<CardGroup>`: Navigation cards
- `<Accordion>` and `<AccordionGroup>`: Collapsible content sections
- `<Tabs>` and `<Tab>`: Tabbed content for organizing related information
- `<Frame>`: Image containers with captions

## Writing Documentation from Screenshots

When writing documentation based on UI screenshots and user requirements, follow this structured approach:

### 1. Information gathering

Before writing, ensure you have:

- Screenshots of all UI sections
- Detailed explanations of features, filters, and metrics
- Understanding of user workflows and common use cases
- Knowledge of edge cases and important caveats

### 2. Documentation structure

Organize content hierarchically using heading levels:

- **h3 (`###`)**: Main feature sections (e.g., "Daily outlet report")
- **h4 (`####`)**: Major subsections (e.g., "Filters", "Actions", "Sales summary")
- **h5 (`#####`)**: Optional deeper nesting if needed

### 3. Component selection guide

Choose Mintlify components based on content type:

#### Use `<Info>` blocks for:

- Important contextual notes that users should be aware of
- Caveats, warnings, or special cases
- Contact support prompts
- Configuration notes

Example:

```mdx
<Info>
  An outlet's sales day defaults to 12AM-12AM, but you can contact support to customize your sales day (e.g. 3AM-3AM).
</Info>
```

#### Use `<AccordionGroup>` and `<Accordion>` for:

- Long lists of definitions or reference material
- Content that users may not need to read every time
- Detailed explanations that would clutter the main flow

Example:

```mdx
<AccordionGroup>
  <Accordion title="Metric definitions">
    - **Gross sales**: Undiscounted, unmodified sales...
    - **Discounts**: Total discounts, including...
  </Accordion>
</AccordionGroup>
```

#### Use `<Tabs>` and `<Tab>` for:

- Multiple related sections of equal importance
- UI that has actual tabs (mirror the UI structure)
- Alternative views or approaches to the same task

Example:

```mdx
<Tabs>
  <Tab title="Sales insights">
    Content for sales insights...
  </Tab>
  <Tab title="Product category sales">
    Content for category sales...
  </Tab>
</Tabs>
```

#### Use `<Frame>` for:

- All screenshots and images
- Always include descriptive captions
- Always include descriptive alt text for accessibility

Example:

```mdx
<Frame caption="Sales summary with unsettled orders">
  <img src="/images/reports/sales-summary-unsettled.png" alt="Sales summary showing overpaid amount and link to view unsettled orders" />
</Frame>
```

#### Use `<Steps>` for:

- Sequential instructions or procedures
- Multi-step processes
- Setup guides

Example:

```mdx
<Steps>
  <Step title="Navigate to settings">
    Click on the settings icon in the top right...
  </Step>
  <Step title="Configure your outlet">
    Select your outlet from the dropdown...
  </Step>
</Steps>
```

### 4. Content writing patterns

#### Filters and controls

When documenting filters, use a bulleted list with bold labels:

```mdx
- **Date**: Serving date (when an order was fulfilled). Defaults to the current date but can be set to a custom time period.
- **Outlet**: Switch between outlets if you have multiple outlets
- **Shift**: Filter the report by shifts (e.g. Lunch, Dinner)
```

#### Actions and buttons

Use a bulleted list for action descriptions:

```mdx
- **Print summary receipt**: Print a summary with high-level metrics to a selected printer
- **Export to PDF**: Export the entire report to PDF
```

#### Metric definitions

For financial or analytical metrics, use bold labels followed by clear definitions:

```mdx
- **Gross sales**: Undiscounted, unmodified sales based on item prices. For tax-inclusive outlets, gross sales includes tax.
- **Net sales**: Gross sales - discounts - points redeemed - tax (included)
```

#### Tables and data displays

When documenting table columns, introduce with context then list:

```mdx
View a breakdown of all discounts applied during the selected period, organized by promo code. This table shows:
- Promo code name
- Total count (number of times the discount was applied)
- Total discounted amount
```

### 5. Image placement strategy

Place `<Frame>` components strategically:

- **Overview images**: Right after the main feature introduction
- **Section images**: After explaining what the section shows, before detailed field descriptions
- **Context images**: After mentioning specific UI elements that users should click or interact with

Example placement:

```mdx
#### Sales summary

Key financial metrics for your selected time period. Only metrics applicable to the selected outlet are displayed.

<AccordionGroup>
  <!-- Definitions here -->
</AccordionGroup>

<Frame caption="Sales summary with unsettled orders">
  <img src="/images/reports/sales-summary-unsettled.png" alt="..." />
</Frame>
```

### 6. Writing style guidelines

- **Be concise**: Users scan documentation, so keep explanations brief
- **Use active voice**: "Click the button" not "The button can be clicked"
- **Provide context**: Explain why a feature matters, not just what it does
- **Include examples**: Use parenthetical examples like "(e.g. Lunch, Dinner)"
- **Link related content**: Use markdown links `[text](url)` to connect to related pages
- **Explain calculations**: For computed metrics, show the formula (e.g., "Net sales + delivery fee + surcharge")

### 7. Special considerations

#### Disclaimers and warnings

Use `<Info>` blocks or plain text with bold "Disclaimer:" prefix:

```mdx
<Info>
  **Disclaimer**: Sales numbers in the products sold table are based on the main product price and may not take into consideration any bundling, discounts, and price overrides for modifiers.
</Info>
```

#### External links

Link to other Atlas pages using full URLs:

```mdx
To set up your product categories, edit your product on the [Products page](https://portal.atlas.kitchen/products) and set its **Reporting category**.
```

#### Support contact prompts

When users need to contact support, be explicit:

```mdx
Contact support to set up shifts.
```

### 8. Review checklist

Before finalizing documentation:

- [ ] All headings use sentence case
- [ ] Dollar signs are escaped where needed (`\$`)
- [ ] Images have descriptive captions and alt text
- [ ] All external links work and use https://
- [ ] Info blocks are used for important notes
- [ ] Complex lists are in accordions
- [ ] Related content uses tabs when appropriate
- [ ] Terminology is consistent throughout
- [ ] User benefit is clear (why they should use this feature)

## Brand & Styling

- Primary color: #FF3279 (pink/magenta)
- Font family: Poppins
- Logo variants: Light and dark mode SVGs in `/logo/`
- Favicon: `/favicon.svg`
