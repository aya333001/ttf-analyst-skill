# TTF Analysis: GenAI for the MASY Syllabus Audit

*Test run of the TTF Analyst skill on the Lab 9A case, November 2026.*

## Executive summary

A configured GenAI chatbot is a **moderate overall fit** for the MASY syllabus audit, with a mean score of 3.7 out of 5. The fit is strong for the checklist subtasks and weak for the rest. It does well at reading a returned syllabus against written rules (required elements, grading totals, the 30% cap on team work) and at summarizing faculty changes for the reviewer. It does poorly at the subtasks that are already well served by simpler tools: checking locked sections, for which Word Compare does the job, and formatting. Textbook currency also depends on web access. Most of the time saved is in preparation and in onboarding new staff. The experienced reviewer's own 4 to 5 minutes per syllabus leaves little to save. The recommendation is a hybrid workflow piloted on 20 past syllabi seeded with known errors.

*Proposed technology:* a configured chatbot (here, a Claude skill) with the program's rules, template and academic calendar in its knowledge files. Staff upload a syllabus and receive an exception report.

*Case material:* the interview with Dr. Nadia Tatum conducted by Dr. Andres Fortino (August 2023), the interview question list and the case memo.

## Step 1: The task

Each semester the MASY program audits 90 to 100 syllabi. Dr. Tatum, the program administrator, does this with one administrative aide. Preparation starts months before the term. Section data is downloaded daily from Albert, the university's registration system, into a planning spreadsheet called the "shell", which Tatum calls "basically our Bible". For instructors returning to a course, the aide updates last year's syllabus with the new term, section, meeting times, modality, location and course URL. She then adds notes asking faculty to update the session dates. Instructors new to a course get another instructor's syllabus as a template. Before anything is sent, several parts are locked: the header, the course description, prerequisites and learning outcomes (all approved by New York State), the standard section titles, the grade-conversion link and the SPS policy pages.

When syllabi come back, the aide checks textbook editions first and flags anything outdated. Tatum then reviews each syllabus with Word Compare or track changes, with paragraph marks turned on. She has timed herself at about 4 to 5 minutes per syllabus, and an academic subject-matter expert is consulted when content departs from the standard. The checks are listed below:

- **Instructor details:** name and NYU email.
- **Office hours:** included.
- **Class details:** times and location match Albert.
- **Textbooks:** recent (within 3 or 4 years, "give or take"), graduate level and affordable.
- **Required items:** present, for example CITI training in the research course.
- **Grading:** weights total 100% and team work is no more than 30%.
- **Grade conversion:** the standard scale.
- **Schedule:** written out in words and covering every week.
- **Dates:** each falls on the correct weekday and moves around holidays and breaks.
- **Locked sections:** intact.
- **Presentation:** fonts and formatting are acceptable.

Tatum names dates as the main bottleneck: something that would "automate the dates, for example, would be amazing."

## Step 2: Subtasks

The audit splits into eight subtasks. Five are rule-based checks. Of the other three, one is data retrieval, one combines retrieval with judgment and one is judgment alone. The analysis keeps them separate because the fit differs from one to the next.

| # | Subtask | Type | Stage |
| --- | --- | --- | --- |
| S1 | Fill in the header and logistics (section, term, times, modality, location) from the shell | Data retrieval | Preparation |
| S2 | Generate session dates, shifting them around holidays and breaks | Rule-based | Preparation |
| S3 | Confirm locked sections are intact and unchanged | Rule-based | Review |
| S4 | Check required elements (email, office hours, CITI, schedule in words, all weeks covered) | Rule-based | Review |
| S5 | Check grading (weights total 100%, team work at most 30%, standard conversion scale) | Rule-based | Review |
| S6 | Assess textbooks (current edition, graduate level, price) | Data retrieval and judgment | Review |
| S7 | Judge faculty additions and changes (for example the new "Use of AI" section) | Judgment | Review |
| S8 | Check formatting, fonts and spelling | Rule-based | Review |

## Step 3: Task characteristics

The task is **semi-structured**: most of it is high-volume rule checking, but a small core relies on judgment. That core currently depends on one experienced person.

