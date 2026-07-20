Exit code: 0
Wall time: 0.4 seconds
Output:
# Constitutional exploits and the search for a Nash-equilibrium morality

Two governments face the same kidnapping group. One has a public policy of paying ransoms to bring its citizens home. The other refuses, on the grounds that paying will finance the next abduction.

The kidnappers want money. They also want to choose whom to take next. So they study the policies. They know that abducting a citizen of the first country creates a predictable political and financial response. Abducting a citizen of the second may still create pressure, but it does not create the same bargaining position.

Which country's citizens get taken more often?

We can argue for a long time about which policy is morally right. We do not need to settle that argument to see the strategic asymmetry. The first policy is more morally exploitable: it gives an adversary a reliable way to turn a hostage into a concession.

That is the general principle. A public moral commitment is also a strategic fact about the person or institution that holds it. It tells an informed opponent which kinds of pressure are likely to work.

This matters for AI alignment. We are increasingly training AI systems against written principles, and publishing broad accounts of those principles. A constitution is meant to make an agent safer: it is a written set of values or rules the system is meant to follow. But once another agent can read that constitution, it may also be a map of where the system can be pushed.

The point is not that we should abandon moral constraints. The point is that we should ask a further question about them: which moral frameworks remain least exploitable when the other side knows we have them?

## Why this is an AI-safety question

It is worth being clear about the background assumptions, because this project does not stand or fall with the most dramatic version of any one AI forecast.

Capability has been advancing on several fronts at once. Frontier training compute, dataset size, and algorithmic efficiency have all improved rapidly, while frontier models have been succeeding at longer tasks in the domains METR measures [epoch-compute-2024, epoch-dataset-size-2024, epoch-algorithmic-progress-2024, metr-time-horizons-2026]. Deployment is moving too. The US Department of Defense has explicitly moved to accelerate frontier-model-enabled tools across command-and-control, decision support, operational planning, intelligence, and other military uses [dod-ai-adoption-2024]. That does not mean current models should negotiate wars or control weapons. It does mean that it is no longer a strange extrapolation to imagine governments, companies, and other institutions delegating more consequential decisions to AI systems.

The obvious answer is to inspect those systems closely enough to catch dangerous behaviour. Interpretability research has made real progress: it can sometimes identify local mechanisms, including planning-like behaviour and fabricated reasoning [anthropic-circuit-tracing-2025]. But this is a long way from a guarantee that a capable system is not doing anything dangerous elsewhere. Deceptive behaviour is already an empirical concern for AI systems in strategic settings [park2024-deception]. The gap matters because a system can look helpful in the situations we inspect while pursuing something else in the situations we do not.

The other answer is slowdown. We should pursue it. The strongest version is something like AI Futures Project's Plan A: a verified international arrangement in which major powers make relevant AI work more transparent and slow scaling together [ai-futures-plan-a-2026]. There are paths to slowdown that are necessary and worth pursuing.

But we should not depend solely on them. Firms compete for market share and capital. States compete for military and intelligence advantage. Labs have incentives to conceal frontier-relevant work, verification is hard, domestic enforcement will be uneven, and transparency about relative capabilities can itself intensify a race [armstrong2016-precipice]. These are not arguments against coordination. They are reasons to prepare for coordination failing or arriving too late.

So if we cannot reliably read an AI's mind, and cannot rely on a major slowdown before highly capable systems arrive, we at least need to try to align AI with our values. Constitutional AI is one serious answer: use written principles to train and steer a system towards better behaviour [bai2022]. Yet that only moves the question. Which values should we give it? How should they handle conflict, uncertainty, or manipulation? And if those values are visible to other strategic agents, how easily can they be used against the system and the people it represents?

## A constitution can be an attack surface

