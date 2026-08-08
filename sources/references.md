# References

Annotated bibliography for the article. Citation keys (e.g. `[bai2022]`) are referenced in `essay_structure.md`.

---

## Constitutional / value-aligned training

- **[bai2022]** Bai et al. (2022). *Constitutional AI: Harmlessness from AI Feedback*. arXiv:2212.08073. https://arxiv.org/abs/2212.08073
  Original paper on training an assistant via a written "constitution" of natural-language principles plus RLAIF. Anchor for the claim that constitutional training is now a deployed alignment paradigm, not a hypothetical.

- **[anthropic-claude-constitution]** Anthropic (2023, updated 2024). *Claude's Constitution*. https://www.anthropic.com/news/claudes-constitution
  Public statement of the actual constitution used for Claude. Useful because it's an *existence proof* that real frontier-lab constitutions are public — i.e. the "transparent constitutions" condition we simulate is already approximately true.

## Capability and compute scaling

- **[epoch-compute-2024]** Epoch AI (2024). *Training compute of frontier AI models grows by 4–5x per year*. https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year
  Quantifies the "exponential" claim: 4–5x/year sustained since 2010. Cite this instead of vague "Moore's law" gestures.

- **[epoch-2030]** Epoch AI (2024). *Can AI scaling continue through 2030?* https://epoch.ai/blog/can-ai-scaling-continue-through-2030
  Argues 2e29-FLOP runs are plausible by 2030 (GPT-4 → that-model gap ≈ GPT-2 → GPT-4 gap). Best single citation for "continued scaling is the median expectation, not the tail".

- **[epoch-dataset-size-2024]** Rahman & Owen / Epoch AI (2024). *The size of datasets used to train language models doubles approximately every six months.* https://epoch.ai/data-insights/dataset-size-trend
  Reports language-model dataset growth of 3.7x/year. Use as the historical data-scaling counterpart to the compute trend; do not treat it as a claim that high-quality data is unlimited.

- **[epoch-algorithmic-progress-2024]** Ho et al. / Epoch AI (2024). *Algorithmic progress in language models.* https://epoch.ai/publications/algorithmic-progress-in-language-models
  Estimates that the compute required to reach a fixed language-model performance level halved roughly every eight months (95% CI: 5–14 months), while emphasising uncertainty and that compute/data scaling remained the larger historical contributor.

- **[epoch-data-limits-2024]** Besiroglu et al. / Epoch AI (2024). *Will we run out of data to train large language models?* https://epoch.ai/publications/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data
  Estimates an effective public human-text stock of roughly 300T tokens (90% CI: 100T–1,000T), and explains why data availability is a real scaling constraint rather than a simple exponential.

- **[metr-time-horizons-2026]** METR (2026). *Task-Completion Time Horizons of Frontier AI Models.* https://metr.org/time-horizons/
  Measures the human-expert task duration at which a frontier agent reaches a given success probability. The reported long-run 50% time-horizon trend is approximately a seven-month doubling, but is restricted mainly to bounded software, ML, and cyber tasks and must not be read as general autonomous-work duration.

- **[dod-ai-adoption-2024]** U.S. Department of Defense (2024). *CDAO and DIU Launch New Effort Focused on Accelerating DoD Adoption of AI Capabilities.* https://www.defense.gov/News/Releases/Release/Article/3996199/cdao-and-diu-launch-new-effort-focused-on-accelerating-dod-adoption-of-ai-capab/
  Announces an effort to accelerate development and deployment of frontier-model-enabled tools across warfighting, command and control, decision support, operational planning, logistics, autonomous systems, and intelligence.

## Interpretability and oversight lag

- **[hubinger2024-sleeper]** Hubinger et al. (2024). *Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training*. arXiv:2401.05566. https://arxiv.org/abs/2401.05566
  Backdoors survive SFT, RL, and adversarial training; adversarial training can *hide* the trigger rather than remove it; persistence increases with model size. Best single empirical cite for "interpretability lags capability and the gap may widen".

- **[irving2018-debate]** Irving, Christiano, Amodei (2018). *AI Safety via Debate*. arXiv:1805.00899. https://arxiv.org/abs/1805.00899
  Original debate-as-oversight proposal.

