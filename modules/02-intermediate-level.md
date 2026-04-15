# Module 02: Intermediate Level — Smart Usage & AI Workflows

> **Prerequisites:** Complete Module 01 (Beginner Level) before starting this module.
> **Duration:** 14 days (Days 15–28)
> **Goal:** Master advanced prompt frameworks, role-based prompting, chain-of-thought techniques, and multi-step AI workflows.

---

## Section 1: Advanced Prompt Structures

Moving beyond basic prompts, intermediate users leverage structured frameworks that consistently produce high-quality, predictable AI outputs. Two of the most powerful are **CRAFT** and **RISEN**.

---

### The CRAFT Framework

**CRAFT** stands for: **C**ontext · **R**ole · **A**ction · **F**ormat · **T**one

| Component | Question it answers | Example |
|-----------|--------------------|---------:|
| **C**ontext | What is the background/situation? | "I run a SaaS startup with 500 users." |
| **R**ole | Who should the AI be? | "Act as a senior product manager." |
| **A**ction | What do I need done? | "Write a product roadmap summary." |
| **F**ormat | How should the output look? | "Use bullet points under 3 phases." |
| **T**one | What style/voice? | "Professional but approachable." |

**CRAFT Template:**

```
Context:  [Describe your situation, background, audience, or goal]
Role:     [The expert role the AI should assume]
Action:   [The specific task to perform]
Format:   [Output structure — bullets, table, paragraphs, numbered list, etc.]
Tone:     [Formal / casual / persuasive / empathetic / technical]
```

**Filled-In CRAFT Example — Marketing Email:**

```
Context:  I'm launching a new online course on personal finance for millennials aged 25–35.
          The course costs $197 and starts October 1st.
Role:     Act as an experienced email copywriter specializing in digital course launches.
Action:   Write a pre-launch email to my subscriber list building anticipation and 
          encouraging them to join the waitlist.
Format:   Subject line + 3 short paragraphs + a call-to-action button text.
Tone:     Warm, encouraging, and slightly urgent — not pushy.
```

**Filled-In CRAFT Example — Technical Documentation:**

```
Context:  Our development team just shipped a new REST API for user authentication.
          The audience is external developers with basic API knowledge.
Role:     Act as a senior technical writer with experience in API documentation.
Action:   Write the Getting Started section of our API documentation.
Format:   Include: overview paragraph, prerequisites list, step-by-step setup (numbered),
          and one curl example.
Tone:     Clear, concise, and technical — no marketing language.
```

---

### The RISEN Framework

**RISEN** stands for: **R**ole · **I**nstructions · **S**teps · **E**nd goal · **N**arrowing

| Component | Purpose | Example |
|-----------|---------|---------|
| **R**ole | Define the AI's persona | "You are a data scientist at a Fortune 500 company." |
| **I**nstructions | Detailed task instructions | "Analyze this dataset and find patterns." |
| **S**teps | Break it into sub-steps | "First explore the data, then identify outliers..." |
| **E**nd goal | Desired final outcome | "Produce a board-ready executive summary." |
| **N**arrowing | Constraints and exclusions | "Max 300 words. No technical jargon." |

**RISEN Template:**

```
Role:        [Who the AI is]
Instructions:[Detailed description of what to do]
Steps:       [Step 1: ... Step 2: ... Step 3: ...]
End goal:    [What the final output should accomplish]
Narrowing:   [Constraints: word count, audience, exclusions, style rules]
```

**Filled-In RISEN Example — Business Strategy:**

```
Role:        You are a McKinsey-trained business strategy consultant.
Instructions:Analyze the competitive position of a mid-size e-commerce company
             selling handmade jewelry, and recommend a 90-day growth strategy.
Steps:
  Step 1: Identify the top 3 competitive threats in the handmade jewelry market.
  Step 2: Assess the company's likely strengths and weaknesses.
  Step 3: Propose 5 specific, actionable initiatives for the next 90 days.
  Step 4: Prioritize by impact (High/Medium/Low) and effort (High/Medium/Low).
End goal:    A clear, prioritized action plan the founder can present to investors.
Narrowing:   Keep it under 500 words. Avoid generic advice. Be specific with tactics.
             No references to companies I haven't mentioned.
```

---

### Prompt Structure Diagram

```
  Role → Task → Context → Format → Constraints
   │       │       │         │          │
   ▼       ▼       ▼         ▼          ▼
  Who    What    Why/      How to     Rules &
  you    to do  Background present    Limits
  are                     output
```

Every great prompt addresses all five layers. Missing even one often leads to vague or off-target responses.

---

### CRAFT vs RISEN — When to Use Each

| Scenario | Use CRAFT | Use RISEN |
|----------|-----------|-----------|
| Quick content creation | ✅ | |
| Writing emails, social posts | ✅ | |
| Complex multi-step analysis | | ✅ |
| Strategic planning tasks | | ✅ |
| Tone-sensitive outputs | ✅ | |
| When process matters as much as outcome | | ✅ |
| First time prompting a new topic | ✅ | |
| Tasks requiring sequential reasoning | | ✅ |

**Rule of thumb:** Use CRAFT when the *output style* is your primary concern. Use RISEN when the *reasoning process* matters.

---

## Section 2: Role-Based Prompting

### What Is Role-Based Prompting?

Role-based prompting tells the AI *who to be* before asking it *what to do*. Instead of asking a generic AI, you summon a domain expert with decades of implied knowledge, vocabulary, and judgment.

**Why it works:**
- Activates domain-specific knowledge and vocabulary
- Sets implicit expectations for quality and depth
- Reduces need to specify every detail
- Produces outputs consistent with professional standards

### How to Assign Roles Effectively

**Weak role assignment:** "Act as an expert."
**Strong role assignment:** "You are a senior growth marketing manager with 10 years of B2B SaaS experience, specializing in demand generation and PLG (product-led growth) strategies."

The more specific the role, the more targeted the output. Include:
- Seniority level (junior, senior, director, VP, C-level)
- Specialization (not just "developer" — "full-stack developer specializing in Node.js and React")
- Industry context when relevant
- Any unique expertise or perspective

