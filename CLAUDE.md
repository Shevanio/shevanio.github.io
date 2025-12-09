# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based personal portfolio website deployed on GitHub Pages for **David (Shevanio)**, a monitoring technician and systems administrator from Barcelona, Spain. The portfolio showcases his professional experience, education, certifications, technical skills, and projects. It features sections for work experience, education timeline, skills (languages, frameworks, tools), personal projects, and open source contributions pulled from GitHub.

The site uses Gulp for asset compilation (SCSS/JS minification) and BrowserSync for local development with live reload.

## Development Commands

```bash
# Install dependencies
bundle install
npm install

# Start development server (builds Jekyll, compiles assets, watches for changes)
npm run dev
# Runs on http://localhost:4000

# Production build
npm run prod
```

## Architecture

**Static Site Generator**: Jekyll with `github-pages` gem
- `_config.yml` - Main site configuration (personal info, section toggles, social links)
- `_config_dev.yml` - Development overrides (merged with main config during `npm run dev`)

**Build Pipeline**: Gulp handles asset compilation
- SCSS: `_sass/main.scss` → `assets/css/main.min.css`
- JS: `_js/app.js` → `assets/js/app.min.js`
- Vendor CSS/JS are concatenated and minified separately

**Content Structure**:
- `_data/*.yml` - Data files for skills, projects, and timeline entries
- `_includes/*.html` - Section partials (aboutme, skills, timeline, projects, contact)
- `_layouts/default.html` - Main layout that conditionally renders sections based on `_config.yml` flags

**Section Visibility**: Each section can be toggled via boolean flags in `_config.yml`:
- `show_aboutme_card`, `show_skills_card`, `show_timeline_card_work`, `show_timeline_card_education`, `show_projects_card`, `show_contact_card`

## Data File Formats

See `docs/data.md` for YAML schema details. Key data files:
- `_data/projects.yml` - Custom projects with name, description, demo URL, tags
- `_data/skills-*.yml` - Skills with name and weight (1-5)
- `_data/timeline_work.yml`, `_data/timeline_education.yml` - Timeline entries with title, date, subtitle, tags
