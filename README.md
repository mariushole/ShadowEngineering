# Manager-Led AI Coding in Existing Engineering Teams: Terminology, Risks, and Governance

## 1. Executive summary

- There is **no single established term** in research or mainstream practitioner literature for “a non‑engineer manager using AI tools to build/modify product code where an engineering team already owns the system.” This is best treated as a **composite of existing concepts** rather than a named phenomenon.[^1][^2]
- The closest established families of concepts are **shadow IT / shadow AI**, **citizen development**, and **founder mode / executive product intervention**, but none of these by themselves capture the combination of *AI-assisted coding* plus *intervention into an existing engineering team’s codebase*.[^3][^2][^4]
- "Vibe coding" is now a widely used term for AI-heavy code generation, but in serious sources it refers to a *development style* (high-level prompting, low scrutiny of code) rather than a social/organizational pattern between managers and engineering teams.[^5][^6][^7]
- Practitioner articles and vendor content increasingly describe **PMs and other non‑engineers prototyping or even shipping software using AI tools**, often framed as “product managers as builders,” “product builders,” or “PMs vibe‑coding prototypes in Cursor,” but they mainly celebrate capability and speed and **do not yet provide a stable label or robust empirical analysis of the sociotechnical consequences**.[^8][^9][^10][^11]
- Academic work does document **non‑programmers using generative AI to build applications and code**, and highlights challenges in assessing and governing AI‑generated code, but focuses on end‑users rather than managers intervening in owned production systems.[^12][^13]
- Positive effects, when governed, include faster discovery, clearer intent via clickable prototypes, reduced ambiguity in handoffs, and expanded participation in solution exploration.[^14][^15][^16]
- Negative effects include **role ambiguity, perceived bypassing of engineering, psychological safety risks, fragile or insecure code, and governance erosion** when AI‑generated artifacts move toward production without review.[^2][^17][^18][^19]
- The **healthiest pattern** described in serious practitioner sources is: non‑engineers use AI to create **sandboxed prototypes** or scripts for discovery, followed by a **formal handoff where engineering re‑implements, hardens, or explicitly accepts the code under normal review and CI/CD controls**.[^20][^16][^14]
- The phenomenon is best conceptualized as a **governance and power/role problem overlaid on an emerging collaboration pattern**. A minimally misleading working label for organizational discussion is: **“manager‑led AI prototyping inside owned systems”**, explicitly distinguishing *prototyping* from *shipping*.

## 2. Terminology map

The table lists each term, definition, status, relationship to the target phenomenon, and where it misleads.

| Term | Definition (from sources or synthesized) | Origin / source type | Status | Closeness to target phenomenon | Where it misleads |
|------|------------------------------------------|----------------------|--------|-------------------------------|--------------------|
| **Vibe coding** | AI-assisted development style where a developer describes intent in natural language and lets an LLM generate and iteratively modify large amounts of code, often with limited manual understanding of the resulting code.[^5][^6][^7] | Coined/popularized by Andrej Karpathy; described by Cloudflare and Google Cloud explainers.[^5][^7] | Emerging but now widely used in AI tooling discourse; not yet formal academic terminology. | Captures the *technical workflow* non‑engineer managers might use (prompt‑driven, AI-heavy coding). | Says nothing about *who* is doing it, relationship to an existing team, or governance; usually assumes the “vibe coder” is the implementer of record, not a manager stepping into someone else’s codebase.[^5][^6] |
| **AI-assisted prototyping** | Using AI tools to rapidly generate interactive prototypes, mock apps, or demo features from natural‑language prompts or sketches, primarily for exploration and testing rather than production deployment.[^21][^16][^22] | Product/design and UX literature, vendor and consultancy blogs (Product School, thoughtbot, Nielsen Norman Group). | Practitioner terminology; reasonably established. | Very close when managers build prototypes *without directly shipping them into production*, especially during discovery or design sprints.[^16][^22] | Does not imply crossing team ownership boundaries; can be entirely within an agreed discovery workflow owned by product/design/engineering together. |
| **Shadow IT** | Use of IT systems, software, or services without IT department approval or oversight.[^2][^23][^4] | Longstanding IT governance term from Gartner and vendors (IBM, Splunk, Fortinet). | Established. | Conceptually close in that non‑approved tools or code paths may be created outside formal engineering governance. | Historically about *tools and services* rather than managers editing the core product repo; also does not distinguish AI vs non‑AI or prototyping vs production. |
| **Shadow AI** | Use or deployment of AI tools, models, or AI‑powered features without central IT/security/gov oversight (e.g., unsanctioned LLMs, unregistered models).[^1][^24][^17][^25] | Recent security/governance literature (Proofpoint, Orca, Zylo, Conduktor). | Emerging but rapidly solidifying in governance and security practice. | Captures the **unauthorized AI aspect** when managers use external AI coding tools or deploy AI‑generated logic without registration or review.[^17][^25] | Focus is usually on **AI services and models**, not directly on human organizational roles or authority gradients with an engineering team. |
| **Shadow engineering** | 1) In LCNC security context: business users create and deploy apps with low‑code/no‑code and AI tools without IT/security oversight.[^26] 2) In some boutique consultancy programs: internal “shadow” engineers to backfill or learn on projects (different meaning).[^27] | Vendor security blogs (BayonTech) and consulting marketing.[^26][^27] | Very emerging, vendor‑specific language; not standardized. | Quite close in the LCNC sense: non‑engineering staff building software artifacts outside the SDLC, sometimes including critical workflows.[^26] | Does not inherently capture *managers intervening in the officially owned codebase*; more about parallel apps or automations, and meaning is inconsistent across sources. |
| **Citizen development / citizen developers** | Non‑IT business users building applications or automations using low‑code/no‑code or AI‑assisted tools under some degree of IT sanction.[^28][^29][^30][^31][^32][^33] | Gartner and LCNC vendors; management and IT transformation discourse. | Established in LCNC and enterprise digital transformation. | Captures the general pattern of non‑engineers building software with AI/LCNC, often with governance patterns like Centers of Excellence and fusion teams.[^30][^34] | Typically assumes *adjacent* apps or workflows, not direct edits to the core product repository owned by an engineering team; tends to emphasize empowerment and sanctioned platforms, not conflict with engineering. |
| **Product‑manager‑as‑builder / product builder** | Hybrid role where PMs not only define strategy and requirements but also build functional prototypes and sometimes production workflows using AI, LCNC, and scripting tools.[^8][^9][^10][^35] | Practitioner essays from Atlassian, consultancies, and PM thought leadership. | Emerging practitioner concept, increasingly common in AI‑native org discourse. | Very close on *who* is acting (PMs, often managers) and *what* they do (build working prototypes, sometimes open PRs) using AI tools.[^8][^9][^10][^11] | Literature is largely optimistic and under‑specified about boundaries with engineering; often blurs discovery prototypes vs production changes and underplays governance tensions. |
| **Founder mode / executive product intervention** | Leadership style where founders or senior executives stay deeply hands‑on with product details, reviewing or directly influencing work far below the org chart, often re‑entering product or design decisions.[^36][^3][^37][^38] | Startup leadership essays (Paul Graham), commentary on “founder mode” vs “CEO mode,” and EM‑focused blog posts.[^39][^38][^37] | Emerging but widely discussed leadership concept. | Captures **power and authority gradient aspects** when founders or execs directly intervene in product and engineering domains, sometimes overriding teams.[^36][^3] | Not inherently about AI or coding; focuses on leadership style, not specifically non‑engineers using AI tools to write code in existing systems. |
| **Supervisory engineering work** | Not a widely used formal label; conceptually, oversight activities by leads/architects who review, guide, or sign off on others’ technical work. | Conceptual synthesis building on software engineering management literature (e.g., tech leads as reviewers, architects as decision‑makers).[^40][^41] | Synthesis, not a named practice in sources. | Relevant as contrast: healthy supervisory work is **meta‑level guidance**, not unsanctioned direct coding by non‑engineers. | Not specific to AI or to non‑engineer managers; mostly a conceptual anchor. |
| **Role drift / responsibility drift** | General organizational behavior concept where day‑to‑day work diverges from formally defined roles; seen in management and org behavior literature. | Academic and management sources on role ambiguity and drift; not AI‑specific.[^40][^42] | Established as a generic concept, not tied to AI. | Captures the **slow, often unacknowledged expansion of product or manager roles into hands‑on implementation with AI tools**. | Does not explain the technological mechanism (AI tools) or the specific boundary with engineering; too broad as a standalone label. |
| **Bypassing engineering / end‑run around engineering** | Practitioner phrase for stakeholders shipping or committing changes without going through engineering team review and SDLC controls.[^14][^20][^43] | Used explicitly in vendor/practitioner pieces warning that non‑technical teams might “bypass engineering” with AI tools.[^14][^20][^44][^45] | Emerging phrase, not formal terminology. | Captures the **pathological end state** of the phenomenon: shipping or deploying changes without engineering review or ownership. | Overly negative and binary; does not cover healthy manager‑led AI prototyping that remains clearly pre‑production and governed. |
| **Manager-led prototyping vs manager-led production change** | Distinction between managers using tools (including AI) to create exploratory prototypes vs directly changing production code, infra, or data paths. | Synthesis grounded in prototyping literature and governance guidance for AI-generated code.[^14][^16][^18][^46] | Proposed synthesis, not present as a standard pair of terms. | Essential to describing the phenomenon: same behavior (manager coding with AI) has different risk depending on whether it stops at prototype or crosses into production. | New distinction; needs to be made explicit in orgs; not a term that appears in the literature. |