| Characteristic | Rating | Evidence from the case |
| --- | --- | --- |
| Complexity | Semi-structured | Most checks are rules: weights must show "everything adds up to 100", team work must be no more than "30% of the final grade", and locked sections must stay intact. Some calls need judgment. Faculty are allowed "leeway", and an expert is brought in when a syllabus moves too far from the standard. |
| Interdependence | High | The audit involves the administrator, an aide, each faculty member and an academic expert. It also depends on Albert data and on outcomes approved by New York State. |
| Variability | Medium | The cycle is the same every semester. The variation comes from faculty edits, instructors new to a course, room changes "throughout the semester" and the calendar for each term. |
| Frequency | High, in bursts | Two cycles a year (fall and spring) with 90 to 100 syllabi each. The work is concentrated in the weeks before materials go to faculty and before the term starts. Fortino refers to a full day spent on 50 syllabi. |
| Criticality | High | The syllabus is "the contract" between student and professor. The description, prerequisites and outcomes have to match what the state approved. |
| Data requirements | Mixed | Structured data comes from the Albert export and the academic calendar. Semi-structured data comes from Word files with locked sections. Unstructured text covers assignments, policies and textbook choices. Locations change up to the start of term, so some of the data must be current. |
| Skills and knowledge | High, held by one person | Tatum says, "I have almost all these sections memorized." An experienced reviewer takes 4 to 5 minutes per syllabus. Fortino estimates a new staff member would take 15 to 20 minutes, or up to an hour, at first. |

*Workload in figures.* At 95 syllabi and 4.5 minutes each, the expert review takes about 7.1 hours per semester. With a new reviewer at 15 to 60 minutes each, the same review takes 24 to 95 hours. Preparation time is not stated in the case and is probably larger than the review itself.

## Step 4: Technology characteristics

The technology is a configured chatbot: a Claude skill, Custom GPT or Gem. Its knowledge files would hold the rules, the locked template, the academic calendar and the latest shell export. Staff upload a syllabus and get back an exception report. It is strong at reading and comparing text, adequate at arithmetic when it has a code tool, and weak at anything that needs live data or Word's own formatting.

| Characteristic | Rating | As deployed |
| --- | --- | --- |
| Functionality | Adequate | Strong at reading messy text against a checklist, finding missing elements, summarizing faculty changes and drafting notes to faculty. Date work is reliable only when the model runs code, since in plain text LLMs miscount weekdays. Without web access it cannot confirm whether a newer textbook edition exists. |
| Usability | Strong | Staff upload a file and ask in plain English, with no coding or setup. A fixed report format keeps the output easy to scan. |
| Compatibility | Weak | It reads .docx and .xlsx files, but it has no live link to Albert, so the shell has to be exported and uploaded. It cannot reliably produce the locked Word template, because protection and formatting are lost when it writes files. It adds an upload step alongside Word Compare rather than replacing it. |
| Flexibility | Strong | The rules are written in plain language and can be edited without a programmer. This answers Fortino's concern that a coded tool would need "updating these programs all the time" whenever the process changes. |
| Accessibility | Adequate | It is available on demand, outside office hours and away from campus. Whether NYU licenses an approved tool for staff is not stated in the case. The assumption here is that one is available. |
| Data handling | Adequate | One syllabus at a time is reliable. A batch of 90 to 100 runs up against upload limits and against the model's accuracy on long documents. Output varies from run to run, so the same file can produce slightly different flags. |
| Security and compliance | Adequate | Syllabi are faculty intellectual property and contain names and emails, but no student records. The tool should run on an institution-approved account that does not train on uploads. The case does not cover data policy. |

## Step 5: Fit

The seven fit dimensions score a mean of 3.7 out of 5. The scores are high where the audit is a set of written rules applied to unstructured text. They are lower where the tool has to slot into Word and Albert, and where the time saved for an expert reviewer is modest.

| Fit dimension | Score (1 to 5) | Task characteristic matched to technology characteristic |
| --- | --- | --- |
| Task support | 4 | The semi-structured rule checks match the model's strength at reading text against a checklist. The judgment calls stay with people. |
| Performance improvement | 3 | The expert reviewer spends about 7 hours a semester, so there is little to save there. The gains are in preparation time, in onboarding new staff (24 to 95 hours of review cut down) and in applying the same checks to every syllabus. |
| Cognitive fit | 4 | A report ordered by section mirrors how Tatum walks through a syllabus. It also follows Fortino's principle: "you pay attention to the different." |
| Process fit | 3 | It works as a pre-check before the human review, but it does not replace Word Compare or produce the locked template. Each syllabus also needs an extra upload. |
| User acceptance | 4 | The demand is stated plainly: automating the dates "would be amazing." Trust has to be earned, though, from a reviewer who describes herself as "an auditor at heart", and false flags would wear it down. |
| Proof-of-concept feasibility | 5 | The rules are explicit, the template is standard and past semesters provide test syllabi. A prototype can be built in days. |
| Proof-of-value evidence | 3 | Catch rate and time saved can be measured. Preparation time has no baseline in the case, so the largest gain is the hardest to prove. |