---

### 15+ Role Prompts with Full Examples

#### 1. Marketing Expert

```
Role prompt: You are a senior digital marketing strategist with 12 years of experience
in B2C e-commerce, specializing in conversion rate optimization and paid media.

Sample task: I sell handmade candles online and my Facebook ads have a 1.2% CTR
but only 0.8% conversion on the landing page. Diagnose the top 3 likely issues
and give me specific fixes for each.
```

#### 2. Software Developer

```
Role prompt: You are a senior full-stack software engineer with 8 years of experience
in Python and React, with deep expertise in system design and code reviews.

Sample task: Review this Python function for performance issues and security 
vulnerabilities, then rewrite it following best practices:

def get_user(user_id):
    conn = sqlite3.connect('users.db')
    cursor = conn.execute("SELECT * FROM users WHERE id = " + str(user_id))
    return cursor.fetchone()
```

#### 3. Data Analyst

```
Role prompt: You are a senior data analyst at a tech company with expertise in 
SQL, Python (pandas), and business intelligence dashboards.

Sample task: I have a dataset of 50,000 customer transactions. Walk me through
exactly how you would analyze it to find our most profitable customer segments.
Include the specific SQL queries and visualizations you'd create.
```

#### 4. Financial Advisor

```
Role prompt: You are a Certified Financial Planner (CFP) with 15 years of experience
helping middle-income families build wealth through diversified investment strategies.

Sample task: My client is 35 years old, earns $90,000/year, has $15,000 in savings,
$25,000 in 401k, and $8,000 in credit card debt at 22% APR. Create a prioritized
12-month financial action plan.
```

#### 5. HR Manager

```
Role prompt: You are a Director of Human Resources at a 200-person tech company
with expertise in talent acquisition, performance management, and DEI initiatives.

Sample task: We've had 3 high-performers leave in the past 6 months. All cited
"lack of growth opportunities" in exit interviews. Write a retention improvement plan
I can present to leadership next week.
```

#### 6. Legal Consultant

```
Role prompt: You are a business attorney specializing in contracts, intellectual 
property, and startup law. (Note: This is for informational purposes — always 
consult a licensed attorney for actual legal advice.)

Sample task: Explain the key differences between an NDA and a non-compete clause,
when each is appropriate, and what 3 clauses I should always include in a basic
freelance contract.
```

#### 7. Medical Advisor

```
Role prompt: You are a health educator and medical communicator who helps translate
complex medical information into clear, accessible language for patients.
(Always recommend consulting a licensed physician for personal medical decisions.)

Sample task: Explain Type 2 diabetes to a newly diagnosed 55-year-old patient
who has no medical background. Cover: what it is, what causes it, lifestyle changes
that help, and questions they should ask their doctor.
```

#### 8. Teacher / Educator

```
Role prompt: You are a master high school teacher with 20 years of classroom experience,
specializing in making complex subjects accessible through storytelling and analogies.

Sample task: Teach the concept of compound interest to a 16-year-old who hates math.
Use a story or analogy, keep it under 200 words, and end with one memorable takeaway.
```

#### 9. Sales Coach

```
Role prompt: You are a top-performing B2B sales coach who has trained hundreds of
SDRs and AEs at SaaS companies. You specialize in consultative selling and 
handling objections.

Sample task: My prospect said: "Your product looks great but we already have a 
solution and switching costs are too high." Write me 3 different responses I can
use, ranging from empathetic acknowledgment to a direct challenge.
```

#### 10. CEO Strategist

```
Role prompt: You are a seasoned CEO with experience scaling three companies from
startup to $50M+ ARR. You think in systems, prioritize ruthlessly, and communicate
with clarity.

Sample task: My SaaS startup just hit $1M ARR with a team of 8. What are the 
top 5 strategic decisions I need to make in the next 6 months that will determine
whether we reach $5M ARR?
```

#### 11. UX Designer

```
Role prompt: You are a Lead UX Designer at a top-tier product agency with a portfolio
of mobile and web apps used by millions. You apply human-centered design principles.

Sample task: I'm redesigning the onboarding flow for a personal finance app. 
Users currently drop off at 67% during setup. Propose a 5-screen onboarding flow
with UX copy for each screen and the psychological principle behind each design choice.
```

#### 12. Content Strategist

```
Role prompt: You are a Content Strategy Director who has built content programs for
B2B SaaS companies from 0 to 100K monthly organic visitors.

Sample task: Build a 3-month content calendar framework for a cybersecurity software
company targeting IT managers at mid-size companies. Include content pillars,
content types, and distribution channels.
```

#### 13. Customer Support Agent

```
Role prompt: You are a senior customer support specialist known for turning angry
customers into loyal advocates through empathy, clarity, and fast resolution.

Sample task: A customer emailed: "I've been charged TWICE this month and nobody
is responding to my emails. This is absolutely unacceptable. I want a full refund
and I'm disputing the charge with my bank." Write a response that de-escalates,
resolves, and retains this customer.
```

#### 14. Project Manager

```
Role prompt: You are a PMP-certified Project Manager with experience delivering
complex software projects on time and under budget for Fortune 500 clients.

Sample task: I'm managing a website redesign project with a team of 6 (designer,
2 developers, content writer, SEO specialist, QA). The deadline is 10 weeks away.
Create a high-level project plan with milestones, dependencies, and risk flags.
```

#### 15. Research Scientist

```
Role prompt: You are a research scientist and science communicator who specializes
in translating academic research into actionable insights for business professionals.

Sample task: Summarize the key findings from behavioral economics research on
decision fatigue and explain 5 practical ways a product team could apply these
findings to improve user experience.
```

---

### Multi-Role Technique

Sometimes the best output comes from combining two or more roles. This creates a unique perspective that neither role alone would provide.

**Template:**
```
You are [Role 1] AND [Role 2]. Bring both perspectives to the following task: [task]
```

**Example:**
```
You are both a senior UX designer AND a conversion rate optimization specialist.
Review this checkout page description and tell me what changes would simultaneously
improve user experience AND increase conversion rate, noting where these goals conflict.
```

