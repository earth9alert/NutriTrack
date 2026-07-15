---
kind: configuration_system
name: No configuration system — single-file SPA with inlined defaults
category: configuration_system
scope:
    - '**'
source_files:
    - index.html
---

This repository contains a single-file Thai-language calorie and macronutrient tracker (index.html). There is no configuration system: all application settings are hard-coded as JavaScript constants inside the same HTML file, and there are no config files (.env, .yaml, .toml, JSON configs), no build-time config loaders, and no runtime environment variable handling.

Key inlined configuration values:
- Daily goals: `const GOALS = { calories: 1800, protein: 120, carbs: 150, fats: 50 }` (line 290)
- Meal labels: `const MEALS = { breakfast: 'มื้อเช้า', lunch: 'มื้อกลางวัน', dinner: 'มื้อเย็น', snack: 'ของว่าง' }` (line 291)
- Preset food database: `const PRESETS = [...]` array of 8 items (lines 293–302)
- Tailwind theme colors: `tailwindcss.config = { theme: { extend: { colors: { brand: {...} } } } }` (lines 9–17)
- Persistence key: `localStorage.getItem('nutritrack_log')` / `localStorage.setItem(...)` (line 304/370)

There is no mechanism to override these values via URL parameters, query strings, env vars, or external files. The app is designed to be edited directly in source for any customization.