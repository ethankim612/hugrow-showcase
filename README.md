# Hugrow

**A family wellness app built around daily check-ins, shared goals, and small weekly challenges.**

1st Place and Ministry of Education Award, e-icon World Contest 2026 · Development Lead

> This repository shows the app's design and architecture. The contest source code is kept private.

<p align="center">
  <img src="screenshots/welcome.png" width="23%" alt="Welcome screen">
  <img src="screenshots/home.png" width="23%" alt="Family home screen">
  <img src="screenshots/daily-check-in.png" width="23%" alt="Daily check-in">
  <img src="screenshots/mood-results.png" width="23%" alt="Mood results">
</p>

## The idea

Families often share a home without sharing how each member is doing. Hugrow gives every member a short daily check-in, turns the results into a family view, and suggests challenges the family can do together. Completing check-ins and challenges earns Seeds that can be redeemed for vouchers from local businesses, and a Ripple Map shows where families using the app are growing.

## My role

**Development Lead.** I led the team's development of the app.

## How it works

```mermaid
flowchart LR
    U[Family members<br>React + Vite SPA] -->|auth, data| S[(Supabase Postgres<br>Row Level Security)]
    U -->|check-in text| F[Supabase Edge Functions]
    F -->|server-side API key| C[Claude API]
    F --> U
    V[Vercel] -.hosts.-> U
```

- **Privacy by default.** Row Level Security lets each user read and write only their own rows. Members of the same household can see each other's profile and daily check-ins, which powers the shared family view.
- **AI kept on the server.** Mood analysis and assessment feedback call Claude through Supabase Edge Functions, so the API key never reaches the browser.
- **Works without AI.** If the Edge Functions are unavailable, check-ins and assessment results fall back to a local heuristic.

## Screens

<p align="center">
  <img src="screenshots/assessment-results.png" width="23%" alt="Assessment results by category">
  <img src="screenshots/challenges.png" width="23%" alt="Challenge center">
  <img src="screenshots/goals.png" width="23%" alt="Personal and family goals">
  <img src="screenshots/ripple-map.png" width="23%" alt="Ripple map of families">
</p>

## Stack

React · Vite · Tailwind CSS · Supabase (Postgres, Auth, Edge Functions) · Claude API · Vercel

<sub>All people and families shown are demo data.</sub>
