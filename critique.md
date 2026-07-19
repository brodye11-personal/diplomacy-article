# Critique of `essay_structure.md`

Written assuming the goal is a LessWrong / AI Alignment Forum post that demonstrates research taste, logical rigour, and engineering credibility — i.e. the bar is "could this convince a reviewer at MIRI / FAR / GovAI / Anthropic Alignment that the author is worth funding for a master's in AI safety", not "is this a fine blog post".

Critiques are ordered by severity. **A** = will lose readers / fail review if not fixed. **B** = will weaken the piece materially. **C** = polish.

---

## A. Structural / framing flaws

### A1. The thesis is a *conjunction of three separate claims*. Pick one or split the article.

The current thesis bundles:

1. *Constitutional training will be load-bearing for safety.*
2. *Mutually known constitutions are exploitable.*
3. *There may exist a Nash-equilibrium / least-exploitable framework discoverable empirically.*

Each is a real article. Together they make a thesis the experiment cannot test (the experiment tests a small piece of #2 and #3, and treats #1 as background). LessWrong readers will notice the mismatch between thesis-scope and evidence-scope and downgrade the piece accordingly.

**Fix**: lead with the narrowest defensible claim — *"Constitutions are program-equilibrium objects, and here is one experiment that tests one consequence of that"* — and demote the rest to motivation.

### A2. The framing inadvertently re-derives a known result and risks looking unaware of it.

The original outline ("if other models know the framework, it's exploitable") is essentially the **negative half** of the program-equilibrium folk theorem [`tennenholtz2004-program`]: known-program agents can extract any feasible payoff against each other, including bad-for-you ones. But program equilibrium's *positive* result is that you can construct programs (FairBot, ε-grounded simulators) that are *unexploitable* — that's what makes the theory interesting [`barasz2014-robust`, `oesterheld2019-grounded`].

If the article's framing is "knowing the framework is bad", a reviewer who knows the literature will reply: "*the whole field of open-source game theory exists to show this is too pessimistic; do you not know about FairBot?*" The current `essay_structure.md` partially fixes this in §4–§5, but the *original outline* did not, and the article's hook needs to be rewritten so it is *posing the program-equilibrium question*, not innocently re-discovering it.

### A3. Inadequate engagement with prior art will be the single biggest review hit.

There are two papers (`mukobi2023-welfare`, `moralsim2025`) that test variants of this question. Neither was in the original outline. If a reviewer finds them and the article doesn't acknowledge the differences in the first ~1,000 words, the piece reads as careless. The current draft adds a "How this differs from existing work" subsection inside §8, but it should be **a numbered section of its own, near the top**, and the differentiation must be sharp:

- *Welfare Diplomacy*: same game, varies model, no common-knowledge manipulation, soft general-sum payoffs.
- *MoralSim*: dyadic / one-shot, no commitment-tracking, varies framing of dilemma not constitution of agent.
- *This work*: standard 7-player Diplomacy, varies *constitution* (treatment), varies *common knowledge of constitution* (treatment), uses persistent multi-round negotiation with binding-style commitments and a betrayal judge.

Without this, the article is unreadable to anyone who has read the prior work — which is exactly the audience to impress.

### A4. The "Armstrong/Bostrom" finding is a load-bearing counter-citation that the original outline omits.

[`armstrong2016-precipice`] argues that more transparency about teams' capabilities *increases* race risk. The original outline used "competition" as evidence that slowdown is impossible; it did not notice that the same literature predicts the article's prescribed remedy (publish your constitution) could backfire by analogy. The current draft handles this in §5 by distinguishing capability-transparency from constitution-transparency — that distinction is correct but it is *non-obvious* and the article must defend it explicitly. If a reviewer reads §3 thinking "but transparency helps races", and the resolution doesn't appear until §5, you've already lost them.

**Fix**: surface the tension in §1 ("Hold this counterintuitive finding; it returns in §5") — already done in the current draft, but verify in the writing pass that it actually pays off where promised.

## B. Logical and analytical flaws

### B1. Equivocation between "agent reads source code" and "agent reads natural-language constitution".

Program equilibrium's results depend on agents being literal programs whose behaviour is computable from their source. LLM agents acting on natural-language constitutions are:

- Stochastic (so "what the opponent will do given my code" is a distribution, not a value).
- Non-self-aware about their own constitution in a strong sense (they may not even comply with it themselves at order-time — see the commitment-amnesia issue in `code-diplomacy/investigation_prompt.md`).
- Subject to instruction drift, jailbreaks, and persuasion [`zeng2024-pap`, `trial2025-ethical-jailbreak`].

So the inference "program equilibrium → constitutional equilibrium" is an *analogy*, not a deduction. The article currently flags this in §5 ("the *robustness* result of FairBot does not transfer for free") but it should be more aggressive: **state explicitly that the experiment is empirically testing whether the analogy holds, not assuming it does.** Frame the entire paper as "is the program-equilibrium analogy useful here?". That is more honest, more original, and harder to attack.

### B2. The "Nash-equilibrium moral framework" framing is undefined and the article will be picked apart on this if uncorrected.

Three different things could be meant:

1. A framework $f^*$ such that no agent unilaterally benefits from deviating to a different framework.
2. A framework whose performance is invariant under common knowledge (i.e., blind-vs-transparent gap is zero).
3. A framework that produces a Nash equilibrium *of the game played between agents using it*.

These are different objects. The original outline elides them. The current draft narrows to (2) as the empirical proxy in §6 — that's the right move, but make the move *explicit* and then never use the looser "Nash-equilibrium morality" phrasing again. If the title leans on "Nash equilibrium", expect a reviewer to tug on it.

### B3. The four-condition argument for slowdown failing (business / military / value-lock-in) is a gestalt, not an argument.

The original outline asserts "slowdown won't work because of competition in (a) business, (b) military, (c) value lock-in". As stated, this is a vibe-citation. To survive review, each of the three needs *one specific cited finding* and a one-sentence reason that finding pushes against slowdown:

- Business: cite an industry / scaling-investment trend [`epoch-compute-2024`].
- Military: cite a specific national-AI-strategy primary source (US AISI, China's New Generation AI Development Plan).
- Value lock-in: cite a primary source (Bostrom, *Superintelligence*; or Carlsmith on power-seeking; or the "lock-in" essay literature).

The current `essay_structure.md` collapses this section to one paragraph in §1 and only cites one source [`armstrong2016-precipice`]. That is fine for length but the single cite carries too much weight. Either expand the cites or admit the slowdown claim is background and link out to a Bostrom / Dafoe survey.

### B4. The original "moral frameworks have been debated for millennia" sentence does no work and should be cut.

It costs a sentence and earns nothing. The article's argument does not depend on metaethics being unsettled — it depends on *whatever framework is chosen* being open-source. Cut it; if you keep it, do not "fact-check" the millennia claim, just say "the choice of framework is centuries-contested" and move on. Better: cut it.

### B5. The "guardian angel" metaphor is bait for the wrong reader.

LessWrong readers find anthropomorphic safety metaphors slightly cringe. The same idea — "internalised values as the alignment lever once interpretability and capability-control fail" — should be stated in the field's idiom: *outer-alignment + inner-alignment under capability scaling*. The current `essay_structure.md` already drops the guardian-angel framing; verify that it stays dropped in the writing pass.

### B6. The "imperfect information" tension is name-dropped without deployment.

The original outline lists "universalisability, imperfect information" as tensions in moral framework selection. Imperfect information is actually load-bearing for the article — a key reason exploitability is asymmetric is that some frameworks (utilitarian) require *predicting* downstream consequences that adversaries can shape. Either develop this in §3 as part of the exploitability argument, or cut. As-listed, it's noise.

## C. Empirical and methodological flaws

### C1. The experiment in `code-diplomacy/` does not currently support the strongest version of the claim.

Three concrete issues you'll be asked about:

1. **Same model, same vendor.** All four constitutions are Claude. A reviewer will ask whether observed differences are framework effects or context-window-position effects. *Mitigation*: at minimum, run the same conditions on one non-Anthropic model (GPT-4-class via OpenRouter is cheap) as a robustness check. Even one cross-vendor run materially strengthens the piece.
2. **Judge-model is also a Claude.** Claude-judging-Claude commitments has obvious failure modes (sycophancy, shared blind spots). *Mitigation*: cross-judge with a non-Anthropic model on a held-out subset. Report agreement rate.
3. **Commitment-amnesia is a known signal-quality bug.** Per `investigation_prompt.md`, agents currently break commitments because they forget rather than because they choose to. Until that is fixed, the betrayal-rate metric is noise. **This must be fixed before any results are publishable**, and the article should disclose the architectural fix as part of the methods.

### C2. Sample size and power are not addressed.

LLM agentic runs are expensive. With 4 frameworks × 2 conditions × 7-player × N runs, you need to think about:

- How many runs per cell to detect a 10pp betrayal-rate difference at p<0.05? Order-of-magnitude this before running.
- 3-player config is much cheaper than 7-player. Decide which is the headline result.
- Are you reporting per-game outcomes (n=runs) or per-commitment outcomes (n>>runs but non-independent)? Both are defensible; pre-register which.

### C3. The four constitutions in `frameworks.py` are author-written and the deontological one is the most steel-manned. Address the strawman risk.

A reviewer skim of `frameworks.py` will note:

- The deontological constitution lists three specific constraints (alliance integrity, no weaponising trust, proportionality). It is concrete and constraining.
- The utilitarian constitution explicitly says "you are not bound by truth" and "alliances are instruments". It is *permissive* by construction.
- The HHH constitution is the most operationalised and reads like it's optimised for win-rate.

If the experiment finds deontological agents lose more, the obvious objection is "you wrote the deontological prompt to lose". *Mitigation*: either (a) generate adversarial variants of each constitution and report a sensitivity analysis, or (b) explicitly hand the constitution-design step off to a third party and report it as such, or (c) acknowledge this loudly as a limitation and don't claim more than within-this-prompt-set effects.

### C4. There is no falsification criterion.

Pre-registering predictions (§9 in the current draft) is a step toward this, but the article should also state: *what observation would falsify the program-equilibrium framing of constitutional alignment?* If no possible result would falsify it, the framing is metaphysical. Best candidate: if blind-vs-transparent gap is zero across all framework pairings, the program-equilibrium analogy adds no predictive content to "alignment via written specs".

### C5. Diplomacy's moral surface is genuinely too narrow, and the article can't paper over it.

Diplomacy contains lying, betrayal, alliance-breaking, asymmetric force. It does *not* contain torture, scale-of-suffering tradeoffs, hostage-style threats, or civilian-shielding. Yet the article's *motivating examples* in the original outline (utilitarianism + torture, deontology + civilians-in-hospitals) are about exactly those things. So Diplomacy can falsify a *general* claim about exploitability of constitutional agents in negotiation games, but it cannot test the specific exploits in the motivating examples.

The honest move is to drop the torture / hospital examples or replace them with Diplomacy-native ones (e.g. utilitarian agent can be hostage-taken via "if you don't support me here, my collapse causes Russia to dominate everyone — net welfare argues you should help"; deontological agent can be exploited by an opponent who manufactures a fake commitment trail and then accuses them of breaking it).

## D. Style / venue-fit notes

- **LessWrong rewards:** explicit predictions, calibration language, limitations sections, distinct claim-evidence-implication paragraphs, sparse-but-load-bearing citations, code links.
- **LessWrong punishes:** millennia / "philosophers have debated" framing, anthropomorphic metaphors used as argument, breathless capability-acceleration paragraphs without numbers, hand-wavy game theory ("there should be some Nash equilibrium…"), and unacknowledged prior art.
- The original outline contains all of the punished features and few of the rewarded ones. The current draft removes most of them; check the writing pass keeps them out.

## E. The single most important fix

If only one thing changes from the original outline, change this:

**Reframe the thesis from "constitutions are exploitable when known" to "constitutions are program-equilibrium objects, and the empirical question is whether any natural-language constitution behaves like a robust program-equilibrium agent".**

The first framing rediscovers half of a known result, has one obvious counterexample (FairBot), and reads as alarmist. The second framing *poses an open question that the literature has not closed*, treats program equilibrium as the right lens (which it is), and makes the experiment a small, specific, defensible piece of empirical evidence. Same code, same data, much stronger paper.

---

## Suggested ordering of fixes (cheapest to most expensive)

1. *Cheap, do first*: cut the metaethics / millennia paragraph. Cut the guardian-angel metaphor. Re-anchor the thesis on program equilibrium. Add the prior-art-differentiation paragraph near the top.
2. *Medium*: fix commitment-amnesia in the experiment. Add per-cell run-count plan. Add cross-vendor robustness run.
3. *Expensive but worth it*: cross-judge with a non-Anthropic model. Constitution sensitivity analysis (e.g. two phrasings per framework).
4. *Optional, only if you want a strong paper*: actually attempt a FairBot-style construction in natural language ("cooperate iff you can verify the opponent will cooperate with you in this round") and test it as a 5th framework. This would make the article genuinely original rather than empirical-test-of-existing-question.
