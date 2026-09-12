---
layout: page
title: Throughline
description: A goal-tracking planner that turns notes and meetings into todos
img: assets/img/projects/throughline-ui.png
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

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/throughline-ui.png" title="Throughline interface" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    The whole app is one screen: the assistant on the left takes pasted notes or plain conversation, and the live task list and Profile sit beside it on the right so you can see what any proposal would change before accepting it. "Review plan vs goals" runs the gap analysis below.
</div>

<!-- TODO(visuals): still wanted — a mid-adjudication shot with pending cards (new / duplicate / in-place update) and a populated task list and Profile; the current screenshot shows the empty state. -->
