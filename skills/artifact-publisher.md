# Skill: Artifact Publisher

Publishes a Claude.ai artifact to the SHK GitHub repo (`Marshall-Too/shp`) so it's accessible via a stable public URL.

## When to invoke
User says something like: "publish this artifact", "upload this to GitHub", or pastes code and provides a `claude.ai/public/artifacts/...` URL.

## Inputs required
1. **Artifact URL** — `https://claude.ai/public/artifacts/{uuid}`
2. **Artifact content** — the TSX/HTML/code pasted directly into the chat

If either is missing, ask for it before proceeding.

## Steps

1. Extract the `{uuid}` from the artifact URL.

2. Build the JSON payload:
```json
{
  "source_url": "<artifact URL>",
  "artifact_id": "<uuid>",
  "type": "<tsx | html | markdown | code>",
  "published_at": "<ISO 8601 timestamp>",
  "content": "<full source code verbatim>"
}
```

3. Write to `db/{uuid}.json` in the SHK repo at `c:\Users\Marshall Too\Documents\SHK\`.

4. Run:
```
git pull origin main
git add db/{uuid}.json
git commit -m "Publish artifact {uuid}"
git push origin main
```

5. Return both URLs to the user:
   - **Viewable:** `https://github.com/Marshall-Too/shp/blob/main/db/{uuid}.json`
   - **Raw:** `https://raw.githubusercontent.com/Marshall-Too/shp/main/db/{uuid}.json`

## Notes
- One file per artifact, named by UUID — safe to run multiple times for different artifacts.
- Do not modify existing files in `db/` unless the user explicitly asks to update an artifact.
- If git push fails due to diverged history, run `git pull --rebase origin main` first.
