---
title: "One Skill to Tend Them All"
summary: "I've spent a lot of time building AI skills like software libraries: repos, releases, versions. It turns out the better workflow was to stop packaging skills and start growing them..."
keywords: ["AI skills", "agent skills", "Claude", "ChatGPT", "Gemini", "skill creator", "prompt engineering", "continuous improvement", "the-one-skill"]
date: 2026-11-19
description: "Why I stopped packaging AI skills like software libraries, and built a skill that grows, refines, and organizes all my other skills from real sessions."
tags: ["AI", "Agent skills", "Developer workflow"]
# TODO: add images/splash.jpg and uncomment.
# featured_image: "images/splash.jpg"
# image_alt: ""
featured: false
draft: true
---

<!-- TODO (Thomas): swap in one or two skills you've actually used or built, and what they did for you. -->
Over the past year, skills have quietly become one of my favorite parts of working with AI. A skill is just a folder: a `SKILL.md` file that tells the model when and how to do a job, plus any scripts or reference files it needs. Drop one into Claude, ChatGPT, or Gemini, and the model picks it up whenever the job comes around. I've used skills for writing, for working with spreadsheets, for code review, and I've tried my hand at building a few of my own.

Being a software engineer, I did what software engineers do: I treated skills like libraries. I set up a repo structure to build and package them. Source files in one place, a build script to bundle them, a version number, a changelog, a release. If skills are code for the model, I figured, they should get the same discipline as code for the machine.

It didn't work as well as I hoped.

## Skills Are Hard to Ship

On the command line, skills are easy. Claude Code and Codex make it simple to search for, install, and update a skill from a terminal. A skill is a folder, and folders are what CLIs are good at. Clone it, and you're done.

The web-based AI apps are a different story. Versioning a skill and getting it into the hands of the ChatGPT, Gemini, or Claude web app means zipping it up and uploading it by hand. There's no package manager, no `upgrade` command, and no easy way to see which version you're actually running.

That made my "skills as libraries" workflow painful. Every change to a skill went something like this:

1. Edit the skill in the repo.
2. Build it and cut a release.
3. Download the release.
4. Upload it to the AI app.
5. Try it out.
6. Find something wrong and go back to step 1.

That's a long loop for changing one sentence of instructions.

The obvious answer is evals: write test cases, run the skill against them, and only release when the numbers look good. Evals have their place, but they're expensive. They cost time to write and tokens to run, and they only test the situations you thought to write down. The honest truth is that you only really know a skill works after you've used it for real, on real work, with all the messiness that comes with it.

## Changing the Workflow

So I started experimenting with a different approach. Instead of hand-crafting a skill and shipping it through a release pipeline, I let the AI do both the building and the improving:

1. **Build the skill from scratch with a skill creator.** Describe the job, and let a skill-creating skill write the first draft.
2. **Use it for real.** Have a long, winding back-and-forth session with ChatGPT or Gemini doing actual work.
3. **Refine it from the session.** At the end, ask a skill to look back at the conversation and improve the skill that did the work.

<!-- TODO (Thomas): a short, concrete example from one of your sessions would land well here. -->
I was surprised by how intuitive this felt. When I corrected the model three times in a session ("table, not prose," "don't count the header row"), those corrections weren't wasted. They were the exact rules the skill was missing. Every session where I had to fight the AI to get something done turned into something valuable: a precise description of where the skill fell short, written in the language of the real problem.

Friction stopped being a cost and became the input.

## From "Continuous Improvement" to the-one-skill

To make that last step repeatable, I built a "skill continuous improvement" skill. Its job was simple: at the end of a session, reflect on what went wrong, trace each correction back to the rule in the skill that caused it, and propose a fix.

It didn't stay simple for long. Once I had a skill that could improve skills, I kept wanting it to do more, and it soon grew into [the-one-skill](https://github.com/mtfuller/the-one-skill): a skill to manage your skills.

> *One skill to tend them all, one skill to find them,*
> *one skill to mend them all, and never leave the old behind.*

Here's what it does today.

### It evolves your skills from real sessions

Ask it to *"reflect on this session,"* and it finds the skill that did the work, names the corrections you made, and proposes a fix in one or two plain sentences. It names any existing rule it's replacing, so nothing gets overwritten quietly, and nothing changes without a yes from you.

It also never loses an original. The first time it changes a skill, it keeps an untouched copy forever, plus the last five versions. *"Undo that"* and *"back to vanilla"* work exactly how you'd hope. That safety net is what makes it comfortable to let the AI edit its own instructions.

### It keeps your skills orthogonal

This is the part I didn't see coming. Once you have a dozen skills, they start getting in each other's way. Two skills fire on the same request. Three different skills each carry their own copy of the same formatting rules, and those copies slowly drift apart.

I wanted every skill to have its own turf: one clear job, with no other skill stepping on it. When you ask the-one-skill to *"review my skills,"* it checks for exactly that:

- **Clashing triggers**: two skills that both want the same request. The fix is a clear boundary or a merge.
- **Repeated procedure**: the same rules copied into several skills. This one is sneaky, because those skills may never fire together, so you never notice the conflict. A small script compares every pair of skills on *what they do*, not just what triggers them.
- **A roster map** of which skill owns each job, so later reviews check against your earlier decisions instead of asking twice.

Each fix lands in the skill that owns it. If a brand font belongs to a `brand-style` skill, that's where the fix goes, not into whichever deck skill happened to be running.

### It finds skills from verified sources

There's no reason to start a new skill from a blank page when Anthropic, OpenAI, or Google has already published one that does most of the job. Ask it to *"find me an official skill for Terraform,"* and it searches only those three publishers. It reads every file of a candidate before installing anything, and tells you what the skill instructs, runs, and reaches over the network.

If a published skill is close but not quite right, it installs it exactly as published and keeps your tweaks as a separate version on top. When the publisher ships an update later, your tweaks carry forward.

### It works where your skills live

Remember the upload problem from earlier? The-one-skill doesn't pretend it away. On its first run it studies the host it's running on and picks the safest way to keep originals there. On Claude Code, that's a local store plus a hook that blocks direct edits to your skills. On ChatGPT, where it can't touch files, it hands you two downloads for every change: a backup of the skill as it was, and the new version to upload. The workflow fits the host instead of fighting it.

## Building Skills Fast

<!-- TODO (Thomas): add your own numbers or a specific example (which account, how many skills, how long). -->
The thing that surprised me most is how quickly this works from a standing start. Even in a brand new AI agent account with no skills at all, you can build out a useful set in a short time: do your normal work, notice the friction, make a skill for it, refine it after the next session, and let the review step keep the roster tidy.

The-one-skill itself was built the same way. Most of it came together over a few days of working sessions, with each round of friction turning into the next improvement.

Looking back, my mistake wasn't wanting discipline around skills. Versions, changelogs, and undo still matter, and the-one-skill keeps all of them. My mistake was putting that discipline in the wrong place. Skills don't get better in a release pipeline. They get better in the session, the moment you notice they fell short.

If you want to try it, [the-one-skill is on GitHub](https://github.com/mtfuller/the-one-skill). Install it, do some real work, and then say *"reflect on this session."*
