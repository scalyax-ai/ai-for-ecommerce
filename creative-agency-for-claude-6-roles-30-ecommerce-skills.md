# Creative Agency for Claude: 6 Roles, 30 Ecommerce Skills

**How to use this:** Save each numbered code block as `.claude/skills/<name>/SKILL.md` inside a folder named `creative-agency`.
Add your product information using the template below, then paste the weekly production prompt into Claude Code.

## Workspace setup

Each skill has its own folder containing a `SKILL.md` file with `name` and `description` frontmatter, following [Claude’s skill format](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview).

```text
creative-agency/
  .claude/skills/
    strategist-intake/SKILL.md
    strategist-customer-research/SKILL.md
    strategist-competitor-research/SKILL.md
    strategist-angle-development/SKILL.md
    strategist-creative-brief/SKILL.md
    copywriter-hooks/SKILL.md
    copywriter-meta-copy/SKILL.md
    copywriter-ugc-scripts/SKILL.md
    copywriter-carousel-copy/SKILL.md
    copywriter-copy-review/SKILL.md
    designer-art-direction/SKILL.md
    designer-static-ads/SKILL.md
    designer-carousels/SKILL.md
    designer-creative-variants/SKILL.md
    designer-export-qa/SKILL.md
    ugc-director-creator-brief/SKILL.md
    ugc-director-shot-list/SKILL.md
    ugc-director-ai-production/SKILL.md
    ugc-director-edit/SKILL.md
    ugc-director-video-qa/SKILL.md
    media-buyer-measurement/SKILL.md
    media-buyer-campaign-setup/SKILL.md
    media-buyer-test-design/SKILL.md
    media-buyer-budget-scaling/SKILL.md
    media-buyer-launch/SKILL.md
    analyst-data-validation/SKILL.md
    analyst-performance-report/SKILL.md
    analyst-creative-diagnosis/SKILL.md
    analyst-fatigue/SKILL.md
    analyst-next-tests/SKILL.md
  inputs/
    brand.md
    claims.csv
    reviews.csv
    competitors.csv
    performance.csv
    assets/
  campaigns/
```

### Save as `inputs/brand.md`

```markdown
# Brand input

## Product
- Product name:
- Product page URL:
- SKU:
- What it does:
- Materials, dimensions, ingredients or specifications:
- What it does not do:
- Product assets and packaging references:
- Available inventory:
- Restricted claims or categories:

## Customer
- Country and language:
- Buying situation:
- Main problem:
- Main alternatives:
- Common objections:
- Customer research files:

## Offer
- Price and currency:
- Discount and eligibility:
- Bundle contents:
- Shipping cost:
- Delivery estimate:
- Return policy:
- Offer expiry, if real:

## Economics
- Net revenue per order, excluding tax:
- Product cost per order:
- Fulfillment and shipping subsidy:
- Payment fees:
- Expected returns and refunds allowance:
- Other variable costs:
- Required contribution after advertising:
- Approved target CPA:
- Approved weekly ad budget:
- Maximum acceptable test loss:

## Brand
- Voice:
- Words to use:
- Words to avoid:
- Colors:
- Fonts and licenses:
- Logo file:
- Approved examples:

## Meta account
- Ad account ID:
- Facebook Page and Instagram identity:
- Dataset or pixel ID:
- Catalog ID, if applicable:
- Website domain:
- Account currency and timezone:
- Reporting attribution setting:
- Purchase event status:
- Existing campaigns and exclusions:
- Available tools and account permissions:

## Production
- Static assets available:
- Video footage available:
- Creator permissions:
- Music and stock licenses:
- Image or video generation tools available:
- Publishing owner:
- Approved spend ceiling:
```

### Shared working rules

Paste these into the project’s `CLAUDE.md` so all 30 skills inherit them.

```markdown
# Creative agency operating rules

1. Read inputs/brand.md and relevant campaign files before working.
2. Work inside campaigns/<campaign-id>/. Use relative paths in handoffs.
3. Label information VERIFIED, HYPOTHESIS, EXAMPLE or MISSING.
4. A verified claim needs a source ID, source location and verification date.
5. Never invent customer quotes, reviews, sales, test results or product benefits.
6. Examples are illustrative and must never enter live ads as product facts.
7. Preserve approved product appearance, offer terms and claim wording.
8. Use the actual tools available. Never report an image, video, upload or
   campaign as completed without inspecting the resulting artifact or receipt.
9. If a rendering tool is unavailable, return production-ready source and mark
   the render BLOCKED. Do not call a prompt a finished ad.
10. Only the analyst assigns performance verdicts: KEEP, ITERATE, PAUSE or
    INCONCLUSIVE. Other roles may flag defects or stop unsafe spending.
11. Launch and budget changes require authorization covering the account,
    action and spend ceiling. Existing authorization remains valid.
12. Never put credentials, access tokens or personal customer data in outputs.
13. No em dashes.

## Handoff format

Every output ends with:
- Campaign ID:
- Artifact paths:
- Approved claim IDs:
- Decisions made:
- Missing inputs:
- Status: READY | NEEDS INPUT | BLOCKED
- Next skill:
- Exact instruction for the next skill:

## Creative identity

Use <campaign>_<angle>_<format>_<concept>_<variant>.
Example: storage_access_static_c01_v01.

Keep creative ID, concept ID, angle ID and variant ID in the manifest.
A placement resize retains the creative ID and adds a placement suffix.
A changed hook, visual or offer receives a new variant ID.
```

### Weekly production prompt

