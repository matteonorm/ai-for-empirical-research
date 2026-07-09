# Content Notes: Skills: Specifying How an Agent Should Think

## Sources

- **Substack post:** https://paulgp.substack.com/p/skills-specifying-how-an-agent-should
- **Video:** https://www.youtube.com/watch?v=a03ehomPqMA (Markus Academy Ep. 162-6)
- **Duration:** 31:04 (from YouTube metadata)

## Draft Summary (DRAFT, pending Paul)

A skill is just a markdown file that gets loaded into Claude's context window,
but the leverage comes from standardizing recurring workflows. This video walks
through building a paper-summary skill from scratch: writing the instructions,
testing it on a real working paper, and iterating when the output confuses
theoretical and empirical contributions. It also covers where skills live
(user-global vs. project-local), Claude Code's built-in skills, the emerging
marketplace, and two warnings about context consumption and third-party trust.

## Tagline

"A skill is just a markdown file; the leverage comes from standardizing workflows."

**Source:** Compressed from takeaway 1 ("A skill is just instructions in a
markdown file loaded into the context window; the leverage comes from
standardizing recurring workflows").

## What you'll learn (from post's takeaways section)

Paul provides six numbered takeaways. All preserved.

Live bullets (6):
1. A skill is just instructions in a markdown file loaded into the context window; the leverage comes from standardizing recurring workflows, not from any new model capability
2. Start narrow and opinionated: one repeated problem, one well-specified output structure
3. The description field is a trigger, not a title; Claude uses it to decide when the skill applies, so write it for the model, not for humans
4. Test on the work you actually do: the theory-vs.-empirical fix in the paper-summary skill only surfaced because it was run on a real paper
5. Check what already ships with Claude Code and what's in the marketplace before building from scratch
6. Be careful what you install: skills fill the context window, and third-party skills are someone else's instructions running in your environment

## High-Level Applications (NOTES ONLY, not published)

- Building custom paper-summary skills
- Standardizing literature review workflows
- Skill development and iteration cycle
- Managing context window consumption
- Third-party skill marketplace evaluation

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- Claude Code skills documentation: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- Superpowers skill collection (Jesse Vincent): https://github.com/obra/superpowers
- Anthropic skills repository: https://github.com/anthropics/skills

### Additional references from the post (not live)
- Strategic-revision skill: https://github.com/jusi-aalto/strategic-revision
- Brainstorming skill example: https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md
- Grill-me skill example: https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md

## Gaps / Flags for Paul

1. **Video duration** (31:04) from YouTube metadata, not manually verified.
2. **Skills documentation URL** may change as Anthropic updates docs.
3. **Paper used in the demo** is Markus's working paper ("Optimal Unconventional Monetary Policy"); not linked since it's the example, not a resource.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
