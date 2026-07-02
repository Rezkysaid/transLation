# SPEC — Malay → Native English Learning App

## 1. What we're building

A translation app that helps Malay speakers learn **real, everyday English** — not the stiff textbook kind.

The user types a phrase in **Bahasa Melayu**, and the app returns English translations the way an actual **native American speaker** would say it in daily life.

The key differentiator: this is **not just a translator**, it's a **mini tutor**. It doesn't only translate — it teaches *why* natives phrase things a certain way.

> Example of the gap we're solving:
> Textbook: "How do you do?"
> Native reality: "What's up?" / "How's it going?"

---

## 2. Core concept

For every Malay phrase the user enters, the app returns:

| Output | Purpose |
|--------|---------|
| **Formal** | For emails, interviews, official/professional situations |
| **Casual / Native** | How Americans actually say it day-to-day |
| **Context note** | A short line explaining *when* to use which one |

The context note is important — learners often use casual English in formal settings (or vice versa) by mistake. This note prevents that.

---

## 3. Scope — START SMALL (MVP first)

**Do NOT build everything at once.** Build the MVP, get it working, then expand.

### MVP (build this first)
- Text input for a Malay phrase
- Output: **2 translations** (Formal + Casual/Native)
- **1 short context note** (when to use which)
- Focus only on **conversational / everyday English** (not business/workplace yet)

That's it. Get this working end-to-end before touching anything below.

### Phase 2 (add later, one at a time)
- **Breakdown** — explain slang/idioms that have no direct translation
  (e.g. "I'm dead" = something is really funny, not literally dead)
- **Common mistake** — what Malaysians typically get wrong with this phrase
- **Example sentences** — a "give me another example" button showing the phrase in different situations
- **Pronunciation hint** — simple guide for tricky words

### Phase 3 (future / optional)
- Workplace / business English mode
- Save favourite phrases / history
- Reverse mode (English → explain in Malay)

---

## 4. How translation should work

- Use an **AI model** for translation, NOT hardcoded rules or a static dictionary.
- Reason: native-speaker nuance, slang, and context are things AI handles far better than rule-based systems.
- The AI prompt should explicitly ask for:
  1. A formal English version
  2. A casual/native American English version (as spoken in daily life)
  3. A one-line context note on usage

### Suggested AI prompt structure (for the backend)
```
You are an English tutor for Malay speakers. 
The user gives you a phrase in Bahasa Melayu.

Return THREE things:
1. FORMAL: a formal/professional English translation
2. CASUAL: how a native American speaker would naturally say this in everyday conversation (use natural slang/contractions where appropriate)
3. CONTEXT: one short sentence explaining when to use the formal vs casual version

Keep it natural. The casual version must sound like a real person, not a textbook.
```

---

## 5. Suggested UI flow (MVP)

```
┌─────────────────────────────────────┐
│  [ Type your Malay phrase here... ]  │
│                          [Translate] │
├─────────────────────────────────────┤
│  FORMAL                              │
│  → ...                               │
│                                      │
│  CASUAL (native)                     │
│  → ...                               │
│                                      │
│  💡 When to use: ...                 │
└─────────────────────────────────────┘
```

Keep it clean and simple. One input, clear output blocks, easy to read.

---

## 6. Design principles (don't skip)

1. **MVP first, always.** A working simple app beats an unfinished complex one.
2. **Teaching > translating.** The value is in helping the user *understand*, not just convert words.
3. **Native, not textbook.** The casual output must sound like a real American, contractions and all.
4. **Clarity over features.** Don't clutter the UI. Add features one at a time only after the core works.

---

## 7. Tech notes (open — decide based on preference)

- Frontend: keep it simple (a single clean interface)
- Backend: needs to call an AI model for the translations
- The exact stack is flexible — pick what's comfortable to build and iterate on quickly.
