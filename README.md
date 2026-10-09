# Management Research Studies

Study board for the FSU Department of Management student research participant pool.

Students open the site, see which credit window is open, and follow each study's survey link. Credit is collected on a separate credit form, so this site stores no student information.

## Updating studies

Edit `studies.json`. Each study looks like this:

```json
{
  "id": "s1",
  "title": "Reactions to coworker requests",
  "researcher": "Lee Lab",
  "minutes": 30,
  "window": "1",
  "status": "open",
  "url": "https://fsu.qualtrics.com/jfe/form/...",
  "about": "Read short workplace scenarios and answer questions.",
  "eligibility": "Open to all students 18 and older.",
  "irb": "STUDY00001234"
}
```

- `window`: `"1"` (Jan 19 – Mar 5) or `"2"` (Mar 22 – Apr 16)
- `status`: `"open"`, `"full"` or `"closed"`
- Also set `coordinator`, `email` and `creditUrl` (the backup credit form) at the top of the file.