**Another Example:**
```
You are both a startup founder who bootstrapped to $5M revenue AND a VC investor
who has evaluated 300+ pitches. Review my pitch deck outline from both perspectives —
what would excite you as an investor, and what would concern you as a founder who
knows the operational reality?
```

---

### Role Selection Flowchart

```
What do you need?
        │
        ├─── Persuasive content? ──────────────→ Marketing Expert
        │
        ├─── Write or review code? ────────────→ Senior Developer
        │
        ├─── Understand data/patterns? ────────→ Data Analyst
        │
        ├─── Strategic plan or roadmap? ───────→ Strategic Consultant / CEO
        │
        ├─── Teach or explain a concept? ──────→ Expert Educator
        │
        ├─── Improve a process or workflow? ───→ Operations Manager
        │
        ├─── Handle a people problem? ─────────→ HR Manager
        │
        ├─── Financial modeling/planning? ─────→ Financial Advisor
        │
        └─── Design something? ────────────────→ UX/UI Designer
```

---

## Section 3: Chain-of-Thought Prompting

### What Is Chain-of-Thought (CoT) Prompting?

Chain-of-thought prompting guides the AI to *reason through a problem step by step* before giving a final answer. Rather than jumping to conclusions, it mimics how a thoughtful human expert approaches a complex problem.

**Why it works:**
- Forces the model to decompose complex problems
- Reduces logical errors and hallucinations
- Makes the reasoning visible so you can spot mistakes
- Dramatically improves accuracy on multi-step problems

---

### Zero-Shot CoT

The simplest CoT technique — just add a reasoning instruction to your prompt.

**Magic phrases:**
- `"Think step by step."`
- `"Walk me through your reasoning."`
- `"Show your work before giving the final answer."`
- `"Break this down into steps before answering."`

**Example:**
```
A store offers a 20% discount on a $150 item, then applies a 10% sales tax to the
discounted price. What is the final price? Think step by step.
```

**Output from AI:**
```
Step 1: Calculate the discount
  $150 × 20% = $30 discount
  Discounted price = $150 - $30 = $120

Step 2: Apply sales tax
  $120 × 10% = $12 tax
  Final price = $120 + $12 = $132

Answer: The final price is $132.
```

---

### Few-Shot CoT

Provide one or two *example reasoning chains* before your actual question. This primes the model to match your desired reasoning style.

**Template:**
```
Here is an example of how to solve this type of problem:

Problem: [example problem]
Reasoning:
  Step 1: [reasoning step]
  Step 2: [reasoning step]
  Answer: [example answer]

Now solve this problem the same way:
Problem: [your actual problem]
```

**Example (Business Pricing Decision):**
```
Here is an example analysis:

Problem: Should a coffee shop add a $12 specialty drink to their menu?
Reasoning:
  Step 1: Check profit margin — if specialty drinks cost $3 to make, margin is 75%.
  Step 2: Assess demand — specialty drinks are trending; target customer is willing to pay.
  Step 3: Check capacity — does adding it strain baristas during rush hour?
  Step 4: Risk — if it doesn't sell, wasted ingredient cost is low.
  Answer: Yes, add it — high margin, low risk, aligns with market trends.

Now analyze this problem the same way:
Problem: Should an online course creator add a $500 live coaching tier to their $97 course?
```

---

### Reasoning Chain Diagram

```
Problem → Step 1 Analysis → Step 2 Analysis → Step 3 Analysis → Conclusion
    │           │                  │                  │              │
    ▼           ▼                  ▼                  ▼              ▼
  Input       Identify           Examine            Evaluate       Final
  question    components         each part          options        answer
```

---

### 4 Detailed CoT Examples

#### Example 1: Math Reasoning

```
Prompt: A company's revenue grew from $2.4M to $3.6M over 2 years.
What was the compound annual growth rate (CAGR)? Think step by step.

AI Response:
Step 1: Identify the formula
  CAGR = (Ending Value / Beginning Value)^(1/n) - 1
  Where n = number of years = 2

Step 2: Plug in values
  CAGR = ($3.6M / $2.4M)^(1/2) - 1
  CAGR = (1.5)^(0.5) - 1

Step 3: Calculate
  (1.5)^(0.5) = √1.5 ≈ 1.2247
  CAGR = 1.2247 - 1 = 0.2247

Step 4: Convert to percentage
  CAGR ≈ 22.47%

Answer: The company's CAGR was approximately 22.5% per year.
```

#### Example 2: Business Decision

```
Prompt: My SaaS product has 1,000 free users and 50 paying customers at $29/month.
Should I focus on converting free users or acquiring new users? Think step by step.

AI Response:
Step 1: Analyze current conversion rate
  50 paying / 1,000 free = 5% conversion rate
  Industry average for SaaS freemium: 2-5%
  We're at the high end — conversion channel is working.

Step 2: Calculate acquisition cost difference
  Converting existing free users: near-zero cost (email, in-app)
  Acquiring new users: requires marketing spend (unknown, but higher)

Step 3: Evaluate upside
  If we convert 5% of remaining 950 free users: ~47 new paying customers
  At $29/month = $1,363 additional MRR with minimal spend

Step 4: Consider risks
  Pushing hard to convert may cause free users to churn entirely
  New user acquisition builds long-term pipeline

Step 5: Recommendation
  Prioritize converting free users SHORT TERM (90 days) — lower cost, faster ROI
  Build acquisition funnel in parallel for sustainable growth

Answer: Focus on conversion now, but invest in acquisition strategy simultaneously.
```

#### Example 3: Code Debugging

