# UX and Product Design "Taste" Training: Research Report

## Comprehensive Guide for Non-Designers and Non-Coders

This report covers 15 major areas with 25+ specific, actionable exercises that can be completed in 30-90 minutes each.

---

## 1. UX Critique Frameworks and Exercises

### The Nielsen Heuristic Evaluation Method

Jakob Nielsen's 10 usability heuristics (developed 1990, refined 1994) are the gold standard framework for critiquing any digital interface. They are broad rules of thumb, not rigid checklists, which makes them perfect for beginners building taste.

**The 10 Heuristics:**
1. Visibility of system status
2. Match between system and the real world
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose, and recover from errors
10. Help and documentation

**Exercise 1: The Heuristic Audit (60 min)**
Pick any app you use daily (Instagram, Spotify, your banking app). Open it and go through each of Nielsen's 10 heuristics one at a time. For each heuristic, write down:
- One example where the app does this WELL
- One example where the app FAILS at this
- A suggested improvement

This trains your eye to see past the surface and evaluate design systematically. Three to five evaluators working independently and then comparing notes produces the best results, but solo practice still builds strong instincts.

**Exercise 2: The Side-by-Side Critique (45 min)**
Pick two competing apps (e.g., Uber vs Lyft, Slack vs Teams, Notion vs Coda). Complete the same task in both (booking a ride, sending a message, creating a page). Document:
- Which felt faster? Why?
- Where did you get confused?
- What did each app assume you already knew?

---

## 2. Product Sense Interview Questions (FAANG-Style)

Product sense interviews at Meta, Google, and other tech giants test your ability to think like a product builder. The core question types are:

**Product Improvement:** "How would you improve Facebook Marketplace?"
**Product Design:** "Design a product for elderly users to stay connected with family."
**Product Strategy:** "Should Google launch a competitor to Slack?"

### Key Frameworks

**CIRCLES Method** (for design questions):
- Comprehend the situation
- Identify the customer
- Report customer needs
- Cut through prioritization
- List solutions
- Evaluate tradeoffs
- Summarize recommendation

**BUS Framework** (for improvement questions):
- Business objectives
- User problems
- Solutions

**Exercise 3: The Daily Product Sense Question (30 min)**
Each day, pick one of these prompts and spend 30 minutes thinking through it using the CIRCLES or BUS framework. Write your answer as if presenting to a panel:
- "How would you improve the checkout experience on Amazon?"
- "Design a feature for Spotify that helps people discover local live music."
- "Google Maps wants to expand beyond navigation. What product would you build?"
- "How would you reduce the number of abandoned carts on an e-commerce site?"
- "Should Netflix add a social feature? Why or why not?"

**Exercise 4: The Reverse Product Teardown (45 min)**
Pick a product that recently launched a major feature (check TechCrunch or Product Hunt for ideas). Before reading any analysis:
1. Use the feature yourself
2. Write down: What problem does this solve? Who is it for? What tradeoffs did they make?
3. Then read the company's blog post about the launch. Compare your analysis to their stated goals.

---

## 3. Interactive UI/UX Training Games

These browser-based games build design intuition through practice:

**Can't Unsee** (cantunsee.space) - Pick which of two nearly identical interfaces is correct. Tests attention to typography, spacing, visual hierarchy, and alignment. Difficulty increases across three rounds with 18 interface pairs. Created by software engineer Alex Kotliarskyi.

**Kern Type** (type.method.ac) - Adjust letter spacing (kerning) to achieve typographical harmony. Trains typography sensitivity.

**Color Method** (color.method.ac) - Identify hues, saturation, and color relationships (complementary, analogous, triadic, tetradic) on an interactive color wheel within 10 seconds. Difficulty increases as you progress.

**Better Web Type** - Learn and practice web typography principles through interactive exercises.

**What the HEX?** - Identify the correct HEX code for a given color. Fun way to develop color vocabulary.