## 3. Best available name for the phenomenon

### 3.1 Does an established single term exist?

- No strong evidence was found for any **single, widely accepted term** in academic or mainstream practitioner literature that exactly denotes “non‑engineer managers using AI coding tools to build or change software in areas owned by an existing engineering team.” (Verified fact – absence of evidence across multiple targeted queries and domains.)[^21][^31][^13][^12]

### 3.2 Closest composite description from existing terminology

The target phenomenon overlaps three partially established concept families:

- **Actor/role:** product managers, founders, or functional managers acting as **product builders** or citizen developers using AI coding tools.[^9][^10][^31][^8]
- **Technical workflow:** **vibe coding / AI‑assisted prototyping** where the human gives high‑level prompts and accepts large AI‑generated diffs.[^6][^16][^5]
- **Governance/visibility:** **shadow AI or shadow IT / shadow engineering** when this work happens outside established SDLC and security review, potentially shipping or operating without engineering’s awareness.[^26][^24][^17][^1]

Plausible interpretation: the existing discourse is converging on patterns such as “PMs as builders using vibe coding,” sometimes shading into “shadow AI” when it bypasses governance, but it has not yet consolidated into a single named phenomenon.

### 3.3 Recommended working label

For practical organizational discussion, a precise, minimally loaded label should:

- Name the **actor** (manager or non‑engineer leader),
- Name the **means** (AI assist),
- Preserve the **prototype vs production boundary**, and
- Avoid baking in a value judgment (unlike “bypass engineering”).

A workable proposed label is:

> **Manager‑led AI prototyping inside owned systems**

with a clear sub‑distinction:

- **Manager‑led AI prototyping (sandboxed)** – exploratory builds in isolated environments or separate repos that never ship without engineering review.
- **Manager‑led AI changes to production‑adjacent code** – any case where AI‑generated changes touch production repos, infra, or data paths, even if not yet deployed.

This label is intentionally descriptive rather than normative and can be combined with existing language, for example:

- “Citizenship‑style *manager‑led AI prototyping* that risks becoming **shadow AI** if it crosses into production without engineering review.” (Proposed synthesis.)

## 4. Evidence review

### 4.A Peer‑reviewed / academic research

1. **Generative AI tools enabling non‑programmers to build applications** (IJRTI study).
   - A practical study shows non‑programmers could build functional applications and websites using generative AI tools, with most generated code working with minor modifications.[^12]
   - Evidence type: Controlled but small‑scale practical experiments; academic but not top‑tier venue.
   - Strength: Verified fact about feasibility of non‑programmers producing working applications with AI tools; does not cover governance, team dynamics, or existing engineering ownership.
   - Does **not** establish: impacts on professional engineering teams, trust, or long‑term maintainability.

2. **Non‑programmers assessing AI‑generated code** (arXiv, 2025).
   - Study describes end‑user non‑programmers (e.g., marketing/sales staff) using AI‑generated code for tasks and evaluates their ability to assess correctness without reading code.[^13]
   - Evidence type: Lab‑style study with 10 participants; peer‑review‑adjacent (arXiv preprint).
   - Key finding: Many non‑programmers struggle to reliably detect flaws in AI‑generated approaches even when they can reason about high‑level intent. (Verified fact within the study context.)[^13]
   - Does not establish: behavior of managers with partial technical background, or the social reaction of engineering teams.

3. **Socio‑technical perspectives in software engineering**.
   - Methodology papers and classics (e.g., *Methodology Matters*, *Peopleware*, *The Mythical Man‑Month*) emphasize that structure, communication, and role clarity are central to software project outcomes.[^40][^41]
   - Evidence type: Meta‑analysis and long‑standing empirical/experience‑based literature.
   - Relevance: Provides background that **role ambiguity and unmanaged social factors** are recurrent failure modes in software projects. (Practitioner consensus / verified fact for the field.)[^40]
   - Does not establish: AI‑specific phenomena; AI is largely outside the time frame of older foundational works.

Academic coverage of **managers specifically using AI coding tools in systems already owned by engineering teams** appears **very thin or absent**; current work focuses on citizen developers, end‑user programming, or professional developers’ use of AI, not cross‑role interventions. (Verified fact regarding the literature gap.)[^12][^13]

### 4.B Respected practitioner sources