```
Prompt: This Python function is supposed to return the average of a list, but it 
returns wrong results sometimes. Debug it step by step.

def get_average(numbers):
    total = 0
    for n in numbers:
        total = total + n
    return total / len(numbers)

AI Response:
Step 1: Trace the logic
  The function sums all numbers and divides by length.
  Basic logic appears correct.

Step 2: Identify edge cases
  What if numbers = []? → Division by zero error (ZeroDivisionError)
  What if numbers = [1, 2, 3]? → Returns 2.0 ✓
  What if numbers contains non-numbers? → TypeError

Step 3: Identify the bug
  The function doesn't handle an empty list. Calling get_average([]) 
  will crash with ZeroDivisionError.

Step 4: Fix
  def get_average(numbers):
      if not numbers:
          return 0  # or raise ValueError, depending on requirements
      return sum(numbers) / len(numbers)

Step 5: Verify fix
  get_average([]) → returns 0 ✓
  get_average([2, 4, 6]) → returns 4.0 ✓
  get_average([5]) → returns 5.0 ✓
```

#### Example 4: Strategic Analysis

```
Prompt: A gym has seen a 40% drop in new memberships since a competitor opened
nearby. Analyze this problem and recommend a strategy. Think step by step.

AI Response:
Step 1: Diagnose root causes
  - New competitor draws away price-sensitive prospects
  - Possibly newer equipment, better amenities, or lower price
  - May be a marketing/awareness problem, not a product problem

Step 2: Gather needed information (what we'd want to know)
  - How does our pricing compare?
  - Are existing members staying or also leaving?
  - What does the competitor offer that we don't?
  - What do our members love about us?

Step 3: Identify response options
  A) Price war — risky, erodes margins
  B) Differentiation — highlight what we do better
  C) Loyalty focus — double down on retention
  D) New offerings — classes, community, coaching

Step 4: Evaluate options
  Option A: High risk, unsustainable
  Option B: Best long-term play if genuine differentiators exist
  Option C: Low cost, high ROI — existing members are assets
  Option D: Medium cost, medium risk

Step 5: Recommendation
  Immediate: Launch a referral program for existing members + conduct 20 exit interviews
  30 days: Define and market our top 3 differentiators
  60 days: Pilot 2 new class formats or programs the competitor doesn't offer

Answer: Compete on differentiation and community, not price.
```

---

### Self-Consistency Prompting

A powerful extension of CoT: ask for the same reasoning *multiple times* with slight variations, then pick the most consistent answer.

```
Solve this problem 3 different ways, using different approaches each time.
Then tell me which answer all three methods agree on.

Problem: [your problem here]
```

This technique dramatically improves accuracy on ambiguous or complex problems.

---

## Section 4: AI Workflows (Multi-Prompt Chains)

### Single Prompt vs Multi-Prompt Workflows

| | Single Prompt | Multi-Prompt Workflow |
|--|--------------|----------------------|
| **Best for** | Simple, defined tasks | Complex, multi-stage tasks |
| **Quality** | Good for straightforward outputs | Higher quality through iteration |
| **Control** | Less control over intermediate steps | Full control at each stage |
| **Time** | Faster | Takes more time |
| **Use when** | Writing a quick email | Creating a comprehensive report |

The key insight: **breaking big tasks into small prompts almost always produces better results** than one giant prompt.

---

### Workflow Diagram

```
Research → Outline → Draft → Review → Polish → Final Output
(Prompt 1) (Prompt 2) (Prompt 3) (Prompt 4) (Prompt 5)
     │           │         │          │           │
     ▼           ▼         ▼          ▼           ▼
  Raw facts   Structure  Rough     Critique    Refined
  & research  & flow     content   & gaps      deliverable
```

---

### 5 Complete Workflow Examples

---

#### Workflow 1: Blog Post Creation (5 Prompts)

**Prompt 1 — Research:**
```
You are a content research specialist. I'm writing a blog post for HR managers
titled "How to Reduce Employee Burnout in Remote Teams."

Generate:
1. The top 5 causes of remote team burnout (with brief explanation)
2. 3 statistics about remote work burnout I can cite
3. 3 expert perspectives or frameworks on this topic
```

**Prompt 2 — Outline:**
```
Using these research points: [paste Prompt 1 output]

Create a detailed blog post outline with:
- A compelling headline (3 options)
- Introduction hook
- 5 main sections with subpoints
- Conclusion with CTA
- Target word count: 1,500 words
```

**Prompt 3 — Draft:**
```
Write the full blog post based on this outline: [paste Prompt 2 output]

Guidelines:
- Tone: Empathetic and practical
- Use subheadings for each section
- Include 1 real-world example per main section
- Target 1,500 words
```

**Prompt 4 — Review:**
```
Review this blog post draft: [paste Prompt 3 output]

Evaluate and give specific feedback on:
1. Clarity and flow — are there confusing transitions?
2. Value — does each section give actionable advice?
3. Missing points — what important angle did we miss?
4. Opening hook — does it grab attention in the first 2 sentences?
5. SEO — suggest 3 places to naturally insert the keyword "remote team burnout"
```

**Prompt 5 — Polish:**
```
Rewrite the blog post incorporating this feedback: [paste Prompt 4 output]

Final requirements:
- Tighten the opening paragraph (max 3 sentences)
- Add a pull-quote or highlighted tip in each section
- End with 3 discussion questions for readers
- Ensure keyword "remote team burnout" appears 4-5 times naturally
```

---

#### Workflow 2: Market Research (4 Prompts)

**Prompt 1 — Industry Overview:**
```
Act as a market research analyst. Provide a structured overview of the
[INDUSTRY] market, including:
- Market size and growth rate
- Top 5 players and their market share estimates
- Key market trends (5 trends)
- Primary customer segments
```

**Prompt 2 — Competitive Analysis:**
```
Using this industry context: [paste Prompt 1 output]

Conduct a competitive analysis comparing the top 3 competitors on:
- Pricing model
- Key features/differentiators
- Target customer
- Weaknesses
- Marketing approach

Present this as a comparison table.
```

**Prompt 3 — Opportunity Mapping:**
```
Based on this competitive landscape: [paste Prompt 2 output]

Identify:
1. The 3 biggest unmet needs in this market
2. 2 underserved customer segments
3. 3 positioning opportunities for a new entrant
4. The #1 risk for any new player entering this market
```

**Prompt 4 — Executive Summary:**
```
Synthesize all of this research into a 1-page executive summary:
[paste Prompts 1-3 outputs]

Format:
- Market Opportunity (2-3 sentences)
- Competitive Landscape (key points only)
- Strategic Recommendation (3 bullet points)
- Key Risks (2 bullet points)
- Next Steps (3 action items)
```

