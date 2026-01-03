# Mac Leather Dashboard Documentation

User documentation for Mac Leather Dashboard, built with [Mintlify](https://mintlify.com).

**Live site:** https://help.macleather.co.uk

---

## Setup

### Prerequisites

- Node.js 18+
- npm or yarn

### Install Mintlify CLI

```bash
npm i -g mintlify
```

### Run Locally

```bash
cd macleather-docs
mintlify dev
```

Opens at `http://localhost:3000`

### Troubleshoot Local Dev

```bash
mintlify install  # Reinstall dependencies
```

---

## Deployment

This repo auto-deploys via Mintlify when pushing to `main`.

### Manual Deploy

1. Push changes to `main` branch
2. Mintlify detects changes automatically
3. Site rebuilds in ~2-3 minutes
4. Check https://help.macleather.co.uk

### Force Rebuild

If deployment seems stuck:

```bash
git commit --allow-empty -m "Trigger rebuild"
git push
```

---

## Project Structure

```
macleather-docs/
├── mint.json              # Navigation and site config
├── introduction.mdx       # Homepage
├── quickstart.mdx         # Getting started guide
├── samples/               # Sample management docs
├── production/            # Production order docs
├── exports/               # Shipment/export docs
├── procurement/           # Purchase order docs
├── customers/             # Customer-specific requirements
├── templates/             # Document templates
├── reference/             # Quick reference material
└── images/                # Image assets
```

---

## Adding New Content

### 1. Create the MDX File

```bash
# Example: Add a new guide in samples
touch samples/new-guide.mdx
```

### 2. Add Frontmatter

Every MDX file needs frontmatter:

```mdx
---
title: "Page Title"
description: "Brief description for SEO"
icon: "icon-name"
---
```

**Icon options:** See [Font Awesome icons](https://fontawesome.com/icons) (use name without `fa-` prefix)

### 3. Add to Navigation

Edit `mint.json`:

```json
{
  "group": "Samples",
  "pages": [
    "samples/overview",
    "samples/new-guide"  // Add here
  ]
}
```

### 4. Write Content

Use Mintlify components:

```mdx
## Section Title

Regular paragraph text.

<Steps>
  <Step title="First step">
    Description of step
  </Step>
  <Step title="Second step">
    Another description
  </Step>
</Steps>

| Column 1 | Column 2 |
|----------|----------|
| Data     | Data     |

<Info>
Informational callout
</Info>

<Warning>
Warning callout
</Warning>

<AccordionGroup>
  <Accordion title="FAQ Question">
    Answer here
  </Accordion>
</AccordionGroup>
```

---

## Content Guidelines

### Style Rules

1. **Software user guide style** - Focus on UI, fields, navigation
2. **No business advice** - Only how to use the system
3. **Tables for field references** - Not paragraphs
4. **Steps for procedures** - Use `<Steps>` component
5. **Troubleshooting in accordions** - Every action page needs these

### Writing Checklist

- [ ] Frontmatter with title, description, icon
- [ ] Clear navigation path (Location: Sidebar → Section)
- [ ] Field/column tables
- [ ] Step-by-step procedures
- [ ] Troubleshooting section (if action-oriented page)
- [ ] Related guides links at bottom

---

## Image Guidelines

### Location

Store images in `/images/` folder:

```
images/
├── logo-dark.svg
├── logo-light.svg
├── favicon.svg
├── screenshots/
│   ├── sample-detail.png
│   └── production-list.png
└── diagrams/
    └── workflow.png
```

### Usage in MDX

```mdx
![Alt text](/images/screenshots/sample-detail.png)
```

### Requirements

| Type | Format | Max Size | Dimensions |
|------|--------|----------|------------|
| Screenshots | PNG | 500KB | 1200px wide max |
| Diagrams | PNG/SVG | 200KB | As needed |
| Icons | SVG | 50KB | 24x24 or 32x32 |

### Best Practices

1. **Compress images** before adding
2. **Use descriptive filenames** (`sample-material-status.png` not `img1.png`)
3. **Add alt text** for accessibility
4. **Crop to relevant area** - no full-screen screenshots

---

## Adding Customer Pages

Use this template for new customer requirement pages:

### Template

```mdx
---
title: "[Customer] Requirements"
description: "Labeling, packing, and documentation requirements for [Customer]"
icon: "building"
---

# [Customer] Requirements

This guide covers requirements for [Customer] shipments.

<Warning>
[Key compliance warning]
</Warning>

---

## Carton Label

### Label Layout

\`\`\`
[ASCII diagram of label]
\`\`\`

### Label Elements

| Element | Position | Format/Requirement |
|---------|----------|-------------------|
| Logo | Top | [Customer] logo |
| PO Number | Upper | [Format] |

### Label Specifications

| Specification | Requirement |
|---------------|-------------|
| Size | [X]mm × [Y]mm |
| Barcode Type | Code 128 / EAN-13 |

### Download Templates

<Card title="Carton Label Template" icon="download" href="#">
  Download template
</Card>

---

## Product Label

### Product Label Specifications

| Specification | Requirement |
|---------------|-------------|
| Size | [X]mm × [Y]mm |
| Material | [Card weight] |

---

## Packing Requirements

### Carton Specifications

| Specification | Requirement |
|---------------|-------------|
| Maximum Weight | [X] kg |
| Maximum Dimensions | [L] × [W] × [H] cm |

### Packing Rules

<AccordionGroup>
  <Accordion title="Size Sorting">
    **Rule:** [Single size / Mixed allowed]
  </Accordion>

  <Accordion title="Poly Bagging">
    **Rule:** [Requirements]
  </Accordion>

  <Accordion title="Sealing Method">
    **Rule:** [H-seal / I-seal / Other]
  </Accordion>
</AccordionGroup>

---

## Required Documents

| Document | Required | Specifications |
|----------|----------|----------------|
| Commercial Invoice | Yes | [X] copies |
| Packing List | Yes | [Details] |
| Certificate of Origin | Yes | [Type] |

---

## Troubleshooting

<AccordionGroup>
  <Accordion title="[Common issue]">
    **Cause:** [Why it happens]

    **Solution:** [How to fix]
  </Accordion>
</AccordionGroup>

---

## Quick Reference Checklist

Before shipping to [Customer], verify:

- [ ] [Checklist item 1]
- [ ] [Checklist item 2]

---

## Related Guides

<CardGroup cols={2}>
  <Card title="Customer Overview" icon="users" href="/customers/overview">
    Compare all customer requirements
  </Card>
</CardGroup>
```

### Steps to Add

1. Copy template to `customers/[customer-name].mdx`
2. Replace `[Customer]` placeholders
3. Fill in specifications
4. Add to `mint.json` navigation under Customers group
5. Update `customers/overview.mdx` comparison table

---

## Mintlify Components Reference

### Callouts

```mdx
<Info>Informational note</Info>
<Tip>Helpful tip</Tip>
<Warning>Warning message</Warning>
<Note>General note</Note>
```

### Steps

```mdx
<Steps>
  <Step title="Step 1">Content</Step>
  <Step title="Step 2">Content</Step>
</Steps>
```

### Cards

```mdx
<Card title="Title" icon="icon-name" href="/path">
  Description
</Card>

<CardGroup cols={2}>
  <Card>...</Card>
  <Card>...</Card>
</CardGroup>
```

### Accordions

```mdx
<AccordionGroup>
  <Accordion title="Question 1">Answer</Accordion>
  <Accordion title="Question 2">Answer</Accordion>
</AccordionGroup>
```

### Mermaid Diagrams

```mdx
\`\`\`mermaid
flowchart LR
    A[Start] --> B[End]
\`\`\`
```

---

## System Codes

| Code | Format | Example |
|------|--------|---------|
| SMP | SMP-YYYY-XXX | SMP-2026-042 |
| PRD | PRD-YYYY-XXX | PRD-2026-015 |
| JC | JC-YYYY-XXXXX | JC-2026-00142 |
| PO | PO-YYYY-XXX | PO-2026-088 |
| SHP | SHP-YYYY-XXX | SHP-2026-007 |

---

## Support

- **Mintlify Docs:** https://mintlify.com/docs
- **Issues:** Report in this repo
- **App Support:** https://app.macleather.co.uk
