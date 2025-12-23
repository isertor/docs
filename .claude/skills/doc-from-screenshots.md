---
description: Generate Mintlify documentation from screenshots, voiceover transcripts, and written context
tags: [documentation, mintlify, content-generation]
---

# Documentation from Screenshots

Generate comprehensive Mintlify documentation from UI screenshots, voiceover transcripts, and brief written context.

## Usage

Invoke this skill when you need to:
- Document a new feature based on UI screenshots
- Create user guides from screen recordings with voiceovers
- Write reference documentation for complex interfaces
- Document reports, dashboards, or data views

## Input Requirements

Before invoking this skill, gather:

1. **Screenshots**: All relevant UI screens showing:
   - Full interface views
   - Important states (empty states, loaded data, error states)
   - Filter panels and control sections
   - Tables, charts, and data visualizations
   - Actions/buttons and their effects

2. **Voiceover transcript** (if available): Verbal explanations of:
   - What each section does
   - How users interact with features
   - Common workflows
   - Important caveats or edge cases

3. **Written context**:
   - Feature purpose and user benefit
   - Target audience (roles/permissions)
   - Related features or pages
   - Metric definitions or business logic
   - Any special configuration requirements

## Process

When you invoke this skill with the required inputs, I will:

### 1. Analyze and organize information

- Review all screenshots to understand UI structure
- Parse voiceover transcript for key explanations
- Identify main sections and subsections
- Map screenshots to content sections
- Note important caveats and edge cases

### 2. Structure the documentation

Create a hierarchical outline using:
- **h3 (`###`)**: Main feature sections
- **h4 (`####`)**: Major subsections (Filters, Actions, Data sections)
- **h5 (`#####`)**: Deeper nesting if needed (rare)

### 3. Select appropriate Mintlify components

Based on content type:

**`<Info>` blocks** for:
- Important contextual notes users should know upfront
- Warnings about edge cases or limitations
- Contact support prompts
- Configuration requirements

**`<AccordionGroup>` and `<Accordion>` for:
- Long lists of metric/field definitions
- Reference material users don't need every time
- Detailed technical explanations
- Multiple related definitions grouped together

**`<Tabs>` and `<Tab>` for:
- UI sections that actually use tabs
- Multiple equally-important related sections
- Alternative views or approaches

**`<Frame>` for:
- All screenshots (always with caption and alt text)
- Strategic placement after section introductions
- Showing specific UI elements being discussed

**`<Steps>` for:
- Sequential procedures
- Multi-step workflows
- Setup instructions

### 4. Write content following patterns

**For filters and controls:**
```mdx
- **Filter name**: Description of what it filters. Default behavior and options.
- **Another filter**: Description with examples (e.g. Lunch, Dinner)
```

**For actions/buttons:**
```mdx
- **Action name**: What happens when you click it
- **Export to PDF**: Download the report as a PDF file
```

**For metric definitions:**
```mdx
- **Metric name**: Clear definition. Include formula if calculated (e.g. Net sales = Gross sales - Discounts)
- **Tax**: Explanation including tax-inclusive vs tax-exclusive handling
```

**For tables/data displays:**
```mdx
View a breakdown of [what the table shows], organized by [organization method]. This table shows:
- Column name and meaning
- Another column
- Calculated columns with formulas
```

### 5. Place images strategically

- **Overview image**: After main feature intro, before diving into sections
- **Section images**: After explaining what section shows, before field details
- **Contextual images**: When referencing specific UI elements to click

### 6. Apply writing style

- Use sentence case for all titles and headings
- Keep explanations concise and scannable
- Use active voice ("Click the button" not "The button can be clicked")
- Provide context on why features matter
- Include parenthetical examples for clarity
- Show formulas for calculated metrics
- Link to related documentation
- Escape dollar signs with `\$` when needed

### 7. Generate complete MDX file

Create the documentation file with:

```mdx
---
title: "Feature name in sentence case"
description: "Brief description of what this feature does and why users need it"
---

<Info>
**Who is this article for?**
- Atlas users with [required permissions]
- [Other relevant audience]
</Info>

## Main feature introduction

Brief paragraph explaining what this feature is, why it's useful, and where to find it.

### Main section name

Overview of this section's purpose.

<Frame caption="Descriptive caption for screenshot">
  <img src="/images/path/to/image.png" alt="Detailed alt text describing what's shown" />
</Frame>

#### Subsection name

Content explaining this subsection...

- **Field name**: Description of field
- **Another field**: Description with example (e.g. specific example)

<AccordionGroup>
  <Accordion title="Detailed definitions">
    - **Term 1**: Definition...
    - **Term 2**: Definition...
  </Accordion>
</AccordionGroup>

<Info>
Important note or caveat users should be aware of.
</Info>

### Another main section

...continue pattern...
```

## Output

I will provide:

1. **Complete MDX file** with:
   - Proper frontmatter (title, description)
   - Appropriate Mintlify components
   - Well-organized hierarchical structure
   - Strategic image placement
   - Clear, concise explanations

2. **Image file checklist** showing:
   - Required screenshots to be saved
   - Suggested filenames following conventions
   - Recommended image locations in `/images/`

3. **Navigation update suggestion**:
   - Where to add this page in `docs.json`
   - Suggested icon from Font Awesome
   - Appropriate group placement

## Example invocation

```
I need to document the Daily Sales Report feature. I have:

Screenshots:
- Full report view showing filters, sales summary, and product breakdown
- Filter panel expanded with date range picker
- Export menu showing PDF and print options
- Sales summary with unsettled orders highlighted

Voiceover explains:
- Report shows sales for a specific date and outlet
- Filters include date, outlet, and shift options
- Sales summary shows gross sales, discounts, net sales, tax
- Unsettled orders are highlighted when present
- Users can export to PDF or print summary receipt
- Product breakdown shows items sold with quantities and revenue

Context:
- For admin users tracking daily revenue
- Sales day can be customized (default 12AM-12AM)
- Metrics include tax for tax-inclusive outlets
- Links to unsettled orders page when applicable
```

## Quality checklist

Before finalizing, I verify:
- [ ] All headings use sentence case
- [ ] Dollar signs escaped where needed (`\$`)
- [ ] Every image has caption and alt text
- [ ] Info blocks used for important notes
- [ ] Long definitions in accordions
- [ ] Tabs used appropriately (not overused)
- [ ] Terminology consistent throughout
- [ ] User benefit clearly stated
- [ ] Related content linked
- [ ] Screenshots referenced match provided images
- [ ] Frontmatter complete and accurate

## Notes

- This skill generates documentation that matches the established patterns in the Atlas documentation
- Follow the component selection guide strictly to maintain consistency
- Always prioritize clarity and scannability over completeness
- When in doubt, use simpler components (plain lists over complex accordions)
- Images should enhance understanding, not duplicate written content