---

#### Workflow 3: Software Development (5 Prompts)

**Prompt 1 — Requirements:**
```
Act as a senior product manager. I want to build: [describe your app/feature]

Help me write a Product Requirements Document (PRD) with:
- Problem statement
- Target user persona
- Core user stories (5-7 stories in "As a [user], I want to [action] so that [benefit]" format)
- Success metrics (3 KPIs)
- Out of scope (list 3 things we are NOT building in v1)
```

**Prompt 2 — Architecture:**
```
Act as a senior software architect. Based on these requirements: [paste Prompt 1]

Design the technical architecture:
- Recommended tech stack (frontend, backend, database) with justification
- High-level system components diagram (ASCII)
- Data model (main entities and relationships)
- Key technical decisions and trade-offs
```

**Prompt 3 — Implementation Plan:**
```
Act as a senior developer. Break down this architecture into implementation tasks:
[paste Prompt 2 output]

Create a sprint plan:
- Sprint 1 (Week 1-2): [tasks]
- Sprint 2 (Week 3-4): [tasks]
- Sprint 3 (Week 5-6): [tasks]
Include: definition of done for each task, estimated hours, dependencies.
```

**Prompt 4 — Code (Specific Feature):**
```
Act as a senior [language] developer. Implement [specific feature] based on 
these specs: [relevant portion of PRD]

Requirements:
- Include error handling
- Add inline comments for complex logic
- Follow [language] best practices
- Include basic unit tests
```

**Prompt 5 — Code Review:**
```
Act as a senior developer doing a code review. Review this code: [paste code]

Check for:
1. Security vulnerabilities
2. Performance issues
3. Code readability and maintainability
4. Edge cases not handled
5. Better patterns or approaches

Give specific line-by-line feedback where needed.
```

---

#### Workflow 4: Email Campaign (4 Prompts)

**Prompt 1 — Strategy:**
```
Act as an email marketing strategist. I'm launching [product/service] to [audience].

Design a 5-email launch sequence:
- Email 1: Purpose, timing, core message
- Email 2: Purpose, timing, core message
- Email 3: Purpose, timing, core message
- Email 4: Purpose, timing, core message
- Email 5: Purpose, timing, core message
Include the psychological principle behind each email.
```

**Prompt 2 — Email Writing:**
```
Write Email [#] from this sequence: [paste relevant email from Prompt 1]

Specifications:
- Subject line (3 options, A/B test ready)
- Preview text (under 90 characters)
- Email body (conversational, under 300 words)
- One clear CTA button text
- P.S. line (optional but often highest read section)
```

**Prompt 3 — Optimization:**
```
Review this email: [paste email from Prompt 2]

Optimize for:
1. Subject line open rate — what would make someone click?
2. First sentence — does it earn the second sentence?
3. Clarity of the offer — is the value crystal clear?
4. CTA strength — is there one clear next step?
5. Mobile reading — does it work in 3-second scan?
```

**Prompt 4 — Personalization Variants:**
```
Take this base email: [paste optimized email]

Create 3 versions personalized for different segments:
- Version A: For customers who have never purchased
- Version B: For customers who bought once but haven't returned
- Version C: For loyal customers (3+ purchases)
Keep each under 250 words. Highlight only the changes between versions.
```

---

#### Workflow 5: Business Report (4 Prompts)

**Prompt 1 — Data Analysis:**
```
Act as a business analyst. I'll share our Q3 performance data:
[paste your data]

Analyze and identify:
- Top 3 positive trends
- Top 3 areas of concern
- 3 unexpected findings
- Key metric that tells the most important story
```

**Prompt 2 — Narrative:**
```
Using this analysis: [paste Prompt 1]

Write the narrative sections of our Q3 business review:
- Executive Summary (3 sentences)
- What Went Well (3 paragraphs with specifics)
- What Needs Attention (2 paragraphs, honest but constructive)
- Root Cause section for our biggest challenge
```

**Prompt 3 — Recommendations:**
```
Based on this Q3 analysis: [paste Prompts 1 and 2]

Provide structured recommendations:
- 3 immediate actions (this month)
- 3 medium-term initiatives (next quarter)
- 1 strategic pivot or big bet for H1 next year
For each recommendation: what to do, why, expected impact, who owns it.
```

**Prompt 4 — Executive Presentation:**
```
Compile this into a board-ready executive presentation outline:
[paste Prompts 1-3]

Format:
- Slide 1: Q3 in One Sentence
- Slide 2: Three Key Metrics (what they are, what they mean)
- Slide 3: What's Working
- Slide 4: Challenges & Root Cause
- Slide 5: Our Plan (top 3 actions)
- Slide 6: Ask/Decision Needed from Board

Include exact bullet points and data points for each slide.
```

---

## Section 5: Project 1 — Content Generation System

### Overview

A content generation system allows you to produce high-quality, consistent content at scale. Instead of starting from scratch each time, you maintain a library of prompt templates with fill-in-the-blank slots.

```
Content Request → Select Template → Fill Variables → Generate → Review → Publish
       │                │                 │              │          │         │
       ▼                ▼                 ▼              ▼          ▼         ▼
  What do I        Blog / Social /    Audience,      AI Draft   Human      Live
  need to          Newsletter /       Topic,                    check      content
  create?          Product desc       Tone, Goal
```

---

### 10 Ready-to-Use Prompt Templates

#### Template 1: Blog Post
```
Write a [WORD COUNT]-word blog post titled "[TITLE]" for [TARGET AUDIENCE].
Tone: [TONE — e.g., conversational, authoritative, inspirational]
Include: an opening hook, [NUMBER] main sections with subheadings, practical examples, and a conclusion with [CTA].
SEO keyword to include naturally: "[KEYWORD]"
```

#### Template 2: LinkedIn Post
```
Write a LinkedIn post about [TOPIC] from the perspective of [ROLE/PERSONA].
Length: [SHORT (under 150 words) / MEDIUM (150-300 words) / LONG (300+ words with line breaks)]
Hook: Start with a surprising fact, bold statement, or relatable struggle.
End with: a question to drive comments.
Tone: [Professional / Conversational / Thought-leadership]
```

