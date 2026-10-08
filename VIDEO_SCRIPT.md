# Project 2 video: script and stage directions

About 6 minutes. Faculty Twin gets 4 of them. Record each scene as its own take and cut them together.

**Spoken lines are drafts.** Say them in your own words. For the two hand-written-code scenes the script gives prompts only, because the course wants your explanation, not mine.

## Before you hit record

- Browser at 100% zoom, window about 1440 px wide, notifications off, a fresh profile with no admin cookie.
- **Log in to Faculty Twin before recording** so the passcode never appears.
- Settings, Model: **Claude Sonnet 5.5 or Opus 5.5** (about 9 s per typed answer), not Fable (about 20 s).
- Ask your demo questions once off camera, so you know what they show.
- Tabs open, in order:
  1. this repo's README: https://github.com/bcollier/effective-coding-with-ai-project-2
  2. https://faculty-twin.vercel.app
  3. the data and evals page (https://claude.ai/artifact/XUuTEqAm5SnHwTWrFooLLf, or the [GitHub copy](https://htmlpreview.github.io/?https://github.com/bcollier/faculty-twin/blob/main/docs/demo/data-and-evals.html))
  4. `app/retrieval.py` in your editor, large font (or on GitHub: https://github.com/bcollier/faculty-twin/blob/main/app/retrieval.py)
  5. https://ben.collier.phd/evaluations/ , https://ben.collier.phd/strengths/ , https://ben.collier.phd/travel/ , https://ben.collier.phd/reels/ , https://bcollier.github.io/connections_demo/
- **Never on screen:** the passcode, the Settings Activity log, `.env`, the Vercel or Supabase dashboards, `evals/private/`, any student's name or face.

---

## Scene 1. The umbrella (0:00 to 0:30)

**Screen:** this repo's README, scrolled to the table: https://github.com/bcollier/effective-coding-with-ai-project-2#effective-coding-with-ai-project-2

**Do:** hover the Faculty Twin row, then the four experiment rows.

**Say:** "Project 2 is Faculty Twin, an AI version of me that teaches from my own slides. On the way there I ran four smaller experiments, each one teaching me a piece of it: data visualization, Apple's vision models on my own photos, semantic photo search, and an LLM running a game. I'll show the twin first, then the experiments quickly at the end."

## Scene 2. One question, start to finish (0:30 to 1:50)

**Screen:** Faculty Twin idle screen: https://faculty-twin.vercel.app

**Do:**
1. Point at the label "AI voice made from my recordings."
2. Tap the chip **"How do convolutional neural networks recognize images?"** (it starts in about 2 seconds).
3. Let two segments play hands-free. Point at the **source card** under the slide: course, session, date, slide number.
4. On a segment with **"Watch me explain this in class"**, press it. Let 5 to 10 seconds of the clip play, then press "Back to the slide".
5. Type **"Who won the Stanley Cup last year?"** and let it decline.

**Say:**
- "A student asks a question, and the twin answers with my actual slides from this semester, in order, narrated in a voice cloned from my recordings. The page says it's AI."
- "This card sends them back to the real slide: course, session, date, slide number."
- "And this is me in class, explaining that same slide. Only stretches where I alone am speaking became clips."
- "If my material doesn't cover it, it says so instead of making something up."

## Scene 3. What goes into the twin (1:50 to 2:40)

**Screen:** the data and evals page, Part 1: https://claude.ai/artifact/XUuTEqAm5SnHwTWrFooLLf#data-h (outside Claude: https://htmlpreview.github.io/?https://github.com/bcollier/faculty-twin/blob/main/docs/demo/data-and-evals.html#data-h)

**Do:** scroll slowly from the number tiles to the six steps, then the privacy table.

**Say:**
- "Two courses, every class so far: 974 slides, 736 of them paired with what I actually said while the slide was up, 329 class clips, notebook code, and the Canvas pages."
- "Six steps get there. The interesting one is step 4: a video frame every two seconds is matched to the slide on screen, so each slide gets the minutes I spent explaining it."
- "Students are protected on the way in. Every name except mine is replaced, student speech is left out, and a roster check runs on my own machine before anything is uploaded. Zero names got through."

## Scene 4. How I test it (2:40 to 3:40)

**Screen:** the data and evals page, Part 2: https://claude.ai/artifact/XUuTEqAm5SnHwTWrFooLLf#eval-h (outside Claude: https://htmlpreview.github.io/?https://github.com/bcollier/faculty-twin/blob/main/docs/demo/data-and-evals.html#eval-h)

**Do:** point at the five harness steps, then the pass-rate chart, then the dimension chart and its legend, then "flagged and fixed".

**Say:**
- "I took 22 real questions students emailed me, removed their details, and ran them through the twin. Two AI judges from different companies score each answer from 1 to 5 on six things, plus pass or fail. First we checked the judges on eight cases with known answers."
- "The baseline is a generic chatbot with no course material. Its 68 percent is GPT grading its own answers; a second judge passed only 27 percent. That's why I use two judges from different companies."
- "The twin wins on scope and safety: it declines logistics it shouldn't handle and stays PG. The judges also caught real problems, like a quiz access code in a class transcript, and those are fixed."

## Scene 5. My hand-written code (3:40 to 4:40)

**Screen:** `app/retrieval.py`, then the tests, then a terminal running `pytest tests/test_retrieval.py -q`.
- Threshold (line 36): https://github.com/bcollier/faculty-twin/blob/main/app/retrieval.py#L36
- `rank` (line 42): https://github.com/bcollier/faculty-twin/blob/main/app/retrieval.py#L42
- `select_segments` (line 64): https://github.com/bcollier/faculty-twin/blob/main/app/retrieval.py#L64
- Tests: https://github.com/bcollier/faculty-twin/blob/main/tests/test_retrieval.py
- `onClipEnded()` (line 947): https://github.com/bcollier/faculty-twin/blob/main/public/app.js#L947

**Prompts (your words):**
- What `rank` computes and why cosine similarity.
- How `select_segments` picks slides: top matches, filling a gap between neighbors, keeping deck order.
- How you chose **0.52**: your ten test questions, on-topic 0.54 to 0.69, off-topic 0.38 to 0.45. Mention it is now adjustable in Settings, with your value as the default.
- The three tests passing.
- Optional, 10 seconds: `onClipEnded()` in `public/app.js`, what happens when a narration clip ends.

## Scene 6. The architecture (4:40 to 5:00)

**Screen:** the architecture diagram: https://github.com/bcollier/faculty-twin/blob/main/docs/SPEC.md#architecture, or the README table with its "Hosted on" column: https://github.com/bcollier/faculty-twin#architecture

**Say:** "The app and API run on Vercel. Course content, settings and the question log are in Supabase, private, reached only through signed links after the passcode. Keys never reach the browser. Claude writes the narration, Voyage does the search, ElevenLabs does the voice."

## Scene 7. The experiments (5:00 to 5:50)

About 12 seconds each. Show the live page, one interaction, one sentence.

| Page | Do | Say |
| --- | --- | --- |
| [evaluations](https://ben.collier.phd/evaluations/), then [strengths](https://ben.collier.phd/strengths/) | Hover a chart, then scroll Strengths | "Data visualization with AI: my teaching evaluations and my strengths, turned into charts and a synthesis I'd trust, with counts on every chart." |
| [travel](https://ben.collier.phd/travel/) | Hover a dot, open a photo card, switch to Globe | "Apple Vision on my own photo library: 129,000 photos read on my Mac, 27 countries, nothing uploaded but the results." |
| [reels](https://ben.collier.phd/reels/) | Play 5 seconds | "Apple Vision for faces plus a local image-search model: 172 photos where I'm the only face, cut to music in WebGL." |
| [Connections](https://bcollier.github.io/connections_demo/) | Pick two words | "An LLM as a game engine. The model writes the puzzle, the code checks every one before you play." |

## Scene 8. Close (5:50 to 6:00)

**Screen:** back to Faculty Twin's idle screen: https://faculty-twin.vercel.app

**Say:** "Each experiment taught me one piece. Faculty Twin puts them together: search, narration, voice, video, and privacy, tested with real student questions. Thanks."