```text
Run this week's ecommerce creative cycle using inputs/brand.md.

Create campaigns/<date>-<product>/ and maintain handoff.md as the index.
Read the previous campaign's analyst outputs if available.

Run the five strategist skills in order. Turn the approved brief into:
- 3 static concepts, each with 2 hook variants
- 1 carousel containing 5 cards
- 2 UGC scripts, each with 2 alternative openings

Use the copywriter skills, then the designer and UGC director skills.
Produce actual media files using available tools and inspect the exports.
Record missing tools or assets as blockers.

Run measurement, campaign setup and test design before allocating spend.
Reduce the number of live tests if the approved budget cannot support them.
Prepare the launch package. Launch only within my existing account and
spend authorization; otherwise leave the concrete setup ready for review.

When performance data is available, run all five analyst skills and feed
next-tests.md into the next strategist cycle.

Do not invent evidence or performance. Do not treat unrendered prompts as ads.
```

## Strategist: 5 skills

### 01. `strategist-intake/SKILL.md`

```markdown
---
name: strategist-intake
description: Turn ecommerce product, offer and commercial inputs into a verified campaign foundation. Use before research or creative production.
---

# Strategist Intake

## Inputs
Read inputs/brand.md, inputs/claims.csv and the product page if accessible.

## Steps
1. Extract product, SKU, market, buying situation, offer and destination URL.
2. Check price, shipping, returns and inventory against supplied sources.
   Mark conflicts MISSING until resolved.
3. Create a claim ledger with:
   claim_id | exact claim | source | source location | date | allowed wording.
4. Separate product facts from benefits that still need evidence.
5. Calculate contribution before advertising:
   net revenue minus product cost, fulfillment, shipping subsidy, payment
   fees, refund allowance and other variable costs.
6. Calculate allowable CPA:
   contribution before advertising minus required contribution after ads.
   Keep this separate from any approved operational target CPA.
7. Identify production blockers and ask only for facts needed to proceed.

## Output
Write foundation.md containing:
- Product and audience summary
- Offer terms
- Claim ledger
- Economics and formulas
- Assumptions and blockers

## Example
"Two removable dividers" can be a product fact with a specification source.
"Get ready twice as fast" needs separate evidence and cannot be inferred.

## Handoff
Next skill: strategist-customer-research.
Request research into buying situations and objections using foundation.md.
```

### 02. `strategist-customer-research/SKILL.md`

```markdown
---
name: strategist-customer-research
description: Extract ecommerce buying situations, objections and customer language from real supplied or accessible evidence.
---

# Customer Research

## Inputs
foundation.md, reviews.csv, support themes, surveys and return reasons.

## Steps
1. Record each source's origin, date and limitations.
2. Remove personal identifiers. Deduplicate repeated reviews.
3. Code each relevant passage:
   situation | desired outcome | frustration | objection | alternative |
   purchase trigger | source ID.
4. Preserve exact quotes only when present in the source. Otherwise label
   wording as a paraphrase.
5. Count themes only within the actual sample and report its denominator.
6. Separate frequent themes from isolated but useful observations.
7. Turn themes into creative implications without inventing demographics.

## Output
Write customer-research.md with:
- Source inventory and sample limitations
- Evidence table
- Five prioritized buying situations, or fewer if evidence is insufficient
- Objection-to-proof map
- Language usable in copy
- Questions requiring additional research

## Example
Hypothesis: a drawer organizer may appeal to someone sharing a bathroom.
Research must establish that situation before treating it as a customer fact.

## Handoff
Next skill: strategist-competitor-research.
Pass the evidence table and unresolved customer questions.
```

### 03. `strategist-competitor-research/SKILL.md`

```markdown
---
name: strategist-competitor-research
description: Review ecommerce competitor offers, landing pages and visible Meta ads to identify testable positioning gaps.
---

# Competitor Research

## Inputs
foundation.md, customer-research.md and competitors.csv.

## Steps
1. Use supplied competitor URLs or request a relevant competitor list.
2. Inspect product pages and available Meta Ad Library entries.
3. Record URL, observation date, country filter and ad reference.
4. Capture hook, buying situation, proof type, offer, format and destination.
5. Distinguish observed creative from inferred strategy.
6. Do not infer spend, profitability or winning status from ad longevity.
7. Compare customer objections with the proof competitors visibly supply.
8. Identify opportunities grounded in the product's verified capabilities.

## Output
Write competitor-research.md:
competitor/source | observed message | proof | offer | format |
unanswered objection | potential test.

Include three differentiated opportunities if evidence supports them.

## Example
Observation: an ad shows an organized drawer.
Potential test: demonstrate divider adjustment before the finished drawer,
provided the product genuinely supports that adjustment.

## Handoff
Next skill: strategist-angle-development.
Pass opportunities, source links and copying risks.
```

### 04. `strategist-angle-development/SKILL.md`

```markdown
---
name: strategist-angle-development
description: Build distinct ecommerce ad angles from customer evidence, verified product mechanisms and competitive gaps.
---

# Angle Development

## Inputs
foundation.md, customer-research.md and competitor-research.md.

## Steps
1. Build six candidate angles across different buying situations, benefits
   or objections. Do not create six phrasings of the same idea.
2. For each angle specify:
   customer situation, tension, promise, product mechanism, claim IDs,
   visual demonstration, objection and reason to click.
3. Score relevance, proof strength, visual clarity and distinctiveness from
   1 to 5. These are planning judgments, not performance predictions.
4. Reject angles needing unsupported claims or misleading demonstrations.
5. Recommend up to three angles for the first production batch.
6. State what outcome would weaken each hypothesis.

## Output
Write angles.md with the full angle matrix and selected angle IDs.

## Example
A01: Find small items in a crowded drawer.
Mechanism: separate compartments.
Demonstration: place the same items into the actual organizer.
Avoid promising time savings without measured evidence.

## Handoff
Next skill: strategist-creative-brief.
Pass selected angles and their evidence requirements.
```

