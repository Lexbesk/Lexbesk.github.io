---
layout: page
title: Throughline
description: A goal-tracking planner that turns notes and meetings into todos
img: assets/img/2.jpg
importance: 2
category: engineering
github: https://github.com/Lexbesk/Throughline
---

Most task apps are containers: you put things in, they hold them. **Throughline** is built the other way around — it reads your notes and meetings, and works out what they imply for what you are actually trying to do.

Built and deployed Jun 2026 – Jul 2026.

## Deciding what is actually new

The hard problem is not extracting candidate todos; it is deciding what to do with each one against a task list that already exists. Throughline uses a two-stage approach: a **pre-filter** narrows the field cheaply, then the model **adjudicates each candidate** as one of three things — **new**, **duplicate**, or an **in-place update** to something already tracked. That third category is the one that keeps a live list from silently accumulating near-copies of the same intention.

## The Profile

The piece the rest of the app is built around is the **Profile**: a representation of the user's background, goals, and opinions. Analysis runs _through_ it, so notes and todos are read from the user's perspective rather than a generic one, and the advice the app produces is tailored rather than boilerplate. Every function in the app is designed around this object.

**Stack:** deployed on [Fly.io](https://fly.io) with [Neon](https://neon.tech) Postgres. Source on [GitHub](https://github.com/Lexbesk/Throughline).

<!-- TODO(visuals): needed — (1) product screenshots (goal view, todo adjudication, Profile editor), (2) architecture diagram: notes → pre-filter → adjudicator → live task list, (3) a worked new/duplicate/update example. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/2.jpg" title="placeholder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder — to be replaced with product screenshots and the pipeline diagram.
</div>
