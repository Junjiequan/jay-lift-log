# Workout Program

A single-file lifting and running tracker. No build step, no server, no account.
Open index.html in a browser and it works.

## What it does

- Weekly plan, Monday to Sunday, lifting days and run days
- Weights calculated from your squat, bench, deadlift and overhead press 1RMs
- Plate breakdown per side for barbell lifts
- Tap each set: done, missed, clear. A missed set sets next week to Stall
- Increase / Stall / Fall back per exercise, applied when you tap Finish week
- Week 5 deload, then a prompt to retest and start a new block
- Add, edit and delete exercises, change sets, reps, percentages and increments

## Your data

Everything is stored in the browser's localStorage on the device you use.
Nothing is uploaded. Clearing site data in the browser deletes it, so take a
backup now and then with Setup > Export.

## Importing a programme

Setup > Import accepts two kinds of JSON file:

- **A backup** exported from the app. Restores everything, logs included.
- **A template** like the ones in this repo. Loads the exercises and starting
  weights, leaves the logs empty.

Two templates are included:

| File | What it is |
|---|---|
| template.json | The programme as written, built off squat 190, bench 140, deadlift 200, OHP 100 |
| template-blank.json | Same exercises with beginner 1RMs, for someone starting from scratch |

Import a template, then go to Setup and put in your own 1RMs. The main lifts,
close grip bench and Romanian deadlift recalculate from those. Accessories use
fixed starting weights, so calibrate them in week 1 to hit the listed reps at
about RPE 8 and edit them from there.

## Making your own template

Set the app up the way you want, tap Setup > Export, then delete the `log`,
`history` and `runLog` contents from the file so other people start clean:

```json
"log": {}, "history": {}, "runLog": {}
```

## Hosting it

Any static host works. GitHub Pages:

    Settings > Pages > Source: main branch, root

Cloudflare Pages: drag the folder into the dashboard, no repo needed.

Serve it over HTTPS if you want "Add to Home screen" on Android to behave like
an app. localStorage is tied to the domain, so stay on one host once you start
logging.
