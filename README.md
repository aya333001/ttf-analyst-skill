# TTF Analyst

A Claude skill that runs a Task-Technology Fit (TTF) analysis: given case material about a business task and a proposed technology, it produces a scored report on how well the two fit, and where they don't.

Built for MSMA 1800 Emerging Technologies, Lab 9A (NYU SPS), by Aishwarya Nambiar.

## What it does

The skill applies Goodhue and Thompson's TTF framework through the 21-point Appendix A checklist, in six steps:

1. Document the task from the case material
2. Break the task into subtasks (rule-based, data retrieval, judgment)
3. Rate the 7 task characteristics, with evidence
4. Rate the 7 technology characteristics, including real limits
5. Score the 7 fit dimensions (1 to 5) and each subtask's fit
6. Give an overall verdict, recommendations and a pilot design

It is built to be balanced: where a spreadsheet, script or existing tool would do a subtask better than the proposed technology, the report says so.

## Repository contents

```
ttf-analyst/                 the skill (install this folder)
  SKILL.md                   instructions Claude follows
  reference/
    ttf-checklist.md         Appendix A checklist (scoring rubric)
examples/
  masy-syllabus-audit-report.md   test run: GenAI for the MASY syllabus audit
```

## How to use it

**Claude (web or desktop app):** download this repository, zip the `ttf-analyst` folder, and upload the zip under Skills in Claude's settings. Then start a chat, attach the case files and ask for a TTF analysis.

**Claude Code:** copy the `ttf-analyst` folder to `~/.claude/skills/`.

Example prompt:

> Run a full TTF analysis on these files. The proposed technology is a generative AI chatbot: staff upload a syllabus and it checks every element they currently check by hand against the program's rules.

## Test case

`examples/masy-syllabus-audit-report.md` is the skill's output for the case set in Lab 9A: using generative AI to streamline the MASY program's syllabus audit, based on Dr. Andres Fortino's interview with Dr. Nadia Tatum.