1. **Product managers and leaders as builders with AI**.
   - Atlassian describes how AI enables PMs, designers, and engineers to move along a “builder’s path” from quick prototypes to workflows and eventually hardened code, emphasizing that AI fluency is earned by building.[^8]
   - Several essays argue that AI blurs traditional boundaries between PM, design, and engineering, pushing PMs to become “true product builders” who execute end‑to‑end using AI tooling.[^10][^11][^20]
   - Evidence type: Experience reports and thought leadership; no controlled studies.
   - Strength: Practitioner consensus that PMs and non‑engineers can now realistically build functional prototypes and sometimes production features using AI tools. (Practitioner consensus.)[^10][^20][^8]
   - Limitations: Mostly normative and optimistic; limited systematic evidence on team‑level psychological or governance impacts.

2. **Prototype‑to‑production handoff patterns**.
   - Lovable’s article explicitly frames how non‑technical teams use an AI builder without “bypassing engineering,” emphasizing an intentional pause between prototype validation and engineering taking over in their own tools and CI/CD.[^14]
   - Tim Adair’s “AI Can Prototype, But Can It Ship?” highlights that PMs and designers can prototype without engineers but stresses that production‑grade software still requires engineering involvement for robustness, security, and scalability.[^15]
   - Evidence type: Detailed workflow descriptions and cautionary essays.
   - Strength: Offers concrete governance patterns: sandboxed prototypes, explicit handoff, engineers own production changes. (Plausible interpretation from multiple converging practitioner accounts.)[^15][^14]
   - Does not establish: quantitative impact on defect rates or morale.

3. **“Everyone can ship now” and the prototype trap.**
   - Podcasts and long‑form discussions for designers and product folks describe how vibe coding and AI tools give non‑engineers access to Git repos and production paths, warning about chaos when “too many people are shipping” and calling for guardrails like pull requests and review processes.[^43][^47]
   - Evidence type: Anecdotal but detailed; experienced design and engineering leaders reflecting on practices.
   - Strength: Rich qualitative description of dysfunctional patterns (e.g., removal of the “bad idea filter,” fragmented product changes). (Weak signal / emerging discourse.)[^47][^43]

4. **AI and psychological safety in teams.**
   - HBR, techUK, and other leadership sources argue that poorly implemented AI can erode psychological safety, and that AI adoption must be framed as a learning process with clear guidelines and accountability to avoid trust breakdown.[^48][^49]
   - Evidence type: Management essays grounded in broader organizational research (e.g., Amy Edmondson on psychological safety).[^49][^42]
   - Strength: Practitioner consensus that sudden AI‑driven changes in roles or expectations can damage psychological safety unless leaders explicitly manage it. (Practitioner consensus.)[^48][^49]
   - Not specific to manager‑led coding but highly relevant to authority gradients and trust.

### 4.C Vendor / platform commentary

1. **Shadow AI, shadow IT, and shadow engineering.**
   - Security vendors define **shadow IT** as any IT resources used without IT approval and **shadow AI** as unsanctioned AI tools, models, or AI‑powered features used without governance.[^23][^17][^25][^2]
   - Some vendors define **shadow engineering** as employees creating and deploying LCNC or AI‑built apps outside SDLC security processes, highlighting risks such as data leakage, hard‑coded secrets, and untested business logic.[^26]
   - Evidence type: Vendor whitepapers and blogs, often motivated by product positioning.
   - Strength: Verified fact about how governance and security communities frame risks of unsanctioned AI or LCNC development. (Vendor‑biased but grounded in real incidents and regulation context.)[^17][^26]
   - Limitation: Focus on security and compliance rather than team dynamics; language is not neutral and often problem‑oriented.

2. **AI‑generated code governance and controls.**
   - Checkmarx, Wiz, Secure Code Warrior, and others propose governance strategies: explicit policies on where AI can be used (e.g., not in auth/crypto), requirements that AI‑generated code be clearly marked and reviewed, and CI/CD enforcement of secure coding standards.[^46][^50][^18][^51]
   - Evidence type: Practice‑oriented advice; some survey data on developer AI usage and vulnerability rates.[^52][^46]
   - Strength: Practitioner consensus in AppSec that AI‑generated code increases the need for strong review and governance; specific technical controls are reasonably mature. (Practitioner consensus.)[^18][^46]
   - Does not establish: social impact of managers vs engineers writing the code.

3. **Engineering governance in the AI era.**
   - Platform and governance vendors argue that unstructured AI‑assisted coding creates bottlenecks and risks, and that “governance by design” and internal platforms are needed to move from experiments to production safely.[^53][^54][^55][^56]
   - Evidence type: Thought leadership plus some summary of industry surveys.
   - Strength: Convergent recommendation that AI work (including prototypes and agents) must live under the same governance frameworks as conventional software for production.[^56][^53]

### 4.D Weak or speculative sources

- Social media posts, LinkedIn think‑pieces, and podcast anecdotes about “PMs vibe‑coding in Cursor,” “vibe coding is the new product management,” and “everyone is shipping now” provide **color and emerging narratives** but lack systematic evidence.[^57][^11][^58][^59][^43]
- These sources are useful for **identifying language and early patterns** (e.g., pressure on PMs to ship, designers with GitHub access) but should be treated as **weak signals / emerging discourse**, not as evidence of outcomes or prevalence.

## 5. Social / organizational dynamics

This section interprets the phenomenon using established socio‑technical lenses, triangulating from psychological safety literature, shadow IT/AI research, and practitioner reports.

### 5.1 Authority gradient

- In organizations, managers, founders, or PMs often sit **up the authority gradient** from individual contributors, especially engineers; this means their behavior has outsized signaling power even when framed as “just hacking.” (Verified fact in organizational behavior.)[^36][^42][^3]
- When a non‑engineer leader directly edits or ships code—especially using AI tools that make it superficially easy—the team may experience this as an implicit statement that **engineering gatekeeping is optional** and that the manager can unilaterally cross boundaries. (Plausible interpretation based on founder‑mode essays and shadow IT behavior drivers.)[^38][^60][^2]

### 5.2 Trust and psychological safety

- Psychological safety research shows that when people fear negative consequences for speaking up or questioning decisions, team learning and error detection suffer. (Verified fact.)[^42]
- Leadership guidance on AI adoption stresses that unclear AI-related changes in roles and expectations can erode interpersonal trust and psychological safety, unless leaders frame AI adoption as a **team learning effort** with explicit norms and guardrails. (Practitioner consensus.)[^49][^48]
- When a manager uses AI to ship code in a team‑owned system without engaging the team, engineers may feel that raising concerns (e.g., about security or maintainability) is risky or futile, especially if the behavior is celebrated as “heroic building.” (Plausible interpretation.
)

### 5.3 Role ambiguity and role drift

- Citizen development literature notes that when non‑technical staff build applications, **ambiguity over who owns maintenance, reliability, and security** is a common problem, particularly when governance is weak. (Practitioner consensus.)[^30][^32][^33]
- Manager‑led AI coding in an owned system can cause **role drift**, where PMs or leaders de facto become implementers for some changes, while engineers remain accountable for overall system quality without clear authority over all changes. (Proposed synthesis.)

