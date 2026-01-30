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