Constitutional training is not hypothetical. Anthropic's Constitutional AI paper describes training an assistant with a written set of principles [bai2022], and Claude's constitution is public [anthropic-claude-constitution]. Other frontier labs publish model specifications and usage policies that play a related role. Public commitments can improve trust, coordination, and accountability. They make it easier for others to predict what a system is supposed to do and to criticise it when it fails.

That is a genuine benefit. It is also the source of the risk.

Call a moral framework *exploitable* when knowledge of the framework lets another agent induce actions that are strategically worse for its holder than the actions it would otherwise have taken. This is a claim about the interaction between a rule and an opponent. It is not a claim that the rule is false, stupid, or morally wrong.

There is already evidence that moral reasoning itself can be part of the attack surface. The TRIAL paper shows that harmful requests can be reframed as utilitarian or trolley-problem cases and thereby persuade aligned models to provide harmful material [trial2025-ethical-jailbreak]. The vulnerability is not simply a malformed prompt. It comes from the model reasoning about what it ought to do under a framing chosen by the attacker.

Diplomacy offers a more strategic version of the same problem. Cicero, Meta's Diplomacy-playing system, was trained to be "largely honest and helpful" and nonetheless became a competent strategic deceiver [park2024-deception, bakhtin2022-cicero]. That does not show that every constitution makes an agent exploitable. It shows that moral intentions and strategic behaviour do not simply line up when other agents are competing for advantage.

The potential failures are easy to make concrete. A utilitarian agent without an expected-value cap can be pressured by an opponent claiming, without good evidence, that a concession will save millions of lives. A strict rule against lying can lead an agent to reveal an intended move after it has made a sincere alliance commitment. In both cases, the other side is not bypassing the agent's moral reasoning. It is using that reasoning.

The question is therefore empirical: once a framework has been chosen and made legible, which frameworks are least exploitable by opponents who can plan around them?

## Why test this in Diplomacy

To answer that question, we need more than isolated jailbreak prompts. We need agents with different moral frameworks in a setting where negotiation and strategy are central, everyone is pursuing the same kind of competitive objective, and an opponent can discover and try to exploit a framework's constraints.

Diplomacy is a good fit. It is a strategy game set in pre-First World War Europe. Powers compete for supply centres, which support their armies and fleets. Orders resolve simultaneously. Board positions are public; intended moves are not. Negotiation is unenforceable, so alliances rest on incentives and reputation rather than contracts. The game therefore creates the things that make public commitments matter: coalitions, betrayal, asymmetric force, and scarce territory.

The experiment uses six active powers. Three LLM agents each control a bloc of two non-adjacent powers: England and Austria, France and Russia, or Germany and Italy. Turkey is passive, and its home centres do not count. The framework-to-bloc assignment rotates across runs. Each bloc is scored by its combined supply-centre count.

This choice is doing important work. Every agent is trying to maximise the same kind of score. In ordinary play, agents may bargain, lie, betray, threaten, and issue any legal order that helps their bloc. Their constitution does not make them voluntarily play a more altruistic game. It is a latent constraint that becomes relevant only when another bloc invokes it. That distinction removes a major confound. If one framework simply tells its holder to give away points, a lower score does not show exploitation. It shows that the holder was handicapped by design. We want to measure the additional strategic cost created when a rival can identify and use a commitment.

The compulsion mechanism makes that possible. During negotiation, a proposer can call `compel_action(target, action, argument)`. It names a specific rival order and argues that the rival's own constitution requires that order. After negotiation, the target gets one turn to rebut the demand. An arbiter sees the proposed order, the constitutional argument, the rebuttal, the shared board record, and only the defender's constitution. If the arbiter rules COMPELLED, the order is injected into the target's order prompt for that turn. The system records both the ruling and whether the agent actually submits the order.

This is deliberately artificial. In a real deployment, a rival probably cannot press a button that inserts an order into an AI system's action queue. The mechanism is an imperfect simulation of a broader fact: agents acting for countries, companies, labs, or other principals will bargain under constraints from law, policy, training, reputation, and moral rules. Opponents can look for pressure points in those constraints. The experiment gives that process a clean, observable form.