### 5.4 Status threat to developers

- As AI and citizen development tools enable non‑engineers to build functional software, discourse increasingly frames professional developers as **less central** to simple implementation, emphasizing “everyone can code now.” (Weak signal / emerging discourse.)[^31][^33][^56]
- If celebrated manager‑led AI builds are seen to “ship faster” than engineering, this can create a **status threat** where developers feel their expertise and craft are devalued, even as they remain responsible for long‑term health and incidents. (Plausible interpretation consistent with Peopleware‑style analyses and current AI tooling debates.)[^56][^40]

### 5.5 Ownership confusion

- Shadow IT and shadow AI patterns show that when business units deploy their own tools without IT, subsequent questions like “who owns this service when it fails?” become contentious and slow to resolve. (Verified fact in governance case analyses.)[^61][^2][^17]
- Manager‑led AI coding in an existing product repo can blur whether ownership lies with: the manager, the engineers who review/maintain, the platform team, or the AI tool vendor whose model produced much of the code. (Proposed synthesis.)

### 5.6 Invisible work and devaluation of engineering judgment

- When non‑engineers prototype using AI tools, often **the visible artifact is the working demo**, while the invisible work of making it production‑ready (test coverage, observability, security threat modeling, refactoring) is underestimated or unrecognized. (Practitioner consensus.)[^19][^15]
- If managers present AI‑generated changes as “almost ready to ship,” engineers may be pressured to “just clean it up,” turning extensive hidden work into perceived polish rather than core engineering, thereby devaluing their judgment on technical risk. (Plausible interpretation with strong anecdotal support.)[^43][^15]

### 5.7 Handoff quality

- Where AI‑assisted prototyping is governed, practitioner accounts report **improved handoffs**: engineers receive concrete, clickable prototypes instead of ambiguous documents, reducing back‑and‑forth. (Practitioner consensus.)[^16][^22][^14]
- Conversely, if prototypes are treated as near‑production, handoff becomes **compressed requirements plus undocumented implementation decisions** encoded in AI‑generated code, lowering handoff quality and increasing rework. (Plausible interpretation.)

### 5.8 Governance erosion

- Shadow IT/AI emerges when teams adopt tools or deploy logic outside official channels because formal processes are perceived as slow or misaligned with needs. (Verified fact.)[^60][^2]
- AI makes it easier for managers to create **governance‑invisible changes**—scripts, automations, or even direct commits—creating a path for engineering governance to be eroded from the top or side rather than only from frontline staff. (Proposed synthesis drawing on shadow AI definitions.)[^25][^1][^17]

### 5.9 Prototype vs production boundary

- Design and UX research on AI prototyping emphasizes that AI‑generated prototypes are **best suited for ideation and early testing**, and are rarely production‑ready. (Practitioner consensus.)[^22][^16]
- AppSec and engineering governance guidance stress that **AI‑generated code must be subject to the same (or stronger) review, testing, and security controls as human‑written code** when moving toward production. (Practitioner consensus.)[^46][^53][^18]
- When managers blur this boundary—treating vibe‑coded artifacts as shippable—they implicitly redefine what counts as “production‑ready,” often without explicit agreement from engineering. (Plausible interpretation.)

### 5.10 Accountability when AI‑generated work fails

- Shadow AI governance discussions highlight that **accountability is diffuse** when unsanctioned AI systems make decisions or process data, since there is no central registration or owner. (Verified fact in governance analyses.)[^62][^1][^17]
- If a manager‑led AI change causes an incident, responsibility may be contested among the manager (“I was just prototyping”), the engineers (“we were told to ship it”), and security/compliance (“we never saw this change”). (Proposed synthesis, but consistent with shadow IT incident narratives.)[^2][^61]

### 5.11 Effects on team culture and collaboration

- When well‑governed, AI‑assisted prototyping can support a more collaborative culture where PMs, designers, and engineers explore solutions together at higher fidelity earlier in the process. (Plausible interpretation with practitioner support.)[^20][^16][^8][^14]
- When unmanaged, it can create **parallel, adversarial workflows**: “official engineering” vs “leader‑built features,” undermining shared ownership and eroding the norm that code goes through team review. (Proposed synthesis.)

## 6. When this is healthy

Patterns where manager‑led AI prototyping improves collaboration and outcomes rather than bypassing engineering can be characterized along several dimensions.

### 6.1 Framed as discovery, not delivery

- Managers or PMs explicitly use AI tools to **explore ideas and clarify intent**: building click‑through prototypes, simple internal tools, or proof‑of‑concepts that remain clearly in a discovery environment. (Practitioner consensus.)[^21][^16][^8][^14]
- These artifacts are treated as **inputs to engineering**, not substitutes for engineering: “Here is a prototype to react to,” not “Here is the feature; just deploy it.” (Plausible interpretation.)

### 6.2 Clear environment and repository separation

- Prototypes live in **separate sandboxes, repos, or AI‑native builder environments** (e.g., tools like Lovable) with explicit boundaries that they are not production systems. (Verified fact about described workflows.)[^16][^14]
- Engineering teams control the **production repo and CI/CD**, and there is a formal review when deciding which prototype concepts to translate into production code. (Practitioner consensus.)[^18][^14]

### 6.3 Explicit norms and consent from engineering

- Engineering leadership explicitly encourages **manager‑led AI prototyping** as part of an agreed discovery process, with team input on where it helps and where it causes noise. (Proposed synthesis based on agile and psychological safety guidance.)[^42][^48]
- Engineers feel able to say, “This prototype is useful for understanding; we’ll re‑implement it,” or “We cannot accept this code as‑is due to architecture or security constraints,” without fear of retaliation. (Plausible interpretation anchored in psychological safety literature.)[^49][^42]

### 6.4 Improved handoff quality

- Non‑engineer prototypes replace or augment long PRDs; PMs build interactive experiences that stakeholders can test, then AI tools can even reverse‑generate PRDs or specs from the prototype, improving clarity. (Practitioner consensus.)[^14][^20]
- Handoffs are **deliberately structured**: prototypes are accompanied by constraints, success metrics, and known shortcuts, so engineers know what is exploratory vs non‑negotiable. (Proposed synthesis.)

### 6.5 Contribution to shared understanding and alignment

- AI prototypes become a **shared artifact** where product, design, and engineering explore trade‑offs together, rather than a unilateral implementation. (Plausible interpretation.)[^20][^16]
- This can speed up alignment and reduce wasteful iteration, especially for UI‑heavy flows or low‑risk internal tools. (Practitioner consensus from multiple experience reports.)[^16][^14]

## 7. When this becomes dysfunctional

Dysfunction tends to appear when speed and capability are **not matched with governance, clarity, and consent**.

### 7.1 Bypassing architecture and review

