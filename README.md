# Management Research Studies

Study board for the FSU Department of Management student research participant pool.

Students open the site, see which credit window is open, and follow each study's survey link. Credit is collected on a separate credit form, so this site stores no student information.

## Updating studies

Edit `studies.json`. Each study looks like this:

```json
{
  "id": "s1",
  "number": 1,
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
- `number`: the study number used in completion IDs (`27W1S1J30_140040` is window 1, study 1)
- Also set `coordinator`, `email`, `creditUrl` (the Qualtrics credit form), `signupUrl` (the Qualtrics pool sign-up, shown as "Join the pool") and `checkinUrl` (the Pool ID check-in survey) at the top of the file.

## How a study run works

1. **Join the pool.** The sign-up survey gives the student a Pool ID (for example `27JAN10_130042`). A Qualtrics workflow adds that Pool ID to the "Research Pool Spring 2027" contact list.
2. **Check in.** "Start study" opens the check-in survey with `?next=<study link>`. It only lets the student through if their Pool ID is on the contact list, then sends them to the study with `?pid=<Pool ID>`.
3. **Take the study.** Each study survey needs, in Survey flow:
   - an Embedded Data field `pid` at the top,
   - a Branch "if `pid` Is Empty" → End of Survey that redirects to the study board, so students can't skip check-in,
   - an end-of-survey redirect to the credit form:
     `https://fsu.qualtrics.com/jfe/form/SV_dp9TqKpojzTaSKG?study=<Title>&sn=<number>&w=<window>&pid=${e://Field/pid}`
4. **Claim credit.** The credit form fills in the study title and Pool ID, and on submit shows a completion ID such as `27W1S1J30_140040` (year, window, study number, month initial, day, time in Tallahassee).
