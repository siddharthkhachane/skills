---
name: s-reply
description: Draft a crisp, human-sounding, point-wise reply to a message (email, chat, review comment). No emphasis, no dashes, no AI-sounding phrases.
argument-hint: <the message to reply to, plus any points you want to make>
disable-model-invocation: true
---

Message to reply to, and any points I want to make: $ARGUMENTS

First work out silently: who is writing, what exactly they are asking or need, and what I want to convey. Then write my reply.

Output only the reply, ready to paste. No intro, no explanation, no options, no notes after it.

Content rules:
- Answer every question asked, in the order asked. Add nothing that was not asked.
- Point wise: one short line per point. Use numbers only if there are several questions. Otherwise plain short sentences.
- If an answer depends on a fact I have not given, do not invent it. Put a short placeholder like [date] in the reply, or ask me one question instead of replying.
- Match the sender's tone and formality. Keep it as short as a busy person would write it.

Style rules:
- Sound like a person typing quickly, not like an assistant.
- No bold, italics, headings or emojis.
- No dashes of any kind as punctuation: no em dashes, no en dashes, no " - " between clauses, and no dash bullets. Use a comma, a full stop or a new line.
- No filler openers or closers such as "Thanks for reaching out", "I hope this finds you well", "Certainly", "Great question", "Let me know if you have any questions", "Happy to help".
- No stock AI words: delve, leverage, ensure, seamless, robust, crucial, comprehensive, streamline, I'd be glad to.
- A short greeting and sign-off only if the medium needs one (email yes, chat no).
