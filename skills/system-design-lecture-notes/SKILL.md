---
name: system-design-lecture-notes
description: Convert raw Markdown notes from system design lectures or learning videos into concise, accurate, beginner-friendly, interview-focused study notes. Use when asked to process `lecture_notes_raw_*.md`, especially with the command "Please proceed with the lecture_notes", or to clean up raw system design learning notes.
---

# System Design Lecture Notes

Turn temporary raw lecture notes into clear Markdown study notes for a system design learning repository.

## Trigger and inputs

- Treat **"Please proceed with the lecture_notes"** as the command to run the full workflow.
- Find the relevant file named `lecture_notes_raw_<topic>.md`.
- Use the repository's existing folders, filenames, and note style. Do not create a module or other folder unless the repository clearly needs one.
- If several raw files exist, use the one named in the request or clearly implied by nearby context. If no file can be identified safely, ask one concise question.

## Workflow

1. Inspect the repository structure and identify any existing final note for the same topic.
2. Read the entire raw file before drafting. Preserve its useful technical points; remove filler, repetition, off-topic material, and unsupported claims.
3. Correct material inaccuracies or inconsistencies. Verify questionable claims with reliable, primary sources when practical. Do not add advanced details unless they are needed to explain the lecture accurately.
4. Create or update one final Markdown note in the appropriate existing module. Avoid duplicate notes. Use the repository's naming convention; if none exists, use a clear topic-based filename such as `<topic>.md`.
5. Write in simple B1/B2 English. Define technical terms in plain language, use short paragraphs and focused bullets, and include a practical example only when it makes a difficult idea easier.
6. Add a small Mermaid diagram only when it improves understanding of a flow, architecture, relationship, or sequence. Keep diagrams simple and valid Markdown Mermaid.
7. Review the final note against the quality checklist, then delete only the raw file that was successfully processed. Never delete other raw notes.

## Required note structure

Adapt headings when the topic needs a different order, but include the useful sections below:

```markdown
# <Topic>

## What is it?

## Why do we need it?

## How does it work?

## Example

## Important Points

## Interview Questions

## Recap
```

Use these rules:

- Explain the core idea before details.
- Include short answers for the most important interview questions when useful.
- Prefer practical examples such as YouTube, Netflix, WhatsApp, Instagram, Uber, e-commerce, banking, or food delivery.
- End every final note with a short recap that supports fast interview review.
- Keep correct technical terminology, but explain it simply.

## Quality checklist

Before finishing, ensure the note:

- Is accurate, concise, and understandable by a beginner.
- Covers the important content of the raw lecture without copying its repetition.
- Uses examples and diagrams only where they add real explanatory value.
- Is useful for system design interviews rather than a long textbook chapter.
- Matches existing repository organization and does not change unrelated files.
- Leaves no processed `lecture_notes_raw_<topic>.md` file behind.