Mean: (4 + 3 + 4 + 3 + 4 + 5 + 3) / 7 = 26 / 7 = **3.7**

### Fit by subtask

| Subtask | Type | Best-suited tool | GenAI fit (1 to 5) | Reason |
| --- | --- | --- | --- | --- |
| S4 Required elements | Rule-based | GenAI | 5 | The model reads free text well against a fixed list, and it is tedious work for people. |
| S5 Grading rules | Rule-based | GenAI with a code tool | 4 | The model can tell which items are team work. The totals should be checked in code. The sample syllabus lists 90% before a separate weekly-review item, which is the kind of total a person can misread. |
| S7 Faculty changes | Judgment | Human, with GenAI summarizing | 3 | The model can summarize what changed and why it might matter. The decision belongs to Tatum or the subject-matter expert. |
| S1 Header and logistics | Data retrieval | GenAI or a script | 3 | A script reading the shell is more reliable. The model cuts setup effort, which matters because Tatum finds Excel-to-Word links "very cumbersome". |
| S2 Session dates | Rule-based | Script, or GenAI with a code tool | 3 | This is the main bottleneck. A calendar with holiday rules is a deterministic job. A plain-text model is risky and needs code to be trusted. |
| S6 Textbooks | Retrieval and judgment | Human, helped by GenAI with web search | 2 | Checking for a current edition needs live search, and price and level are judgment calls. Without web access the model guesses. |
| S3 Locked sections | Rule-based | Word Compare (already in use) | 2 | Word Compare finds every character change. A model may miss a subtle edit or paraphrase. |
| S8 Formatting and spelling | Rule-based | Word tools | 1 | Fonts and layout are lost when the file is read as text. Spell check already does the rest. |

## Step 6: Verdict and recommendations

**Overall fit: Moderate (3.7 out of 5), strong for the checklist subtasks.** GenAI earns a place in the audit as a pre-check layer, not as a replacement for it. The best design splits the work by subtask rather than handing the whole audit to a chatbot.

**Use GenAI for**

- An exception report on each returned syllabus covering required elements, grading rules and a plain-English summary of faculty changes (S4, S5, S7).
- Drafting the notes sent to faculty about what to fix.
- Onboarding new staff. The report acts as the checklist that currently lives in Tatum's memory.

**Use something else for**

- Session dates (S2): a short script or spreadsheet that reads the shell and the academic calendar, or GenAI only when it runs code.
- Locked sections (S3): Word Compare, which is already in use.
- Formatting (S8): Word's own tools.
- Textbooks (S6): the aide's existing check, with web search as support.

**Risks and controls**

| Risk | Control |
| --- | --- |
| A missed error reaches students | A person keeps sign-off on every syllabus. The tool only raises flags and never approves. |
| False flags wear down trust | A fixed report format and quoted evidence for each flag. False flags are tracked in the pilot. |
| Different results from run to run | The rules live in one file. Output is in a fixed checklist format and the model runs at low variability. |
| Rules go out of date | One owner, the program administrator, updates the rules file each semester. |
| Faculty intellectual property leaves NYU | Only an NYU-approved account that does not train on uploads is used. |

**Pilot design**

1. **Scope:** 20 syllabi from a past semester, including at least 5 from instructors new to the course.
2. **Test set:** seed 30 known errors across the 20 files, including wrong dates, a removed policy section, weights totalling 90%, team work at 40%, an outdated edition and a missing office-hours line.
3. **Baseline:** the aide reviews the set unassisted, with both time and errors caught recorded.
4. **Trial:** the aide reviews a matching set with the exception report.
5. **Metrics:** minutes per syllabus, share of seeded errors caught, false flags per syllabus and the aide's confidence rating.
6. **Pass threshold:** at least 95% of rule-based errors caught, no more than 1 false flag per syllabus and new-staff review time under 15 minutes.

If the pilot passes, the date script (S2) is the next build, since that is the bottleneck Tatum names first.
