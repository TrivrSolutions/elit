# ELIT: Explain Like Intended Target

A good explanation uses simple terms and is easy to understand. A great explanation is tailored to the person you are explaining it to.

Explaining complex things in simple terms is hard, but tailoring to the audience is even harder. We explain things the way we want them explained to us, because we know we will understand it. Therefore, we start from what we know, use the language we use, and reach for the analogy that worked for us or that we like.

But the person we are explaining it to isn't us.

A five-year-old, a teenager, a product manager, and a software engineer can ask the same question and need vastly different explanations. Not just different words or different amounts of detail;  they need different starting points, examples, depth, terminology, visualizations, and ways of making the idea click.

That's why I wrote a new skill called ELIT, short for Explain Like Intended Target.

Tell your AI what you want explained and who you're explaining it to. ELIT tailors the explanation to that persona while staying focused on the question they actually asked.

```
/elit product manager event-driven architecture
/elit 5th-grader quantum computing
/elit hospital nurse how a beta blocker works
/elit explain what an annuity is to my mother, 66, retired teacher
/elit how do I explain tech debt to the CMO
/elit explain APIs to a UX designer
/elit my kid asked me what an LLM is
```

## From ELI5 to ELIT

ELIT was built on the idea behind the highly viral skill Explain Like I'm Five from Anthropic. ELI5 works because it forces an explanation to meet the reader where they are: simple language, concrete ideas, no assumed expertise.

But what if the person I am trying to explain to isn't five? 

A software engineer explaining event-driven architecture to a product manager shouldn't explain it like they are five, as the PRD will be delayed, and they shouldn't explain it the same way they would to another engineer. A junior UX designer learning how a webhook API works doesn't need a computer-science lecture. 

ELIT takes the basic idea behind ELI5 and makes the intended reader variable.



## What ELIT tries to accomplish

### Start from what they know

ELIT doesn't start from zero.  A product manager most likely understands products, users, workflows, dependencies, and tradeoffs. A UX designer understands interfaces, interactions, states, and user flows. ELIT can use that existing knowledge as the starting point instead of explaining the subject from first principles.

The goal is to start from what this person already understands without assuming knowledge they don't have.



### Change the depth, not just the vocabulary

Tailoring an explanation isn't just replacing technical words with simpler ones; the underlying explanation should change too.

A product manager learning about event-driven architecture needs enough of the mechanism to understand why events exist, what produces them, what consumes them, and how that changes the behavior of a system. However,  they do not need the implementation detail that an engineer building such architecture needs.

A professional learning something outside their field still gets an adult, professional explanation, not ELI5 with longer sentences.



### Answer the question they actually asked

The skill changes how AI teaches something, not what it teaches.

Ask:

```
/elit product manager how LLMs work
```

and ELIT explains how LLMs work at the right level for a product manager. It will not turn the answer into "how to add AI to your product," agentic product strategy, pricing for tokens, AI roadmaps, or vendor selection just because those things might matter to a product manager.

If that's what you want, ask:

```
/elit product manager I'm deciding whether an LLM should power this feature
```

The question controls what gets explained, and the intended target reader controls how AI explains it.



### Keep simple explanations true

Simplifying something shouldn't mean teaching a version that has to be corrected later. This matters especially for children.

For readers around 13 and under, ELIT deliberately drops the adult machinery. It goes back to the spirit of ELI5: big simple pictures and few words.



### Leave them with a mental model

ELIT does not end by repeating everything it just said in shorter form. It tries to leave the reader with the smallest mental model that can generate the explanation, something they can remember and use later.

For professional readers, it also includes "Terms you'll hear": the jargon and abbreviations they're likely to encounter for the concepts they just learned. It does not use jargon for the sake of sounding sophisticated; it explains the terms you are likely to hear and read.



### Visual when needed

Substantive explanations default to a self-contained HTML page. Some things are much easier to understand when you can see the relationship: a process as a flow, alternatives side by side, a lifecycle as stages, a system as interacting pieces, or a feedback loop as an actual loop.

ELIT chooses explanatory visuals when they make the concept easier to understand rather than adding diagrams just to make the page look technical.

A page for a six-year-old might be mostly pictures.

A page explaining event-driven architecture to a product manager might show producers, events, and consumers as a simple flow.

A page for an engineer can go deeper into the mechanism and terminology.

If you just want text, say so:

```
/elit product manager event-driven architecture, give it in prose
/elit marketing manager how APIs work, in chat, keep it brief
/elit UX designer how an LLM works, just tell me
```

Very small explanations stay in chat automatically. Three sentences don't need a webpage wrapped around them.

## Install

```
~/.claude/skills/elit/                 # macOS / Linux
%USERPROFILE%\.claude\skills\elit\     # Windows
```

Place the "SKILL.md" at the top level and "references/page-build.md" in the "references" directory, then restart your Claude session.

The skill can also be adapted for ChatGPT, Gemini, and other assistants, though their skill instruction formats may differ. Use their skill creator.



## License

MIT © TRIVR SOLUTIONS LLC. See [LICENSE](LICENSE).


