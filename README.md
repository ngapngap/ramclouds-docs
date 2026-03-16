# Ramclouds API Documentation

This folder contains the documentation for [docs.ramclouds.me](https://docs.ramclouds.me).

## Quick Start

This documentation uses [Docsify](https://docsify.js.org/) - a simple documentation site generator.

### Local Development

1. Install docsify-cli:
```bash
npm i docsify-cli -g
```

2. Run local server:
```bash
docsify serve docs
```

3. Open http://localhost:3000

### Deploy to GitHub Pages

1. Create a new repository on GitHub
2. Push this folder to the repository
3. Go to Settings > Pages
4. Set source to the `docs` folder on main branch
5. Your docs will be available at `https://yourusername.github.io/reponame`

### Custom Domain

To use `docs.ramclouds.me`:

1. Create `docs/CNAME` file with content:
```
docs.ramclouds.me
```

2. Configure DNS:
   - Add CNAME record: `docs` -> `yourusername.github.io`

## Endpoint/Model Mapping Note

When using the `v1/messages` endpoint with Claude models, use the canonical model ID **without** the `-CL` suffix.

- Correct (`v1/messages`): `claude-sonnet-4.6`
- Incorrect (`v1/messages`): `claude-sonnet-4.6-CL`

Scope note: this rule is specific to `v1/messages`. If another endpoint has different model ID conventions, follow that endpoint's documentation. In OpenAI-compatible flows, use the model suffix expected by that adapter (for Claude models, typically `-CL`) and do not reuse that suffix on `v1/messages`.

Security note: a mismatched endpoint/model pair (for example, using `-CL` on `v1/messages`) can cause request failures. Add endpoint-aware input validation in clients to reduce configuration errors.

## File Structure

```
docs/
├── index.html          # Main entry point
├── README.md           # Home page content
├── _coverpage.md       # Cover page
├── _sidebar.md         # Sidebar navigation
├── _navbar.md          # Top navigation
├── guide/
│   ├── introduction.md
│   ├── quickstart.md
│   └── authentication.md
├── api/
│   ├── overview.md
│   ├── chat-completions.md
│   ├── models.md
│   ├── images.md
│   └── embeddings.md
├── integrations/
│   ├── cherry-studio.md
│   ├── lobe-chat.md
│   └── others.md
├── faq.md
└── contact.md
```

## Customization

Edit `index.html` to customize:
- Theme colors
- Plugins
- Search settings
- Navigation options