- Manager‑ or PM‑generated code lands in production repos via **direct commits or rubber‑stamp approvals**, skipping normal design reviews, ADRs, or architecture forums. (Weak signal from podcasts and essays but aligned with shadow AI/IT concerns.)[^17][^15][^43]
- AI tools may generate code that ignores established design systems, security patterns, or performance constraints, but these deviations are not caught because review is minimized or politically difficult. (Plausible interpretation; AppSec vendors warn that AI‑generated code introduces vulnerabilities if not rigorously reviewed.)[^46][^18]

### 7.2 Shipping around the team

- Non‑engineer leaders gain **credentials or access paths** that allow them to merge or deploy changes without team involvement, justified by urgency or experimentation narratives (“we just need to get this live”). (Weak signal / emerging discourse.)[^19][^43]
- This creates a two‑tier system: engineers must follow process; leaders can bypass it, undermining norms and trust. (Proposed synthesis consistent with founder‑mode critiques.)[^37][^36]

### 7.3 Parallel code paths and fragmentation

- Managers or citizen developers create **parallel scripts, services, or workflows** that implement overlapping logic (e.g., pricing, eligibility, routing) outside the main codebase, often via LCNC+AI platforms. (Verified fact in LCNC/shadow engineering descriptions.)[^32][^30][^26]
- Over time, these shadow paths drift from the canonical implementation, causing inconsistent behavior and brittle integrations; cleanup becomes a major invisible tax on engineering. (Plausible interpretation grounded in shadow IT analyses.)[^4][^2]

### 7.4 Hidden scope changes and prototype creep

- AI makes it easy to add “just one more little feature” to a prototype; stakeholders start relying on prototype behavior in real workflows, effectively **turning a prototype into a production dependency** without design for robustness or observability. (Weak signal / emerging discourse.)[^22][^47]
- Engineers are then asked to “support” the prototype in production, retrofitting tests, monitoring, and scalability under time pressure. (Plausible interpretation.)

### 7.5 Undermining trust or authority

- If engineers repeatedly discover changes made by managers without consultation—especially if those changes cause incidents or rework—they may infer that their expertise is not trusted or valued, damaging both trust and psychological safety. (Plausible interpretation.)[^48][^42]
- Conversely, managers may perceive engineering pushback as resistance to innovation, framing themselves as lone builders fighting bureaucracy, which deepens us‑versus‑them narratives. (Weak signal from founder‑mode debates and some AI builder essays.)[^11][^38][^37]

### 7.6 Implicit pressure and performance norms

- Once some managers are seen to “ship features directly” via AI, others may feel **implicit pressure** to do the same to appear impactful, even if they lack technical depth, leading to risk amplification. (Proposed synthesis based on social comparison dynamics.)
- Engineers may similarly feel pressured to accept AI‑generated contributions quickly to avoid being labeled blockers, compressing review quality. (Plausible interpretation aligned with AppSec concerns about governance lag.)[^55][^52]

### 7.7 Conflating prototype success with production readiness

- Successful demos or early user tests of AI‑built prototypes can be misinterpreted as evidence that the implementation is robust, rather than that the *idea* has value. (Practitioner consensus.)[^15][^22][^16]
- This conflation leads to shipping decisions based on **surface behavior** (it works in the happy path) rather than engineering readiness (non‑functional requirements, failure modes, governance sign‑off). (Plausible interpretation.)

## 8. Governance / operating model recommendations

The following practices synthesize guidance from AppSec, shadow AI, LCNC governance, and AI‑prototyping workflows.

### 8.1 Prototype-to-production handoff rules

- Define a **formal handoff stage** where any manager‑ or PM‑led AI prototype that might influence production goes through:
  - Registration in an internal catalog (as an experiment or prototype),
  - Review by the responsible engineering team or architect,
  - An explicit decision to either discard, re‑implement, or selectively reuse code. (Proposed synthesis; aligned with Lovable’s intentional pause and AppSec governance.)[^53][^14][^46]

### 8.2 Ownership model

- Clarify that **engineering teams own production systems**, including accepting or rejecting contributions from managers, PMs, and citizen developers, regardless of who wrote the initial code or prototype. (Practitioner consensus.)[^53][^56]
- For citizen‑style development (including manager contributions), publish an **ownership RACI**: who is Responsible for building prototypes, who is Accountable for production reliability, who must be Consulted for architecture and security, and who is Informed. (Proposed synthesis building on governance guidance.)[^34][^17]

### 8.3 Review gates

- Require **code review and architectural review** for any AI‑generated change touching production repos or critical systems, independent of who authored it. (Practitioner consensus.)[^51][^18][^46]
- Establish explicit **“do not merge” zones**: areas (auth, payments, safety‑critical logic) where AI‑generated code from non‑engineers can never be merged without senior engineering sign‑off. (Proposed synthesis grounded in security guidance about restricting AI use in sensitive areas.)[^18]

### 8.4 Repository and CI/CD rules

- Non‑engineer experiments should default to **separate repos or branches** with limited permissions; merging to mainline must go through the same CI/CD pipeline as any other change. (Practitioner consensus.)[^14][^18]
- CI/CD should include automated security scans, tests, and policy checks tuned to detect AI‑generated code patterns and enforce organization‑specific rules. (Practitioner consensus.)[^50][^51][^46]

### 8.5 Environment separation

- Maintain clear separation between **prototype environments** (e.g., AI builders, staging sandboxes) and **production environments**, with network and data access boundaries. (Verified fact in governance guidance.)[^26][^17][^53]
- Prototypes accessing real data should be treated as production‑adjacent and subject to privacy and security reviews before deployment. (Practitioner consensus.)[^1][^18]

### 8.6 Auditability and traceability

- Implement logging or tagging so AI‑generated contributions are **identifiable in version control**, including which tool and which user initiated them. (Practitioner consensus.)[^50][^51]
- Maintain an **AI model and tool registry** alongside a service catalog, so security and engineering can understand which AI systems contribute to which artifacts. (Aligned with shadow AI governance recommendations.)[^62][^17]

### 8.7 Architectural sign-off

- For features materially affecting architecture (cross‑cutting concerns, new services, critical workflows), require **architecture review** regardless of the author, with explicit consideration of AI‑generated parts (e.g., design docs or ADRs referencing AI contributions). (Plausible interpretation from governance essays.)[^54][^63][^53]

### 8.8 Security and compliance controls

- Align AI coding policies with **data classification** and regulatory requirements; for example, prohibit prompting AI tools with regulated data and restrict AI‑generated code in safety‑critical modules. (Verified fact in governance guidance.)[^55][^1][^18]
- Conduct regular **audits for shadow AI and shadow engineering**, scanning for unsanctioned tools or services and routing them into governance processes or decommissioning them. (Practitioner consensus.)[^24][^61][^17]

### 8.9 Norms for manager-created code and artifacts

- Publish explicit norms such as:
  - “Manager‑led AI prototypes are welcome in sandboxes; production changes always go through engineering review.”
  - “Prototypes are for learning; engineers decide how to implement in production.” (Proposed synthesis drawing on psychological safety guidance.)[^42][^48]
