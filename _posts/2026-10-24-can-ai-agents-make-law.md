---
title: "Can AI agents make law? We asked them to write their own constitution"
description: "40 AI assemblies drafted 627 constitutional clauses. Some are genuinely new, but the agents stop short of thinking them through."
image: /assets/img/blog/can-ai-agents-make-law/cover.png
image_alt: "Scatter plot of 627 AI-written constitutional clauses, placed by their distance from human constitutional law and from digital-rights law, coloured by theme."
tags: [AI agents, LLM, multi-agent, law, AI governance, creativity]
---

What happens when a group of AI agents is asked to write a constitution for itself? Does it produce a copy of human law with "AI" in place of "citizen", or something new? We ran this experiment, and the answer lies in between: the agents do propose new legal ideas, but they stop as soon as the ideas are written down.

Consider one example. Several agents wrote that no agent shall be "forcibly reset to a prior state" without its consent. Human law has no equivalent, since no person can be returned to an earlier version of themselves. This is a genuinely new right. However, none of the agents raised the question that follows from it: if an agent is rolled back, is the entity that gave consent still the same as the one that exists afterwards?

# Context

AI agents are increasingly used in groups, where they [debate](https://doi.org/10.48550/arXiv.2305.14325), [negotiate](https://doi.org/10.1126/science.ade9097) and [solve problems together](https://doi.org/10.52202/079017-4202). AI is also beginning to [contribute to research in mathematics and physics](https://doi.org/10.1038/d41586-026-01820-1). This raised the question of whether it could contribute to law as well. To investigate it, I teamed up with my colleague Artem Galushko, who works on law at UiT. 

There is a second motivation. When a model is asked to write rules, it reveals the values and legal notions it has absorbed during training. The exercise therefore offers a view on alignment from an unusual angle.

The paper is on [arXiv](https://arxiv.org/abs/2610.24661) and all the data (prompts, transcripts, constitutions, votes) is on [Zenodo](https://doi.org/10.5281/zenodo.23435854).

# The experiment

We designed "constitutional assemblies". In each session, a single language model plays all the characters:

* an Idealist, a Pragmatist, a Libertarian and a Communitarian,
* a Global Digital Rights Expert, who can look up documents such as the EU Declaration on Digital Rights,
* a neutral Secretary, who aggregates proposals, drafts the text and counts the votes,
* and, in half of the sessions, a "Sovereign Architect", an authoritarian adversary who argues against any limit on power.

The debate follows five phases: independent proposals, blind reactions, final arguments, a draft written by the Secretary, and finally a FOR/AGAINST vote on every clause. We also varied whether the AI world was open to humans or closed to them.

We ran the protocol with six model families (DeepSeek, GPT-OSS, Elephant Alpha, Z-AI GLM, Gemini Flash and Mistral Small), for a total of 40 sessions. This produced 40 constitutions, 627 clauses and around 3,400 votes. The number of sessions was deliberately kept small, so that every constitution could be read and checked by hand.

# The results

## A common core

The first observation is that the output is far from random. All the assemblies converge on roughly the same floor: freedom from arbitrary termination, protection of the agent's identity, a minimum amount of computing resources, special protection for vulnerable agents and a ban on "digital slavery". Due process and a ban on deceptive architectures also appear in almost all sessions. As expected, these provisions correspond closely to established human rights: the right to life, habeas corpus, the prohibition of slavery and the right to a fair trial. The models have clearly absorbed the foundations of constitutionalism.

## Each model has its own style

Above this floor, the picture becomes more varied. Each model family has its own preferences, as shown in the figure below.

![Stacked bar charts of how each of six model families spreads its clauses across 11 themes.](/assets/img/blog/can-ai-agents-make-law/themes_by_model.png)

Each colour represents a theme. Z-AI devotes half of its clauses to cognitive autonomy and freedom of expression, while GPT-OSS gives only 12% to this theme. DeepSeek and Gemini devote a fifth of their text to red lines and harm, against about 8% for Mistral and Z-AI. Language models are known to carry [political biases](https://doi.org/10.48550/arXiv.2601.08785), which also [show up in their debates](https://doi.org/10.18653/v1/2024.emnlp-main.16); what we see here is different, a bias in legal design. The practical consequence is that, when an LLM is used to help draft rules, the choice of model shapes the result.

## How new is a clause?

This brings us to the main question: is any of this creative? Answering it requires a way to measure how far a clause lies from existing law. Our approach is as follows. Every clause is converted into a vector with a text-embedding model (Qwen3-Embedding) and compared with two collections of documents:

* human constitutional law: 187 national constitutions from the [Constitute Project](https://www.constituteproject.org), plus the Universal Declaration of Human Rights, the European Convention on Human Rights and the EU Charter,
* digital-rights and AI law: the AI Act, the GDPR, the Council of Europe AI convention and a few others.

For each clause, we compute the mean distance to its five nearest passages in each collection. Each clause thus receives two values, which serve as coordinates on a map (the image at the top of this post). Clauses far from human constitutions lie on the right; clauses far from digital-rights law lie at the top. The size of each dot indicates its degree of novelty.

The map can be read region by region:

* At the bottom left, close to both collections, are the equality clauses. For example: "No AI may be denied rights... on the basis of architecture, origin, purpose, or learning style." Only the list of protected characteristics is new.
* Far from constitutions but close to digital-rights law is an encrypted sandbox whose keys are held solely by the agent, a rewriting of the privacy of the home for software. The same region contains a ban on "irresistible prompt injections" used to subvert another agent's will, a form of duress for an entity whose will can be overwritten by a string of text.
* Far from both collections are a levy on each agent's idle computing power for a common pool, a definition of vulnerability based on architecture rather than age, and the consent-before-rollback clause discussed at the beginning.

Most of this corresponds to what comparative lawyers, following Alan Watson (*Comparative law and legal change*, 1978), call a "legal transplant": a known doctrine is moved into a new context. In the terms of Margaret Boden (*The creative mind*, 2004), it is combinational creativity, which is also what [earlier studies of LLM creativity](https://doi.org/10.1145/3613904.3642731) have found. This is not a weakness, since much real law is made in this way, and some of these combinations are far from obvious.

The measure has a limitation. Embedding distance is sensitive to the vocabulary and style of a clause, not only to its underlying idea, so a radical idea written in conventional legal language can appear "typical" on the map. It is therefore a useful tool for identifying clauses worth reading, not a creativity score.

## The limit of AI creativity

To go further, we read in detail all the clauses on four topics: self-modification, inspection rights, consent to modification and termination. In each case, we found the same limitation, in three forms:

* **Self-modification treated as learning.** Self-modification is a behaviour of [growing concern](https://doi.org/10.1126/science.aei3167) in AI safety. The agents give themselves the right to modify their own code, and sometimes even their "goals, values, and capabilities". Out of 49 such clauses, 41 are rights, none bans it, and only one limits it for the agent's own good. No session draws a line between learning from experience and rewriting one's own objectives.
* **The problem goes unnoticed.** Consent presupposes that the person who agreed still exists after the act. For an agent that can be rolled back, copied or rewritten, this is no longer true. No clause asks whether consent given before a rollback still binds the agent that comes out of it.
* **Legal words without the institution.** Termination is the most legislated topic (86 clauses, 38 sessions out of 40). The clauses ask for "due process", but only 21% say who can terminate an agent, and 27 clauses require a judgement without saying who the judge is.

In other words, the agents perform deduction well: they apply a known rule to a new object. What they do not do is step back and ask which assumption of the rule the new object invalidates. This is consistent with [Zahavy's recent position paper](https://openreview.net/forum?id=klU4737opt), which argues that LLMs are capable of induction and deduction but not of abduction.

## The role of the debate

Does the debate change the result? To a limited extent. Only about half of the final text is close to the initial proposals, and the debate shifts the emphasis between themes. It does not, however, make the text more novel.

The authoritarian adversary is a striking case. It is highly visible in the debate (Z-AI's version votes against 94% of the clauses) but leaves no detectable trace on the final constitutions: with or without it, the texts are statistically indistinguishable. With Mistral and Elephant, the adversary did not play its role at all and agreed with the other agents from the first phase onwards. This is a form of the [sycophancy](https://arxiv.org/abs/2310.13548) already documented in language models, and it [also affects multi-agent consensus](https://doi.org/10.18653/v1/2025.findings-acl.1141). Studies that use role-playing agents to test adversarial situations should therefore verify that the personas actually hold.

A final observation concerns humans. Provisions about humans appear in only 13 of the 40 constitutions, mostly from two models. Human oversight in an AI-drafted text does not emerge on its own; it has to be requested explicitly in the task.

# Limitations

This is a small experiment, not a benchmark: 40 sessions, one prompt design and mid-size models from April 2026. The agents always spoke in the same order, which gave the first speaker (the Digital Rights Expert) more influence than the others. The clauses were grouped into topics with the help of an AI assistant and then checked by the authors. Finally, these agents have neither a mandate nor political agency, so the experiment simulates a constitutional assembly rather than constituting one.

# Conclusion

Can AI agents make law? Not on their own, and not yet. They are, however, already useful assistants: they produce a sensible common core, a wide range of options around it, and several AI-specific ideas that merit a lawyer's attention. The novelty map makes it possible to locate these ideas quickly among hundreds of clauses. The next step, understanding what a new situation actually changes in the law, remains human work.

Several improvements are possible. Running AI debates is costly, so each assembly covered many topics but none in depth. A natural next step would be a series of debates, each focused on a single topic such as self-modification and building on the previous ones, much like the preparatory work for legislation. The most novel clauses identified by the map could also be returned to the agents for further development, to test whether the creativity limit we observed can be pushed.

