# Building the page

- [For a reader 13 or under](#for-a-reader-13-or-under)
- [The parts, in order](#the-parts-in-order)
- [Theming and the shell](#theming-and-the-shell)
- [Pictures that explain](#pictures-that-explain)
- [Explanatory visuals for professional and senior readers](#explanatory-visuals-for-professional-and-senior-readers)
- [Mermaid, one technique among several](#mermaid-one-technique-among-several)
- [The check question, when one is called for](#the-check-question-when-one-is-called-for)
- [Print and PDF export](#print-and-pdf-export)
- [Before you ship it](#before-you-ship-it)

---

## For a reader 13 or under

The parts below do not apply. That page is what the child branch in SKILL.md says it is: big
simple pictures and few words, under 100 words of text, warm, accurate, nothing frightening,
nothing that will need unlearning. The structure stays separate: no adult page order, no
mermaid, no "Terms you'll hear", no comprehension test.

What does carry over is how pictures teach, because that part of this file is about drawing
rather than about adult structure:

- the picture explains rather than decorates
- it shows relationships and cause and effect, not objects rendered in detail
- visual properties carry meaning: size is amount, position is order, one colour means one
  thing across the whole page
- labels sit directly beside the thing, in as few words as the child can read
- the picture and the words agree, with nothing in one contradicting the other

Take the theming and layout mechanics from the rest of this file too, and leave the structure
alone.

## The parts, in order

Every page for a reader of about 14 and up carries ELIT's teaching sequence, in this order:

**answer → ground → climb → reconstruction → "Terms you'll hear" where SKILL.md requires it**

The order is the teaching: a standalone true answer, down to the foundation, then up to where
the reader needs to be, then the model that regenerates it. A page is a format for that
sequence, never a substitute for it, so the parts below do not replace the reconstruction or
the glossary rule and cannot skip either of them.

**1. The answer.** One or two sentences at the very top. Complete on its own. A reader
who stops here has still been told something true and useful. This is not a teaser and
it is not a summary of what is coming; it is the answer.

**2. The ground.** The single idea everything else hangs off, starting from the entry
point. For an expert this is the one property of
the system that makes the rest follow. One idea, not three.

**3. The climb.** From the ground to the exit point, in order, with a picture per step
where a picture helps. Then stop. The temptation to add one more interesting thing past
the exit point is the main way these pages get bad.

**4. The reconstruction.** The two to four sentences from SKILL.md that regenerate the
explanation. This ends the explanation on the page exactly as it does in prose. It is not a
summary of the sections above it, and no page furniture replaces it.

**5. "Terms you'll hear"**, where the reader qualifies under the rule in SKILL.md. It goes
after the reconstruction, never above it or inside it, and the page ends after it rather than
before it.

**6. The check question, only when one is called for.** See
[the check question](#the-check-question-when-one-is-called-for). A page without one is
finished at part 4, or part 5 where the glossary is required.

At the end, a single quiet line offering the next thing: a deeper version, a related topic,
or the same concept for a different target. Write it as a plain request ("Ask for the version
for a network engineer"), never as a slash command, because the slash form only exists where
this is installed as a plugin.

**Length is an outcome, not a target.** The page format does not change the exit point.
Content depth was determined in SKILL.md before any of this: the sweep, the filter, the exit
point, the no-unlearning rule and the causal spine decided what this reader needs, and
rendering is downstream of that decision. Do not drop required teaching to make the page
shorter, prettier or more visually sparse. Where the explanation is long, reach for layout,
hierarchy, visuals, progressive disclosure where it suits the reader, and tighter sentences,
so that what the reader needs is readable rather than absent.

A short concept still makes a short page. A complex concept for an expert may legitimately
make a long one, and a page that runs long because the concept is genuinely that deep is
working correctly.

What you may cut is redundancy, visual or verbal: a sentence that restates what the picture
already shows, two visuals that expose the same structure, an example that repeats the point
of the one above it. What you may not cut is a concept that survived SKILL.md's filter,
because the reader needs it to reason correctly, and a page that leaves it out has quietly
lowered the exit point it was rendering.

## Theming and the shell

**Publishing through an artifact tool that wraps content in a page skeleton:** write
only the body content plus `<title>` and `<style>`. No doctype, no `<html>`, `<head>`,
or `<body>` tags of your own.

**Writing a standalone file:** wrap the same content in a full document yourself.

Define the complete light palette on bare `:root`, then override only the tokens in
both dark blocks, so the page is right in all three viewer states:

```css
:root { --bg:#f4f2ee; --surface:#fff; --ink:#16181c; --ink-soft:#5c5f66;
        --line:#dcd9d2; --accent:#1f5f6b; --accent-wash:#e0eced;
        --ok:#2c6349; --no:#8f2e1e; }
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) { /* redefine the same tokens, darker */ }
}
:root[data-theme="dark"] { /* repeat them so the toggle wins both ways */ }
body { background: var(--bg); color: var(--ink); }
```

Give `body` an explicit background from a token: a transparent body borrows whatever
ground the viewer paints behind it. Never define a colour only inside a media or
`[data-theme]` block. Cap the reading column near 62 characters. Put anything wide
inside its own `overflow-x: auto` container so the page never scrolls sideways.

**Match the shell to the reader.** A page for a 6 year old wants large type, generous
space, rounded shapes and warm colour. A page for a surgeon or an engineer wants tighter
type and restrained colour used only to carry meaning. The visual register is part of
aiming at the right person, and it is the first thing the reader judges.

## Pictures that explain

The test: **delete every word on the page. Does the picture still carry the idea?** If
not, it is decoration, and decoration costs attention and returns nothing.

- **Draw relationships, not objects.** Boxes and labelled arrows showing what goes where
  teach more than a detailed rendering of the thing.
- **Let visual properties mean something.** Size means amount. Position means order.
  Colour means category, and one colour means one thing across the whole page.
- **Number the steps in the drawing** and use the same numbers in the text.
- **Label directly and briefly.** A short phrase beside the thing beats a legend that
  makes the eye travel.
- **Draw the failure too**, where the reader needs it. A greyed box with a broken arrow
  next to the working version teaches the mechanism twice.

### Labels go in HTML, not in the SVG

This is the rule that prevents the most common visible defect in these pages.

**SVG text does not wrap and does not reflow.** A `<text>` element placed at a fixed `x`
with `text-anchor="middle"` will grow in both directions from that point, and it has no
idea another label is doing the same thing 100 units away. The moment two captions are
longer than their share of the width, they overlap and the page looks broken. Nothing
warns you, and it gets worse on narrow screens.

So split the work:

- **The SVG holds shapes**: boxes, arrows, bars, lines, the diagram itself.
- **HTML holds the words**: put captions in a grid or list directly under the SVG, in
  the same column order as the shapes above them.

HTML text wraps, respects the container, and restacks on a phone for free.

```html
<div class="figbox">
  <svg viewBox="0 0 700 92"> ...shapes only... </svg>
  <ul class="legend">      <!-- grid, same number of columns as the shapes -->
    <li><b>Your line</b><span>Nothing works at all.</span></li>
    <li><b>The directory</b><span>You have the name, but you cannot get the address.</span></li>
    <li><b>Their computer</b><span>You arrive, and nobody answers.</span></li>
  </ul>
</div>
```

Keep any text that must stay inside the SVG to **two short words at most**, and only
where nothing else can sit near it. A single word on a wide axis is safe. A phrase
between two other phrases is not.

Mechanics: `viewBox` with no fixed width or height so it scales; colours from theme
tokens or `currentColor` so it survives dark mode; effective text size 14px or larger;
a `<title>` inside the SVG describing what it shows.

### Verify it rather than trusting it

If you can render the page, check for collisions mechanically. Overlapping labels are
invisible in the source and obvious to the reader, which is the worst combination.

Get every `<text>` element's bounding rectangle, test each pair inside the same SVG for
intersection, and check that no label escapes its own SVG box. Do it at a wide viewport
and at roughly 390px. Any intersection is a defect, not a judgement call.

For young readers, draw warm: thick strokes, rounded ends, big simple shapes, few words,
and every word one they can read. For expert readers, draw precise.

## Explanatory visuals for professional and senior readers

For a practitioner, senior or expert reader, go looking for the chance to *show* the
mechanism rather than only describing it. These readers absorb structure faster from a
picture than from a paragraph that asks them to hold five relationships in their head while
reading about the sixth.

**Where the concept contains structure that would be materially easier to understand
visually, include the visual representation that best exposes that structure.** This is a
requirement, not a nice-to-have: where the picture plainly cuts cognitive load, or exposes
structure that prose forces the reader to hold in their head while reading on, leaving it out
makes the page worse in a way you could have fixed.

What it must not become is a reflex. **Do not default to a flowchart or a diagram simply
because the concept is technical.** A flowchart is one answer to one kind of question, and
reaching for it by habit is how a page ends up with boxes that restate the paragraph under
them. Choose the form from what needs to become visible:

| What the structure is | What to draw |
| --- | --- |
| process, sequence | flow or sequence diagram |
| feedback, recurrence | loop diagram |
| states and transitions | state diagram |
| components, dependencies | architecture or relationship diagram |
| stages, lifecycle | staged progression or timeline |
| alternative paths | branching diagram |
| inputs → transformation → outputs | transformation diagram |
| the parts of a thing | annotated illustration, exploded or layered view |
| before vs after, A vs B | visual comparison |
| relative amount, growth, distribution, change | simple chart or quantitative visual |
| hierarchy, levels | layered or nested visual |
| one central idea with several consequences | infographic-style visual |
| spatial relationship | schematic or map-like visual |
| abstract mental model | conceptual infographic or visual metaphor, only where it preserves the causal mechanism |

The goal is not "add a diagram." The goal is: **make the important structure visible.**

**The visual draws the causal spine of the explanation, not a second layer of information.**
It teaches the same causal model the prose teaches, so a reader can move between the two
without translating. It may compress several sentences into one picture, which is most of why
it is there, but it must not introduce information the explanation never taught. A picture
carrying facts the prose never covered has stopped being the explanation and started being
documentation.

A reader should be able to look at the visual and understand the important relationship,
transformation, comparison, progression or mechanism without reconstructing it from the
captions. Numbered boxes with paragraphs underneath are not a successful visual when the
causal relationship still has to be inferred from the prose: that is prose with decoration
attached.

**Prefer visual explanation over visual documentation.** Use the simplest visual form that
produces the insight. A small infographic, an annotated mechanism or a three-stage picture is
often better than a formal flowchart, and a five-box flow that makes the model obvious beats a
technically impressive architecture drawing that has to be studied. Architecture-documentation
style is for documenting a system, not for teaching one, so do not reach for it just because
the reader is technical.

Before you draw, answer this: **what becomes easier to understand by seeing this rather than
reading another paragraph?** If there is no good answer, do not add the visual. Seniority
alone is not a reason, and the requirement above does not reach a concept that is genuinely
clearer in prose. If the words say it better, write the words.

These visuals may be more schematic, more compact and denser than a child's picture, but the
test from [pictures that explain](#pictures-that-explain) still governs them: delete the
words, and the picture must still carry the idea.

## Mermaid, one technique among several

Mermaid is one available technique, not the default form. It suits a narrow band of
structures: reach for it when order or state is the hard part, and the reader is old
enough to read a schematic. That means roughly 12 and up, and in practice mostly adult
technical readers. For comparisons, quantities, parts of a thing, layered hierarchies or
anything that wants annotation, hand-drawn inline SVG with HTML labels will explain better
than mermaid will.

- **Flowchart** when the question is what happens in what order.
- **Sequence** when the question is who talks to whom, and when.
- **State** when the question is which situations exist and how you move between them.

Under about ten nodes. Past that it stops being an explanation and becomes wallpaper.
Label every edge: an unlabelled arrow asserts that something happens without saying what.

Where it goes changes how you include it. Artifact pages render mermaid natively, so
write `<pre class="mermaid">` and add no script. A standalone file renders nothing by
default, so either pull in the library from a CDN and accept the network dependency, or
draw the equivalent as inline SVG and keep the page working offline.

Never give mermaid to a child. It is a notation, not a picture.

## The check question, when one is called for

**Not every page needs one.** Include a check question when the user asked for learning,
studying, teaching or checking comprehension, or when testing the mental model genuinely
makes the page more useful to them. A plain "make me a page explaining X" is not that
request: that page may end after the required ELIT structure, with no quiz attached. A
comprehension test bolted onto a page somebody wanted for reference reads as homework nobody
set.

Where you do include one, everything below applies.

One question. It has to be failable, and it has to test the model rather than the text.

A question answerable by matching a sentence from the page proves nothing: the reader
reread, which is exactly the illusion this is here to break. Ask instead what happens
next, what breaks if a part fails, which of two situations is different, or what they
would expect to see if it were true.

**Every wrong option must be something this specific reader would plausibly believe.**
Mine the real confusion for that persona. If you cannot think of two tempting wrong
answers, you do not understand the topic well enough to be testing anyone on it.

Never the word "incorrect" in a reveal; say what the right answer is and why.

```html
<section class="check">
  <h2>One question</h2>
  <p class="q" id="q"></p>
  <div class="options" id="options"></div>
  <p class="why" id="why" hidden></p>
</section>

<script>
const Q = {
  q: "The address book computer is down. What happens when you type the name?",
  options: [
    { text: "Your computer guesses the number",
      why: "It cannot guess. Nothing connects a name to a number except the lookup." },
    { text: "Nothing loads, because nobody can find the number", correct: true,
      why: "Right. The name is useless alone. Something must turn it into a number first." },
    { text: "The page loads slowly",
      why: "Tempting, because an outage often feels like slowness. Without the lookup there is no address at all." }
  ]
};

const box = document.getElementById("options");
document.getElementById("q").textContent = Q.q;

Q.options.forEach((opt, oi) => {
  const btn = document.createElement("button");
  btn.type = "button";
  btn.className = "option";
  btn.textContent = opt.text;
  btn.addEventListener("click", () => {
    if (box.dataset.done) return;
    box.dataset.done = "1";
    box.querySelectorAll(".option").forEach((b, i) => {
      b.disabled = true;
      if (Q.options[i].correct) b.classList.add("is-correct");
      else if (i === oi) b.classList.add("is-wrong");
    });
    const why = document.getElementById("why");
    why.hidden = false;
    why.textContent = opt.correct
      ? opt.why
      : opt.why + " The answer is: " + Q.options.find(o => o.correct).text;
  });
  box.appendChild(btn);
});
</script>
```

Style `.is-correct` with the `--ok` token and `.is-wrong` with `--no`, and never carry
that meaning in colour alone: add a tick and a cross, or change the border weight, so it
reads for colourblind users. Buttons go full width and stay comfortably tappable. Give
focus a visible outline.

## Print and PDF export

People print these pages and save them as PDFs, and a visual split across a page break stops
being an explanation: half the mechanism sits on one sheet and its labels on the next. Keep
meaningful units whole where practical.

Keep together: a visual and its labels or captions, the reconstruction block, each individual
glossary entry, and the check question with its answers.

```css
@media print {
  .figbox, .figbox > svg, .legend li,
  .reconstruction, .glossary li, .check { break-inside: avoid; page-break-inside: avoid; }
  h2, h3 { break-after: avoid; page-break-after: avoid; }
}
```

Apply this to the units, not to whole sections. A long section marked unbreakable gets pushed
wholesale onto the next page and leaves half a sheet blank, which is worse than the break you
were avoiding. Let large sections break naturally and protect only the pieces that lose their
meaning when separated.

## Before you ship it

These are the **page-only** checks. The nine writing checks are in SKILL.md step 8 and
apply first.

- The page carries the full teaching sequence: answer, ground, climb, reconstruction, and
  "Terms you'll hear" where SKILL.md requires it. The reconstruction is present and is the
  model that regenerates the explanation, not a recap of the sections; where the glossary is
  required, it sits after the reconstruction and the page does not end before it.
- Rendering as a page did not lower the exit point. Every concept that survived SKILL.md's
  sweep and filter is on the page, and nothing the reader needs in order to reason correctly
  was dropped to make the page shorter, tidier or more sparse. If anything came out, it was
  redundancy, not teaching.
- Where meaningful structure would be easier to understand visually, an explanatory visual
  **is present**. Name the structure in the explanation and point at the visual that shows it.
  A page that leaves it in prose passes only where the prose is genuinely clearer than any
  picture would be, and "I thought about it" is not that; if the reader has to hold the stages
  in their head while reading the next paragraph, draw them.
- The chosen visual form matches the kind of structure being taught, rather than being a
  flowchart by default. Check it against the table in
  [explanatory visuals](#explanatory-visuals-for-professional-and-senior-readers).
- The visual exposes the mechanism or relationship itself rather than decorating or numbering
  the prose. Numbered boxes above paragraphs that still carry the causal work do not pass.
- The visual and the prose teach the same causal model: same steps, same direction, same
  claims.
- The visual introduces no unexplained information: nothing shown that the text never taught.
- The visual survives responsive layout, light and dark themes, and print or PDF export.
- Visual and labels stay together where practical in print output, along with the
  reconstruction, each glossary entry, and the check question with its answers. See
  [print and PDF export](#print-and-pdf-export).
- Every caption is HTML, not SVG `<text>`. See
  [labels go in HTML](#labels-go-in-html-not-in-the-svg).
- No overlapping labels, checked at a wide width and at 390px. See
  [verify it rather than trusting it](#verify-it-rather-than-trusting-it).
- The visual agrees with the prose: same numbers, same names, same colours meaning the
  same things.
- Every colour is defined on bare `:root`, not only inside a media or `[data-theme]`
  block, and `body` sets an explicit background from a token.
- The page reads in light and in dark.
- Nothing loads from the network, unless you deliberately took the mermaid CDN tradeoff.
- Where a check question is included, its correct answer is correct and the wrong ones are
  tempting. Where none was called for, none was added.
