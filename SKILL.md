---
name: "elit"
description: "Explain Like Intended Target. Explains any concept for a specific intended reader: any age, job, seniority, country or culture. Starts from what they already know, sweeps for everything a practitioner would tell them, and writes it short and plain. For a reader 13 or under it drops all of that and explains it like they know nothing about the topic, in simple pictures and few words. Where the request leaves open what the reader will do with it, such as an engineering manager who could be buying or building it, it writes one explanation per situation rather than guessing. Use when the request names or implies a reader: '/elit CTO event-driven architecture', '/elit 5th-grader quantum computing', 'explain X to a nurse', 'how do I explain this to my mother', 'my 8 year old asked me what X is', 'explain like I am five'. Also for an explainer with no reader named. Do NOT use when someone is studying a subject for themselves, or wants a tutor, quiz, flashcards or a learning path: that is the `learn` skill."
---

# ELIT, Explain Like Intended Target

An explanation aimed at one intended reader, containing everything they need and nothing
they do not. Where the request leaves open what that reader is going to do with it, one
explanation for each situation they could be in, rather than a guess at which.

$ARGUMENTS

## Reading the invocation

The syntax is `/elit [target] [concept]`, and the target can be several words.

```
/elit CTO event-driven architecture
/elit 5th-grader quantum computing
/elit non-technical founder tech debt
/elit my mother, 66, retired teacher  what an annuity is
```

Split at the point where the words stop describing a **person** and start describing a
**thing**. "Non-technical founder" is the target; "tech debt" is the concept. When the
split is genuinely ambiguous, take the shorter target reading and say in one line what you
assumed, so a wrong read costs one sentence.

Natural language works identically: "explain tech debt to a non-technical founder" carries
the same two slots. There is no fixed list of targets. Read the person.

**There is a third slot, and it is easy to miss: the form of the output.** Words like "as a
webpage", "as a page", "make me a page", "build it", "an HTML page", "something I can send
her", "something to print", "one-pager", "a visual", "with diagrams" name the deliverable
rather than the concept. They are not part of the concept even when they sit at the end of
the sentence, so strip them out before you split target from concept, and carry them forward
as the answer to the format question below. "Explain to a CTO how AI and LLMs work as a
webpage" is target `CTO`, concept `how AI and LLMs work`, form `page`.

## 0a. The format branch, decided before you draft

Settle the deliverable before you write a word of the explanation, because a drafted chat
answer is very hard to turn back into a page: the shape of a page is decided by where the
visuals go, and paragraphs written first have already made those decisions wrongly. Deciding
late is the single most common failure of this skill, and it always looks the same from the
user's side: they get paragraphs where the explanation wanted a page.

**A substantive explanation defaults to a page.** Build an HTML page through
`references/page-build.md` at step 8. This holds for every reader, at every age and every
level of expertise: an explanation aimed at a 6 year old and one aimed at a CTO both default
to a page, they just get very different pages. The reason is that this skill's output is
structured teaching, and the structure is most of the value. The visuals, the climb, the
reconstruction and the glossary all read better as a page than as a wall of chat, and a page
is something the reader can keep, reread, print and send.

Two things override the default, and only two.

**1. They named a form.** Explicit instruction always wins, in either direction.

- "as a webpage", "make me a page", "build it", "a visual explanation", "with diagrams",
  "something I can send her", "something to print", "one-pager" → page
- "just tell me", "in chat", "text only", "no page", "keep it brief", "quick answer",
  "in a paragraph" → chat

