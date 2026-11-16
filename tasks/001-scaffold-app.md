---
id: "001"
title: Scaffold the React + TypeScript app
week: 1
status: todo
depends: []
---

## Goal
A running Vite + React + TypeScript app that installs as a PWA, with linting, tests and routing ready.

## Steps
- `npm create vite@latest . -- --template react-ts`
- Add Tailwind CSS, React Router, `vite-plugin-pwa` (app name "PetTrack", placeholder icons)
- Add Vitest + Testing Library with one sample test
- Add ESLint + Prettier; npm scripts: `dev`, `build`, `test`, `lint`
- Create folders: `src/features/`, `src/components/`, `src/lib/`
- Simple layout: header + bottom nav (Today, Pets, Health, Settings) with placeholder pages

## Done when
- `npm run dev` shows the layout and nav works on a phone-sized screen
- `npm run build`, `npm test` and `npm run lint` all pass
