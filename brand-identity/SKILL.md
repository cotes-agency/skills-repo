---
name: brand-identity
description: Build a complete brand identity from scratch or audit and polish an existing one. Covers brand strategy (purpose, values, personality, archetypes), storytelling, voice and tone, visual identity system (colors, typography, logo usage, imagery, CSS design tokens), and creating a formal Brand Guidelines Document. Use when creating a new brand, rebranding, or when a client needs to formalize and document their existing visual identity. Trigger on "create my brand", "brand identity", "brand guidelines", "define my brand voice", "brand personality", "what should my brand look like", "brand strategy", "rebrand", "audit brand", "document brand identity", "improve client brand".
---

# Brand Identity

## Overview
Brand identity is the system of signals that makes a business instantly recognizable and trustworthy. A strong, consistent brand elevates the perceived value of any business, helping it attract high-value clients and build trust. This playbook guides you through building a brand from strategy down to execution, or auditing an existing brand to create a cohesive Brand Guidelines Document.

Getting the strategy wrong and then designing around it is the #1 brand mistake. Strategy must always precede visual execution.

---

## Phase 0: Context Gathering & Track Selection

**0.1 Automatic Context Search**
Before asking the user any questions, the Agent MUST scan the root workspace for any existing documents that could provide context (e.g., knowledge bases, `README.md`, marketing strategy docs, or business plans). Use this context to avoid asking repetitive questions.

**0.2 Track Selection**
After gathering available context, the Agent MUST ask the user: **"Are we creating a brand completely from scratch (Track A), or are we auditing and documenting an existing brand that already has some assets like a logo or colors (Track B)?"**

### Track A: Creation from Scratch (Rebranding / New Business)
Follow all steps in Phase 1 through Phase 4 in order. Do not skip strategy.

### Track B: Audit, Polish & Document (Existing Clients)
1. **Asset Collection:** Ask the user to provide the existing logo, website URL, current color codes, or any existing marketing materials.
2. **Reverse-Engineering Strategy:** Help the user deduce their Phase 1 (Purpose, Values, Archetype) based on what they are currently doing or want to project.
3. **Refinement:** Polish existing colors (e.g., tweaking a harsh red into a more balanced tone) and define rules for existing logos instead of creating new ones.
4. **Documentation:** Compile everything into Phase 4 (Brand Guidelines Document).

---

## Phase 1: Brand Foundations (Strategy & Storytelling)

Do not pick colors or logos until these are locked. Everything visual flows from here.

**1.1 Brand Purpose**
Why does this business exist beyond making money? One sentence. This is the north star for every brand decision.
*Example: "To give independent consultants the client-facing polish that enterprise teams get for free."*

**1.2 Brand Values (pick exactly 3)**
Values are the principles the brand consistently embodies. Three is the sweet spot.
*Choose from or write your own:* Simplicity, Trustworthiness, Innovation, Warmth, Efficiency, Boldness, Transparency, Craftsmanship.
For each value, write one sentence describing what it looks like in practice.

**1.3 Brand Archetype & Personality**
- **Archetype:** Define the core psychological archetype that drives the brand (e.g., The Creator, The Sage, The Hero, The Rebel, The Everyman).
- **Personality:** Describe the brand as if it were a person at a party. Use spectrums (Serious vs. Playful, Traditional vs. Modern). Write 3-5 sentences describing this person.

**1.4 Brand Storytelling & Narrative**
Define the core narrative or origin story. What is the "Hero's Journey" for the customer, and how does the brand act as the guide? Keep it to a short, compelling paragraph that sales and marketing can use.

**1.5 Target Audience Reminder**
Define the primary persona. The brand must resonate with THEM.

---

## Phase 2: Voice and Tone

Voice is who you are. Tone is how you adjust based on context.

**2.1 Define Your Voice (3 adjectives)**
Pick three words that describe how the brand always sounds. (e.g., "Clear, confident, human")

**2.2 Voice Do's and Don'ts**
For each of the three voice words, write:
- One thing you ALWAYS do (e.g., "Use plain language.")
- One thing you NEVER do (e.g., "Never use corporate jargon.")

**2.3 Tone Adjustments by Context**
Define how the tone shifts for: Marketing copy, Error messages, Success moments, Support interactions, and Social media.

---

## Phase 3: Visual Identity System & Design Tokens

### 3.1 Color Palette
*(Track B: Use existing colors as a base, refine for accessibility).*
Define Primary, Secondary, Neutral (Background/Text), and Accent/Alert colors.
**Requirement:** Provide hex codes, rules of use, AND CSS variables.

### 3.2 Typography
Pick two typefaces (Heading and Body). Both must be web-safe or Google Fonts.
**Requirement:** Define scales, weights, AND CSS variables.

### 3.3 CSS Design Tokens (For Web Development)
Compile the visual decisions into actionable CSS root variables so the development team can immediately implement the brand.
*Example output:*
```css
:root {
  --color-primary: #1A202C;
  --color-secondary: #2B6CB0;
  --color-background: #F7FAFC;
  --color-text: #2D3748;
  --font-heading: 'Outfit', sans-serif;
  --font-body: 'Inter', sans-serif;
}
```

### 3.4 Logo Direction & Rules
Define rules for safe space, minimum size, color variations, and dark/light mode usage.

### 3.5 Imagery Style
Define the visual style of photos, illustrations, and graphics (e.g., Bright and airy, Abstract illustrations, People-focused).

---

## Phase 4: Brand Guidelines Document

Compile everything above into a single reference document. Structure:

```text
1. Brand Strategy (Purpose, Values, Archetype, Narrative)
2. Brand Personality & Voice (Do's/Don'ts, Tone by Context)
3. Visual Identity (Color Palette & Typography)
4. CSS Design Tokens (Ready-to-use code snippet)
5. Logo Usage (Rules, variations)
6. Imagery Style
7. Brand Decision Filter
```

---

## Brand Consistency Checklist (Ongoing)
Every time a new asset is created, run it through:
- [ ] Uses only brand colors (no random colors creeping in)
- [ ] Uses only brand fonts
- [ ] Tone matches the context-specific tone guide
- [ ] Imagery matches defined style
- [ ] Logo usage follows the rules
