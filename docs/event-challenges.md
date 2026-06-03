# Event challenges (admin guide)

Run a **live, presenter-led challenge** during a workshop, meetup, or conference. Attendees register, join with a code or QR, complete timed missions in NoGira (activities, wiki, exploration), and see scores on a big-screen leaderboard.

This guide is for **system administrators** who have never run a challenge before. Attendees use a normal user account; only admins create and drive sessions.

## Screenshots

![Live event challenges — admin guide](assets/nogira-challenge.gif)

*End-to-end admin flow in one view: **Settings → Challenges** list (create session, join token, workspace, status, presenter / manage / delete); then presenter lobby (QR, **Open Queue**, **Start Challenge**), missions, leaderboard, and results. The animation walks through the same steps documented below.*

## Who can administer challenges

- You need the **System Administrator** role.
- Open **Settings** (gear) → **Challenges** (`/settings/challenges`).
- If you do not see **Challenges**, ask another admin to grant **SYSTEM_ADMIN** or use the account created in the setup wizard.

## What you need before the room

| Prerequisite | Why |
|--------------|-----|
| A **workspace** for the event | Missions score actions inside that workspace (activities, wiki, navigation). |
| At least one **activity** attendees can complete | Mission 1 expects an activity the user can move to **Done** (e.g. a welcome task). |
| A projector or large display | **Presenter mode** is built for the room screen. |
| Stable Wi‑Fi for attendees | Phones join via QR or link; scoring syncs over the API. |

You do **not** need a separate Docker service. Challenges run on the same **nogira-core** and **nogira-ui** images as the rest of NoGira (see [0.1.14 release notes](releases/0.1.14.md)).

## Overview (30 seconds)

```text
Create challenge (DRAFT)
    → Presenter mode → Open Queue (WAITING_FOR_PLAYERS)
    → Attendees scan QR / register with ?game=
    → Start Challenge (RUNNING) → missions + leaderboard
    → Next phase (presenter) → Results / podium → Finish
```