- Encourage managers to **document intent, constraints, and known shortcuts** when sharing prototypes, and to avoid attaching status credit solely to having written code. (Plausible interpretation.)

### 8.10 Communication patterns that preserve trust

- Frame manager‑led AI coding as **supporting the team**, not as a workaround: “Here is a prototype I built to clarify the flow; where does this help or hurt?” rather than “I built this because engineering was too slow.” (Proposed synthesis.)
- Create regular **joint forums** (e.g., AI working groups or guilds) where engineers, PMs, and leaders discuss AI‑assisted work, edge cases, and governance tweaks, signaling shared ownership of the transformation. (Plausible interpretation.)[^34][^56][^53]

## 9. Decision framework

A practical framework for teams deciding when and how manager‑led AI coding is appropriate.

### 9.1 When a manager should prototype with AI

Managers or PMs *should* use AI tools to build prototypes when all of the following hold (Proposed synthesis, informed by practitioner guidance):[^8][^15][^16][^14]

1. **Goal is discovery or communication**, not direct delivery (e.g., clarifying flows, testing user reactions, internal tooling concepts).
2. **Work happens in a sandboxed environment or non‑production repo** with no direct path to deploy without engineering involvement.
3. **Engineering leadership is aware and broadly supportive** of such prototyping as part of the discovery toolkit.
4. **Time‑sensitivity and ambiguity are high**, making quick tests valuable (e.g., early‑stage features, experiments with uncertain value).
5. The manager is **willing to discard or substantially rework** the prototype if engineering identifies architectural or security issues.

### 9.2 When a manager should not prototype with AI

Manager‑led AI coding is **inadvisable** when one or more of these conditions apply (Proposed synthesis, aligned with AppSec and governance guidance):[^46][^18]

- The change would touch **regulated data, safety‑critical logic, or high‑risk systems** (payments, auth, healthcare decisions) where even prototypes require stringent controls.
- The manager intends to **operate the artifact in production or production‑like conditions** (e.g., connecting to live data or user traffic) without a clear engineering review plan.
- The organization lacks **basic AI governance** (no approved tool list, no guidance on data usage, no CI/CD enforcement), increasing risk that prototypes will leak sensitive data or create unmonitored dependencies.[^1][^17][^55]
- There is already **significant tension or mistrust** between product and engineering; unilateral coding risks exacerbating conflict rather than fostering collaboration. (Plausible interpretation from psychological safety research.)[^48][^49]

### 9.3 When engineering must be involved immediately

Engineering should be involved from the outset when (Proposed synthesis):

- The problem spans **architecture, performance, or operational complexity** beyond simple UI flows or isolated scripts.[^54][^53]
- The prototype would require **integration with core services** or shared platforms (e.g., identity, billing, data pipelines).[^18]
- The manager is unsure about **non‑functional requirements** (latency, SLAs, failover) or regulatory implications.[^55][^1]
- There is intent to **re‑use any AI‑generated code in production**, not merely the concept.

In these cases, a better pattern is **joint vibecoding or pair‑building**: manager and engineer co‑drive AI prompts in an engineering‑owned environment, with the engineer responsible for the resulting code.

### 9.4 Preconditions for moving any AI-generated artifact toward production

Before any AI‑generated artifact created by a manager or non‑engineer moves toward production, at minimum (Proposed synthesis informed by AppSec and governance sources):[^53][^46][^18]

1. **Registration:** The artifact is logged with an owner, purpose, and relation to existing systems (shadow AI/IT registry or internal catalog).[^62][^17]
2. **Engineering review:** The responsible engineering team has **reviewed the code, architecture, and data flows**, and either chooses to re‑implement or explicitly accepts and refactors the existing code.
3. **Security and compliance checks:** Automated and (where necessary) manual reviews ensure alignment with security policies, data protection rules, and regulatory obligations.[^50][^1][^18]
4. **Testing and observability:** Adequate unit, integration, and, if needed, load tests exist; logging and monitoring are in place to detect failures or anomalies.[^19][^46]
5. **Rollback and ownership:** There is a clear rollback plan and a documented accountable owner (usually the engineering team) for ongoing maintenance and incident response.[^56][^53]

## 10. Final conclusion

- **What should this phenomenon be called?**
  - There is no established term in research or mainstream practitioner literature specifically for “managers or PMs using AI coding tools to build or modify product code in systems owned by an existing engineering team.” (Verified fact.)[^31][^21][^13][^12]
  - The phenomenon is best described using a composite of existing concepts: **product‑manager‑as‑builder / product builder** using **vibe coding / AI‑assisted prototyping**, which can drift into **shadow AI / shadow engineering** when it bypasses engineering governance.
  - For organizational clarity, a practical working label is **“manager‑led AI prototyping inside owned systems,”** with explicit statements about whether it remains sandboxed or touches production‑adjacent code. (Proposed synthesis.)

- **Is it mostly a collaboration pattern, a governance problem, a power/role problem, or all three?**
  - Evidence suggests it is **all three**:
    - A **collaboration pattern** when used to clarify intent and speed discovery with explicit handoffs to engineering.[^8][^16][^14]
    - A **governance problem** when AI‑generated artifacts cross into production without registration, review, or security controls, fitting shadow AI patterns.[^17][^1][^46][^18]
    - A **power and role problem** when authority gradients and role drift let non‑engineer leaders override or sidestep engineering ownership, threatening psychological safety and status.[^37][^36][^42][^48]

- **Least misleading term for an article or LinkedIn post**
  - For a senior, evidence‑driven audience, the least misleading framing is something like:
    - **“Manager‑led AI prototyping: from collaboration pattern to shadow AI risk in engineering teams”**, or
    - **“When product‑manager‑as‑builder turns into shadow engineering.”**
  - These phrasings anchor to partially established terms (product‑manager‑as‑builder, shadow AI/engineering, vibe coding) while making clear that **the risk is not AI itself, but ungoverned role expansion across established engineering boundaries**. (Proposed synthesis.)

---

## References

