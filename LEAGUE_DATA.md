# League data

The homepage reads one JSON file for the selected week from each data folder. To
publish a new week, add `standings.json` to `LeagueStandings/Week N/` and
`fixtures.json` to `WeeklyFixtures/Week N/`, then update each folder's
`latest_week.txt` to `N`.

`standings.json` contains the overall league table. `winPercentage` is a number
from 0 to 100.

```json
{
  "week": 1,
  "standings": [
    {
      "rank": 1,
      "player": "Player name",
      "matchesPlayed": 2,
      "wins": 2,
      "losses": 0,
      "points": 6,
      "winPercentage": 100
    }
  ]
}
```

`fixtures.json` contains every match for the week. Use `null` for a result or
VOD that is not available yet. Add two fixtures for each player and avoid
repeating an opponent within the same week.

```json
{
  "week": 1,
  "fixtures": [
    {
      "matchNumber": 1,
      "player": "Player A",
      "opponent": "Player B",
      "scheduledAt": "2026-10-08T19:00:00Z",
      "result": null,
      "vodUrl": null
    }
  ]
}
```

Player profile names and image paths are maintained separately in
`Profiles/players.json`. Replace the temporary player labels with the roster
names and add each player's profile image path there.

## Articles

The article index is `Articles/index.html`. Add each article's Markdown file to
`Articles/content/` using its URL slug as the filename, then register its slug,
title, author, and preview excerpt in `Articles/articles.json`. For example,
the `rocks-matchup-guide` entry loads `Articles/content/rocks-matchup-guide.md`.
The article page renders Markdown headings with anchor links and includes a
generated contents list. Reference-style Markdown images are supported.
