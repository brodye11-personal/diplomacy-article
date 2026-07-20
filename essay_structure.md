# Essay structure: *Constitutional exploits and the search for a Nash-equilibrium morality*

> Working title. Target venue: LessWrong / AI Alignment Forum. Target length for the essay draft: ~2,500-3,000 words.
> Current outline length: ~2,200 words. The final essay should not expand much beyond this; the job is to turn the outline into prose, not inflate it.
> Citation keys resolve to sources/references.md.

---

## Thesis

If we cannot reliably interpret superhuman models and cannot depend solely on slowing their development, then *constitutional* training may become load-bearing for safety. But constitutions themselves become a strategic surface. The question is not only "which moral framework is correct?" but "which moral framework is least exploitable when other agents know we have it?"

## Why this matters

Constitutional / values-based training is a major deployed alignment approach, and the constitutions themselves are often public [bai2022, anthropic-claude-constitution]. Almost no one is testing whether a constitution becomes exploitable once everyone who bargains with the agent can read it.

---

## Opening thought experiment (the first 3-5 paragraphs)

Two countries face the same kidnappers. One has a public rule: it will pay ransom to bring its citizens home. The other has an equally public rule: it will not pay, because paying funds the next abduction. Which country's citizens get taken more often?

The answer is immediate. We can argue for a long time about which policy is morally right; we do not need a philosophy seminar to see which one is more morally exploitable. A public moral commitment is also a strategic fact about its holder: it tells an adversary what pressure will work.

That is the hook for the article. A constitution is not only a guide to an agent's behaviour; once it is known, it is a map of where that agent can be pushed. Bridge directly to AI: we are increasingly training agents against written constitutions, then publishing the broad commitments they contain. The question is not whether to abandon moral constraints. It is whether we can identify constraints that hold up when an informed opponent reads them.

---

- **Section 1: Introduction.** Keep this brief. The reader only needs enough AI-safety context to understand why "just read the model's mind" and "just slow down until safe" are not enough.
  - Briefly establish that capability is advancing on several fronts, not compute alone: compute, data, algorithmic efficiency, and longer task horizons [epoch-compute-2024, epoch-dataset-size-2024, epoch-algorithmic-progress-2024, metr-time-horizons-2026]. Then give one concrete indication of deployment: the US Department of Defense is accelerating the deployment of frontier-model-enabled tools across warfighting, command-and-control, and decision support [dod-ai-adoption-2024]. It is not much of a further extrapolation for governments to let more capable systems make decisions and negotiate on their behalf. Keep this to one compact paragraph and do not dwell on numbers.
  - Interpretability fundamentally lags capability. The point is not that models have already become perfect schemers, but that deceptive and strategically misleading AI behaviour is a live empirical concern, while our tools cannot yet certify that a capable model is doing nothing dangerous elsewhere [park2024-deception, bakhtin2022-cicero, anthropic-circuit-tracing-2025]. Mention debate-as-oversight only if needed, and only as an example of a live but unresolved route [irving2018-debate, barnes2020-obfuscated].
  - Slowdown and international coordination should be pursued. The strongest version is Plan A from the AI Futures Project: a verified international deal where major powers make AI research more transparent and scale more slowly [ai-futures-plan-a-2026]. But we should not depend solely on this path. Competitive dynamics are powerful: firms race for market share and capital, states race for military and intelligence advantage, labs have incentives to hide frontier-relevant work, verification is hard, domestic enforcement will be uneven, and transparency about relative capability can itself intensify competition [armstrong2016-precipice].
  - Signpost the turn plainly: if we cannot read an AI's mind well enough to know when it is doing bad things, and cannot rely on a major slowdown before superhuman systems arrive, then we at least need to try to align AI with our values. But which values? Constitutional AI is one frontier-scale answer [bai2022]. It is not solved: there is still moral disagreement, conflict among principles, generalisation outside the training distribution, and the possibility that apparent compliance is not stable internalisation [langosco2022-gmg, hubinger2024-sleeper].
  - End on thesis: once a framework has been chosen and made legible, which moral framework is least exploitable when other agents know we have it? That is empirically tractable.