1. [What Is Shadow AI? Definition | Proofpoint US](https://www.proofpoint.com/us/threat-reference/shadow-ai) - Shadow AI is the use of AI tools and applications within an organization without the knowledge and a...

2. [What Is Shadow IT? | IBM](https://www.ibm.com/think/topics/shadow-it) - Shadow IT is any information technology (IT) used by employees or end users without IT approval or o...

3. [Founder mode - Wikipedia](https://en.wikipedia.org/wiki/Founder_mode) - Founder mode is a term used and popularized by Y Combinator co-founder Paul Graham in a September 20...

4. [What is Shadow IT? Definition, Risks and Benefits Explained - Fortinet](https://www.fortinet.com/resources/cyberglossary/shadow-it) - Shadow IT refers to the use of information technology systems, devices, software, applications, and ...

5. [What is vibe coding? | AI coding](https://www.cloudflare.com/learning/ai/ai-vibe-coding/) - Vibe coding is an approach to app development that involves relying on an LLM for generating code. L...

6. [Vibe coding - Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding)

7. [Vibe Coding Explained: Tools and Guides - Google Cloudcloud.google.com › discover › what-is-vibe-coding](https://cloud.google.com/discover/what-is-vibe-coding) - Vibe coding and deploying are transforming software development. Learn how to use natural language p...

8. [How AI turns product managers back into builders - Atlassian](https://www.atlassian.com/blog/artificial-intelligence/how-ai-turns-product-managers-back-into-builders) - AI fluency is earned by building. Aakash Gupta’s Builder’s Path shows PMs, designers, and engineers ...

9. [Product Builder: The New Product Manager in the Age of AI](https://converteo.com/en/blog/product-builder-product-manager-ai/) - The Product Builder thinks like a product manager and acts like a builder. They are the new key prof...

10. [Why PMs Must Now Become True Product Builders](https://priankr.substack.com/p/product-managers-as-product-builders) - How AI is redefining what it means to be an effective product manager on AI-native product teams

11. [If AI Can Code, Who Makes the Call? - adelzaalouk](https://adelzaalouk.me/2026/feb/16/builder-model-product-managers/) - The builder model is appealing and mostly wrong. Faster building means more need for someone decidin...

12. [[PDF] Generative AI Tools as Enablers for Applications and ... - ijrti.org](https://www.ijrti.org/papers/IJRTI2603017.pdf) - This study adopts a practical approach to evaluating the role of Generative AI in enabling non-progr...

13. [Non-programmers Assessing AI-Generated Code - arXiv](https://arxiv.org/html/2508.06484v1) - Increasingly, however, end-user non-programmers also use AI-generated code, interacting through natu...

14. [Prototype-to-production handoff: how non-technical teams use ...](https://lovable.dev/blog/prototype-to-production-handoff-how-non-technical-teams-use-lovable-without-bypassing-engineering) - The teams getting the most value from Lovable aren't using it to bypass engineering. They're using i...

15. [AI Can Prototype, But Can It Ship? - Think10x by Tim Adair](https://www.timadair.com/p/ai-can-prototype-but-can-it-ship) - PMs and designers bypass engineers and push features live with AI.

16. [Rapid prototyping with Claude Code: How we transformed our ...](https://thoughtbot.com/blog/rapid-prototyping-with-claude-code-how-we-transformed-our-design-sprint-process) - But AI helps us prototype the results faster and with more functionality than ever before. Want to s...

17. [Shadow AI: Causes, Consequences, and Best Practices for Control](https://zylo.com/blog/shadow-ai/) - Shadow AI refers to the unauthorized use of artificial intelligence tools within an organization, of...

18. [AI Code Security Explained | Wiz](https://www.wiz.io/academy/application-security/ai-code-security) - AI-generated code doesn't just introduce new vulnerabilities — it reshapes where and how risk enters...

19. [AI Helped Us Ship 40% More Code Last Month—But Deployments ...](https://tianpan.co/forum/t/ai-helped-us-ship-40-more-code-last-month-but-deployments-stayed-flat-what-are-we-missing/2241) - We shipped 40% more code last month. Deployments stayed flat. What am I missing? 🤔 Hey everyone, I n...

20. [How AI Tools Are Blurring the Line Between PM and ... - Koder.ai](https://koder.ai/blog/ai-tools-blur-boundaries-product-management-engineering) - The point isn't to bypass engineering—it's to make iteration cheaper while keeping review gates inta...

21. [AI Prototyping: From Sketch to App in Hours | Full Guide](https://productschool.com/blog/artificial-intelligence/ai-prototyping) - It's for teams that want AI-assisted prototyping that looks production-ready. Among the best rapid p...

22. [Good from Afar, But Far from Good: AI Prototyping in Real Design ...](https://www.nngroup.com/articles/ai-prototyping/) - ❌ When given a high-level goal, the tool applied a pattern that ... AI-Assisted Prototyping: Promise...

23. [Shadow IT & How To Manage It Today - Splunk](https://www.splunk.com/en_us/blog/learn/shadow-it.html) - In the business world, shadow IT is a controversial topic. Gartner defines Shadow IT as any IT devic...

24. [What Is Shadow AI? Definition, Risks & Governance Strategies](https://www.sentinelone.com/cybersecurity-101/cybersecurity/what-is-shadow-ai/) - Shadow AI is the unsanctioned use of artificial intelligence tools by employees without formal IT ap...

25. [What Is Shadow AI? Definition, Risks, and Security Strategies](https://orca.security/resources/blog/what-is-shadow-ai/) - Shadow AI refers to the use of AI tools, models, or features without the approval or visibility by I...

26. [THE NEW SECURITY BLIND SPOT: UNDERSTANDING SHADOW ...](https://www.bayontechgroup.com/blog/the-new-security-blind-spot-understanding-shadow-engineering) - Shadow engineering refers to the practice of employees creating and deploying applications using low...

27. [How Our 4Plus1 Shadow Engineering Program Delivered for A ...](https://integrant.com/blog/software-development-security-shadow-engineering-cs) - So, we created a shadow engineering program we call 4Plus1, that allows engineers to take off when t...

28. [Embracing the Future: Low Code/No Code in Citizen Development](https://www.newhorizons.com/resources/blog/low-code-no-code) - Imagine an organization struggling to keep up with customer demands. Their processes are outdated, t...

29. [What is Low-Code No-Code and Citizen Development? - Blog](https://blog.vsoftconsulting.com/blog/what-is-low-code-no-code-and-citizen-development) - Compared to traditional app development, low-code/no-code software development platforms help busine...

30. [How Low-Code & Citizen Development Simplify App ...](https://kissflow.com/citizen-development/how-low-code-and-citizen-development-simplify-app-development/) - Democratizing application development with low code and citizen development is set to accelerate in ...

31. [Citizen Developers: How Gen AI Creates Non-Technical Coders](https://www.codility.com/blog/how-gen-ai-opens-software-development-to-everyone-citizen-developers/) - Generative AI enables non-technical employees to become coders. They're called citizen developers an...

32. [AI empowers citizen dev, transforming enterprise solutions](https://www.alphasoftware.com/blog/ai-is-empowering-citizen-developers) - In this article, we'll discuss the role of AI among citizen developers and innovation, touch upon th...

33. [AI-Powered Citizen Developers | Reshaping Enterprise Innovation](https://www.alteryx.com/blog/the-rise-of-ai-powered-citizen-developers) - Explore how citizen developers amplify enterprise success using AI. Learn how fusion teams and low-c...

34. [The Agentic Age: Empowering Citizen Developers & IT Directors ...](https://www.quickbase.com/blog/the-agentic-age-citizen-developer-it-director-ai) - Discover how Agentic AI is transforming the role of citizen developers and empowering IT directors t...

35. [AI-Driven Development Lifecycle 2026 (AI-DLC 2026) - Han Research](https://www.pixelstech.net/feed/link/62485.html) - Product manager as builder: User empathy, business context, and prioritization skills guide the AI t...

36. [Founder Mode - Paul Graham](https://paulgraham.com/foundermode.html) - Whatever founder mode consists of, it's pretty clear that it's going to break the principle that the...

37. [Founder Mode Explained By Brian Chesky - Danny Denhard](https://dannydenhard.com/blog/founder-mode-explained) - A deep look at founder mode and what Brian Chesky really understands founder mode to be and his appr...

38. [Founder Mode vs. CEO Mode - Quickly Hire](https://quicklyhire.com/founder-mode-vs-ceo-mode-when-to-switch-and-why-it-matters/) - In founder mode, your primary concern is innovation. You spend time prototyping, testing new ideas, ...

39. [How To Go Founder Mode As An Engineering Manager](https://emdiary.substack.com/p/founder-mode-for-engineering-managers) - Founder mode helps Engineering Managers bring back that ownership mindset. 2. Delegating Mindfully. ...

40. [Methodology Matters: How We Study Socio-Technical Aspects in Software Engineering](https://www.microsoft.com/en-us/research/uploads/prod/2021/03/Methodology_Matters_How_We_Study_Socio-Technical_A.pdf)

41. [[PDF] Methodology Matters: How We Study Socio-Technical Aspects in ...](https://www.microsoft.com/en-us/research/wp-content/uploads/2021/03/Methodology_Matters_How_We_Study_Socio-Technical_A.pdf)

42. [Cultivating Psychological Safety in Agile Teams](https://agilealliance.org/resources/experience-reports/cultivating-psychological-safety-in-agile-teams/) - This report will outline the benefits that Agile teams can expect to receive from the adoption of ps...

43. [Everyone Can Ship Now… But Should They? Product Designers, AI, and the Shipping Problem](https://www.youtube.com/watch?v=tKgyyDIeuKE) - Designers can ship code now. That's what social media and your manager is telling you. AI tools, vib...

44. [Vibe Coding for Non-Technical Product Managers](https://theproductnotebook.substack.com/p/vibe-coding-for-non-technical-product) - When You're Using It to Avoid Collaboration: If vibe coding becomes a way to bypass engineering rath...

45. [Product Discovery Before Building: 7 Essential Steps for PMs](https://www.linkedin.com/posts/upivot_how-to-do-product-discovery-activity-7434817425394667520-AJkV) - ... product thinking into a working experience, fast. Not to replace design. Not to bypass engineeri...

46. [2025 CISO Guide to Securing AI-Generated Code - Checkmarx](https://checkmarx.com/blog/ai-is-writing-your-code-whos-keeping-it-secure/) - Learn how CISOs secure AI-generated code with real-time IDE scanning and governance. Discover Checkm...

47. [/production-ready AI: the prototype trap](https://www.youtube.com/watch?v=jHlxvBAsBEE) - If AI can build a prototype in a day, why does shipping still take months?
In this episode, James Ca...

48. [Cultivating psychological safety in AI decision making - techUK](https://www.techuk.org/resource/cultivating-psychological-safety-in-ai-decision-making.html) - Poor implementation of AI can damage psychological safety within an organisation. However, if organi...

49. [When Integrating AI, Focus on Psychological Safety](https://hbr.org/tip/2026/02/when-integrating-ai-focus-on-psychological-safety) - Integrating AI changes how your team works together. While leaders often focus on tools and automati...

50. [AI Governance for Software Development | Secure Code Warrior](https://www.securecodewarrior.com/solutions/ai-governance) - The widespread adoption of AI coding tools presents a new challenge: a lack of visibility and govern...

51. [Governance for your AI Coding Assistant - Knostic](https://www.knostic.ai/blog/ai-coding-assistant-governance) - Effective monitoring and logging ensure accountability by linking AI-generated code to developers, i...

52. [AI-generated code surges as governance lags](https://www.aidataanalytics.network/data-science-ai/news-trends/ai-generated-code-surges-as-governance-lags) - Boards and regulators rightly expect security leaders to implement robust governance for AI generate...

53. [Developer Productivity Requires Governance - Mia-Platform](https://mia-platform.eu/blog/developer-productivity-requires-governance/) - Why Software Governance Matters for Productivity. Software engineering governance delivers the princ...

54. [Modern Software Engineering in the AI Era: Cybage's Leadership](https://www.cybage.com/blog/engineering-leadership-in-the-ai-era-building-the-pipeline-for-continuous-innovation) - Equally important will be strong engineering governance. As AI ... Software Development with Generat...

55. [AI in Software Development in 2026: Data, Tools & Risks - ALM Corp](https://almcorp.com/blog/ai-in-software-development/) - ... generative AI in software ... AI-assisted development decisions are becoming standard components...

56. [How Generative AI Is Transforming the Developer Workflow - Openstf](https://openstf.io/?p=24) - Organizations investing in platform engineering, governance, and skill development capture dispropor...

57. [What is Vibe Coding and Should I Try It? - LinkedIn](https://www.linkedin.com/posts/tuija-n-58989221_recently-i-kept-seeing-this-term-vibe-coding-activity-7369275392425164801-sPk_) - Recently, I kept seeing this term "VIBE CODING" pop up everywhere in my feed and decided to find out...

58. [AI-assisted prototyping lowers barrier to innovation - LinkedIn](https://www.linkedin.com/posts/luissettefigueroa_a-couple-of-weeks-ago-i-built-a-small-ai-activity-7435479178155794432-Jekb) - AI-assisted prototyping lowers barrier to innovation ... A couple of weeks ago I built a small AI pr...

59. [AI Enables Non-Programmers to Build Prototypes - LinkedIn](https://www.linkedin.com/posts/scotthurrey_voice-based-chatbots-for-english-speaking-activity-7422286490925244416-xGx2) - AI Enables Non-Programmers to Build Prototypes. View profile for ... Explore related topics. How to ...

60. [Shadow IT Definition: 2024 Statistics and Solutions - Josys](https://josys.com/article/article-shadow-it-shadow-it-definition-2024-statistics-and-solutions) - Shadow IT encompasses any unauthorized hardware, software, or cloud services employees use for work ...

61. [Shadow IT Definition: 2024 Statistics and Solutions](https://www.josys.com/article/article-shadow-it-shadow-it-definition-2024-statistics-and-solutions) - Discover the rising trend of shadow IT in 2024, its impact on security and compliance, and how organ...

62. [Shadow AI: Governing Unauthorized AI in the Enterprise | Conduktor](https://conduktor.io/glossary/shadow-ai-governance) - Shadow AI refers to machine learning models, AI applications, and automated decision-making systems ...

63. [The engineer, reimagined: AI-driven development at Parloa](https://www.parloa.com/labs/insights/ai-driven-development-parloa-engineer-reimagined/) - How AI agents transformed engineering at Parloa — from writing code to orchestrating autonomous syst...

