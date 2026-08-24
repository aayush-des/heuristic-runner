# Heuristic Evaluation Runner

A single-page tool for running a usability review of one screen against
[Nielsen's 10 usability heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/),
rating each finding on Nielsen's 0–4 severity scale, and printing the result
as a report.

Built by a product designer learning to build things.

## Using it

**[→ Open the tool](https://aayush-des.github.io/heuristic-runner/?v=4)**

1. Name the screen you're reviewing and, optionally, the task the user is trying to complete.
2. Drop, paste, or pick a screenshot. It pins to the side and stays there while you scroll.
3. Work down the ten heuristics, adding findings where you see problems.
4. Rate each finding 0–4. Severity is what makes the report actionable rather than a list.
5. Generate the report and print it, or save it as a PDF.

Skipping the screenshot is fine — the layout returns to a single column and everything still works.

### Severity scale

| | Meaning |
|---|---|
| 0 | Not a usability problem |
| 1 | Cosmetic — fix if there's spare time |
| 2 | Minor — low priority |
| 3 | Major — important to fix |
| 4 | Usability catastrophe — imperative to fix before release |

## How it works

One file. No build step, no dependencies, no server, no accounts.
Download `index.html`, double-click it, and it runs.

Everything the app knows lives in a single `state` object. Every click changes
`state` and then redraws the page from it:

```
click → change state → render() → screen matches state
```

That's the whole architecture. The code is commented throughout for anyone
learning to read it.

**Your screenshots never leave your browser.** There's no server and nothing is
uploaded anywhere — the image is held in memory and drawn straight onto the
page. That's also why closing the tab loses your work.

## Known limitations

- **No saving yet.** Refreshing the page clears your findings. Do an evaluation
  in one sitting and print to PDF at the end — the PDF is the saved copy.
- **One screen per evaluation.** Reviewing a flow means running it once per screen.
- **No annotation.** You can't drop numbered pins on the screenshot and link them
  to findings.

## Roadmap

- [ ] Save an evaluation and reopen it later
- [ ] Numbered pins on the screenshot, linked to findings
- [ ] Multiple screens in one audit
- [ ] Editable heuristics, so teams can add their own

## Credits

The ten heuristics are Jakob Nielsen's, first published in 1994 and refined since.
The severity scale is his too. This tool is just a place to apply them.