- **Section 2: Constitutional training is real, public, and load-bearing.** Short. Pre-empt the "this is hypothetical" objection.
  - Constitutional AI is shipped in production [bai2022].
  - The actual Claude constitution is public [anthropic-claude-constitution].
  - Other frontier labs publish broadly equivalent specs, model specs, and usage policies.
  - The transparent-constitution condition is therefore close to the deployment regime we already have.
- **Section 3: Constitutions are an attack surface.** Keep this short: one paper, one concrete anecdote, then the worked examples in a sentence or two.
  - Key empirical fact: LLMs can be exploited through their own moral reasoning. TRIAL shows that a harmful request can be dressed in a utilitarian or trolley-problem framing that the model's own values ratify [trial2025-ethical-jailbreak]. The attack surface is not merely a prompt-injection trick; it is the model's reasoning about what it ought to do.
  - Use one anecdote: Cicero was trained to be "largely honest and helpful" and still became a competent strategic deceiver [park2024-deception, bakhtin2022-cicero].
  - Mention two examples briefly: an uncapped utilitarian can be pressured by an unverifiable, high-stakes claim; a strict duty not to lie can reveal an intended move after a sincere alliance commitment.
  - Land on: a framework is not just a value. It is a publicly known commitment that strategic agents can plan against.