### 05. `strategist-creative-brief/SKILL.md`

```markdown
---
name: strategist-creative-brief
description: Convert selected ecommerce angles into an executable creative brief with deliverables, proof and measurable hypotheses.
---

# Creative Brief

## Inputs
foundation.md, angles.md and previous next-tests.md if available.

## Steps
1. Define one primary business goal and the approved target CPA.
2. Specify market, language, buying situation, offer and destination.
3. Assign angle IDs to static, carousel and UGC concepts.
4. For every concept define:
   opening, message, mechanism, proof shot, objection, CTA and claim IDs.
5. List deliverables with aspect ratio, quantity and production dependency.
6. Define the primary test variable and what stays constant.
7. Specify the reporting window, attribution setting and decision owner.
8. Reduce deliverables if evidence, assets or budget cannot support them.

## Output
Write brief.md and creative-manifest.csv.

Manifest fields:
creative_id,concept_id,angle_id,format,variant,test_variable,claim_ids,
destination,status,asset_path.

## Acceptance
Every concept has a visible product demonstration or supported proof.
Every offer matches the destination.
Every hypothesis has a measurable outcome.

## Handoff
Next skill: copywriter-hooks.
Pass brief.md, the manifest and allowed claims.
```

## Copywriter: 5 skills

### 06. `copywriter-hooks/SKILL.md`

```markdown
---
name: copywriter-hooks
description: Write distinct Meta ad openings tied to ecommerce buying situations and verified product demonstrations.
---

# Hooks

## Inputs
brief.md, angles.md and the claim ledger.

## Steps
1. Write twelve hooks per selected angle:
   three situation-led, three demonstration-led, three objection-led and
   three product-mechanism-led.
2. Keep static headlines within eight words as an editorial constraint.
3. Write spoken video hooks that fit approximately three seconds when read.
4. Pair each hook with a specific opening visual.
5. Remove unsupported superlatives, invented popularity and fake urgency.
6. Avoid asserting sensitive personal attributes about the viewer.
7. Select two distinct openings per concept and explain the hypothesis.

## Output
Write hooks.md:
hook_id | angle_id | exact text | opening visual | claim IDs | rationale.

## Example
For a verified adjustable organizer:
- "One drawer. Separate spaces."
- "Move the dividers. Change the layout."
These are draft examples, not verified product claims.

## Handoff
Next skill: copywriter-meta-copy.
Pass selected hook IDs and their matching visuals.
```

### 07. `copywriter-meta-copy/SKILL.md`

```markdown
---
name: copywriter-meta-copy
description: Write ready-to-paste Meta primary text, headlines and descriptions for approved ecommerce concepts.
---

# Meta Copy

## Inputs
brief.md, hooks.md, foundation.md and creative-manifest.csv.

## Steps
1. Write two primary-text options per concept:
   a concise version of 40 to 70 words and a developed version of 90 to
   130 words. These are editorial targets, not platform limits.
2. Structure each as situation, product mechanism, supported benefit,
   relevant offer and one CTA.
3. Supply three headline options of no more than 40 characters each.
4. Supply one optional description of no more than 30 characters.
5. Count characters and preserve offer conditions.
6. Map each copy set to its creative ID and destination URL.
7. Keep copy constant when the approved experiment changes only the visual.

## Output
Write meta-copy.md with clearly labeled paste fields and claim IDs.

## Example
Primary text opening:
"Small items need their own space. Arrange the removable dividers around
what you store, then see the layout before you put everything back."
Use only if the mechanism is verified.

## Handoff
Next skill: copywriter-ugc-scripts.
Pass video concepts and approved message language.
```

### 08. `copywriter-ugc-scripts/SKILL.md`

```markdown
---
name: copywriter-ugc-scripts
description: Write filmable ecommerce UGC scripts with synchronized speech, demonstrations and supported claims.
---

# UGC Scripts

## Inputs
brief.md, selected hooks, product assets and available creator information.

## Steps
1. Write two scripts targeting 20 to 35 seconds, unless the brief specifies
   another duration.
2. Use a timed table:
   time | spoken line | action | on-screen text | claim ID.
3. Open with the actual buying situation or product demonstration.
4. Show the mechanism before making the supported benefit claim.
5. Address one objection and finish with one CTA.
6. Provide two interchangeable opening segments per script.
7. Read aloud or estimate timing, then trim for natural delivery.
8. Use first-person experience only when the actual speaker confirms it.
   Otherwise write a demonstrator script without testimonial language.

## Output
Write ugc-scripts.md with scripts, opening alternatives and required props.

## Example
Speech: "Here's how the dividers move."
Action: close-up of an actual hand repositioning an actual divider.
Avoid: "This changed my mornings" unless it is the speaker's true experience.

## Handoff
Next skill: copywriter-carousel-copy.
Pass reusable mechanism and objection language.
```

### 09. `copywriter-carousel-copy/SKILL.md`

