# Gustavo AI project instructions

## Project shape

- This repository is a static bilingual Spanish/English portfolio site.
- The complete site implementation is in `index.html`; keep changes in that file unless a change clearly requires a new asset or page.
- Do not introduce a framework, build system, package manifest, or dependencies for routine content or presentation changes.
- Preserve the existing single-file pattern: HTML structure, embedded CSS, and embedded JavaScript belong in `index.html`.
- The GitHub Actions workflow builds the repository with Jekyll in Docker. It is not a deployment workflow.

## Content and localization

- Spanish is the default language; English is the alternate language.
- Any visible text change must keep both `data-es` and `data-en` values in sync.
- Update the same content meaning in Spanish and English, including navigation labels, headings, descriptions, buttons, accessible labels, and aria text.
- Use clear, professional language consistent with an AI and software consultancy.
- Do not claim that experimental projects are finished or that AI features provide guaranteed translations or automation.
- Preserve project cautions: Drama Sign AI is an experimental concept and INCLUSIA AI is a solution concept.
- The WhatsApp and professional profile links are public placeholders or external destinations. Do not replace or remove them unless explicitly requested.

## HTML, CSS, and JavaScript

- Follow the existing semantic structure: `header`, `nav`, `main`, `section`, `article`, `aside`, and `footer`.
- Reuse existing CSS variables from `:root` before adding colors or changing the visual system.
- Reuse existing components and classes such as `.wrap`, `.grid`, `.card`, `.project`, `.aboutbox`, `.btn`, `.primary`, `.secondary`, and `.skills`.
- Preserve the responsive breakpoint behavior, especially the `@media(max-width:760px)` layout.
- Use valid, descriptive HTML; avoid duplicate IDs and unnecessary wrapper elements.
- Keep user-facing controls keyboard accessible. Buttons need explicit `type` attributes, and interactive elements need appropriate labels.
- Preserve text contrast and focus visibility; do not remove focus styles or rely on color alone to communicate status.
- Keep external links safe with `target="_blank"` and `rel="noopener noreferrer"` when appropriate.
- Keep JavaScript small and browser-native. The language toggle must update `document.documentElement.lang`, visible translated text, button text, and the toggle's `aria-label`.
- Update the footer year dynamically; do not hard-code a new year.

## Validation

- Before finishing, inspect the final diff and check for broken HTML structure, duplicate IDs, missing localization attributes, and placeholder regressions.
- Serve the page locally with `python3 -m http.server 8000` and open `http://localhost:8000/index.html` for visual and interaction checks.
- For a static syntax check, use Python's `html.parser` or run `python3 -c "from html.parser import HTMLParser; HTMLParser().feed(open('index.html', encoding='utf-8').read())"`.
- The CI-equivalent Jekyll build is:
  `docker run -v "$PWD:/srv/jekyll" -v "$PWD/_site:/srv/jekyll/_site" jekyll/builder:latest /bin/bash -c "chmod -R 777 /srv/jekyll && jekyll build --future"`
- Run the CI build when changing workflow or site structure. Docker availability can vary, so report that limitation explicitly if it cannot run.