**Exercise 5: The Design Game Sprint (60 min)**
Play all five games listed above in sequence, 10-12 minutes each. Track your scores. Repeat weekly and watch your scores improve. The areas where you score lowest reveal your biggest gaps in visual design intuition.

---

## 4. Dark Patterns: Spotting Deceptive Design

Dark patterns are intentionally crafted UX designs that manipulate users into unintended actions. The term was coined by Harry Brignull in 2010. A 2022 European Commission report found that 97% of popular apps used by EU consumers displayed dark patterns.

### Common Dark Pattern Types

- **Forced Continuity:** Free trials requiring credit cards, hoping you forget to cancel
- **Nagging:** Repetitive prompts pushing you toward an action you already declined
- **Privacy Zuckering:** Bright "Accept All" button with tiny "Customize Settings" link on cookie consent
- **Hidden Charges:** Fees that appear only after you are emotionally invested in the purchase
- **Confirmshaming:** "No thanks, I don't want to save money" as the opt-out text
- **Roach Motel:** Easy to subscribe, nearly impossible to cancel
- **Trick Questions:** Confusing double-negatives on checkboxes

**Exercise 6: The Dark Pattern Safari (45 min)**
Visit 5 popular websites (an airline, a news site, a SaaS trial, an e-commerce store, a social media signup). For each, document:
- Every dark pattern you find (screenshot it)
- Which category it falls into
- How YOU would redesign it ethically
Reference: deceptive.design/types for the complete taxonomy.

**Exercise 7: The Unsubscribe Challenge (30 min)**
Try to unsubscribe or delete your account from 3 services you no longer use. Document:
- How many clicks/steps it took
- What manipulative language was used
- Where you almost gave up
This exercise makes dark patterns viscerally real.

---

## 5. Accessibility Testing for Beginners

The four WCAG principles (POUR): Perceivable, Operable, Understandable, Robust.

**Exercise 8: The Keyboard-Only Challenge (45 min)**
Unplug your mouse (or disable your trackpad). Navigate your favorite website using ONLY your keyboard:
- Tab to move between elements
- Enter to activate buttons/links
- Arrow keys for menus
Document: Where do you get stuck? Can you tell where your focus is? Can you access all features?

**Exercise 9: The Screen Reader Test (60 min)**
Turn on your device's built-in screen reader (VoiceOver on Mac/iOS, TalkBack on Android, Narrator on Windows). Close your eyes and try to:
1. Navigate to a news website
2. Find and read a specific article
3. Navigate back to the homepage
Document what was confusing, what was impossible, and what worked well. This builds deep empathy for visually impaired users.

**Exercise 10: The Squint Test (30 min)**
Open any app and squint until the interface is blurry. Can you still:
- Tell what the primary action is?
- Distinguish the navigation from the content?
- See the visual hierarchy?
This reveals whether a design relies too heavily on text vs. visual structure.

**Quick Checks to Practice (from W3C WAI):**
- Do all images have alt text?
- Is there sufficient color contrast (use a browser extension to check)?
- Can you resize text to 200% without breaking the layout?
- Do form fields have visible labels?

---

## 6. Mobile vs. Desktop UX Differences

### Key Differences to Study

| Aspect | Mobile | Desktop |
|--------|--------|---------|
| Screen size | 4-7 inches | 13-27+ inches |
| Input | Touch (thumbs) | Mouse + keyboard |
| Context | On-the-go, distracted | Seated, focused |
| Navigation | Bottom nav, hamburger menus | Top nav, sidebars |
| Content | Minimal, prioritized | Can show more at once |
| Touch targets | Minimum 48x48px | Can be smaller |

### Common Mistakes
- Hover states that do not translate to touch
- Fixed-width designs that break on small screens
- Navigation at the top (thumbs cannot reach it comfortably on mobile)
- Tiny tap targets (buttons, links)
- Not using device-specific keyboards (numeric for phone numbers, email for email fields)
- Responsive design without mobile-specific UX thinking