See [Screenshots](#screenshots) above for the full UI walkthrough.

---

## Step 1 — Create a challenge

1. Go to **Settings → Challenges**.
2. Click **Create Challenge**.
3. Fill in:
   - **Code** — short uppercase id (e.g. `ACE-DUBLIN`); used internally and in URLs.
   - **Name** — title shown to attendees (e.g. *ACE Dublin Challenge*).
   - **Description** — optional; visible on manage screen.
   - **Workspace** — where missions run; pick the demo or event workspace.
4. Save. The new row starts in **DRAFT**.

**Tip:** Create the challenge at least a day before the event so you can test join and presenter flow once in **DRAFT** (you can delete only while **DRAFT**).

---

## Step 2 — Open presenter mode

1. On the list, click the **monitor** icon (**Presenter mode**), or open **Manage challenge** and use **Open presenter**.
2. Presenter opens full-screen style modal (`/settings/challenges/:id/present`).
3. Use the header control to **expand / full-screen** on the projector (press **Escape** to exit full-screen).

While **DRAFT**, the lobby shows a QR and join URL, but attendees **cannot** join yet.

---

## Step 3 — Open the queue (let people join)

1. In the lobby, click **Open Queue**.
2. Status becomes **WAITING FOR PLAYERS**; registration opens.
3. The QR and link become active. Share either:
   - **QR** on the big screen, or
   - **Join URL** — `https://<your-host>/register?game=<JOIN_TOKEN>`  
     (local eval: `http://localhost:3000/register?game=<JOIN_TOKEN>`).

The **join token** is on the admin list and manage page (monospace string). It is not the same as the challenge **code**.

### What attendees do (so you can brief the room)

| Step | Attendee action |
|------|-----------------|
| 1 | Scan QR or open the join link. |
| 2 | **Register** or **sign in** if prompted. |
| 3 | After login, land on **Home** with a **waiting** overlay (“you joined …”) until you start. |
| 4 | Already logged in? **Profile menu → Challenges** → enter join token. |

After join, attendees land on **Home** with a waiting overlay until you click **Start Challenge** (shown in the [screenshot](#screenshots)). Watch **Registered Players** in the lobby; names appear as people connect.

---

## Step 4 — Start the challenge

When everyone important is in the queue:

1. Click **Start Challenge** in presenter mode.
2. Status becomes **RUNNING**; Mission 1 timer starts (server-driven).
3. Attendees see a **mission HUD** over the product; you see mission + live leaderboard on the projector.

**Do not** start until you are ready: timers and scoring begin immediately.

---

## Step 5 — Run missions (presenter drives pace)

Default missions (MVP1) are fixed for every challenge:

| Phase | Duration | What attendees do | Scoring idea |
|-------|----------|-----------------|--------------|
| **Mission 1** — Complete activity | 45 s | Complete an activity they report on (e.g. move to **Done**) | Base points + bonus for 1st/2nd/3rd finisher |
| **Mission 2** — Create wiki page | 60 s | Create a wiki page in the workspace | Same race bonus pattern |
| **Mission 3** — Explore NoGira | 90 s | Visit Activities, Plan, Wiki, Insights; comments/attachments count once | Speed multiplier on exploration actions |

Mission 1 uses **Activities** in the linked workspace; Mission 2 uses **Wiki**; Mission 3 rewards first-time visits across product surfaces (see [screenshot](#screenshots)).

After each mission block, click **Next phase** at the bottom of presenter mode to advance (Mission 2 → Mission 3 → Leaderboard → Results).

You control pacing; attendees do not auto-advance between missions without your **Next phase**.

---

## Step 6 — Leaderboard and results

- **Leaderboard** — top scores refresh about every 3 seconds on presenter and attendee views.
- **Results** — podium-style top 3 (and more ranks); post-challenge CTAs can be tracked when attendees click them.
- Click **Finish** (or close flow from results) to end the session (**FINISHED**). Registration closes.

You can also use **Manage challenge** → **Next phase** / **Finish** if you exited presenter accidentally.

---

## Admin list actions

| Action | When to use |
|--------|-------------|
| **Presenter mode** (monitor) | Run the live session on the big screen. |
| **Manage** (pencil) | Edit name/description/workspace; copy join URL; lifecycle buttons. |
| **Delete** (trash) | **DRAFT only** — type the challenge name to confirm. |

After **Open Queue**, you **cannot** delete from the UI (participants and scores exist). Plan test runs in **DRAFT** and delete mistakes before opening the queue.

---

## Status reference

| Status | Meaning |
|--------|---------|
| **DRAFT** | Created; queue closed; safe to delete. |
| **WAITING_FOR_PLAYERS** | Queue open; joins allowed; no mission timer. |
| **RUNNING** | Challenge live; missions and scoring active. |
| **FINISHED** | Session ended; read-only results. |

---

## URLs (local vs hosted)

| Surface | Local evaluation | Hosted example |
|---------|------------------|----------------|
| UI | `http://localhost:3000` | `https://demo.nogira.io` |
| Join link | `http://localhost:3000/register?game=<JOIN_TOKEN>` | `https://demo.nogira.io/register?game=<JOIN_TOKEN>` |
| Admin list | `http://localhost:3000/settings/challenges` | `https://<host>/settings/challenges` |

Replace `<JOIN_TOKEN>` with the value from the **Join token** column (not the challenge code).

---

## Troubleshooting

| Problem | What to check |
|---------|----------------|
| No **Challenges** in Settings | Your user must be **SYSTEM_ADMIN**. |
| QR works but “cannot join” | Click **Open Queue** first (**WAITING_FOR_PLAYERS**). |
| Attendee stuck after login | They should land on **Home** with waiting HUD; if not, use **Profile → Challenges** and enter the token. |
| Scores not moving | Challenge must be **RUNNING**; actions must happen in the **linked workspace**. |
| Cannot delete | Only **DRAFT** rows; finish or leave finished challenges in the list for history. |
| Presenter blank / loading | Refresh; confirm API is up (`/api/admin/challenges/:id/live`). |

---

## Quick checklist (day of event)

1. [ ] Challenge created; workspace has a completable activity.
2. [ ] Presenter mode tested on the projector (full-screen).
3. [ ] **Open Queue** only when doors open.
4. [ ] Join URL / QR on screen; staff know token backup.
5. [ ] **Start Challenge** when room is ready.
6. [ ] **Next phase** after each mission segment.
7. [ ] **Finish** and thank the room.

---

## Related docs

- [README — Challenge game](../README.md#challenge-game)
- [Release 0.1.14 — Event Challenge Engine](releases/0.1.14.md)
- [Deployment & upgrades](deployment.md)
