# ScoutAI ⚽🏀

**AI-powered sports match analysis & prediction platform**

ScoutAI is a real-time sports intelligence web app that uses the Sofascore API to deliver live match data, standings, player stats, and AI-generated match predictions — all in a single HTML file with zero dependencies or build steps.

---

## Features

- **Live Match Scores** — Real-time football, basketball, and tennis scores with goal/card/substitution incidents on click
- **Match Analysis & Predictions** — Enter two team names, ScoutAI fetches their last 10 matches and generates predictions for: Match Result (1/X/2), Over/Under 2.5, Both Teams Score, HT/FT, and Handicap
- **League Standings** — Current 25/26 season tables for Super Lig, Premier League, La Liga, Bundesliga, and Serie A
- **Player Search** — Search any player by name to see position, team, and market value
- **Coupon Builder** — Add predictions to a coupon, track total odds, risk level, and confidence score
- **Prediction History** — Save predictions and mark them as correct/incorrect to track your accuracy rate over time

---

## Tech Stack

| Technology | Usage |
|---|---|
| **Sofascore API** (via RapidAPI) | Live scores, match data, team stats, standings, player info |
| **Chart.js** | Goal form charts, prediction accuracy graphs |
| **Vanilla JS** | All logic — async/await, localStorage, DOM manipulation |
| **CSS Variables** | Full dark theme with dynamic theming |
| **HTML5** | Single-file app, no framework, no build step |

---

## How to Run

Since this app makes API requests, it needs to be served over HTTP (not opened as a `file://` URL).

**Option 1 — Python (recommended):**
```bash
cd path/to/scoutai
python -m http.server 8080
# Open http://localhost:8080/scoutai.html
```

**Option 2 — Use the included batch file (Windows):**
```
Double-click BASLAT.bat
```

---

## API Integration

ScoutAI integrates with the **Sofascore API** on RapidAPI. The following endpoints are used:

- `GET /search` — Team and player search
- `GET /teams/get-last-matches` — Last 10 matches per team
- `GET /teams/get-next-matches` — Upcoming fixtures
- `GET /tournaments/get-live-events` — Live match feed by sport
- `GET /tournaments/get-standings` — League table with 25/26 season IDs
- `GET /matches/get-incidents` — Goals, cards, and substitutions per match
- `GET /categories/list-live` — Active live categories

All API calls are handled via `async/await` with a centralized `api()` function for clean error handling.

---

## Prediction Model

The prediction engine uses a weighted scoring formula based on real match data:

```
Team Score = (Wins × 3) + Draws + (Avg Goals × 2) − (Avg Conceded × 1.5)
```

Win probability is derived from relative team scores, then mapped to:
- Match result (1/X/2)
- Over/Under threshold (based on combined average goals)
- Both Teams Score (based on individual attack strength)
- HT/FT (derived from win probability)
- Handicap (based on score differential)

---

## Screenshots

> Live scores, match incidents, standings, and coupon builder — all in one dark-themed interface.

---

## License

MIT — free to use, modify, and distribute.

---

*Built with Sofascore API + RapidAPI | Designed for sports analytics portfolios*
