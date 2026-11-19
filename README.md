# Paper Queue

A reading tracker: papers on priority shelves, plus an optional reading plan in order.

It is one static file, `index.html`. No build step.

## How data is stored

The page itself ships with an empty queue. Statuses, notes, order and added papers are saved in the browser, and, once sync is connected, in a `queue.json` file in a separate private GitHub repo, so every device shows the same queue.

To connect a browser:

1. Create a private repo (for example `paper-queue-data`) containing `queue.json`. The format is described at the top of the `<script>` in `index.html`.
2. Create a fine-grained token at https://github.com/settings/personal-access-tokens with access to only that repo and the "Contents: Read and write" permission.
3. Open the site, expand "Sync across devices", enter the repo and paste the token. This is needed once per browser.

Edits made on two devices, or offline, are merged the next time the page syncs.

## Run locally

```
python3 -m http.server 8000
```

then go to http://localhost:8000.

## Notes

- Shelves, plan slots, labels and the built-in paper list come from `config` and `seed` in `queue.json`.
- Paste-a-link lookup uses the arXiv API, then Semantic Scholar, and Crossref for DOIs.
