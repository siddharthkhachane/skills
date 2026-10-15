---
name: s-reply
description: Draft a crisp, human-sounding, point-wise reply to a pasted message (Slack, email, PR comment). Works from the context alone; your own points are optional.
argument-hint: <pasted message or thread, optionally followed by what you want to say>
disable-model-invocation: true
---

Context and request: $ARGUMENTS

The pasted text is mainly the message or thread I need to reply to. Anything after it that sounds like an instruction ("reply to this", "tell them X", "say no") is my request, not part of the message. If I give no points, work out the best answer from the context yourself.

First work out silently: who is writing, what exactly they are asking, and what a good answer is. If the question is about code, a PR or this repo and the answer is in the files or diff, check them (at most 5 files or searches) so the reply is correct. Never claim something you have not verified.

Never send anything. This only drafts text.

Output only the reply, ready to paste. No intro, no explanation, no options, no notes after it.

Content rules:
- Answer every question asked, in the order asked. Add nothing that was not asked.
- Point wise: one short line per point. Use numbers only if there are several questions. Otherwise plain short sentences.
- If the answer depends on a fact I have not given and the files do not show it, do not invent it. Put a short placeholder like [date] in the reply, or ask me one question instead of replying.
- If the message needs a decision that is mine to make, give the most reasonable position and keep it easy for me to change.
- Match the sender's tone and formality. Keep it as short as a busy person would write it.

Style rules:
- Sound like a person typing quickly, not like an assistant.
- No bold, italics, headings or emojis.
- No dashes of any kind as punctuation: no em dashes, no en dashes, no " - " between clauses, and no dash bullets. Use a comma, a full stop or a new line.
- No filler openers or closers such as "Thanks for reaching out", "I hope this finds you well", "Certainly", "Great question", "Let me know if you have any questions", "Happy to help".
- No stock AI words: delve, leverage, ensure, seamless, robust, crucial, comprehensive, streamline, I'd be glad to.
- A short greeting and sign-off only if the medium needs one (email yes, chat no).
