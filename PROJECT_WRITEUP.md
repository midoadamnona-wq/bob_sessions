# Trust 0 — Project Write-up
## IBM Bob Dev Day Hackathon · May 2026

## The challenge addressed

Every corporate employee carries KPIs that determine whether they keep their job, get promoted, or get fired. Most of those KPIs hide an uncomfortable truth: the person being measured rarely controls all the inputs.

A sales rep is measured on collection rate. The actual collection happens in Operations. A customer support agent is measured on resolution time. The product itself causes most of the issues. A marketing manager is measured on lead quality. The lead source is determined by procurement choices made two years earlier.

When the number disappoints, the person being measured pays the price. The person who actually controlled the input keeps walking.

This is not a rare edge case. It is the default state of corporate measurement. The tools we use to track KPIs — Workday, BetterWorks, Lattice, SAP — all do the same thing: they ingest whatever target the manager assigns and visualize it. They never ask "does this employee actually have authority over this number?"

Trust 0 asks that question and refuses to pretend the answer doesn't matter.

## The solution

Trust 0 is a KPI integrity platform built on three principles:

**One.** Every KPI is decomposed into its authority chain. Collection rate is not a number. It is a four-step chain: Customer pays → Operations records → Operations reports to HR → Sales credited. Each step has a controlling stakeholder. Each step is signed.

**Two.** Authority distribution is computed and locked. If Operations controls 75% of the steps, then 75% of the consequence for missing the target accrues to Operations, not the sales rep at the end of the chain. The math is transparent and auditable.

**Three.** The chain is signed quarterly by every stakeholder. CEO commits. Executives commit to their branch. Department heads commit to their slice. Individuals sign their own evaluation. When something goes wrong, you can walk the chain back to whose signature failed to reflect reality.

The product walkthrough in the demo shows this concretely. The same KPI clause that appeared in Hossam's signed contract — a single sentence about collection rate — is converted by Trust 0 into a four-step authority chain. When Q3 reports a 67% collection rate, Trust 0 cross-references its own signed evidence and finds the real number was 84%. The discrepancy is not Hossam's fault. The discrepancy traces to whoever signed off on the misreporting.

## The story shows the stakes

The first two minutes of the submission video are not a product demo. They are a story.

Adam Hossam is twelve. He has just made it to the top 5 of the Global Hackathon London Final. His father Hossam has promised him a MacBook Pro arriving tomorrow morning and tickets to fly to London with his mother on Tuesday. We see Adam confirm both promises to his team on a Teams call.

Hossam is at the office finishing a $5M deal that his manager Don Corleone congratulates him for. We see his calendar — 10,567 unread emails, 3,677 tasks due Sunday, 147 meetings this week. The MacBook is in his cart. The London tickets are on hold until 6 PM. His wife Ann gently complains that this is the third weekend in a row. He promises to make it up to her.

At 7:00 PM Hossam receives a termination email. Q3 KPI failure. Section 4.3 of the agreement he signed in January — collection rate 80% target, actual 67%, terminated effective immediately. The MacBook cart, the London tickets, the hotel — they evaporate. Adam learns the bad news on WhatsApp and replies "It's okay Dad. We'll figure it out."

Then the film splits into two universes that play in parallel. In Universe A, Hossam appeals through HR and his manager. Both reject him. The KPI he signed becomes the offer he can't refuse. In Universe B, Hossam opens Trust 0. The platform reads the chain it has been recording for six months. It produces evidence: actual collection was 84%, Operations reported 67%, four quarters of similar discrepancies for Hossam's accounts only. Hossam sends the evidence with one click. Within minutes he receives an apology and a reinstatement. The Operations Manager is placed on administrative leave pending investigation.

Same employee. Same effort. Same family. One difference: the architecture in place when the data was being recorded.

## How IBM Bob was leveraged

IBM Bob acted as the primary development partner for this submission. The collaboration unfolded across multiple iterative turns:

**Initial scoping.** I shared the concept with Bob and asked it to validate the approach as a hackathon submission. Bob confirmed that a story-led product demonstration was a strong differentiator versus pure technical demos, and reframed my initial scope from "Layer 0 architecture demo" to a customer-facing KPI integrity narrative that was easier for judges to grasp in three minutes.

**Scene-by-scene scaffolding.** I provided detailed scene specifications written as markdown files. Bob converted each scene into the appropriate HTML structure, CSS animation timing, and JavaScript scheduler logic. The two-laptop side-by-side stage with synchronized pause-resume across screens was Bob-generated based on my structural specification.

**Iteration on tone and pacing.** When initial drafts felt too fast for an audience to read, I directed Bob to slow the pacing and increase font sizes. Bob produced multiple variants and surfaced the tradeoff between number of beats and per-beat dwell time. We landed on 6-8 second beats with 14-15px message fonts.

**Product demo construction.** The 7-stage demo (Original KPI sheet → Chain conversion → Approval cascade → Hossam's KPI dashboard → Collection chain zoom → Side-by-side comparison → Q3 simulation impact split → Closing tagline) was structurally my design but rendered into HTML by Bob. The visual language for chain nodes, authority badges, signed/warned indicators was generated by Bob from my prose descriptions.

**Final closing rewrite.** When the original Don Corleone Teams message felt redundant, I asked Bob to rewrite the closing to show the actual KPI clause Hossam signed paired with the literal Godfather quote ("I'm gonna make him an offer he can't refuse"). Bob produced the layout in two iterations.

The full session export and screenshots are included in `bob_sessions/`.

Bobcoins consumed: see exported usage report. Estimated total around 280 Bobcoins across approximately 12 substantive build turns.

## Design, usability, and innovation highlights

**Design.** Two-laptop split-screen with macOS chrome creates immediate visual recognition. The pause-one-side technique (opacity 0.55 + grayscale 0.6 + frozen clock indicator) lets the audience track which universe is playing without narration. Color discipline: warm sunset for Adam's home, cool corporate for the office, dark navy with cyan accents for Trust 0 platform. The dream corner widget (MacBook + flight + hotel) sits constant in the bottom-left of Hossam's screen and visibly evaporates when termination arrives — the dream literally fades from view.

**Usability.** The film auto-plays on load. No setup required. A control bar at the bottom of the screen lets a viewer pause, jump scenes, or restart. Pause halts both JavaScript timeouts and CSS animations simultaneously through `animationPlayState`. Clock display shows ⏸ when frozen. Total runtime fits the 3-minute hackathon constraint.

**Innovation.** The submission combines three things rarely combined in hackathon entries:

1. A real product (Trust 0 — KPI integrity platform with measurable category differentiation from existing tools).
2. A real story (a father's two universes diverging on Adam's twelfth birthday).
3. A real walkthrough (seven stages showing genuine product capability, not slideware).

The Godfather thread ("Don Corleone" as manager name, "Michael Corleone" as antagonist, closing on the literal movie quote tied to the KPI clause) creates a memorable hook that distinguishes this submission from competitors.

The dual-universe parallel structure is itself a product argument. Same data. Same effort. Same family. The architecture that records the data is what determines whether Hossam keeps his job. That is what Trust 0 is selling.