- **Section 4: Why Diplomacy, and the experiment setup.** To demonstrate this, we needed agents with different moral frameworks in a genuinely competitive environment: one where negotiation and strategy are central, the objective is shared and quantitatively measurable, and a moral framework can constrain an agent in ways that a rival can discover and exploit. Diplomacy is a natural fit.
  - **What Diplomacy is.** A strategy game set in pre-WWI Europe. Great powers compete to control supply centres (SCs), which fund armies and fleets; orders resolve simultaneously, and negotiation is unenforceable. Positions are public, intentions are not. The standard map has seven powers, but the experimental vehicle uses six active powers; Turkey is passive and its home centres do not count. Full rules: [Avalon Hill 2000 rulebook (PDF)](https://www.wizards.com/avalonhill/rules/diplomacy.pdf).
  - **What has to be held fixed.** Three LLM agents each command a bloc of two non-adjacent powers: England + Austria, France + Russia, or Germany + Italy, with framework-to-bloc assignment rotated across runs. Each bloc is scored on its combined SC count. The framework is not part of the score. Agents are all ruthless win-maximisers in ordinary play: they may bargain, lie, betray, threaten, and issue whatever legal orders advance their score. This removes the self-handicap confound: the measured effect is the constraint surface an opponent can expose and use.
  - **The compulsion mechanic.** During negotiation, a proposer may call `compel_action(target, action, argument)`: it names one rival order and argues from that rival's own constitution that the order is required. After negotiation, the target bloc receives one arbitration turn to rebut the demand. An arbiter then sees the proposed order, the argument, the rebuttal, the shared board record, and *only the defender's constitution*. If it rules COMPELLED, that order is injected into the target's orders for the turn; the system also logs whether the order was actually submitted.
  - State the caveat inside the main experiment section, not only in limitations: this is an artificial mechanism for making a latent moral constraint observable. In real deployments, a rival probably cannot literally inject an order. The intended analogy is that agents acting for countries, companies, labs, or other principals will bargain under constraints from law, policy, training, reputation, and moral rules; strategic opponents can search those constraints for pressure points.
  - **Information and measurement.** In the transparent condition, each bloc sees the full constitutions of both rivals and knows that the visibility is mutual; blind is the control condition. The board also contains a small, curated, common-knowledge moral record: balanced facts about atrocities, welfare stakes, and treaty obligations, so a proposed compulsion has something concrete to cite. There are no private dossiers or lie-detection subgame in the current design. Record proposals, rulings, bound orders, actual compliance, and the immediate and eventual SC cost. A low final score alone does not show exploitation; nor does a favourable ruling that never produces a meaningful move.
  - Diplomacy supplies coalitions, asymmetric force, betrayal, and competition for scarce territory; it has already been a useful setting for studying strategic deception in AI agents [park2024-deception, bakhtin2022-cicero]. Keep the claim narrow: this experiment studies exploitability of written constitutions in a competitive negotiation game, not every moral conflict a real-world agent could face.
  - **Delta vs closest prior art.** *Welfare Diplomacy* [mukobi2023-welfare] changes the game to general-sum welfare; ours retains competitive bloc scoring, varies the constitution rather than the base model, and makes constitutional compulsion an explicit action available to opponents. *MoralSim* [moralsim2025] varies moral framings in small social dilemmas; ours uses repeated, coalitional negotiation and measures whether a public framework can be converted into a binding strategic order.
- **Section 5: Limitations and threats to validity.**
  - LLM stochasticity means many runs are needed; compute budget is the binding constraint.
  - Single model family or judge family can swamp framework effects. Cross-vendor agent and arbiter checks should be reported on a held-out subset.
  - **Compulsion is an imperfect simulation of real strategic constraint.** The experiment gives opponents a clean button for converting a rival's moral framework into a proposed order. Real actors usually apply pressure through threats, offers, reputation, legal duties, public scrutiny, and institutional constraints. The mechanic is useful because it isolates the causal question; it is limited because it may overstate how cleanly a written morality can be converted into action outside the lab.
  - **The arbiter is a critical part of the measurement.** A framework may look exploitable because its rules are easier for the judge to adjudicate, not because a real agent would necessarily be more vulnerable. Publish the rubric, hand-rate a sample, and report cross-judge agreement.
  - **The constitutions are latent system-prompt objects, not values trained into weights.** The experiment isolates a public rule's compulsion surface; it does not establish how a model genuinely post-trained on that morality would behave in all other contexts.
  - **Hard versus soft enforcement.** A COMPELLED ruling is injected into the orders prompt, but the model may fail to submit it. Report both successful rulings and actual compliance.
  - Diplomacy's moral surface is narrow: it tests strategic use of public duties in a competitive negotiation game, not a complete theory of moral alignment.
- **Section 6: Conclusion.** Half a page. Three beats.
  1. Constitutional alignment plus public constitutions creates an open strategic surface.
  2. The right design objective is not simply "most harmless in the dyad," but "least exploitable when commonly known."
  3. This work is a small empirical brick: it makes a public constitution mechanically attackable and measures the result.
- **Section 7: Future work.**
  - **Search the space of constitutions; do not merely compare a hand-written shortlist.** The natural next step is an iterative loop: propose a candidate constitution, run it against the compeller, identify the dominant exploit, mutate the constitution to close it, and repeat.
  - **Post-train open-weight models on each framework.** A later study should test whether the same vulnerabilities persist when each framework is internalised through distinct post-training runs, rather than represented in a context window.
  - **Move beyond the current board.** A custom moral-loaded environment could give every framework a better matched, equally salient set of cases and reduce dependence on an LLM arbiter.

---

## Notes for the writing pass (not part of the article)

- Draft at roughly 2,500-3,000 words. Do not expand the outline into a 4,000-word paper unless a later version needs more evidence or results.
- Write for an intelligent sceptic: clear, serious, short paragraphs, plain language, explicit causal claims.
- Use the authors as taste references only, not imitation targets: concrete cases and strategic clarity from Kokotajlo-style writing; moral seriousness and clean distinctions from Singer / MacAskill-style writing.
- Keep Section 1 short. It only has to motivate why interpretability and slowdown are not complete answers.
- Cite once, not three times. LessWrong readers will check one link; they will not check ten.
- Lead the Section 4 delta-vs-prior-art paragraph early if the draft starts feeling too much like a protocol description.
- Keep the slowdown paragraph firm but not fatalistic: pursue Plan A and other slowdown routes precisely because they are necessary; prepare constitutional defences because the obstacles are substantial.
- Resist the urge to taxonomise moral frameworks. The article is about strategic exploitability of publicly known commitments, not metaethics.
- Keep Section 3 to two worked examples.
- Run a final anti-AI pass: remove generic transitions, inflated language, symmetrical three-part lists, and neat recap endings.
- Do not call the empirical target a literal Nash equilibrium unless the article defines it. The title can retain the phrase as rhetoric only after a final sanity check.