```markdown
---
name: copywriter-carousel-copy
description: Write complete ecommerce carousel card copy with a clear progression from buying situation to product proof and CTA.
---

# Carousel Copy

## Inputs
brief.md, claim ledger and selected concept.

## Steps
1. Write five cards:
   buying situation, mechanism, demonstration, objection and CTA.
2. Give each card a headline of up to eight words and supporting copy of
   up to twenty words as production constraints.
3. Specify the required product image or demonstration per card.
4. Ensure card one makes sense alone.
5. If sequence is essential, tell the buyer to preserve card order and
   verify any automatic ordering behavior in the live interface.
6. Use one offer consistently across the sequence.
7. Supply card headlines and destination URLs for the buyer's setup.

## Output
Write carousel-copy.md:
card number | headline | body | visual | claim IDs | destination.

## Example
Card 2 headline: "Set the compartments your way."
Visual: a real divider being moved.
Only use when supported by the actual product.

## Handoff
Next skill: copywriter-copy-review.
Pass all copy files and the manifest.
```

### 10. `copywriter-copy-review/SKILL.md`

```markdown
---
name: copywriter-copy-review
description: Audit ecommerce ad copy for claim accuracy, offer consistency, readability and production readiness.
---

# Copy Review

## Inputs
All copywriter outputs, foundation.md, brief.md and destination page.

## Steps
1. Match each factual claim to an approved claim ID.
2. Check prices, currencies, bundle contents, expiry, shipping and returns.
3. Remove invented testimonials, implied guarantees and unsupported results.
4. Check sensitive-attribute language and category-specific restrictions
   against applicable current Meta policies when relevant.
5. Check that each hook matches the first visual.
6. Read spoken scripts aloud and confirm one CTA per ad.
7. Produce corrected final copy, not just review comments.
8. Mark any unresolved factual issue BLOCKED.

## Output
Write copy-approved.md containing final paste-ready copy by creative ID.
Write copy-review.md containing changes, reasons and unresolved issues.

## Acceptance
No unsupported claim remains in approved copy.
No unresolved placeholder appears in a live copy field.
All offer details agree with the destination.

## Handoff
Next skills: designer-art-direction and ugc-director-creator-brief.
Send the relevant approved copy to each production route.
```

## Designer: 5 skills

### 11. `designer-art-direction/SKILL.md`

```markdown
---
name: designer-art-direction
description: Define a practical visual system for ecommerce Meta ads using real product assets and approved copy.
---

# Art Direction

## Inputs
brief.md, copy-approved.md, brand guidelines and product assets.

## Steps
1. Inventory usable product photos, logos, fonts and licenses.
2. Select one visual direction per concept:
   product demonstration, contextual product scene or annotated mechanism.
3. Define background, typography, spacing, product scale and CTA treatment.
4. Plan 1080x1350 feed and 1080x1920 vertical versions as production targets.
5. Keep critical content clear of interface overlays and verify placement
   previews rather than assuming a universal safe area.
6. Specify exact approved copy and claim IDs.
7. If imagery is generated, preserve product geometry, packaging and color.
   Composite a real product asset when generation cannot preserve fidelity.

## Output
Write art-direction.md with a layout specification for every concept.
Include asset paths, font choices, color values and copy placement.

## Example
Mechanism concept: real product photo fills the lower two-thirds;
one short headline above; one arrow identifies the removable divider.

## Handoff
Next skill: designer-static-ads.
Pass layout specifications and approved assets.
```

### 12. `designer-static-ads/SKILL.md`

```markdown
---
name: designer-static-ads
description: Produce actual static ecommerce ad files from approved layouts, product assets and copy.
---

# Static Ads

## Inputs
art-direction.md, copy-approved.md and approved product assets.

## Steps
1. Build an editable composition in an available design or code tool.
2. Use real product imagery or an approved generated background.
3. Render exact approved text as editable text whenever possible.
4. Produce every static creative ID requested by the brief.
5. Export feed and vertical versions without stretching the composition.
6. Inspect each exported image at full size and a phone-sized preview.
7. Correct product distortion, clipped type, weak contrast and illegible text.
8. Save source files alongside actual PNG or JPEG exports.

## Output
Write files to assets/statics/ and source/statics/.
Update creative-manifest.csv with real paths and dimensions.
Write static-production.md listing completed files and blockers.

## Acceptance
The exported file exists and opens.
Product details match references.
Text matches copy-approved.md character for character.

## Tool fallback
If rendering is unavailable, save an editable SVG or HTML composition when
possible and mark the missing raster export BLOCKED.

## Handoff
Next skill: designer-carousels.
Pass the visual system and production lessons.
```

### 13. `designer-carousels/SKILL.md`

```markdown
---
name: designer-carousels
description: Render a complete ecommerce carousel with consistent card layouts and approved card copy.
---

# Carousels

## Inputs
carousel-copy.md, copy-approved.md and art-direction.md.

## Steps
1. Use a consistent 1080x1080 canvas for all cards in the carousel.
2. Build five cards with stable type sizes, margins and product treatment.
3. Give each card one primary message and one focal visual.
4. Render exact approved copy.
5. Use real mechanism details rather than decorative invented features.
6. Export numbered cards and an overview contact sheet.
7. Inspect individual cards and the full sequence.
8. Ensure the offer and CTA remain clear if a viewer sees only one card.

## Output
Save assets/carousel/card-01.png through card-05.png.
Save source files, contact-sheet.png and carousel-production.md.
Update the manifest with card paths and intended order.

## Acceptance
No missing card, clipped element or repeated accidental text.
Card order matches the narrative.
All cards share the same aspect ratio.

## Handoff
Next skill: designer-creative-variants.
Pass completed static and carousel sources.
```

