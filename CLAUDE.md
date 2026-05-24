# Chinese Stories — Format & Guidelines

## Project Overview

A collection of bilingual Chinese short stories for primary school children (ages 6–12). Each story is presented character-by-character with pinyin annotations alongside an English translation.

## Story JSON Format

Stories live in `stories/<story-id>.json`. Each file follows this schema:

```json
{
  "id": "story-id-in-kebab-case",
  "titleZh": "Chinese title",
  "titleEn": "English title",
  "paragraphs": [
    {
      "zh": [["汉","hàn"], ["字","zì"], ["，",""], ["…",""]],
      "en": "English translation of the paragraph."
    }
  ]
}
```

### `zh` array rules

- Each element is a two-item array: `[character, pinyin]`.
- Punctuation characters (，。！？：""…、) use an **empty string** for pinyin: `["，",""]`.
- Every Chinese character must have a pinyin value — never leave it blank.

### Pinyin conventions

- Use tone marks (ā á ǎ à), never tone numbers.
- Apply sandhi for 一: use `yì` before 1st/2nd/3rd tone; `yí` before 4th tone; `yī` in ordinal positions (第一次).
- 不 becomes `bú` before a 4th-tone syllable, otherwise `bù`.
- Neutral-tone syllables use no tone mark (e.g. 着 `zhe`, 了 `le`, 们 `men`, 子 `zi`).
- 地 as an adverbial particle: `de` (not `dì`).

## Story Index

All stories must be registered in `stories/index.json`:

```json
[
  { "id": "story-id", "titleZh": "中文标题", "titleEn": "English Title" }
]
```

Add new entries to the end of the array.

## Writing Guidelines for New Stories

### Level
- Target vocabulary: primary school (小学) level, roughly HSK 1–3 for core words.
- Unusual or topic-specific words (e.g. 入侵者, 搔背棒) are fine when the story context makes them clear.
- Sentences should be short and punchy. Aim for 20–40 characters per paragraph.

### Structure
- **8 paragraphs** is the recommended length (enough for a complete arc, short enough to hold attention).
- Follow a clear narrative arc: setting → inciting event → conflict → resolution → emotional beat.

### Story elements
- Ground imaginative settings (space, fantasy worlds) in concrete sensory details children can picture.
- Give characters a clear personality through their actions, not exposition.
- End with a meaningful emotional moment rather than a moral lecture.

### English translation
- Write the English as a natural read-aloud translation, not a literal one.
- Match the tone: playful where the Chinese is playful, tense where it is tense.
- Keep sentences short enough for a child to follow easily.

## Adding a New Story — Checklist

1. Create `stories/<new-id>.json` following the schema above.
2. Verify every `zh` element has the correct pinyin (tone marks, sandhi).
3. Append the story to `stories/index.json`.
4. Commit both files together with a descriptive message.