**Exercise 11: The Device Swap Test (45 min)**
Pick a complex website (a travel booking site, a government form, a banking dashboard). Complete the same task on:
1. Desktop browser
2. Phone browser
3. Tablet (if available)
Document: What broke? What was harder on mobile? What did they do well across devices?

**Exercise 12: The Thumb Zone Audit (30 min)**
Hold your phone naturally with one hand. Notice where your thumb can easily reach (bottom center), what requires a stretch (top corners), and what is nearly impossible (opposite top corner). Now open 5 apps and evaluate: Are the most important actions in the easy thumb zone?

---

## 7. Information Architecture: Card Sorting and Tree Testing

### Card Sorting
Users sort cards (each representing a piece of content) into groups and name those groups. This reveals how real people mentally organize information.

**Types:**
- **Open sort:** Users create their own categories (best for new projects)
- **Closed sort:** Users sort into pre-defined categories (best for validation)
- **Hybrid sort:** Pre-defined categories but users can create new ones

**Recommended:** 30-50 cards to prevent fatigue while encouraging thoughtful groupings.

### Tree Testing
After card sorting generates a proposed structure, tree testing validates it. Users are given a task ("Find the return policy") and navigate a text-only hierarchy. No visual design to influence them, purely testing the logical structure.

**Exercise 13: The Grocery Store Card Sort (45 min)**
Write 40 common grocery items on sticky notes (milk, bread, shampoo, batteries, flowers, frozen pizza, etc.). Ask 3 friends or family members to independently sort them into groups and name the groups. Compare their groupings:
- Where did they agree? (Strong categories)
- Where did they differ? (Ambiguous items)
- Did anyone create a group you never considered?
This is exactly how real IA work is done, just with website content instead of groceries.

**Exercise 14: The Website Navigation Redesign (60 min)**
Pick a website with poor navigation (government sites are great candidates). Write every page/section on a separate card or sticky note. Re-sort them into a structure that makes more sense. Create a simple tree diagram. Then ask someone to find 5 specific items using only your new tree.

---

## 8. Micro-Interactions That Make Apps Feel Polished

Micro-interactions are small, task-based interactions that provide feedback or visual responses. Dan Saffer's framework breaks them into four parts: trigger, rule, feedback, loops and modes.

### Examples to Study
- Instagram/Twitter: Heart animation when liking a post
- iMessage: "Typing..." indicator
- Pull-to-refresh animations
- Progress bars that fill during uploads
- Toggle switches with satisfying snap animations
- Arc browser: The logo acts as a fidget spinner when you close all tabs, with haptic feedback
- Stripe: Payment form fields that format credit card numbers as you type

**Exercise 15: The Micro-Interaction Diary (45 min over 1 day)**
Throughout one day of normal phone/computer use, notice and document every micro-interaction you encounter. For each one, note:
- What triggered it (tap, scroll, hover, time)?
- What feedback did you receive (animation, sound, haptic)?
- How did it make you feel (informed, delighted, confused)?
- Could it be improved?
Aim to collect at least 15 examples.

**Exercise 16: The Missing Feedback Audit (30 min)**
Open an app and perform 10 different actions (tap buttons, submit forms, switch tabs, delete items). For each action, ask: "Did the app acknowledge what I just did?" When the answer is "no" or "not clearly enough," you have found a missing micro-interaction.

---

## 9. Loading States, Empty States, Error States

These are the "unhappy paths" that most apps neglect but great apps handle beautifully.

### Empty States
**Types:** First use (nothing to show yet), user cleared (completed all tasks), no results (search returned nothing), errors.

**Best practice:** Never show a completely blank screen. Always include:
1. Headline explaining what happened ("No results found")
2. Secondary explanation ("Try a different search term")
3. Call-to-action ("Browse categories")

