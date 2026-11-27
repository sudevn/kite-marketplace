# Kite marketplace

A marketplace is just an `index.json` file you can host anywhere over https
(this folder on GitHub works). Point Kite at it in **Settings → General →
Marketplace index**.

```json
{
  "name": "My marketplace",
  "items": [
    { "id": "meeting-notes", "kind": "skill", "name": "Meeting notes", "description": "…", "url": "skills/meeting-notes.md" },
    { "id": "focus-timer", "kind": "app", "name": "Focus timer", "description": "…", "url": "apps/focus-timer.html" }
  ]
}
```

- `id`: letters, digits and dashes. It becomes the installed skill or app's id.
- `kind`: `skill` (a Markdown file with `name`/`description` front matter) or
  `app` (one self-contained HTML file).
- `url`: absolute, or relative to the index file.

Mini apps run in a sandbox with no access to Kite or your files, and can only
reach the network over https. To keep data, they use
`await kite.storage.get(key)`, `await kite.storage.set(key, value)` and
`await kite.storage.all()`.
