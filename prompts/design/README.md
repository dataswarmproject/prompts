# Design Prompts

Professional prompts for designers, UX/UI professionals, and creative teams.

## Categories

1. [UX Design](#ux-design)
2. [UI Design](#ui-design)
3. [Design Systems](#design-systems)
4. [User Research](#user-research)
5. [Accessibility](#accessibility)

---

## UX Design

### User Flow Design

```
Design a user flow for [feature/task]

Product: [product description]
User goal: [what user wants to accomplish]
Entry point: [where flow starts]

User context:
- User type: [new/returning/power user]
- Device: [mobile/desktop/both]
- Technical proficiency: [low/medium/high]

Requirements:
- Steps should be: [minimal/thorough/flexible]
- Success criteria: [what completion looks like]
- Edge cases to handle:
  - [Case 1]
  - [Case 2]

Provide:
1. User flow diagram (text description):
   - Each step
   - Decision points
   - Alternative paths
   - Error states

2. For each step:
   - Screen/page name
   - User action required
   - System response
   - Success/failure paths

3. Interaction details:
   - CTAs and labels
   - Validation rules
   - Loading states
   - Error messages

4. UX considerations:
   - Cognitive load assessment
   - Friction points
   - Optimization opportunities
   - Accessibility notes

5. Success metrics:
   - Completion rate target
   - Time to complete target
   - Drop-off risk points

Format: Step-by-step with rationale for each decision
```

### Information Architecture

```
Design information architecture for [website/app]

Project: [description]
Content types: [types of content]
User needs: [main user tasks]
Scale: [number of pages/screens]

Users:
- Primary: [persona 1]
- Secondary: [persona 2]

Goals:
- [Goal 1: e.g., easy product discovery]
- [Goal 2: e.g., quick checkout]
- [Goal 3: e.g., self-service support]

Provide:
1. Site map (hierarchical structure):
   - Main navigation
   - Sub-navigation
   - Utility navigation
   - Footer navigation

2. Content organization:
   - Grouping logic
   - Labeling recommendations
   - Hierarchy rationale

3. Navigation strategy:
   - Primary navigation structure
   - Secondary navigation patterns
   - Search functionality
   - Filters/facets needed

4. URL structure:
   - Pattern recommendations
   - SEO considerations

5. User paths:
   - Path to key tasks
   - Cross-linking strategy

6. Taxonomy:
   - Categories
   - Tags
   - Metadata structure

7. Validation plan:
   - Card sorting approach
   - Tree testing goals

Format: Visual hierarchy with annotations
```

---

## UI Design

### Interface Design Brief

```
Create UI design specifications for [screen/component]

Feature: [what this is]
Purpose: [what it accomplishes]
Context: [where it lives in the product]

Design requirements:
- Brand: [brand guidelines to follow]
- Platform: [iOS/Android/Web/all]
- Responsive: [breakpoints needed]
- Accessibility: [WCAG level]

Content elements:
- [Element 1: heading, image, etc.]
- [Element 2]
- [Element 3]

Interactions:
- [Interaction 1: tap, hover, swipe]
- [Interaction 2]

Provide:
1. Layout structure:
   - Grid system
   - Spacing rules
   - Component arrangement
   - Responsive behavior

2. Visual hierarchy:
   - Primary focus
   - Secondary elements
   - Tertiary information

3. Component specifications:
   - Buttons (types, states)
   - Forms (fields, validation)
   - Cards/containers
   - Icons needed

4. Typography:
   - Heading styles
   - Body text styles
   - Special text treatments

5. Color usage:
   - Primary colors
   - Accent colors
   - Feedback colors (success/error/warning)

6. States:
   - Default
   - Hover/focus
   - Active
   - Disabled
   - Loading
   - Error

7. Motion/animation:
   - Transitions
   - Micro-interactions
   - Duration and easing

8. Accessibility:
   - Color contrast
   - Focus indicators
   - Screen reader considerations
   - Keyboard navigation

Format: Detailed specifications with rationale
```

### Design System Component

```
Design a [component type] component for our design system

Component: [button/input/modal/card/etc.]

System context:
- Design language: [Material/iOS/Custom]
- Brand personality: [adjectives]
- Current components: [existing components]

Requirements:
- Variants needed: [primary/secondary/sizes]
- States: [default/hover/active/disabled]
- Responsive: [behavior on different screens]
- Accessibility: [WCAG compliance level]

Define:
1. Anatomy:
   - Component parts
   - Required elements
   - Optional elements

2. Variants:
   - [Variant 1]: when to use
   - [Variant 2]: when to use

3. Properties:
   - Size options
   - Color options
   - Configuration options

4. Behavior:
   - Interactions
   - Animations
   - Response to user input

5. States:
   - Visual appearance for each state
   - Transition between states

6. Specifications:
   - Dimensions
   - Spacing (internal and external)
   - Typography
   - Colors
   - Shadows/elevation
   - Border radius

7. Accessibility:
   - ARIA attributes
   - Keyboard interaction
   - Screen reader text
   - Focus management

8. Usage guidelines:
   - When to use
   - When not to use
   - Best practices
   - Common mistakes

9. Code properties (for developers):
   - Props/attributes
   - Default values
   - Required vs optional

Provide examples of correct and incorrect usage
```

---

## Design Systems

### Design System Setup

```
Create a design system foundation for [company/product]

Product context:
- Products: [web app, mobile app, marketing site]
- Team size: [designers and developers]
- Current state: [inconsistent/no system/partial system]

Brand:
- Personality: [adjectives]
- Industry: [industry]
- Target users: [user types]

Establish:

1. Color System:
   - Primary palette (3-5 colors with scales)
   - Semantic colors (success, warning, error, info)
   - Neutral palette (grays, backgrounds)
   - Usage guidelines
   - Accessibility compliance

2. Typography Scale:
   - Font families (primary, secondary, mono)
   - Type scale (sizes from smallest to largest)
   - Line heights
   - Letter spacing
   - Usage (headings, body, captions)
   - Responsive adjustments

3. Spacing System:
   - Base unit
   - Spacing scale (4px, 8px, 16px, etc.)
   - Margin and padding standards
   - Layout spacing

4. Grid System:
   - Column counts (mobile, tablet, desktop)
   - Gutter sizes
   - Margins
   - Breakpoints

5. Elevation/Shadows:
   - Shadow levels (1-5)
   - Usage for each level
   - Shadow values

6. Border Radius:
   - Radius scale
   - Usage guidelines

7. Iconography:
   - Icon size scale
   - Style (outline/filled/etc.)
   - Icon library recommendation

8. Component List (priority):
   - Tier 1 (essential): [list]
   - Tier 2 (important): [list]
   - Tier 3 (nice to have): [list]

9. Documentation structure:
   - Sections needed
   - Format
   - Maintenance plan

10. Implementation plan:
    - Phase 1 (foundation): [what and when]
    - Phase 2 (components): [what and when]
    - Phase 3 (patterns): [what and when]

Provide: Comprehensive foundation specifications
```

---

## User Research

### Usability Test Plan

```
Create a usability test plan for [product/feature]

Test goals:
- [Goal 1: e.g., evaluate checkout flow]
- [Goal 2: e.g., identify navigation issues]

Product: [description]
Stage: [prototype/beta/live]

Design:
1. Methodology:
   - Type: [moderated/unmoderated, remote/in-person]
   - Duration: [per session]
   - Number of participants: [n]

2. Participants:
   - Recruitment criteria:
     - [Criterion 1]
     - [Criterion 2]
   - Screener questions
   - Incentive: [amount]

3. Tasks:
   Task 1: [description]
   - Scenario: [realistic context]
   - Success criteria: [what constitutes success]
   - Time limit: [if applicable]

   [Repeat for 5-8 tasks]

4. Script:
   - Introduction (5 min)
   - Task instructions
   - Think-aloud prompt
   - Probing questions
   - Wrap-up questions

5. Metrics:
   - Task success rate
   - Time on task
   - Error rate
   - Satisfaction rating
   - Qualitative feedback

6. Setup:
   - Tools needed
   - Recording setup
   - Prototype link
   - Note-taking template

7. Analysis plan:
   - How to code issues
   - Severity rating
   - Reporting format

8. Timeline:
   - Recruitment: [duration]
   - Testing: [dates]
   - Analysis: [duration]
   - Report: [delivery date]

Deliverables:
- Research plan
- Discussion guide
- Findings report
- Prioritized recommendations
```

### User Interview Guide

```
Create an interview guide for [research goal]

Research question: [main question to answer]
Product: [product or concept]
Interviewees: [user segment]

Goals:
- [Learn about behavior/pain points/needs]
- [Validate assumptions]
- [Explore attitudes]

Create:
1. Screening questions (3-5):
   - [Question to qualify participants]

2. Interview structure (60 min):

   Introduction (5 min):
   - Welcome and purpose
   - Consent and recording
   - Anonymity assurance

   Warm-up (5 min):
   - [Easy opening questions]
   - Build rapport

   Context (10 min):
   - Current behavior questions
   - Workflow questions
   - Pain point exploration

   Main topics (30 min):
   Topic 1: [theme]
   - [Question 1]
   - [Follow-up probes]

   Topic 2: [theme]
   - [Question 1]
   - [Follow-up probes]

   [If applicable] Concept test (5 min):
   - Show prototype/concept
   - Reaction questions
   - Comprehension checks

   Wrap-up (5 min):
   - Anything else to share?
   - Thank you and next steps

3. Probing techniques:
   - "Tell me more about that"
   - "Can you give me an example?"
   - "Why is that important to you?"
   - "How did that make you feel?"

4. What not to ask:
   - Leading questions
   - Multiple questions at once
   - Yes/no questions (rephrase to open-ended)

5. Note-taking template:
   - Key quotes
   - Observations
   - Hypotheses
   - Follow-up questions

Output: Complete interview guide ready to use
```

---

## Accessibility

### Accessibility Audit

```
Conduct an accessibility audit for [product/page]

Product: [description]
URL: [if applicable]
Standards: [WCAG 2.1 Level AA / Section 508 / etc.]

Audit:
1. Automated scan results:
   - Tool used: [WAVE/axe/etc.]
   - Issues found: [list]

2. Manual testing:

   Keyboard Navigation:
   - Can all interactive elements be reached?
   - Is focus visible?
   - Is focus order logical?
   - Can user skip to main content?
   - Are keyboard traps present?

   Screen Reader:
   - Screen reader tested: [NVDA/JAWS/VoiceOver]
   - Heading structure logical?
   - Alt text present and meaningful?
   - Form labels associated correctly?
   - Error messages announced?
   - Dynamic content announced?

   Visual:
   - Color contrast ratios (provide measurements)
   - Text resizable to 200%?
   - Information conveyed without color alone?
   - Focus indicators visible?

   Content:
   - Language specified?
   - Link text descriptive?
   - Headings used properly (h1-h6)?
   - Lists marked up correctly?

3. Issues found:
   For each issue:
   - Severity: [Critical/Serious/Moderate/Minor]
   - WCAG criterion violated
   - Location/element
   - Current state
   - Impact on users
   - Recommended fix
   - Code example of fix

4. Prioritized remediation plan:
   - Must fix (blockers)
   - Should fix (important)
   - Nice to fix (enhancements)

5. Prevention:
   - Design guidelines to prevent issues
   - Development checklist
   - Testing integration

Provide: Detailed report with actionable fixes
```

---

**See Also**:
- [AI Best Practices](../../AI-BEST-PRACTICES.md)
- [Designer's Quick Start Guide](../../guides/designers.md)
- [Design System Examples](./design-system-examples.md)

**Last Updated**: 2025-10-28