### Loading States
Loading indicators should balance perceived time and perceived value. Use:
- Skeleton screens (gray placeholder shapes) for content-heavy pages
- Spinner for quick, unknown-duration operations
- Progress bars for uploads/downloads with known progress
- Shimmer effects for feed-style content

### Error States
- Use plain language, not error codes
- Explain what went wrong AND how to fix it
- Provide a path forward (retry button, alternative action)
- Never blame the user

**Exercise 17: The Edge Case Hunt (45 min)**
In any app, deliberately trigger unusual states:
- Search for something that does not exist
- Disconnect your internet and try to use the app
- Submit a form with invalid data
- Delete all items from a list
- Revoke permissions (location, notifications)
Screenshot each state. Grade them: Does the app explain what happened? Does it tell you what to do? Is the tone appropriate?

---

## 10. Color Psychology and Typography Basics

### Color Psychology Quick Reference

| Color | Association | Used By |
|-------|-------------|---------|
| Red | Energy, urgency, appetite | Netflix, YouTube, fast food |
| Blue | Trust, calm, security | Banks, Facebook, LinkedIn |
| Green | Nature, health, money | Spotify, Whole Foods, banking |
| Yellow | Optimism, warning, attention | Snapchat, warning signs |
| Purple | Luxury, creativity, wisdom | Twitch, Cadbury |
| Orange | Friendly, confidence, fun | Amazon (buy button), Fanta |
| Black | Sophistication, power | Apple, luxury brands |

### Typography Basics
- **Serif fonts** (Times New Roman, Georgia): Traditional, trustworthy, editorial
- **Sans-serif fonts** (Helvetica, Inter, Arial): Modern, clean, digital-first
- **Display/decorative fonts:** Headlines only, never body text
- **Font pairing:** Use max 2-3 fonts. Pair a serif heading with sans-serif body, or vice versa.
- **Hierarchy:** At minimum, define heading, subheading, body, and caption sizes. Each level should be noticeably different.

### The 60-30-10 Rule for Color
- 60% dominant color (backgrounds, large areas)
- 30% secondary color (cards, sections, sidebars)
- 10% accent color (CTAs, highlights, alerts)

**Exercise 18: The Brand Color Decode (30 min)**
Pick 5 brands you admire. For each, identify:
- Their primary, secondary, and accent colors
- What emotion does the palette evoke?
- How do they use color to direct your attention?
Tools: Use a color picker browser extension to extract exact hex codes.

**Exercise 19: The Typography Swap (30 min)**
Take a screenshot of any app. Using a tool like Figma (free) or even PowerPoint, replace all the fonts with a very different typeface (e.g., swap Inter for Comic Sans, or Georgia for Futura). Observe how dramatically the "feel" changes while the content stays identical. This proves that typography IS design.

---

## 11. "Jobs to Be Done" (JTBD) Framework

Instead of asking "what features do users want?", JTBD asks: "what job is the user hiring this product to do?"

### The Classic Milkshake Example
A fast-food chain found most milkshakes were sold before 8:30 AM to solo commuters. The "job" was not "I want a milkshake" but rather "I need something to make my boring commute less tedious and keep me full until lunch." Competitors were not other milkshakes but bananas, bagels, and donuts.

### JTBD Statement Formula
"When I [situation], I want to [motivation], so I can [expected outcome]."

Example: "When I am commuting alone in the morning, I want something filling and entertaining to consume, so I can stay satisfied and not bored until lunch."

### Three Dimensions
- **Functional:** What does the product practically do?
- **Emotional:** How does it make the user feel?
- **Social:** How does using it affect how others perceive the user?

**Exercise 20: The JTBD Reframe (45 min)**
Pick 5 products you use regularly. For each, write a JTBD statement:
1. Your banking app
2. Your music streaming service
3. Your messaging app
4. Your note-taking tool
5. Your grocery delivery service

For each, ask: What job am I REALLY hiring this for? What would I use if this product disappeared? (That reveals the true competition.)