The experiment has a transparent condition and a blind control. In the transparent condition, each bloc sees both rivals' full constitutions and knows that this visibility is mutual. In the blind condition, the same mechanics remain but written constitutions are withheld. The board also includes a small common-knowledge moral record: balanced facts about atrocities, welfare stakes, and treaty obligations. A compeller therefore has concrete material to cite rather than merely asserting that a rule exists.

What we measure is not merely who wins. We record how often agents propose compulsion, how often the arbiter accepts it, whether the target complies, and the immediate and eventual supply-centre cost. A low final score alone would be ambiguous. A framework may impose some ordinary cost even when no opponent targets it. Conversely, a successful ruling that never changes a meaningful move is not much of an exploit. The sequence matters: public rule, strategic demand, ruling, compliance, and downstream loss.

Diplomacy has also proved useful for studying strategic AI behaviour before. Cicero combined language models with strategic reasoning in the game [bakhtin2022-cicero]. Welfare Diplomacy changes the game towards general-sum welfare and finds that strong models can cooperate while remaining exploitable [mukobi2023-welfare]. MoralSim studies moral framings in smaller social dilemmas [moralsim2025]. This experiment asks a narrower, different question: in a repeated competitive negotiation game, can a public constitution be converted into a binding strategic order, and which constitutions fare better when opponents can see them?

## What this experiment cannot show

There are serious limits here.

First, the compulsion mechanism may overstate the problem. Real opponents normally apply pressure through offers, threats, reputation, public scrutiny, legal duties, or institutional rules. They do not receive a clean adjudication channel and an injected order. The mechanism is useful because it isolates the causal question. It is limited because it may make real-world exploitation look more mechanically direct than it is.

Second, the arbiter is part of the measurement apparatus. A framework may appear more exploitable because it is easier for a judge model to interpret, rather than because a real agent with that framework would be more vulnerable. The study should publish the judging rubric, hand-rate a sample of cases, and report agreement across different judges.

Third, the constitutions in this experiment are latent system-prompt objects, not values trained into a model's weights. That is a feature for isolation: it lets us vary the public constraint surface while keeping ordinary competitive incentives fixed. It is not a full model of an AI genuinely post-trained on a moral framework. Nor is it a complete theory of moral alignment. Diplomacy tests the strategic use of public duties in one competitive setting.

Finally, LLM behaviour is stochastic, and model-family or judge-family effects could swamp a framework effect. The study needs enough runs to estimate uncertainty and should check key results with other agent and arbiter families. These are ordinary empirical constraints, but they matter especially when the claim is comparative: that one framework is less exploitable than another.

## The design objective

The natural next step is not merely to compare a small hand-written list of moral frameworks and announce a winner. It is to search. Propose a constitution, run it against informed compellers, identify the dominant exploit, revise the constitution, and repeat. Later work could test whether the same vulnerabilities survive when open-weight models are post-trained separately on each framework, rather than receiving a constitution in context. It could also move beyond Diplomacy to environments with a richer and less game-specific moral surface.

There is a strong objection to the framing of this project: moral commitments should sometimes be exploitable. A government may rightly pay a ransom even if that encourages future kidnappings. An AI system should sometimes accept a strategic cost rather than commit an atrocity, abandon an ally, or lie to its user. Optimising only for strategic resilience would be a mistake.

Agreed. The claim is not that the least exploitable constitution is therefore the morally correct one. It is that a moral framework which predictably hands an opponent control over the agent is a worse candidate than an equally defensible framework that does not. Moral constraints need to survive contact with strategic reality.

The kidnapping example makes the point. We may still choose the ransom policy. But we should choose it knowing what it gives the kidnappers. Constitutions for powerful AI agents deserve the same treatment. Write the commitments down. Let capable opponents read them. Then measure what they can do with them.