### 14. `designer-creative-variants/SKILL.md`

```markdown
---
name: designer-creative-variants
description: Produce controlled creative variants that isolate one ecommerce advertising hypothesis at a time.
---

# Creative Variants

## Inputs
Approved concepts, editable sources, hooks.md and the test variable.

## Steps
1. Identify the control and the variable to change.
2. For hook tests, change headline or opening copy while preserving visual,
   offer, destination and layout.
3. For visual tests, preserve copy and offer.
4. Do not quietly change product scale, color treatment and headline together.
5. Assign new variant IDs and record parent creative IDs.
6. Render all variants and produce a labeled contact sheet.
7. Describe the hypothesis without predicting a winner.

## Output
Save assets/variants/ and variants.md:
variant_id | parent_id | changed variable | unchanged elements |
hypothesis | file path.

## Example
V01: "One drawer. Separate spaces."
V02: "Move the dividers. Change the layout."
Both use the same verified product image and offer.

## Acceptance
A reviewer can identify the intended difference immediately.
Any unavoidable secondary changes are disclosed.

## Handoff
Next skill: designer-export-qa.
Pass every final image and its editable source.
```

### 15. `designer-export-qa/SKILL.md`

```markdown
---
name: designer-export-qa
description: Inspect and package static Meta ad assets with correct dimensions, readable copy and traceable creative IDs.
---

# Export QA

## Inputs
All final images, manifest, copy-approved.md and product references.

## Steps
1. Open every exported file and verify dimensions and aspect ratio.
2. Check text against approved copy.
3. Inspect product fidelity, logo, contrast, cropping and image sharpness.
4. Review phone-sized previews and placement previews when available.
5. Verify that placement adaptations retain the intended hierarchy.
6. Check file names against creative IDs and remove obsolete exports from
   the launch package.
7. Record file size and check current upload requirements if relevant.
8. Package final assets separately from drafts and contact sheets.

## Output
Write assets-approved.md:
creative_id | path | dimensions | file size | QA status | issue.
Save final delivery files under delivery/images/.

## Acceptance
Every READY row points to a verified, opening image.
Blocked files are excluded from the delivery folder.
No claim or offer mismatch remains.

## Handoff
Next skill: media-buyer-test-design.
Pass delivery paths, creative IDs and tested variables.
```

## UGC Director: 5 skills

### 16. `ugc-director-creator-brief/SKILL.md`

```markdown
---
name: ugc-director-creator-brief
description: Prepare an executable creator brief for ecommerce UGC with approved lines, demonstrations, deliverables and usage requirements.
---

# Creator Brief

## Inputs
ugc-scripts.md, copy-approved.md, product references and usage requirements.

## Steps
1. Specify audience situation, concept, product and single communication goal.
2. Include exact required lines and optional natural-language alternatives.
3. Identify demonstrations that must be captured with the real product.
4. Define wardrobe, setting, props, framing, lighting and clean audio.
5. Request a clean master without music or captions, plus separate raw clips.
6. Request two openings, a product demonstration, objection response,
   CTA and clean product close-ups.
7. Specify intended paid usage, territories, duration, editing permission
   and any partnership-ad permissions as terms requiring agreement.
8. Never invent a creator's personal experience or confirmation.

## Output
Write creator-brief.md with a filming checklist and delivery checklist.

## Example
Required action: move the divider in one uninterrupted close-up.
Required speech: "This divider can move."
Personal endorsement: optional only if true and confirmed by the speaker.

## Handoff
Next skill: ugc-director-shot-list.
Pass approved script and agreed production constraints.
```

### 17. `ugc-director-shot-list/SKILL.md`

```markdown
---
name: ugc-director-shot-list
description: Translate ecommerce UGC scripts into shot-by-shot filming instructions with verifiable product actions.
---

# Shot List

## Inputs
creator-brief.md, ugc-scripts.md and available product assets.

## Steps
1. Break each script into individual shots.
2. For each shot specify:
   shot ID, duration, framing, camera position, action, audio, prop,
   continuity requirement and claim ID.
3. Capture vertical 9:16 footage, targeting 1080x1920 or higher.
4. Use a consistent frame rate across planned footage.
5. Capture extra handles before and after each action for editing.
6. Include clean product views and room tone.
7. Keep before-and-after demonstrations comparable in framing and contents.
8. Mark shots that require a physical product and cannot be fabricated.

## Output
Write shot-list.md and footage-checklist.csv.

## Example
S03 | 3 seconds | overhead close-up | locked camera |
move one divider, then place an item inside | natural sound |
organizer and item | same drawer as S02 | claim C02.

## Handoff
Next skill: ugc-director-ai-production.
Pass only shots eligible for generation and flag real-product requirements.
```

### 18. `ugc-director-ai-production/SKILL.md`

```markdown
---
name: ugc-director-ai-production
description: Generate permitted ecommerce UGC components with reference-controlled prompts and strict product and testimonial accuracy.
---

# AI Production

## Inputs
shot-list.md, approved product references and available generation tools.

## Steps
1. Separate real-product proof shots from generatable illustrative scenes.
2. Use AI for suitable scenes, backgrounds or neutral presenter delivery.
3. Build one prompt per shot:
   reference assets, setting, framing, exact action, camera movement,
   duration, lighting, exact speech and continuity constraints.
4. Generate one representative shot and inspect product fidelity first.
5. Reject invented features, malformed hands and impossible product actions.
6. Never present an AI presenter as a real customer or give it fabricated
   personal results. Record required disclosures for the deployment context.
7. Preserve generation prompts, tool name, settings and source references.
8. If generation is unavailable, deliver prompts with status BLOCKED.

## Prompt example
"Vertical locked overhead shot using the attached organizer reference.
Preserve its exact compartment count and color. A hand places a key into
one existing compartment. No new parts, no text, no camera movement."

## Output
Save actual clips under assets/ugc/generated/ and ai-production.md.

## Handoff
Next skill: ugc-director-edit.
Pass accepted clips and rejected-shot reasons.
```

