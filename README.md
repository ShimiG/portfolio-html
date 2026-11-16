# Shimi Goldshlak Projects

A one-page portfolio of selected projects: AI agents, automation pipelines and desktop apps. Each project gets a short description, a strip showing how it moves work from input to result, its main design choices and its tech stack.

Projects covered:

- **Is It Real?**: on-device detector for AI-generated text, images and video
- **Music Manager**: desktop music player that combines several streaming services and local files in one library
- **Job Agents**: multi-agent job search pipeline
- **LinkedIn post pipeline**: GitHub Actions workflow that drafts posts and sends them for approval
- **readme-autoupdate**: weekly workflow that proposes README updates as pull requests

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | Site entry point. It redirects to `docs/`. |
| `docs/index.html` | The portfolio page. It is a single self-contained HTML file with inline CSS and loads fonts from Google Fonts. |
| `html/Shimi Goldshlak Projects.html` | Standalone copy of the portfolio page. |
| `md/Shimi Goldshlak Projects.md` | The same content as Markdown. |

## Viewing

There is no build step. Open `docs/index.html` in a browser, or serve the repository root with any static file server. `index.html` will redirect to `docs/`.