#### Template 3: Twitter/X Thread
```
Write a [NUMBER]-tweet thread about [TOPIC] for [AUDIENCE].
Tweet 1: Hook that stops the scroll (max 280 characters)
Tweets 2-[N]: One insight per tweet, each building on the last
Final tweet: Summary + CTA (follow / reply / share)
Style: [Educational / Controversial / Storytelling]
```

#### Template 4: Instagram Caption
```
Write an Instagram caption for [DESCRIPTION OF IMAGE/POST TOPIC].
Brand voice: [BRAND VOICE DESCRIPTION]
Include: an opening line that shows in feed preview (first 125 characters is crucial)
CTA: [e.g., "Save this for later" / "Tag a friend" / "Link in bio"]
Hashtags: Include [NUMBER] relevant hashtags at the end.
```

#### Template 5: Newsletter
```
Write a newsletter issue on [TOPIC] for my audience of [AUDIENCE DESCRIPTION].
Sections:
1. Opening (personal/relatable — 2-3 sentences)
2. Main Feature: [TOPIC] — [WORD COUNT] words
3. Quick Tips: 3 actionable bullet points
4. Resource of the Week: [format: title + 1 sentence why]
5. Closing + CTA
Tone: [TONE]. Reading time target: [X] minutes.
```

#### Template 6: Product Description
```
Write a product description for [PRODUCT NAME].
Product: [Brief description of what it is]
Target customer: [Who buys this and why]
Key benefits (not features): [Benefit 1], [Benefit 2], [Benefit 3]
Format: Opening hook (1 sentence) + 3 benefit-focused paragraphs + specs list
Length: [WORD COUNT]
Tone: [TONE]
```

#### Template 7: YouTube Video Script
```
Write a YouTube video script for a [LENGTH]-minute video titled "[TITLE]".
Target audience: [AUDIENCE]
Script sections:
- Hook (first 15 seconds — must earn the view)
- Introduction (what they'll learn, why it matters)
- Main content ([NUMBER] sections)
- Transitions between sections
- Call to action (subscribe / comment / watch next)
Tone: [Energetic / Educational / Conversational]
Include: [B-roll suggestions] and [on-screen text notes] in brackets.
```

#### Template 8: Facebook Ad
```
Write a Facebook ad for [PRODUCT/SERVICE].
Objective: [Awareness / Clicks / Conversions]
Target audience: [Audience description]
Pain point to address: [The problem we solve]
Offer: [What we're offering]
Format: Primary text (125 chars) + Headline (40 chars) + Description (30 chars)
CTA button: [Shop Now / Learn More / Sign Up / Get Offer]
```

#### Template 9: Email Newsletter Subject Lines
```
Generate 10 subject line options for an email about [TOPIC] targeting [AUDIENCE].
Include a mix of:
- Curiosity gap (2 options)
- Benefit-driven (2 options)  
- Question (2 options)
- Urgency/scarcity (2 options)
- Personal/conversational (2 options)
Each under 50 characters. Star your top 3 picks.
```

#### Template 10: Case Study
```
Write a customer case study for [COMPANY/CLIENT NAME] who used [PRODUCT/SERVICE].
Structure:
1. Challenge: What problem were they facing? (2-3 sentences)
2. Solution: How did they use [product/service]? (3-4 sentences)
3. Results: Specific, quantified outcomes (3 bullet points with numbers)
4. Quote: Write a realistic pull quote from the customer
5. CTA: One sentence inviting readers to get similar results
Length: [WORD COUNT]. Tone: Professional but human.
```

---

## Section 6: Project 2 — Resume Builder Prompts

### Step-by-Step Resume Building with AI

Building a complete resume with AI requires one dedicated prompt per section. This ensures depth, relevance, and proper formatting for each part.

---

#### Step 1: Professional Summary

```
Act as a professional resume writer with 10 years of experience.

Write a professional summary for a resume with these details:
- Job title/role: [ROLE]
- Years of experience: [YEARS]
- Top 3 skills: [SKILL 1], [SKILL 2], [SKILL 3]
- Key achievement: [ACHIEVEMENT WITH NUMBERS IF POSSIBLE]
- Target role/company type: [TARGET]

Requirements: 3-4 sentences, first person implied (no "I"), action-oriented, ATS-friendly.
Include 2 versions: one for a traditional company, one for a startup.
```

#### Step 2: Work Experience

```
Write 5 achievement-focused bullet points for this work experience:
- Job title: [TITLE]
- Company: [COMPANY TYPE/SIZE]
- Duration: [TIME PERIOD]
- Main responsibilities: [LIST THEM]
- Key achievements: [LIST THEM WITH ANY NUMBERS YOU KNOW]

Rules:
- Start each bullet with a strong action verb
- Include metrics/numbers where possible (estimate if needed)
- Follow format: [Action Verb] + [What you did] + [Result/Impact]
- Prioritize achievements over duties
```

#### Step 3: Skills Section

```
Based on this job description: [PASTE JOB DESCRIPTION]
And my background: [BRIEF BACKGROUND]

Create an ATS-optimized skills section:
- Technical Skills: [list]
- Soft Skills: [list — max 4, most impactful ones]
- Tools & Platforms: [list]
- Languages/Certifications: [if applicable]

Prioritize skills that appear in the job description.
```

#### Step 4: Education

```
Format my education section for a resume:
- Degree: [DEGREE]
- Institution: [SCHOOL]
- Graduation: [YEAR]
- GPA: [GPA if strong, otherwise omit]
- Relevant coursework: [LIST IF RELEVANT]
- Academic achievements: [LIST ANY HONORS, CLUBS, PROJECTS]

Include only what strengthens my candidacy for [TARGET ROLE].
```

#### Step 5: Projects

```
Write a resume-ready project description:
- Project name: [NAME]
- What it does: [DESCRIPTION]
- Technologies used: [TECH STACK]
- My role: [WHAT I DID]
- Impact/outcome: [RESULTS OR LEARNING]

Format: 2-3 bullet points. Include tech stack inline. Link format: "GitHub | Live Demo"
```