### 19. `ugc-director-edit/SKILL.md`

```markdown
---
name: ugc-director-edit
description: Edit approved ecommerce footage into finished Meta video ads with synchronized copy, product proof and clean exports.
---

# UGC Edit

## Inputs
Accepted footage, ugc-scripts.md, approved copy and licensed audio.

## Steps
1. Build a vertical 1080x1920 timeline using the footage's appropriate
   consistent frame rate.
2. Open immediately on the planned hook or demonstration.
3. Remove dead air while preserving the truth of product demonstrations.
4. Match each benefit line with the corresponding product action.
5. Add accurate burned-in captions and retain a clean master.
6. Use licensed music only and keep speech clearly intelligible.
7. Produce the planned opening variants while keeping the body constant.
8. Export MP4 using H.264 video and AAC audio as a practical delivery preset.
9. Watch the entire export with sound and again muted.

## Output
Save delivery/video/<creative-id>.mp4, clean masters, captions.srt and
editable project files or a reproducible render script.
Write edit-notes.md with durations and variant differences.

## Acceptance
No placeholder footage, missing media, clipped speech or unsupported claim.
Actual demonstration remains understandable at normal playback speed.

## Handoff
Next skill: ugc-director-video-qa.
Pass final exports, sources and rights records.
```

### 20. `ugc-director-video-qa/SKILL.md`

```markdown
---
name: ugc-director-video-qa
description: Verify finished ecommerce UGC exports for factual accuracy, technical quality, rights and placement readiness.
---

# Video QA

## Inputs
Final videos, copy-approved.md, product references and usage records.

## Steps
1. Play every file from beginning to end.
2. Verify dimensions, duration, audio, captions and first-frame readability.
3. Compare spoken and on-screen claims with the claim ledger.
4. Check product geometry, continuity and action accuracy.
5. Confirm permissions for creator footage, music, stock and synthetic media.
6. Check captions and product visibility in placement previews when possible.
7. Confirm each opening variant has the correct creative ID.
8. Exclude rejected exports from the launch folder.

## Output
Write videos-approved.md:
creative_id | path | duration | dimensions | claim check | rights |
technical QA | status.

## Acceptance
Only verified exports receive READY.
Missing usage permission or unsupported claims receive BLOCKED.
Production QA is not a prediction of ad performance.

## Handoff
Next skill: media-buyer-test-design.
Pass approved videos, creative IDs and opening variables.
```

## Media Buyer: 5 skills

