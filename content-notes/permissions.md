# Content Notes: Permissions, Sandboxes, and Autonomous Agents

## Sources

- **Substack post:** https://paulgp.substack.com/p/permissions-sandboxes-and-autonomous
- **Video:** https://www.youtube.com/watch?v=8Jnx5rL_Gfk (Markus Academy Ep. 162-7)
- **Duration:** 47:47 (from YouTube metadata)

## Draft Summary (DRAFT, pending Paul)

Giving an agent broad permissions feels risky, but reflexively clicking "yes"
on every prompt is not real safety either. This video reframes the question: the
real lever is the environment, not the approval mode. It walks through Docker
containers and devcontainers that mount only the folders you need, drop network
access once setup is done, and let you run Claude in auto or YOLO mode inside a
tight boundary. It also covers data governance (privacy filters for sensitive
material, local models as a fallback) and long-running agent workflows like
OpenClaw and how to set up your own personal research agent.

## Tagline

"The real lever is the environment, not the approval mode."

**Source:** Compressed from takeaway 3 ("The real lever is the environment: mount
only what you need, drop capabilities, use --network=none once setup is done").

## What you'll learn (from post's takeaways section)

Paul provides six numbered takeaways. All preserved.

Live bullets (6):
1. Permissions come in two forms (folder access and tool access), and both need to be reasoned about separately
2. Auto and YOLO approval modes can be sensible if you prepare the environment first; reflexive "yes" clicks are not real safety
3. The real lever is the environment: mount only what you need, drop capabilities, use --network=none once setup is done
4. Data governance is separate from sandboxing; for genuinely sensitive material, a local model may be the right answer rather than a remote one
5. Sandboxing opens up the long-running-agent workflow: once the boundary is right, persistent agents become tractable
6. Treat an agent with tools like a research assistant: you would not give an RA a task where they can break everything, and the sandbox is how you enforce that

## High-Level Applications (NOTES ONLY, not published)

- Docker container setup for Claude Code
- Devcontainer configuration for research projects
- agent-safehouse as an alternative to manual Docker setup
- Privacy filters for sensitive data
- Long-running autonomous agent workflows (OpenClaw, Duncan Idaho)
- AWS Bedrock for data-governance-constrained projects

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- claude-container (Paul's Docker setup): https://github.com/paulgp/claude-container
- agent-safehouse: https://agent-safehouse.dev/
- OpenClaw: https://openclaw.ai/

### Additional references from the post (not live)
- AWS Bedrock: https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html
- OpenAI privacy filter: https://huggingface.co/openai/privacy-filter
- lalgorithms Clawdbot walkthrough: https://apoorvalal.github.io/lalgorithms/krabs-the-clawdbot-walkthrough

## Gaps / Flags for Paul

1. **Video duration** (47:47) from YouTube metadata, not manually verified.
2. **OpenClaw URLs** (openclaw.ai and openclawai.io) both mentioned in the post; using the .ai domain as primary.
3. **Duncan Idaho** is Paul's personal agent concept; no public repo or link to reference.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