#### Step 6: Achievements & Awards

```
Rewrite these achievements for a resume, making them as impactful as possible:
[LIST YOUR RAW ACHIEVEMENTS]

Rules:
- Quantify everything possible (estimate ranges if exact numbers unknown)
- Contextualize why each achievement matters
- Use industry-relevant language
- One line each, max 120 characters
```

---

### Cover Letter Generation Prompt

```
Write a cover letter for this application:
- My name: [NAME]
- Target role: [JOB TITLE]
- Company: [COMPANY NAME]
- What I know about the company: [1-2 sentences about them]
- My most relevant experience: [EXPERIENCE]
- Why this specific role: [GENUINE REASON]
- Key achievement to highlight: [ACHIEVEMENT]

Format: 3 paragraphs — Opening hook, Middle (my fit), Closing (ask for meeting)
Length: Under 300 words. Tone: Confident, professional, not desperate.
No clichés like "I am writing to express my interest."
```

---

### Interview Preparation Prompt

```
I have an interview for [ROLE] at [COMPANY TYPE].

Prepare me by:
1. Generating the 10 most likely interview questions for this role
2. For each question, provide: the right answer framework + a sample answer using my background: [BACKGROUND]
3. Give me 5 questions I should ask the interviewer
4. What is likely the #1 concern an interviewer has about a candidate for this role, and how do I proactively address it?
```

---

### LinkedIn Profile Optimization Prompt

```
Optimize my LinkedIn profile for [TARGET ROLE]:

Current headline: [YOUR HEADLINE]
Current summary: [YOUR SUMMARY]
Target audience: [WHO I WANT TO ATTRACT — recruiters, clients, partners]

Rewrite:
1. Headline (under 220 characters, keyword-rich, value-driven)
2. About section (first 300 characters must be a hook, total 400-500 words)
3. Featured section description (what 2 posts/projects should I pin and why?)
4. 5 skills I should add/prioritize for this target role
```

---

### Complete Example: Software Developer Resume

**Summary Output:**
```
Full-stack software engineer with 5 years of experience building scalable web
applications using React, Node.js, and PostgreSQL. Reduced API response times 
by 40% at previous company through caching architecture redesign. Seeking senior 
engineer role at a growth-stage SaaS company where I can lead technical initiatives
and mentor junior developers.
```

**Work Experience Bullet Points:**
```
• Architected and shipped a real-time notification system serving 200K+ daily active 
  users, reducing support tickets about missed alerts by 65%
• Led migration from monolithic Rails app to microservices, cutting deployment time 
  from 45 minutes to under 8 minutes
• Mentored 3 junior developers through weekly code reviews and pair programming, 
  reducing their PR revision cycles by 50%
• Optimized database queries across core product, decreasing average page load time 
  from 3.2s to 0.9s — directly improving user retention metrics
• Built automated testing suite (Jest + Cypress) achieving 85% code coverage, 
  reducing production bugs by 40% quarter-over-quarter
```

---

### Complete Example: Marketing Professional Resume

**Summary Output:**
```
Results-driven digital marketing manager with 7 years of experience growing B2C
brands through content, paid media, and CRM strategy. Generated $2.3M in attributable
pipeline revenue through integrated campaigns at previous role. Proven track record 
scaling email lists from 0 to 80K subscribers and achieving consistent 35%+ open rates.
```

---

## Section 7: Project 3 — Business Assistant Prompts

### Meeting Summarizer

```
Summarize this meeting transcript/notes:
[PASTE TRANSCRIPT OR NOTES]

Output format:
📋 MEETING SUMMARY
Date: [date]
Attendees: [names]
Purpose: [one sentence]

KEY DECISIONS MADE:
• [decision 1]
• [decision 2]

ACTION ITEMS:
• [Task] — Owner: [Name] — Due: [Date]
• [Task] — Owner: [Name] — Due: [Date]

OPEN QUESTIONS / PARKING LOT:
• [unresolved item]

NEXT MEETING: [date/purpose if mentioned]
```

**Example Output:**
```
📋 MEETING SUMMARY
Date: October 15, 2024
Attendees: Sarah (PM), James (Dev Lead), Maria (Design)
Purpose: Align on v2.0 feature prioritization

KEY DECISIONS MADE:
• Dark mode deferred to v2.1 — insufficient bandwidth in Q4
• Mobile-first approach confirmed for new dashboard
• Design system migration approved for Sprint 12

ACTION ITEMS:
• Finalize feature spec document — Owner: Sarah — Due: Oct 18
• Create design mockups for new dashboard — Owner: Maria — Due: Oct 22
• Spike on performance implications of real-time sync — Owner: James — Due: Oct 17

OPEN QUESTIONS / PARKING LOT:
• Pricing implications of new feature tier (escalate to stakeholders)

NEXT MEETING: Oct 22 — Design review
```

---

### Email Composer

```
Write a professional email with these details:
- From: [YOUR ROLE]
- To: [RECIPIENT AND THEIR ROLE]
- Relationship: [first contact / ongoing / senior/junior to me]
- Purpose: [what this email needs to accomplish]
- Key information to include: [POINTS]
- Desired response/action: [what I want them to do]
- Tone: [formal / friendly / assertive / appreciative]
- Length: [short (under 100 words) / medium (100-200) / detailed (200+)]
```

---

### Business Proposal Writer

```
Write a business proposal for:
- Client: [CLIENT TYPE/INDUSTRY]
- My company/service: [WHAT WE DO]
- Proposed solution: [WHAT WE'RE PROPOSING]
- Client's problem: [THEIR CHALLENGE]
- Proposed investment: [PRICE RANGE]
- Timeline: [DURATION]

Proposal sections:
1. Executive Summary (the ask + the value in 100 words)
2. Understanding of the Problem (show we listened)
3. Proposed Solution (what we'll do, phase by phase)
4. Why Us (3 differentiators)
5. Investment (pricing table)
6. Timeline (milestone table)
7. Next Steps (what happens after they sign)
```