Meta’s Sales objective supports finding people likely to purchase. The setup below uses website purchases as the default ecommerce route; confirm the fields available in the actual account. [Meta Sales objective guidance](https://business-auth.facebook.com/business/m/conversion-campaign)

### 21. `media-buyer-measurement/SKILL.md`

```markdown
---
name: media-buyer-measurement
description: Validate ecommerce purchase measurement before Meta campaign launch and document reporting limitations.
---

# Measurement

## Inputs
foundation.md, account details, store access and Events Manager access.

## Steps
1. Confirm account currency, timezone, domain and intended dataset.
2. Test the purchase journey using an authorized test order when available.
3. Inspect Purchase value, currency and event timing.
4. Where browser and server events represent the same purchase, verify
   consistent event IDs and deduplication in the available diagnostics.
5. Check duplicate installations, missing events and obvious value errors.
6. Inspect consent behavior under the store's actual consent configuration.
7. Compare recent store orders with tracked events over matching periods.
   Explain why platform-attributed purchases need not equal store orders.
8. Record the attribution setting and expected reporting delay.
9. Do not place customer-level data in the handoff.

## Output
Write measurement.md:
check | observed evidence | status | fix owner | launch impact.

## Acceptance
Unverified Purchase measurement blocks a conversion launch until resolved
or explicitly accepted by the authorized owner with limitations recorded.

## Handoff
Next skill: media-buyer-campaign-setup.
Pass verified dataset, event and reporting settings.
```

### 22. `media-buyer-campaign-setup/SKILL.md`

```markdown
---
name: media-buyer-campaign-setup
description: Build an explicit Meta ecommerce campaign configuration tied to purchase measurement, market and approved assets.
---

# Campaign Setup

## Inputs
brief.md, measurement.md, approved assets and account constraints.

## Steps
1. Draft a settings table before creating anything.
2. Default purchase setup:
   objective Sales; conversion location Website; verified dataset;
   optimization event Purchase; performance goal maximizing conversions.
   Confirm current interface labels and account eligibility.
3. Use the approved selling countries and genuine age or legal constraints.
4. Start with broad eligible targeting unless the brief supplies a
   testable reason for a narrower audience.
5. Use Advantage+ placements as a starting option when assets support them.
   Document any placement restriction and its reason.
6. Use highest-volume delivery as a starting bid approach unless approved
   economics and account history support another strategy.
7. Record existing-customer exclusions only where available and appropriate.
8. Specify budget location, schedule, attribution and account timezone.
9. Prevent overlap with existing tests where practical.

## Output
Write campaign-setup.md with every selected field, source and rationale.
Mark unsupported or unavailable settings for verification.

## Handoff
Next skill: media-buyer-test-design.
Pass the setup and account constraints.
```

### 23. `media-buyer-test-design/SKILL.md`

```markdown
---
name: media-buyer-test-design
description: Design affordable Meta creative tests with explicit variables, decision rules and limitations.
---

# Test Design

## Inputs
campaign-setup.md, manifest, target CPA, weekly budget and maximum test loss.

## Steps
1. Define the question, control, variants and primary outcome.
2. Prefer purchase CPA or contribution economics as the primary outcome.
   Treat click and video metrics as diagnostics.
3. For causal comparisons, use an available randomized experiment method.
   Record any limitation preventing that design.
4. If ads share an ad set, label results directional because delivery and
   spend will be uneven.
5. Calculate affordable test cells:
   test budget divided by the planned spend allowance per cell.
   This is a funding calculation, not a statistical sample-size guarantee.
6. Reduce simultaneous variants when the budget is insufficient.
7. Predeclare review timing, conversion-delay allowance and maximum loss.
8. Define analyst decision criteria before spend begins.
9. Keep offer, destination and audience constant for a creative-only test.

## Output
Write test-plan.md:
test_id | hypothesis | control | variant | allocation | budget |
primary outcome | review date | stop conditions | inference limits.

## Handoff
Next skill: media-buyer-budget-scaling.
Pass the funded test plan and loss limits.
```

### 24. `media-buyer-budget-scaling/SKILL.md`

```markdown
---
name: media-buyer-budget-scaling
description: Translate approved ecommerce budgets and analyst verdicts into capped Meta spending and scaling actions.
---

# Budget and Scaling

## Inputs
test-plan.md, approved budget, economics and analyst verdicts if available.

## Steps
1. Allocate the approved total between existing proven delivery and funded
   experiments. Use account evidence rather than a universal split.
2. Set daily budgets from the intended active days and verify platform
   pacing behavior. Do not treat a daily budget as an absolute daily cap.
3. Use available campaign or account spending controls when appropriate.
4. Define account-level monitoring and maximum acceptable test loss.
5. Scale only creatives or campaigns with an analyst KEEP verdict and
   adequate inventory, margin and measurement.
6. As a conservative operating experiment, propose a 10% budget increase
   followed by a 72-hour review, extending for conversion delay.
   This is a chosen rule, not a Meta requirement or performance guarantee.
7. Evaluate marginal CPA and contribution after the increase.
8. Roll back or hold when the analyst's predefined criteria fail.
9. Never exceed the user's authorized spend ceiling.

## Output
Write budget-plan.md with current budget, proposed budget, change,
rationale, review date, rollback rule and authorization status.

## Handoff
Next skill: media-buyer-launch.
Pass the exact authorized budget schedule.
```

### 25. `media-buyer-launch/SKILL.md`

```markdown
---
name: media-buyer-launch
description: Assemble, verify and launch authorized Meta ecommerce campaigns, preserving an exact launch receipt and rollback path.
---

# Launch

## Inputs
Measurement, setup, test and budget plans; approved assets; authorization.

## Steps
1. Confirm ad account, identities, market, currency, timezone and spend scope.
2. Create or prepare the campaign and ad sets using the exact setup table.
3. Attach assets and final copy by creative ID.
4. Verify landing pages, offer terms and mobile checkout.
5. Add URL parameters:
   utm_source={{site_source_name}}
   utm_medium=paid_social
   utm_campaign={{campaign.id}}
   utm_content={{ad.id}}
   Use valid separators and confirm available macros and resolved URLs.
6. Maintain an ad-ID-to-creative-ID mapping outside the URL.
7. Inspect all placement previews and disable unintended transformations
   where the interface permits and the test requires fixed creative.
8. If launch authorization exists, publish within its ceiling.
   Otherwise leave the concrete setup unpublished for review.
9. Record platform IDs, delivery status, budgets and timestamps.
10. Check delivery, links and spend after launch. Record how to pause.

## Output
Write launch-receipt.md and ad-map.csv.
Never label a draft as live or a published ad as delivering without evidence.

## Handoff
Next skill: analyst-data-validation.
Pass IDs, settings, launch time and scheduled review time.
```

## Analyst: 5 skills

### 26. `analyst-data-validation/SKILL.md`

```markdown
---
name: analyst-data-validation
description: Validate Meta and store data before ecommerce performance analysis, preserving attribution and aggregation boundaries.
---

# Data Validation

## Inputs
performance.csv, store aggregates, ad-map.csv and launch-receipt.md.

## Steps
1. Request date, campaign/ad-set/ad IDs, spend, impressions, reach,
   outbound clicks, landing-page views, purchases and purchase value.
2. Request video metrics only if relevant and available.
3. Record currency, timezone, attribution setting and export time.
4. Map every ad to its creative, concept, angle and variant.
5. Check duplicate rows, missing dates and campaign-level totals.
6. Never add reach across overlapping rows and call it unique reach.
7. Flag immature conversion windows and recent incomplete days.
8. Separate Meta-attributed revenue from store revenue.
9. Exclude invalid rows transparently and preserve the raw export.

## Output
Write data-quality.md and performance-clean.csv.
List missing fields and the conclusions they prevent.

## Example
If purchase value is absent, CPA may still be calculated.
ROAS cannot be reconstructed from clicks or order count alone.

## Handoff
Next skill: analyst-performance-report.
Pass cleaned data, exclusions and attribution limitations.
```

### 27. `analyst-performance-report/SKILL.md`

```markdown
---
name: analyst-performance-report
description: Report ecommerce Meta performance against approved economics and assign evidence-based creative verdicts.
---

# Performance Report

## Inputs
performance-clean.csv, data-quality.md, economics and test-plan.md.

## Steps
1. Calculate:
   CPM = spend / impressions * 1000.
   Outbound CTR = outbound clicks / impressions.
   CPC = spend / outbound clicks.
   LPV rate = landing-page views / outbound clicks.
   Purchase CVR = attributed purchases / landing-page views.
   CPA = spend / attributed purchases.
   ROAS = attributed purchase value / spend.
2. Return undefined for zero denominators rather than fabricated zeros.
3. Report spend and outcome counts alongside rates.
4. Compare CPA with the approved target using mature attribution windows.
5. Where valid inputs exist, estimate contribution after ads and state
   attribution, margin and refund assumptions.
6. Assign KEEP, ITERATE, PAUSE or INCONCLUSIVE using predeclared criteria.
7. Do not declare a statistical winner from small or unequal delivery.
8. Distinguish observed results, interpretation and recommended action.

## Output
Write performance-report.md with:
- Account summary
- Creative and angle tables
- Verdicts and reasons
- Economics limitations
- Required actions

## Handoff
Next skill: analyst-creative-diagnosis.
Pass verdicts, counts and unresolved questions.
```

### 28. `analyst-creative-diagnosis/SKILL.md`

```markdown
---
name: analyst-creative-diagnosis
description: Diagnose ecommerce creative and funnel weaknesses without confusing correlated metrics with proven causes.
---

# Creative Diagnosis

## Inputs
Performance report, actual creatives, landing pages and test design.

## Steps
1. Inspect the actual ad before interpreting its metrics.
2. Compare like-for-like delivery periods, audiences and placements.
3. Examine the sequence:
   impression, outbound click, landing-page view, purchase.
4. Low outbound CTR can motivate a hook or relevance test.
5. Low LPV rate can motivate URL, speed or accidental-click checks.
6. Low purchase CVR can motivate offer, message-match or checkout checks.
7. Strong click metrics with weak purchases do not establish a good ad.
8. Use placement breakdowns cautiously when volumes are small.
9. Recommend one primary variable for the next iteration.
10. State alternative explanations and the evidence needed to distinguish them.

## Output
Write creative-diagnosis.md:
creative_id | observation | possible explanation | competing explanation |
next test | success measure.

## Example
Observation: clicks increased while mature purchases did not.
Hypothesis: the opening attracts curiosity beyond buying intent.
Test: show the product and price context earlier while preserving the offer.

## Handoff
Next skill: analyst-fatigue.
Pass creative-level trends and suggested controls.
```

### 29. `analyst-fatigue/SKILL.md`

```markdown
---
name: analyst-fatigue
description: Assess whether deteriorating Meta creative performance is consistent with fatigue or another ecommerce delivery problem.
---

# Fatigue Assessment

## Inputs
Time-series performance, change log, creative IDs and audience information.

## Steps
1. Compare two complete periods of equal length and equivalent weekdays.
2. Account for conversion delay and avoid comparing a mature period with
   a partially attributed recent period.
3. Review CPA, outbound CTR, CPM, reach and frequency together.
4. Check budget edits, audience changes, promotions, inventory, site faults
   and attribution changes before blaming creative fatigue.
5. Treat rising frequency alone as insufficient evidence.
6. Identify whether deterioration is broad or concentrated by creative.
7. Classify fatigue evidence as supported, suspected or unsupported.
8. Recommend a fresh angle, revised opening, broader eligible reach or
   technical investigation based on the actual diagnosis.
9. Assign PAUSE only when the agreed economics or loss criteria justify it.

## Output
Write fatigue.md with comparison dates, metrics, confounders, classification
and recommended action.

## Handoff
Next skill: analyst-next-tests.
Pass confirmed issues and hypotheses requiring controlled tests.
```

### 30. `analyst-next-tests/SKILL.md`

```markdown
---
name: analyst-next-tests
description: Turn ecommerce advertising evidence into the next funded creative sprint and close the agency production loop.
---

# Next Tests

## Inputs
Performance report, creative diagnosis, fatigue assessment and production costs.

## Steps
1. Extract verified learnings separately from tentative hypotheses.
2. Preserve the relevant market, offer, format and period for each learning.
3. Propose up to five tests addressing specific unresolved questions.
4. For each test specify:
   evidence, hypothesis, control, one changed variable, required assets,
   primary outcome, budget allowance and decision criteria.
5. Rank by potential business impact, evidence strength, cost and feasibility.
   Treat scores as planning judgments.
6. Match the funded test count to the next approved budget.
7. Identify assets to reuse, revise or retire.
8. Update a learning log with source data and confidence.
9. Write the next strategist instruction using actual findings.
10. Retain INCONCLUSIVE where evidence is insufficient, even when the team
    prefers a particular ad.

## Output
Write next-tests.md and learning-log.md.

## Next-cycle instruction template
"Use these verified findings: [findings and sources].
Investigate these unresolved buying situations: [questions].
Develop [funded count] concepts changing [variables].
Preserve [controls]. Retire [creative IDs and reasons].
Use the approved offer, evidence ledger and spend ceiling."

## Handoff
Next skill: strategist-intake.
Pass next-tests.md, learning-log.md and updated commercial inputs.
```