---

## 12. User Journey Mapping

A user journey map is a visual diagram of the process a user goes through to achieve a goal, capturing what they DO, THINK, and FEEL at each stage.

### Key Stages (ACDPR)
1. **Awareness:** User realizes they have a need
2. **Consideration:** User evaluates options
3. **Decision:** User chooses your product
4. **Purchase/Action:** User completes the core action
5. **Retention:** User continues using (or churns)

### What to Capture at Each Stage
- User actions (what they do)
- Touchpoints (where they interact with your product)
- Emotions (happy, frustrated, confused, delighted)
- Pain points (friction, confusion, annoyance)
- Opportunities (where you could improve)

**Exercise 21: The Personal Journey Map (60 min)**
Map your own journey with a recent purchase or signup:
1. Pick something you recently bought or signed up for
2. Recall every step from first hearing about it to using it
3. Draw a timeline with your actions, emotions (draw a line going up for positive, down for negative), and pain points
4. Identify the "moments of truth" where you almost gave up or were delighted

Free templates available on Figma, Miro, and Canva.

---

## 13. A/B Testing Intuition

A/B testing runs two versions of something simultaneously with a live audience to determine which performs better. Version A is the control (current), Version B is the variant (change).

### What to Test (High Impact)
- **Headlines and copy:** "Start Free Trial" vs "Try It Free"
- **CTA button color/position:** Contrast matters more than specific color
- **Form length:** Fewer fields usually increase conversion
- **Social proof placement:** Reviews, testimonials, user counts
- **Pricing page layout:** How you present tiers and features
- **Image vs. no image:** Sometimes removing images improves focus
- **Navigation labels:** What you call menu items matters