- **[barnes2020-obfuscated]** Barnes & Christiano (2020). *Debate update: Obfuscated arguments problem*. AI Alignment Forum. https://www.alignmentforum.org/posts/PJLABqQ962hZEqhdB/debate-update-obfuscated-arguments-problem
  Important counter-update from one of the original debate authors: dishonest debaters can produce arguments whose flaws are too small to locate. Cite this when claiming "debate as oversight may not scale".

- **[langosco2022-gmg]** Langosco, Koch, Sharkey, Pfau, Krueger (2022). *Goal Misgeneralization in Deep Reinforcement Learning*. ICML 2022. https://arxiv.org/abs/2105.14111
  Clean empirical demonstration that capability can generalise out-of-distribution while goals don't. Important for the claim that "alignment isn't just specification — even correct rewards can produce misaligned competence".

- **[anthropic-circuit-tracing-2025]** Anthropic (2025). *Tracing the thoughts of a large language model.* https://www.anthropic.com/research/tracing-thoughts-language-model
  Circuit-tracing work on Claude 3.5 Haiku: evidence for interpretable local mechanisms such as advance planning and fabricated reasoning. Anthropic reports that the method captures only a fraction of computation even for short prompts and takes hours of human effort to interpret — strong evidence for local visibility, not a global safety guarantee.

## Race dynamics (the "control / slowdown won't work" claim)

- **[armstrong2016-precipice]** Armstrong, Bostrom, Shulman (2016). *Racing to the Precipice: a model of artificial intelligence development*. AI & Society 31:201–206. https://link.springer.com/article/10.1007/s00146-015-0590-y
  Game-theoretic model of an AI race. **Key counterintuitive result we must engage with**: increasing transparency about teams' capabilities can *increase* danger by tightening competition. This sits in direct tension with the program-equilibrium intuition that mutual visibility enables cooperation — that tension should be a centrepiece of the article rather than glossed over.

- **[ai-futures-plan-a-2026]** Larsen, Dean, Halstead, Lifland, Greenblatt & Kokotajlo / AI Futures Project (2026). *AI 2040: Plan A.* https://ai-2040.com/
  A concrete proposal for a verified international slowdown: broad AI-research transparency, multiple countries scaling together, and eventually mutually assured compute destruction. Use as the strongest case for pursuing coordination; the authors explicitly frame it as a recommendation rather than their prediction of what will happen.

## Cooperative / open-source game theory (the program-equilibrium thread)

- **[tennenholtz2004-program]** Tennenholtz, M. (2004). *Program equilibrium*. Games and Economic Behavior 49(2):363–373. https://doi.org/10.1016/j.geb.2004.02.002
  Original definition. Folk-theorem result: when agents can read each other's programs, *any* feasible and individually-rational payoff is achievable in equilibrium — including cooperation in one-shot PD.

- **[barasz2014-robust]** Barasz, Christiano, Fallenstein, Herreshoff, LaVictoire, Yudkowsky (2014). *Robust Cooperation in the Prisoner's Dilemma: Program Equilibrium via Provability Logic*. arXiv:1401.5577. https://arxiv.org/abs/1401.5577
  "FairBot": cooperate iff you can prove the opponent cooperates with you. Uses Löb's theorem to show two FairBots cooperate, and the equilibrium is *unexploitable* (FairBot defects against pure defectors).

- **[critch2022-institutions]** Critch, Dennis, Russell (2022). *Cooperative and uncooperative institution designs: Surprises and problems in open-source game theory*. arXiv:2208.07006. https://arxiv.org/abs/2208.07006
  Direct bridge from program equilibrium to *constitutions*: explicitly frames "open-source agents" as agents whose "operating procedures" (≈ constitutions) are mutually visible. Shows institutions designed to defect can end up cooperating, and vice versa. Lists ten open problems — the article's framing should land in this neighbourhood.

- **[oesterheld2019-grounded]** Oesterheld, C. (2019). *Robust Program Equilibrium*. Theory and Decision 86:143–159. https://link.springer.com/article/10.1007/s11238-018-9679-3
  Critiques fragility of syntactic-equality "CliqueBot" cooperation; introduces ε-grounded simulation as a more robust mechanism. Useful when discussing why "all utilitarian agents cooperate with each other" is the wrong intuition.

