# Spinx Web

The web client for the Spinx auth system. Next.js App Router, TypeScript and Tailwind, with the full account lifecycle wired to the API — and a WebGL galaxy behind it so the marketing pages don't look like a boilerplate.

Part of the Spinx trio:
[spinx-api](https://github.com/adityasinghin01-hash/spinx-api) ·
[**spinx-web**](https://github.com/adityasinghin01-hash/spinx-web) (this repo) ·
[spinx-mobile](https://github.com/adityasinghin01-hash/spinx-mobile)

---

## Pages

| Route | What it does |
| --- | --- |
| `/` | Landing page |
| `/signup` · `/login` | Account creation and sign-in, reCAPTCHA-guarded |
| `/auth/callback` | Google OAuth return leg |
| `/forgot-password` | Reset request |
| `/dashboard` | Signed-in home |
| `/profile` | Account details |
| `/blog` · `/blog/[slug]` | Blog index and post |
| `/contact` | Contact form |
| `/newsletter` | Newsletter signup |
| `/waitlist` | Waitlist capture |

## Stack

Next.js 16 · React 19 · TypeScript · Tailwind CSS v4 · Framer Motion · Lenis smooth scroll · Three.js via React Three Fiber and Drei · Lucide icons

## Getting started

```bash
git clone https://github.com/adityasinghin01-hash/spinx-web.git
cd spinx-web
npm install
npm run dev        # http://localhost:3000
```

You need [spinx-api](https://github.com/adityasinghin01-hash/spinx-api) running for
anything past the landing page to work.

> **Pointing at your own API.** The base URL is currently a constant at the top of
> `lib/api.ts`, not an environment variable. Change it there, or lift it to
> `NEXT_PUBLIC_API_URL` if you want per-environment builds.

## Layout

```
app/                 App Router — one folder per route
components/          Navbar, Footer, GalaxyBackground, SmoothScroll
lib/api.ts           Fetch wrapper — auto-retries once on 401 with a refreshed token
lib/auth.ts          Token storage and read/clear helpers
tailwind.config.ts   Theme tokens
```

`lib/api.ts` is the piece worth reading first: every call goes through it, and it
transparently refreshes an expired access token and replays the request once
before giving up.

## Notes

- `AGENTS.md` carries a standing instruction for AI coding assistants — this is Next.js 16, and its conventions differ from what most models were trained on. Read the bundled docs in `node_modules/next/dist/docs/` before writing App Router code.