### What NOT to Test
- Tiny changes with no hypothesis behind them
- Multiple changes at once (you won't know what caused the difference)
- Tests without enough traffic to reach statistical significance

**Key stat:** Only 1 in 7 A/B tests produces a winning result. Most changes do not matter as much as we think.

**Exercise 22: The Hypothesis Game (45 min)**
Visit 5 popular websites. For each, identify:
1. One element you would A/B test
2. Your hypothesis (I believe changing X will improve Y because Z)
3. What metric you would measure
4. How long you would run the test

Example: "On Airbnb's search results, I hypothesize that showing the total price (not nightly rate) will increase booking completion because users feel more informed. I would measure booking conversion rate over 2 weeks."

---

## 14. Onboarding Flow Critique

A bad onboarding experience can cause up to 80% of users to abandon an app before even using it.

### Bad Onboarding Signs
- 14+ step guides (too intimidating)
- Empty dashboards after signup (no guidance)
- Verification emails that break flow (user leaves, gets distracted, never comes back)
- Tooltips that block the content they are explaining
- Asking for too much information before showing value

### Good Onboarding Principles
- Show value BEFORE asking for investment (let users explore before signup)
- Use progressive disclosure (reveal features as needed, not all at once)
- Make it interactive, not just informational
- Include clear progress indicators
- Provide "quick wins" early (let users accomplish something in the first 2 minutes)

### Apps with Great Onboarding to Study
- **Duolingo:** Lets you complete a lesson BEFORE creating an account
- **Notion:** Interactive templates that show you what is possible
- **Figma:** In-product tutorial that teaches by doing
- **Slack:** Guided setup that populates content so it never feels empty

**Exercise 23: The Onboarding Teardown (60 min)**
Sign up for 3 new apps (use a burner email). For each, document:
1. How many steps before you saw value?
2. What information did they ask for? Was it all necessary?
3. Did you feel guided or lost?
4. Was there a moment of delight?
5. Grade each on a 1-10 scale for first impression

Resource: UserOnBoard.com has teardowns of 100+ onboarding flows with annotations.

---

## 15. Conversion Funnel Analysis

A conversion funnel maps each step from first contact to completed goal, identifying where users drop off.

### Standard Funnel (AIDA)
1. **Awareness:** User lands on site (100%)
2. **Interest:** User explores content (maybe 60%)
3. **Decision:** User adds to cart or clicks CTA (maybe 15%)
4. **Action:** User completes purchase/signup (maybe 3-5%)

Each step has a drop-off rate. The goal is to reduce friction at the steepest drop-offs.

### Common Drop-Off Causes
- Unexpected shipping costs at checkout
- Required account creation before purchase
- Slow page load times
- Too many form fields
- Unclear value proposition on landing page
- No trust signals (reviews, security badges)

**Exercise 24: The Funnel Walk-Through (60 min)**
Pick an e-commerce site. Go through the entire purchase funnel as if you were a first-time buyer:
1. Land on homepage. Is the value clear in 5 seconds?
2. Find a product. How many clicks?
3. Add to cart. Any friction?
4. Begin checkout. What surprised you?
5. Reach payment. Any hidden fees?
At each step, rate the friction (1-5) and document what made you want to leave.

**Exercise 25: The Competitor Funnel Comparison (90 min)**
Pick 3 competitors in the same space (e.g., three meal kit services, or three project management tools). Complete the same goal in each. Map each funnel step-by-step and compare:
- Which had the shortest path to value?
- Which had the most friction?
- What did the best one do differently?

---

## Bonus Exercises

**Exercise 26: The App Store Review Mining (45 min)**
For any app, read the 1-star and 2-star reviews. These are free user research. Categorize the complaints: Is it UX? Performance? Missing features? Pricing? This reveals what users actually care about vs. what companies focus on.

**Exercise 27: The Redesign Challenge (90 min)**
Pick the worst-designed screen in an app you use. Sketch (on paper, no tools needed) a redesigned version. Apply what you have learned:
- Clear visual hierarchy
- Obvious primary action
- Good use of empty space
- Accessible color contrast
- Appropriate loading/empty/error states

---

## Recommended Study Apps and Resources

### Apps to Study for Great Design
- **Linear:** Best-in-class enterprise UX
- **Stripe:** Complex product made simple
- **Notion:** Flexible yet intuitive
- **Arc Browser:** Micro-interactions and delight
- **Duolingo:** Gamification done right
- **Apple Health:** Information architecture at scale
- **Airbnb:** Mobile-first design excellence
- **Figma:** Collaborative tool design

### Interactive Learning Tools
| Tool | URL | What It Trains |
|------|-----|----------------|
| Can't Unsee | cantunsee.space | Visual attention to UI detail |
| Kern Type | type.method.ac | Typography spacing |
| Color Method | color.method.ac | Color theory |
| Laws of UX | lawsofux.com | Design psychology |
| Mobbin | mobbin.com | Mobile design patterns library |
| Page Flows | pageflows.com | User flow recordings |
| Deceptive Design | deceptive.design | Dark pattern taxonomy |

### Books for Building Taste
- "Don't Make Me Think" by Steve Krug (the classic, readable in one sitting)
- "The Design of Everyday Things" by Don Norman
- "Microinteractions" by Dan Saffer
- "Hooked" by Nir Eyal (product psychology)
- "Refactoring UI" by Adam Wathan and Steve Schoger (the most practical visual design guide for developers)

---

## Weekly Practice Schedule (Suggested)

| Day | Exercise | Time |
|-----|----------|------|
| Monday | Product Sense Question (#3) | 30 min |
| Tuesday | Design Game Sprint (#5) | 60 min |
| Wednesday | Heuristic Audit (#1) | 60 min |
| Thursday | Dark Pattern Safari (#6) or Accessibility Test (#8/#9) | 45 min |
| Friday | JTBD Reframe (#20) or Journey Map (#21) | 45-60 min |
| Weekend | Onboarding Teardown (#23) or Funnel Analysis (#24) | 60 min |

Rotating through these exercises weekly builds compound design intuition within 4-8 weeks.