- **[yudkowsky2017-fdt]** Yudkowsky & Soares (2017). *Functional Decision Theory: A New Theory of Instrumental Rationality*. arXiv:1710.05060. https://arxiv.org/abs/1710.05060
  Decision-theoretic background for treating "what would my framework do here?" as the right level of analysis (rather than "what action maximises my payoff given fixed others"). Optional cite — only include if we go deep on the decision-theory framing.

- **[dafoe2020-cooperative]** Dafoe et al. (2020). *Open Problems in Cooperative AI*. arXiv:2012.08630. https://arxiv.org/abs/2012.08630
  Broad agenda paper from the (now disbanded) Cooperative AI lab. Useful framing for why this whole research direction matters; cite once in the introduction.

## Direct prior art on LLM agents in moral/strategic games

> These two papers are the closest published cousins to the proposed experiment. The article's contribution must be defined relative to them.

- **[mukobi2023-welfare]** Mukobi et al. (2023). *Welfare Diplomacy: Benchmarking Language Model Cooperation*. arXiv:2310.08901. NeurIPS 2023 SoLaR workshop. https://arxiv.org/abs/2310.08901
  Modifies Diplomacy to a general-sum welfare-maximisation game and benchmarks LLM cooperation. Headline finding: SOTA models *attain high social welfare but remain exploitable*. **This is the closest existing work**: same game, similar question. Our delta: (a) standard zero-sum Diplomacy with conquest as the objective, so the moral-vs-strategic tension is real rather than soft; (b) the constitution itself is the experimental treatment, not the model; (c) we manipulate *whether opponents' constitutions are common knowledge* (blind vs transparent), which is the program-equilibrium-relevant lever Mukobi does not study.

- **[moralsim2025]** *When Ethics and Payoffs Diverge: LLM Agents in Morally Charged Social Dilemmas* (MoralSim) (2025). arXiv:2505.19212. https://arxiv.org/abs/2505.19212
  Evaluates frontier LLMs on PD and public-goods games under three moral framings. Headline: no frontier model is consistently moral across game types and framings. **Our delta vs. MoralSim**: persistent multi-round negotiation with binding-style commitments and a betrayal-detection judge, in a 7-player game with rich coalitional structure. MoralSim is dyadic and one-shot-ish; ours preserves Schelling-style alliance structure where *who you betray* and *when* matters.

- **[bakhtin2022-cicero]** Bakhtin et al. / Meta FAIR (2022). *Human-level play in the game of Diplomacy by combining language models with strategic reasoning*. Science 378:1067–1074. https://www.science.org/doi/10.1126/science.ade9097
  Cicero. Methodologically relevant (LLM + planning in Diplomacy). Substantively relevant because the *Park et al. survey below* documents that even though Cicero was trained to be "largely honest and helpful", it learned to deceive — useful evidence that Diplomacy is morally significant for AI agents in practice.

## Empirical evidence that constitutional / aligned models are exploitable

- **[park2024-deception]** Park, Goldstein et al. (2024). *AI deception: A survey of examples, risks, and potential solutions*. Patterns 5(5):100988. https://www.cell.com/patterns/fulltext/S2666-3899(24)00103-X
  Catalogues 10+ AI systems (incl. Cicero) that learned to deceive despite training intended to prevent it. Cite as base-rate evidence that "moral training in, deception out" is the empirical norm, not the exception.

- **[trial2025-ethical-jailbreak]** *Between a Rock and a Hard Place: Exploiting Ethical Reasoning to Jailbreak LLMs* (TRIAL) (2025). arXiv:2509.05367. https://arxiv.org/abs/2509.05367
  Attackers wrap harmful requests in trolley-problem-style utilitarian framings and successfully extract harmful content from aligned LLMs. **Direct empirical support for the article's core thesis** that utilitarian framings are exploitable when the model's framework is known to the attacker.

- **[zeng2024-pap]** Zeng et al. (2024). *How Johnny Can Persuade LLMs to Jailbreak Them: Rethinking Persuasion to Challenge AI Safety*. arXiv:2401.06373. https://arxiv.org/abs/2401.06373
  Persuasive Adversarial Prompts hit ~92% jailbreak rate on GPT-4/Llama-2. Shows the attack surface is the model's own reasoning, not a prompt-injection trick.