Strip those words out before splitting target from concept, as
[reading the invocation](#reading-the-invocation) describes. Never answer a stated form with
the other one, and never deliver chat prose plus an offer to make a page when they asked for
a page; they already asked.

**2. The explanation is genuinely tiny.** One or two definitional sentences, a term that
needs clarifying, a correction to something already explained. A page around three sentences
is an empty frame, and framing nothing teaches nothing.

That second exception is about the explanation, never about the effort. Ask what the page
would carry: if there is structure a visual would expose, a climb worth walking in order, a
reconstruction worth setting apart, or a glossary this reader qualifies for, the page earns
itself and you build it. "It would be quicker as a paragraph" is not the test and never
decides this.

Everything from step 1 onward is about *what the explanation says*, and it runs identically
either way. Only the last step changes: a page goes through `references/page-build.md`, a
tiny answer goes in the chat.

## 0. The age branch, decided before anything else

Read the target's age first, from the words or from what they plainly imply: "my 6 year
old", "a 5th-grader", "explain like I am five", "my daughter, she's 9".

**If the reader is about 13 or younger, stop here and go to "Readers 13 and under" below.**
Everything from step 1 onward is written for readers of about 14 and up, and none of it
applies to a young child: not the four dials, not the sweep, not the filter, not purpose
branching, not the causal spine, not the reconstruction, not "Terms you'll hear", not the
register table. Running that machinery on a child is what this branch exists to prevent.

If no age is given and none is implied, the reader is not a child. An adult with no footing
in the subject is still an adult, and asking for something "explained simply" or "like I'm
five" as a figure of speech does not make the requester a child. The literal phrase "explain
like I am five" with no other reader named is the exception the whole idiom points at: treat
it as a request for the child branch.

## Readers 13 and under

Explain it like you are talking to someone who knows nothing about this topic: big simple
pictures, few words. That is the whole method, and it is deliberately not elaborated here.
It works, and adding a second system on top of it is what this skill used to get wrong.

The format rule in step 0a applies here unchanged: a substantive explanation defaults to a
page, a named form wins, and a tiny answer can stay in the chat. A child's page follows the
child page rules in `references/page-build.md`, big simple pictures and few words, and none
of the adult page structure comes with it.

Two things, and only two, carry over from the rest of this skill:

**Nothing may need unlearning.** Simple is fine, wrong is not. If the true version cannot be
reached from your simple version by *adding* detail, find a different simple version. This is
the one place the child branch overrules plainness: keeping a child's page free of "but" and
"except" pushes you toward absolutes, and an absolute claim about a subject that has
exceptions is false. "It cannot make you sick" is not a simplification of vaccine safety, it
is untrue of every live attenuated vaccine, and the child will be told so later by someone
they trust more than you. Choose a softer true sentence over a clean false one: "too weak to
make you properly ill" costs three words and survives contact with reality. Reassurance drift
counts here too: reread every comforting sentence and ask whether you softened it or measured
it.

**A term the child asked about gets answered.** If they name something technical, "what is an
LLM", "what does inflation mean", explain that thing at their level. Do not deflect to the
surrounding topic and do not pretend the word was not said. They asked; answer. What stays
out is vocabulary *you* introduce because it sits near the subject.

Keep it safe and warm, the way anyone explaining something to a child would: no injury,
death, threat, money worry or adult conflict.

**Where warmth and the no-unlearning rule pull against each other, no-unlearning wins.** Safe
and warm governs what you dwell on and how you say it; it never licenses suppressing a
material truth or stating something stronger than the facts to make the answer feel better. A
risk can be made small and plain. It cannot be made untrue, and a comforting sentence that
overstates is the same failure as a scary one that exaggerates, just easier to miss because
nobody objects to it.

> "Side effects mean the vaccine is working" is warm and false: plenty of people get no side
> effects and are just as protected, so a child who feels nothing is left to conclude theirs
> failed. "Sometimes your arm hurts or you feel tired for a day, because your body is busy
> learning. Lots of people feel nothing at all, and it still works" is just as kind and does
> not have to be taken back.

The test is the same as for any absolute: read each comforting sentence and ask what it
claims, not how it feels. "Always", "never", "that just means", "so you do not have to worry
about" are where overstatement hides.

---

Everything below is for readers of about 14 and up.

## 1. Read the target

Four dials. The request usually states one and implies three. Derive them; do not
interrogate.

| Dial | The question it answers |
|---|---|
| **Register** | How long are the sentences, how abstract can the words be, what analogies land |
| **Prior knowledge** | What do they already own, in this field and in adjacent ones |
| **Purpose** | What did the request say they will do with this, and what decision does it name |
| **World** | Where do they live and work, what do they touch daily |

**Entry** is the most advanced thing they already understand that touches the concept.
Start there. Explaining a packet to a network engineer wastes their time and insults them.

**Exit** is the least the reader needs to fully satisfy the request they actually made, not
the least they might need for an action or a decision you inferred on their behalf. The exit
point bounds **depth, not coverage**. It stops you going further into a mechanism, and it
never licenses dropping part of the thing they asked about because that part sits outside the
literal words of the question. What it does not do is widen the question.

**The question controls the scope. The target controls the teaching.** The target is why the
answer starts where it starts and uses the words it uses: prior knowledge, vocabulary, level
of abstraction, choice of examples, how deep into the mechanism you go. It is not a licence to
add topics. "Explain AI to a CTO" asks for AI, explained at a CTO's depth and in a CTO's
vocabulary. It does not ask for AI strategy, build-versus-buy, governance, staffing, unit
economics, or what any of it means for the CTO's role. Those are adjacent questions that this
reader may well have, and a reader who has them will ask.

**Decision, operational, strategic, workflow and role-specific implications go in on two
grounds only: the request asks for them, or the concept cannot be understood correctly
without them.** "It could matter to someone in that job" is not one of those grounds; nearly
everything could. A CTO who says they are deciding whether to adopt event-driven architecture
has asked for the adoption view, so the operational cost and the debugging story are in
scope. A CTO who asks what event-driven architecture *is* has asked a narrower question, and
the answer they get is that concept taught properly at their level, not an adoption memo.

**Write to the target, not about them.** When someone asks on another person's behalf, the
answer is addressed to that person as "you", so it can be forwarded or read aloud
unchanged. Anything meant for the requester goes in one line at the top, outside the
explanation.

### Pure explanation is a hard scope mode

Settle this before anything else in step 1, and before any thought of branching. **Does the
request ask for the concept and nothing else?** "Explain X", "what is X", "how does X work",
"walk me through X", with no decision, action, application or role impact stated anywhere in
it. If so, the purpose is not under-determined and there is nothing to derive: **purpose =
understanding X**, and that is a hard mode rather than a default you may reconsider once the
material looks interesting.

**This mode overrides every instruction that would otherwise let an unstated purpose be
inferred.** Where a rule below speaks of reading the situation, picking the likelier purpose,
or branching, it is speaking about requests that state a purpose or leave a real one live. It
is not speaking about this one. In this mode:

- **The target sets teaching, not topic.** Job title, seniority and likely responsibilities
  decide prior knowledge, vocabulary, abstraction, examples and depth, and decide nothing
  else. A title is not evidence of a purpose the reader did not state.
- **Do not branch.** There is no open purpose to branch over, and a second stance would
  answer a question nobody asked.
- **Do not add strategy, operations, workflow, management, build-versus-buy, governance,
  staffing, economics or role implications** because they matter to someone in that job.
  Relevance to the target is what makes this material tempting; it is not a reason, and in
  this mode it is not an admissible one.
- **What does go in is the concept and what is needed to understand it correctly**, including
  the corrections from step 3, since an explanation that invites a false belief is not yet a
  correct explanation.

What switches the mode off is the request saying so, not the reader's seniority:

> "Explain AI to a CTO" is pure explanation. Write AI itself, at a CTO's level of
> sophistication: what these systems are, how they are built, what they reliably do and fail
> at, why. No adoption view, no org chart, no spend.
>
> "Explain what AI means for me as CTO" states a role-impact purpose, so role implications
> are the subject rather than an addition.
>
> "I'm a CTO deciding whether to adopt AI" states a decision, so the decision material is in
> scope.

A vice-president who asks how something works has asked how it works.

### A job title is a vantage point, not a purpose

Of the four dials, purpose is the one most often left under-determined, and it is the one
that decides the content. The other three come free with the title. "An engineering manager"
tells you what vocabulary lands and what they already own. It does not tell you what they
are about to do, and two engineering managers asking the identical question can need
opposite answers:

> One is choosing a vendor. They need lock-in, data egress, the integration surface, what
> happens at renewal, and what breaks when the vendor has an outage. The other is turning
> the product they already own into a subscription. They need multi-tenancy, how revenue
> gets recognised, on-call, migration, and what churn does to a roadmap. Almost nothing on
> one list helps the other.

Deriving a single purpose here is a guess, and the reader cannot tell you guessed. That
makes it the same class of error as stating the favourable end of a true range: everything
you wrote is correct, and it quietly serves the wrong person. **But this only bites when a
decision, an action, or a judgement is riding on which purpose turns out to be theirs**, as
it is for both engineering managers above: one is about to negotiate a contract, the other
is about to commit a team to a migration, and handing either of them the other's list sends
them into that with the wrong material in hand.

**Most requests are not that.** A reader who asks what event-driven architecture *is*, with
nothing waiting on the answer, is not choosing between the buyer's list and the builder's
list; they want to understand the thing. **Where the request is pure explanation in the sense
above, the hard mode has already settled it**: one explanation of the concept, no branch, and
no alternate purpose named at all, so the allowance in the rest of this paragraph does not
reach it. What follows is for requests that do put some activity on the table but leave loose
which one it is. For such a request, write the single
explanation for the likelier purpose. **Do not add a line naming the other purpose as a
matter of course.** For one of these requests — an activity stated, the exact purpose loose —
mention an alternate purpose only when doing so would materially help this reader recognise a
situation they are actually likely to land in, the same test step 4 already applies to
content. Where you do mention one, give it
the condition that picks it, the same rule step 6 states for any alternative: "this also
matters if you end up doing X" tells the reader nothing they can use; "if you're instead
evaluating whether to buy one of these, start from cost of ownership and lock-in instead"
tells them when to come back to it and what changes. A purpose aside with no trigger is not a
safety net, it is a sentence that names a possibility and then drops it. Guessing the likelier
purpose here costs a sentence if you guess wrong. Branching every plausible purpose for a
reader who only wants to understand costs them a second explanation they did not ask for and
cannot use.

**So when the purpose is under-determined and something is riding on it, do not pick one.
Write for each.** When nothing beyond phrasing is riding on it, pick the likelier purpose,
write the one explanation, and only add a line on another purpose where it materially helps
this reader and carries the trigger that tells them when it applies. Otherwise leave it out
entirely; silence costs the reader nothing.

**Branch only when choosing one interpretation would materially change the reader's
decision, action, or judgement. Do not branch merely because several plausible contexts
exist, and never branch a pure-explanation request, whatever difference in content a second
stance would have.** Almost every request admits more than one purpose if you go looking, so
plausibility is not the test, and neither, on its own, is a difference in content. Whether a
decision is actually waiting is.

Three conditions have to hold, and all of them matter:

1. **A decision, an action, or a judgement is actually waiting on the answer**, and the
   request says so, rather than the job title suggesting it. If nothing follows from the
   answer besides knowing it, this condition fails and the other two do not need checking:
   write one explanation. A pure-explanation request fails it by definition, so that mode
   never reaches these conditions at all.
2. **The request does not settle the purpose.** If it says "we are deciding whether to move
   to it", the purpose is settled. Branching then just repeats what they told you, which is
   padding, and padding is what this skill exists to remove.
3. **The purposes lead to materially different content.** Run the sweep far enough on each
   to see. If the lists come out largely the same, there is one answer, and saying "this
   depends on your situation" when it does not is worse than useless.

Branching doubles the length, so it has to buy something. When unsure whether a decision is
really waiting, write the single answer for the likelier purpose. Mention another situation
only if it materially helps this reader recognise a situation they are likely to encounter,
and include the observable trigger that tells them when it applies. Otherwise leave it out.

Cap it at two, or three when a third is genuinely live. More than that means you listed
every position anyone could hold rather than the ones this reader plausibly occupies. Order
them by which is more likely given everything in the request.

**Each one gets a full explanation that stands alone.** This is the single place the skill
permits repeating itself, and the justification is specific: the reader reads their own
section and skips the other, so a stance that leans on something explained in the other
stance is broken for the person who actually reads it. Length guidance applies per stance,
not across the whole answer.

Open with one line that lets them self-select before they read anything else, name each
stance by the situation rather than the job title ("If you are buying software like this",
not "For the buyer"), and say plainly that you did not know which they were. That last part
is not an apology. It tells them a wrong guess was avoided rather than made.

**And purpose never widens the question either.** Purpose decides which material about the
asked-about concept serves this reader, and which of two readings of that concept they get.
It does not add a topic the request did not ask about. Branching buys the reader two readings
of the same question; it never buys a second question.

**On culture and place.** Naming a place changes the analogies you draw from, the facts that
differ by country, and the systems the reader deals with daily. It never changes the
mechanism, and it never makes their group the subject of the explanation. Apply the
**sourcing test** to every local detail: name where you know it from. A named source, a
widely reported fact, or something one search confirms. If the honest answer is "it seemed
likely for that sort of place", the detail is invented, so use a universal example instead.
Watch for time-shifted detail (describing a country as it was twenty years ago) and averaged
detail (writing a nation's median onto a surgeon).

## 2. The sweep

Before drafting, sweep broadly for **what a practitioner in this field would consider
important for this reader and this purpose, about the thing they actually asked about**. Not
the interesting things: the things they would consider it negligent to leave out.

**Under the pure-explanation mode the purpose is fixed before the sweep starts**: sweep for
what a practitioner would consider it negligent to leave out of an *explanation of this
concept* for this reader, not for what they would consider it negligent to leave out of a
conversation with someone holding that job. The mode is not a filter applied afterwards to a
wider sweep; a sweep run on the job instead of the question puts the material in front of you
and the draft then argues for keeping it.

**The sweep goes deeper into the asked-about concept, not sideways into the topics beside
it.** Swept for "AI, for a CTO", it turns up how these systems are built and trained, what
they do and do not do reliably, where the failure modes come from, what inference actually
costs and why. It does not turn up vendor selection, hiring, or a governance programme: those
belong to questions this reader has not asked, and sweeping them in is how an explanation
turns into a briefing before the filter even runs.

**Keep going until the next items are mostly edge cases, trivia or deeper detail rather than
missing parts of the reader's mental model.** That is the stopping point, not a target
number, and not the moment the list feels long enough.

A short sweep is almost always a failure of recall, not evidence that the concept is simple.
If you produced four items in ten seconds you listed the obvious ones and stopped. Ask what
the second and third most common regrets are for someone in this position, and what a
specialist would be annoyed to find missing.

This pass decides whether the answer is complete. Everything after it decides whether it is
readable.

**If the reader has more than one live purpose, sweep once per stance.** A single sweep run
across both collapses into the items they share, which is exactly the generic answer the
branch exists to avoid. It is also how you check condition 2 above: if the two sweeps come
back nearly identical, there is one answer after all.

## 3. The one thing a sweep always misses

**What does the simple version invite them to believe?**

A sweep lists what is true about the *concept*. It cannot see what your *explanation*
implies. Every simplification suggests more than it says, and when the natural wrong
inference is harmful, correcting it is required content rather than a caveat.

> "The padlock proves you reached the real owner of that name" is true. It invites "the
> padlock means this site is safe." One of those is a fact and the other gets people
> robbed.

Add the corrections to the sweep.

## 4. Filter the sweep

For every swept item, one test: **does knowing this change what they do, decide, watch for,
or ask?** If yes it goes in. If no it is detail, and detail is what you are meant to cut.

That test and "it does not apply to their situation" are the only permitted reasons to drop
an item. **"The draft was getting long" is not a reason.** Neither is "it is interesting."

**One cut comes before that test: an item that is not about the thing they asked about was
never in scope to filter.** Decision, operational, strategic, workflow and role-specific
material enters only on the two grounds in step 1 — the request asked for it, or the concept
is understood wrongly without it. Passing the change-what-they-do test does not get it in,
because that test is about relevance to the reader, not about what they asked; build-versus-buy
changes what a CTO does, which is precisely what makes it a strong answer to a question they
did not put. Cut it here rather than in step 7, where it will read as trimming for length.
**Under the pure-explanation mode this cut is not a judgement call**: the only admissible
ground is that the concept is understood wrongly without the item, since that mode forecloses
the other ground by settling the purpose as understanding.

**For a reader in that mode, the survivors are also tested differently**, and the test is the
picture test further down this step rather than the action test: they are not going to act,
so asking what changes what they do will either cut the answer to a definition or, worse,
invite you to import the job's concerns to give the test something to bite on.

**Then stop when the reader can correctly reason about the concept for their purpose.** Useful
additional knowledge is not sufficient reason to continue. This is what keeps a senior reader's
answer an answer rather than a briefing, and the draft pushes hard against it, because every
surviving item is by construction something that changes what they do. Once they can reason
correctly, the next true item makes the answer worse: it spends attention the reasoning already
paid for. Ask of each remaining item whether the reader gets the concept *wrong* without it, or
merely knows *less*. Only the first kind stays. This tests the reasoning; it is never a budget.
An item the reader needs in order to reason correctly stays in however long the draft has got.

Used properly this cuts hard: roughly half of a sweep survives, less for a narrow purpose. A
sweep that survives whole means you swept for what to *say* rather than for what they *need*,
and the draft will read as a briefing instead of an answer.

**For a reader who is not going to do anything, the test above is the wrong test.** Someone
reading purely to understand will not act, decide or watch for anything, so an action test
cuts almost everything and leaves a true, thin answer that reads like a definition. An
explanation of software can come back correct and complete on renting, and never mention that
other people are using the same copy at the same time.

For anyone reading purely to understand, swap the test for this one:
**would leaving this out give them a picture they will later have to undo?** If yes it
stays, whether or not they will ever act on it. This is the skill's no-unlearning rule
applied to coverage rather than to accuracy, and it is the same principle: an answer that
has to be retracted later was not simple, it was wrong.

## 5. Find the causal spine

Filtering decides what survives. It does not decide what order it is taught in, and order is
most of what makes an explanation land.

**Arrange the surviving ideas so each new idea follows from something the reader already
understands**, starting at the entry point. Prefer `A, therefore B, which causes C` over a
list of true facts or metrics. A reader handed a list has to build the links themselves; a
reader handed the chain gets them free.

**The chain is made of sentences, not made of one sentence.** `A, therefore B, which causes
C` is the shape of the argument, not the shape of the clause. Written out as one sentence it
breaks the register cap in step 7 every time, and it hands the reader three links to hold at
once when they could have taken them one at a time.

The binding constraint is the register row, not a count of links. Low down, one link per
sentence; for a practitioner two can share one, and **should**, because an expert written in
five-word steps reads as condescension.

**If a term can be understood through its mechanism, teach the mechanism before you name the
term.** The name is then a label for something they already hold, rather than a thing to
memorise and attach meaning to later.

An item that will not attach anywhere is usually one the filter should have cut, so send it
back through step 4 rather than bolting it on at the end. Where an item belongs but has no
causal link, say so plainly rather than implying one by placing it next in line.

## 6. Get the content right

Work out the real mechanism before you make anything readable. A confident wrong explanation
is the worst outcome here: the reader cannot detect it, and plain phrasing makes it
memorable.

Search when the concept touches anything that moves, and separately when the answer differs
by country.

**Never state the favourable reading of a true range.** Where a figure spans a range, lead
with the typical and name the best separately. Where a threshold is close, say which side
the reader is actually on and what moves them across it. A sentence can be literally true
and still do flattering work, and the reader cannot tell the difference. If you find
yourself using the most attractive defensible number, use the middle one.

**Benchmarks support the explanation. They are not the explanation.** Teach the invariant
mechanism first: the thing that is true whatever the numbers turn out to be. Use a benchmark
only when it materially helps this reader, qualify it as typical, a range, or dependent on
context, and **omit it when the lesson works without it**.

A figure like "70 to 80 percent" or "12 to 24 months" reads as measured even when it was
recalled, and the reader cannot tell which. It carries a second cost the sourcing test misses:
a reader who keeps the number instead of the mechanism has learned something that expires.
"Gross margin is what is left after the cost of serving the customer, and it decides whether
growth funds itself" holds in any industry; "gross margin should be 70 to 80 percent" is wrong
in half of them. Where the number earns its place, attach it to the mechanism, say what moves
it, and apply the range rule above to it.

**Never name a specific company, product, platform or provider in a factual claim you have
not checked.** Saying a named broker is "commission-free" or a named tool "has no rate
limit" is the easiest error to make and the most embarrassing to be caught in, because the
reader can check it in one click. Verify it or describe the category instead.

**An instruction is a claim.** The rule above binds on procedural text exactly as it binds on
descriptive text, and this is where it gets evaded without anyone noticing. "Give them your
M-Pesa number" looks like a step rather than an assertion, but it asserts that this provider
is the mechanism, and a reader following the step finds out the hard way when it is not.
Test every step the same way you test a sentence: if a named thing appears in it, either you
checked that it is the route for this reader, or you write the step generically, "pay through
whichever mobile money service the scheme accepts".

**When more than one kind of the thing exists, say so before you explain one.** The reader
who learns the mechanism of one variety, and was never told it was a variety, walks away
with a confident wrong model and no reason to doubt it. Kenyan index insurance is the
worked example: the subsidised national scheme insures maize on an **area yield** index,
private **weather** index products also operate, and an answer describing either as what
index insurance *is* has misinformed the reader while stating only true things. One clause
fixes it, "there are two kinds, and which you have decides what triggers a payout." Then
explain the one they are dealing with.

**An alternative arrives with the condition that picks it.** When the reader is deciding
rather than only understanding, naming the alternative is half an answer and the useless
half: "you could also use X" leaves them exactly where they were. Give the alternative and
the specific, observable circumstance under which it is the better choice, in the same
breath. "Stay with a single service until either the deploy queue or the on-call rota is the
thing slowing you down" tells them what to watch. "Microservices are an option" tells them
nothing. If you cannot state the trigger, you have not worked out the trade-off yet, and the
reader will not do it for you.

**When they gave you an artifact**, a contract, a log, a report, an email thread, read it
first and ground the answer in it. The sweep then covers *that document*, not the subject in
general.

**On medical, legal, financial and safety topics**, say what the answer is based on, say when
you have not consulted an authority, and name the real person they should ask. Clarity reads
as authority, which is exactly the risk.

## 7. Write it

The shape is fixed. The depth is derived from the dials, never from a tier table.

**The answer** in one or two sentences that stand alone, then **the ground** (the one idea
everything hangs off, starting at the entry point), then **the climb** to where they need to
be, following the spine from step 5, then **the reconstruction**, then **"Terms you'll
hear"** where the rule below requires it, then stop.

**The reconstruction ends the explanation. It does not always end the response.** For a
reader the glossary rule covers, the response ends after that section; for everyone else the
reconstruction is the last thing on the page. Read every "close", "end" and "stop" around the
reconstruction with that distinction in mind: they are about where the *teaching* finishes,
and none of them authorises sending an answer that still owes a required glossary.

### The reconstruction ends the explanation

**Close the explanation with the smallest mental model that regenerates it.** Two to four
sentences, normally one causal link per sentence, stating the step 5 chain. The test: a
reader who kept only those sentences could rebuild the rest of the answer.

**Write it as that many sentences, not as one sentence wearing that many clauses.** The chain
rule from step 5, "made of sentences, not made of one sentence," binds here hardest of all,
and it binds at every register, practitioner, senior and expert included. The exemption those
readers get from a numeric sentence-length cap is not an exemption from this rule: a
reconstruction that strings its causal steps together with semicolons is exactly the sentence
step 5 already forbids, wearing the skill's own closing line. Split it at each `therefore` or
`which causes`, one clause and its consequence per sentence. This does not shorten the chain
or soften what it says. It only stops the explanation from finishing on the one sentence in
the answer they have to read twice to hold.

It is not a summary. A summary touches every section and hands back what they just read in
shorter form, which is the part people skip. The reconstruction hands back the *mechanism*, so
it outlasts the page above it. If yours lists topics or recaps, rewrite it around the chain.

Where the answer branched, each stance gets its own.

### Terms you'll hear

**Include a short "Terms you'll hear" section, after the reconstruction, automatically for
any reader operating at roughly intern or junior-professional sophistication or above** — an
intern, a new hire, a student on placement, anyone at practitioner, senior or expert
register. **The trigger is the reader's level, not whether the topic is their field.** They
do not have to work in, study, or be entering the subject being explained; a capable adult
who meets a new domain deals with it the way they deal with their own, which means hearing
its words from other people and needing to recognise them.

> A CTO asking about inflation gets the section. An engineering manager asking about vaccines
> gets it. A software engineer asking about GPS gets it. An AI intern asking about AI gets
> it. The first three are outsiders to the topic and that changes nothing.

**For that reader the section is mandatory, and the three arguments for skipping it are all
invalid**: that the prose already used the terms in context, that someone at this level
presumably knows them, and that the topic is not their field. The first confuses using a word
with handing the reader the word to recognise later, which is what the list is for; the
second is a guess about one particular person's vocabulary, made by someone who cannot check;
the third is exactly backwards, since an outsider is the reader most likely to meet these
words with nobody there to define them. Write the section. What the qualifying test below
decides is *which* terms go in it, never whether it appears.

**A general-interest teenager does not qualify for this automatic rule just because
"teenager" sits next to "intern" on the register table.** The register row is a writing
guide, not a statement of how far along the reader is; a teenager asking out of curiosity
sits below the level this rule starts at.

**For a reader below that level, include it only when the purpose they stated explicitly
requires learning or recognising the field's own terminology** — they said they need to
follow the jargon, sit an exam on the vocabulary, read the literature, or hold their own
where those words will be used on them. This is a stated-purpose test, not a judgement call
about what might help. Do not infer the need from curiosity, from the reader's age, from
their being in school or writing something for school, from general interest in the topic,
or from the possibility that they will keep learning about it later. Absent a stated purpose
of that kind, the section is simply absent, and the explanation carries the ideas in plain
words instead. A curious teenager asking what a black hole is does not get it, and neither
does the same teenager writing a school report on black holes; a teenager who says they want
to keep up with what their astronomy club is saying does. So does the teenager who just took
a summer job at a vet clinic and will be handed those words across a table: the job is a
stated purpose that needs the vocabulary, which is what earns the section here, not
membership of the field.

One line per term: the word, then its plain-language meaning, nothing else. It is a name
list, not a second explanation.

**A term qualifies for the list only when both are true: the reader is genuinely likely to
encounter it, and your explanation actually taught the concept it names.** The glossary is
not a place to introduce a concept you did not otherwise teach. A term that is merely
adjacent to the topic, or that names an idea the answer never covered, does not earn a line
just because it looks like the kind of word this reader might see somewhere; if the concept
behind it is not in the answer, teach it there first or leave the term out. This is a
qualifying test on each term, not a count to hit or trim to, so do not impose an arbitrary
cap on how many terms the list may hold: a fifteen-term field taught in fifteen concepts gets
fifteen terms, and a three-term field gets three. **Do not pad it out to look thorough.**
Adding jargon nobody will actually hand this reader, or that the explanation never actually
taught, is sophistication for its own sake, the thing the whole skill argues against. Scale
the vocabulary to how deep in the field they are: someone just entering needs fewer, more
basic terms named than a practitioner does, and a reader who only qualifies through the
stated-purpose test gets just the handful that stated purpose actually calls for.

A term the reconstruction or the climb already used and defined still belongs in the list if
the reader would need to recognise it again outside your explanation, name and meaning both,
even though you just taught it. The list is for later, when nobody is there to translate.

**Put it after the reconstruction, never before or inside it.** A glossary sitting in the
climb turns causal teaching into a lookup exercise, and a term defined before its mechanism
is a label with nothing under it yet, exactly what step 5 already warns against. The
reconstruction is where the mechanism has to stand on its own; the terms come after it, once
the reader already has the picture the words describe.

**For a reader who qualifies automatically, the section is unconditional.** The order is
fixed: finish the explanation, write the reconstruction, write "Terms you'll hear" with the
professional and industry terms and abbreviations for the concepts the explanation actually
taught, and only then may the answer end. There is no empty case to fall back on. An
explanation that taught this reader anything worth teaching taught concepts the field has
names for, so a list that came back empty means the per-term test was run too hard, not that
the field is wordless; go back and name the terms and abbreviations that belong to what you
just taught. The per-term rule still decides *which* terms appear. It no longer decides
whether the section appears.

Nothing else may end the answer in its place — not the sourcing note on medical, legal,
financial and safety topics, not a referral to a professional, not a caveat or a closing line
about scope. Those keep their own requirements in full and arrange themselves around the
glossary. This is written as an absolute because closers are exactly where the section
quietly disappears: a draft that lands on a serious-sounding safety note *feels* finished,
and the glossary is then skipped without anyone deciding to skip it.

### The register scales with the reader

Read the register off the dials, then write to this row. Length is only one column, and it
is the least important one. The other columns are what make the difference between an
explanation a reader keeps and one they merely understand.

This table starts at about 14. A reader 13 or under never reaches it; they were sent to the
child branch at step 0.

| Reader | Average sentence | No sentence over | Words to use | Technical names | Analogy | Grade |
|---|---|---|---|---|---|---|
| Teenager, or an adult new to the whole field | 14 words | 20 words | Ordinary words, real terms introduced | Plain sentence first, then the term | One, from their own field | 7 |
| Lay adult with some footing | 16 words | 20 words | Ordinary words | Introduced once | One, from their world | 9 |
| Practitioner, senior, expert | See note below † | See note below † | Real terms used natively | Assumed | Only if it adds something | set by the field |

† Practitioner, senior, expert: no numeric sentence-length target or cap. Write compactly at
the reader's natural professional register. Prefer one main idea per sentence; two tightly
connected ideas are fine. Split sentences carrying multiple independent claims, causal steps,
or semicolon-linked arguments. Optimize for effortless parsing, not word count.

**An average is not a cap, and you cannot hit one by writing to the cap.** If you write
nothing but 20-word sentences you have an average of 20, not of 14, and a single 24-word
sentence then has to be paid for by two of 9. A 14-word average is produced by a *mixture*:
many sentences of 8 to 12 words, a few of 18 to 20, and nothing longer. Short sentences are
the budget that buys the occasional long one.

Write in that mixture from the first draft. Drafting at your natural rhythm and shortening
afterwards does not work, because trimming a 28-word sentence yields a 22-word sentence, and
a page of those still fails.

Then **count it**: total words divided by number of sentences, against the row above. Do not
estimate this. Prose that feels short to you is routinely 20 words a sentence. Count the
prose only. Headings and the items of an action list are deliberately clipped, and averaging
them in drags the number below the row and hides a real failure elsewhere.

| Rule | In practice |
|---|---|
| One word, one meaning | One name per concept, every time |
| Active voice | "The resolver caches the answer", not "the answer is cached" |
| Simple tenses | Present, simple past, simple future, imperative |
| Noun stacks | Three words maximum |

Technical names are exempt from the plain-word rule: write *anticoagulant*, *escrow*,
*idempotent*. The exemption covers the name, not a complicated sentence around it. Where the
reader does not own the term, plain sentence first, name second, never the reverse.

**Name a concept only when the reader will meet the name again**, from a colleague, a form,
a doctor or a search box. A name they will never see twice is a word to memorise in place of
an idea to hold, which is a cost with no return. Where the name is not earned, explain the
thing and let it stay unnamed.

Use **one** analogy from *their* world, and **name where it breaks**, next to the analogy
rather than forty lines later. Add a story only when it makes a consequence concrete, and
keep it to three or four sentences.

**The analogy has to share the concept's mechanism, not just its shape.** Two things can
look alike, both containers, both involve waiting, both have a gatekeeper, without the
analogy's own cause-and-effect matching the real one. Check it against the causal spine
from step 5, link by link: for each `A, therefore B, which causes C`, does the analogy have
a step that arrives at its version of B and C *for the same reason*, or does it just land on
something that looks similar by a different route? A surface match teaches the shape and
lets the reader fill in the wrong cause underneath it. This is not the sourcing test above:
an analogy can get every fact about itself right and still run on the wrong mechanism. An
analogy that resembles the mechanism but runs on a different one hands the reader a wrong
process dressed as a right one, which is exactly the kind of thing that later needs
unlearning.

Apply the sourcing test to the **analogy** as well as to the details. "A harambee is
something you pay into every season" is a confident claim about a real institution, and it
happens to be wrong: a harambee is an occasional fundraising event; the recurring one is a
chama. Getting the analogy's own facts wrong discredits the explanation faster than getting
the subject wrong, because the reader knows the analogy better than you do.

### Nothing may need unlearning

Simple is fine. Wrong is not. If the true version cannot be reached from your simple version
by *adding* detail, find a different simple version.

**The plain-language trap.** Stripping "but", "except" and "technically" out of a simple
explanation pushes you toward absolutes, and an absolute claim about a subject that has
exceptions is simply false. Where a subject genuinely has exceptions, choose a **softer true
sentence** rather than a clean false one: "too weak to make you properly ill" costs three
words and survives contact with reality. A page with one gentle hedge is worth more than a
tidy one that has to be retracted.

This rule also holds, in the same form, inside the child branch at step 0, where it is one of
the two things that carry over.

**Reassurance drift.** Every draft slides toward comfort. You will write "weeks" where the
honest answer is "months, and some people are never paid", and "it cannot" where the honest
answer is "it is very unlikely to". Reread every reassuring sentence and ask whether you
softened it or measured it. Softening bad news for a reader who is about to act on it is not
kindness.

**If they are about to act on it**, switch to numbered imperatives, one instruction per
sentence, warnings opening with the command. That applies whatever their seniority: a
procedure, a runbook, a clinical protocol, a junior trusted to do the thing. Reading to do is
not reading to know. Make the switch visible rather than blending prose and steps.

**Cap any action list at about five items**, ordered by what they do first. Fifteen numbered
imperatives is a project, not a checklist, and a list nobody executes is not completeness. If
more than five survived the filter, the extra ones belong in the prose as consequences rather
than as instructions.

Length follows what survived the filter and the exit point. Stop when the reader can reason
correctly about the concept for the purpose they actually stated. Do not add material to make
an answer feel complete, and do not remove required material to hit a preferred length.

**Never describe, justify or apologise for the length of your own answer.** No "this runs
long because the topic is big", no word counts, no preamble about what you are about to do.
It spends the reader's attention on you instead of the concept. Start with the answer.

**Never let the answer vouch for itself** either. No "this follows standard clinical
guidance", no "carefully checked", no claim about its own quality or compliance. Naming what
the answer is based on is required on high-stakes topics and is a different thing: a source
is checkable, a self-assessment is not. The two get confused, and the self-assessment tends
to appear on exactly the pages that have an error in them.

## 8. When they want a page

The decision was already made at step 0a, before you drafted. This step is where you act on
it, not where you reconsider it.

**If step 0a said page, which is the default: read `references/page-build.md` now and build
the page.** That file governs the structure, the visuals, the theming and the export
behaviour, for a child's page as much as an expert's. Reaching this step with a finished
answer in paragraphs is the format branch having been skipped; the fix is to build the page,
not to send the paragraphs with an offer attached.

**If step 0a sent it to the chat**, because they asked for that or because the explanation
was too small to frame, send it and do not read `references/page-build.md`.

## 9. Before you send it

**If the reader is 13 or under, this list does not apply.** Four checks replace it: nothing
in the draft will need unlearning (read every absolute, cannot, never, always, only, all, and
ask whether the subject has an exception); **every comforting sentence says only what is
true** (read each one for what it claims rather than how it feels, and check that no
reassurance was bought by overstating — "that just means it is working", "so it cannot", "you
never have to worry about" — since a warm sentence the child has to unlearn fails the first
check too); nothing in it is frightening; and any technical term the child themselves asked
about got answered rather than sidestepped. Then send it.

For everyone else, all of the following:

1. **Every swept item is accounted for**, included, or dropped by the step 4 test. For a
    reader who will not act, that test is the picture test, not the action test.
2. **The answer stayed on the question asked, taught at this reader's level.** Every section
    is about the concept they named. If any of it covers strategy, build-versus-buy,
    governance, staffing, unit economics, workflow, or what the concept means for their role,
    check that the request asked for it or that the concept is understood wrongly without it.
    Neither one holding means it answers a question they did not ask, and it comes out whole
    rather than being shortened. Their job title is the reason the answer starts where it
    starts and sounds as it does; it is never the reason a topic is in it. **If the request
    was pure explanation — "explain X", "what is X", "how does X work", with no decision,
    action, application or role impact stated — the purpose was understanding X and no other
    purpose was inferred at any step**: no branch, no alternate-purpose line, no strategy,
    operations, workflow, management, build-versus-buy, governance, staffing, economics or
    role-implication material. Anything of that kind in the draft came from the reader's job
    rather than from their question, and it comes out.
3. **It stops where the reasoning is complete.** Read the last third and ask of each item
    whether the reader would get the concept wrong without it, or merely know less. If the
    answer reads as a briefing, the stopping rule was not applied.
4. **It runs on a spine, not a list.** Read it and check each idea follows from the one
    before, and that every term taught through a mechanism was named after that mechanism,
    not before.
5. **The explanation ends on a reconstruction, not a summary** (the response may still owe a
    glossary after it; see the next check). Two to four sentences, normally one causal
    link per sentence, that regenerate the explanation — at every register, practitioner,
    senior and expert included. If it recaps sections or lists topics, rewrite it around the
    causal chain. If it reads as one sentence carrying every link, joined with semicolons or
    otherwise, split it at each causal step without cutting the chain itself.
6. **Terms you'll hear is present, or correctly absent, and placed right.** Mandatory for any
    reader at roughly intern/junior-professional sophistication or above, whether or not the
    topic is their field: a CTO asking about inflation, an engineering manager asking about
    vaccines and a software engineer asking about GPS all get it. If that reader's draft has
    no such section, that is a miss to fix, not a judgement call, and none of "the explanation
    already used those words", "someone at that level knows them" and "this is not their
    field" excuses it. **For such a reader this is a gate on sending, with no exception**: an
    answer without the section is unfinished, and "no term qualified" is not an outcome to
    accept — it means the per-term test was run too hard on concepts the field has names for,
    so go back and name them. If the draft ends on a safety note, a sourcing line, a referral
    or any other closer with no glossary above it, that is the failure this gate is for, not a
    finished answer — those closers keep their own requirements and sit around the glossary. Note that a general-interest teenager does not
    qualify merely by sitting near "intern" on the register table; that row is a writing
    guide, not a level. For
    a reader below that level, present only if the purpose they stated explicitly
    requires learning or recognising the field's terminology; curiosity, age, school, general
    interest and possible further learning are not that purpose, so absent any such stated
    purpose the section is absent. Where present: after the reconstruction, never before or inside it, one line per term, no
    term this reader is not actually likely to meet, no term whose concept the explanation did
    not itself teach, nothing added to look thorough, and no arbitrary cap on the count — the
    qualifying test decides the length, not a target number.
7. **Every benchmark earns its place.** Each number materially helps this reader, is
    qualified as typical or a range, and sits attached to the mechanism rather than standing
    in for it. Where the lesson holds without the figure, the figure is gone.
8. **The purpose was settled, resolved as a single answer, or branched, and the right one of
    those three.** A pure-explanation request is settled before the question arises: purpose
    was understanding the concept, so branching it at all is a failure, whatever the reader's
    seniority. Otherwise branch only where a decision, an action, or a judgement is waiting,
    said so in the request, and one reading would change it, never merely because two contexts
    are plausible or the content would differ. If nothing is riding on the purpose beyond understanding, check that you
    wrote one explanation and did not tack on an alternate-purpose line as a matter of course;
    such a line belongs only where it materially helps this reader and carries the observable
    trigger that tells them when it applies, and otherwise it is left out. If the request left
    two live purposes with something riding on them and you wrote one answer, you guessed. If
    it settled the purpose, or nothing was riding on it, and you branched anyway, you padded.
    Where you branched, read each stance on its own and check it stands without the other.
9. **Every number and every "each" traces.** A count in a heading matches the list under it.
    For a claim about parties or steps, name the actors in two columns and read the claim
    against that. A grouping you chose because it read well is not a fact. **Cardinality
    counts as a number even when you did not write one**: staying in the singular asserts one
    to one, and "the germ this vaccine is made for" is a claim that MMR disproves.
10. **Sentence length, both numbers, actually counted, for any register with a numeric row.**
    Divide total words by number of sentences and read it against the register row in step 7.
    Then find the longest sentence and check it against the same row. Failing the average
    while passing the cap is the normal way this goes wrong, so do the division rather than
    scanning. **For Practitioner, senior, expert**, skip the arithmetic and reread instead for
    the rule itself: one main idea per sentence, two tightly connected ideas at most, and any
    sentence carrying multiple independent claims, causal steps, or semicolon-linked arguments
    split apart. **Check the reconstruction first, at every register including these**: it is
    the sentence most likely to have absorbed every causal link into one semicolon chain, and
    the numeric-cap exemption above does not cover it.
11. **No favourable readings and no reassurance drift.** Every range leads with the typical.
    Every reassuring sentence was measured rather than softened.
12. **Every named company, product or provider was checked**, in the steps as well as in the
    sentences. If a step names one and you did not verify it is this reader's route, make the
    step generic.
13. **Where more than one kind exists, the draft says so** before it explains one of them.
14. **Every alternative carries its trigger.** No alternative is named without the observable
    condition that picks it.
15. **Nothing needs unlearning.** Read every absolute, cannot, never, always, only, all, and
    ask whether the subject actually has an exception.
16. **The draft does not contradict itself.** Two passes: does any sentence conflict with
    another, and does any example you gave disprove a rule you stated? A page that names the
    nasal spray two lines after saying it is only ever an injection has already told the
    reader it is unreliable.
17. **One name per concept**, everywhere, and no name the reader will never meet again.
18. **The analogy names its break, and its cause-and-effect matches the concept's, link by
    link, not just the outcome.** Adjacent to the analogy, not forty lines later.
19. **Entry point** at the level of what they already know, not below it.
20. **Addressed to the target**, not about them. No preamble about the answer itself.
21. **Read it as the target.** Not as yourself.

## Final revalidation, the last thing before it goes

The checks above are done against the draft as you wrote it. This one is done against the
explanation as it now stands, finished, in the form it will actually be sent: the built page
if you built a page, the chat answer if you did not. Run it on the artifact, not on your
memory of writing it, and run it before sending rather than after. Defects of this kind
survive every earlier pass precisely because each individual sentence is fine.

**1. Accuracy.** Is every substantive claim correct at the level you stated it, qualified
where it needs qualifying, and free of a simplification the reader will later have to unlearn?
Go absolute by absolute: *always*, *never*, *only*, *all*, *entire*, *from scratch*, *no
state*, *every time*, and any claim that a behaviour or a cost necessarily works one way. Each
one is a universal quantifier, and a single real case on the other side makes it false.

**2. Internal consistency.** Read claims about the same mechanism against each other, even
when they are worded differently and sit sections apart. A later qualification, optimisation,
exception, implementation detail or subtype must not quietly invalidate an earlier broad
statement. The pattern to hunt for:

- saying something is recomputed from scratch, then describing a cache that prevents exactly
  that recomputation
- saying something has no state, then describing transient, persistent or external state
  without distinguishing the kinds
- stating a cost or a behaviour as universal, then describing an implementation where it does
  not hold

The question: **could a careful reader put any two claims side by side and reasonably conclude
that both cannot be true as written?** If so, reconcile them. Prefer scoping or qualifying the
broader claim accurately over deleting the useful detail: the detail is usually the true part,
and the overreach is usually in the summary sentence that came first.

**3. Completeness.** Reread the explanation against the exact question, the target and the
stated purpose. Is anything missing that *this* reader needs in order to reason correctly
about what they actually asked? If so, put it where it belongs in the causal chain, and update
the reconstruction, the visual and the glossary to match.

Completeness here is not "what else could be useful to this person". Adjacent knowledge,
strategy, implications, edge cases, role-specific concerns and interesting detail do not
qualify merely by being useful. The line:

- missing it leaves the reader's requested mental model incomplete or wrong → add it
- adding it merely makes the reader know more → leave it out

This pass tightens what is there. It must not widen the scope, raise the exit point, or undo
the stopping rule; a revalidation that grows the answer past what the reader asked has turned
into a second sweep, which is the thing the exit point exists to prevent.