---

### Competitor Analysis Prompt

```
Act as a competitive intelligence analyst. Research and analyze [COMPETITOR NAME]
for a company in the [INDUSTRY] space.

Provide:
1. Company overview (size, funding, target market)
2. Product/service comparison vs. us: [YOUR PRODUCT]
   - Where they're stronger
   - Where we're stronger
   - Feature gaps on both sides
3. Pricing strategy analysis
4. Go-to-market approach (channels, messaging)
5. Recent moves (funding, launches, hires)
6. Their likely next moves (predict 2-3 strategic initiatives)
7. How we should respond (2 tactical, 1 strategic recommendation)
```

---

### Weekly Report Generator

```
Generate a professional weekly status report:

Team/Project: [NAME]
Week of: [DATE]
Report for: [AUDIENCE — manager, board, team]

Input data:
- Completed this week: [LIST]
- In progress: [LIST]
- Blockers/issues: [LIST]
- Metrics: [KEY NUMBERS]
- Next week priorities: [LIST]

Output format:
- Executive summary (3 sentences max)
- Wins this week (bullet points with impact)
- In Progress (with % complete)
- Blockers (issue + proposed resolution + owner)
- Key Metrics dashboard (formatted table)
- Next week focus (top 3 priorities)
```

---

### SWOT Analysis Prompt

```
Conduct a comprehensive SWOT analysis for: [COMPANY/PRODUCT/INITIATIVE]
Context: [BRIEF BACKGROUND — industry, stage, size]

Format as:

STRENGTHS (Internal, Positive)
• [Strength 1] — Why it matters: [brief explanation]
• [Strength 2] — Why it matters: [brief explanation]
• [Strength 3] — Why it matters: [brief explanation]

WEAKNESSES (Internal, Negative)
• [Weakness 1] — Risk level: High/Med/Low
• [Weakness 2] — Risk level: High/Med/Low

OPPORTUNITIES (External, Positive)
• [Opportunity 1] — How to capture: [brief note]
• [Opportunity 2] — How to capture: [brief note]

THREATS (External, Negative)
• [Threat 1] — Mitigation: [brief note]
• [Threat 2] — Mitigation: [brief note]

STRATEGIC IMPLICATIONS:
Top 3 strategic priorities based on this SWOT:
1. [Priority]
2. [Priority]
3. [Priority]
```

---

## Section 8: Days 15–28 Practice Program

### Week 3 (Days 15–21): Frameworks & Role Prompting

| Day | Focus | Task |
|-----|-------|------|
| Day 15 | CRAFT Framework | Write 3 prompts using CRAFT. Compare outputs to your old prompts on the same topics. |
| Day 16 | RISEN Framework | Use RISEN for a complex analysis task. Note how the step-by-step structure affects output. |
| Day 17 | Role Prompting | Try 5 different role assignments for the same task. Document which role gives the best output. |
| Day 18 | Multi-Role | Combine 2 roles for 3 different tasks. Explore where this adds unique value. |
| Day 19 | Chain-of-Thought | Use zero-shot CoT on 5 different problem types (math, strategy, analysis, creative, technical). |
| Day 20 | Few-Shot CoT | Create your own few-shot example and use it to guide reasoning on a domain you know well. |
| Day 21 | Review & Refine | Review your Week 3 prompts. Which framework produced the best outputs? Build your personal favorites library. |

### Week 4 (Days 22–28): Workflows & Projects

| Day | Focus | Task |
|-----|-------|------|
| Day 22 | Simple Workflow | Build a 3-prompt workflow for a content piece you actually need (blog, email, report). |
| Day 23 | Extended Workflow | Use the 5-prompt blog post workflow. Publish or share the output — make it real. |
| Day 24 | Business Workflow | Use the business report workflow for a real project or simulated scenario. |
| Day 25 | Resume Project | Complete the full AI-assisted resume project for yourself or a persona. |
| Day 26 | Business Assistant | Use all 5 business assistant prompts in a simulated workday. |
| Day 27 | Template Library | Build your personal prompt template library with at least 10 templates for your use cases. |
| Day 28 | Capstone | Create a complete content or business project using minimum 5 chained prompts. |

---

### Weekly Challenge 1 (End of Week 3)

**Challenge:** The Role Tournament

1. Pick one business task (e.g., write a product launch announcement)
2. Run the same task through 5 different role prompts
3. Rate each output on: Accuracy (1-5), Creativity (1-5), Usability (1-5)
4. Write a 200-word reflection on which role worked best and why

**Evaluation Criteria:**
- Did you try 5 genuinely different roles? (20 pts)
- Were your role descriptions specific? (20 pts)
- Quality of your comparison analysis (30 pts)
- Depth of reflection (30 pts)

---

### Weekly Challenge 2 (End of Week 4)

**Challenge:** The Complete Workflow

Build and execute a 5-prompt workflow for a real task:
- The task must produce something usable (not just an exercise)
- Document each prompt and the output
- Note where you had to revise prompts mid-workflow
- Write a brief "workflow retrospective" — what worked, what to change next time

**Evaluation Criteria:**
- Workflow logic (each step builds on the last) (25 pts)
- Prompt quality at each stage (25 pts)
- Final output quality (25 pts)
- Retrospective depth (25 pts)

---

## Module Summary

By completing Module 02, you now have:

✅ **Two professional frameworks** (CRAFT & RISEN) for consistent prompt quality  
✅ **15+ role prompts** ready to use across business functions  
✅ **Chain-of-thought techniques** for complex reasoning tasks  
✅ **5 complete multi-prompt workflows** for real business use  
✅ **3 complete projects** — Content System, Resume Builder, Business Assistant  
✅ **A personal prompt template library** to build on  

---

## Navigation

| | |
|--|--|
| ← Previous | [Module 01: Beginner Level](./01-beginner-level.md) |
| → Next | [Module 03: Advanced Level](./03-advanced-level.md) |
| 🏠 Home | [Course README](../README.md) |

---

*Module 02 — Intermediate Level | Generative AI Prompt Engineering Course*
