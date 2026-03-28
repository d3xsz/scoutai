
# ScoutAI ⚽🏀
### Real-Time Sports Analysis & Prediction Platform

> A single-file web app that fetches live match data from the Sofascore API, processes team statistics, and generates AI-assisted match predictions — built entirely with vanilla JavaScript, no frameworks.

**[Live Demo](https://github.com/d3xsz/scoutai)** | Built by [@d3xsz](https://github.com/d3xsz)

---

## What I Built & Why

I wanted to build something that combined real API integration with a practical use case. Sports analytics felt like the perfect challenge — it required handling async data fetching, processing raw statistics into meaningful predictions, and building a UI that updates dynamically without any framework.

The result is a fully functional sports intelligence dashboard that works in a single HTML file.

---

## Key Technical Achievements

- **7 Sofascore API endpoints** integrated with a centralized async handler and proper error management
- **Real-time match incidents** — clicking any live match fetches goals, cards, and substitutions on demand
- **Statistical prediction model** — custom weighted formula using win rates, goal averages, and head-to-head data to generate 5 bet types per match
- **localStorage persistence** — coupon builder and prediction history survive page refreshes
- **Dynamic DOM rendering** — no framework, all UI updates handled manually with efficient innerHTML patterns
- **Zero build step** — single HTML file, runs anywhere with a local server

---

## Features

| Feature | Description |
|---|---|
| Live Scores | Real-time football, basketball, tennis with incident details on click |
| Match Analysis | Fetch any two teams and get MS1/X/2, Over/Under, BTTS, HT/FT, Handicap predictions |
| Standings | Current 25/26 season tables for 5 major leagues |
| Player Search | Name search with position, team, and market value |
| Coupon Builder | Add predictions, track total odds, risk level, and confidence score |
| Prediction History | Save results, mark correct/wrong, see accuracy rate with chart |

---

## Tech Stack

```
Frontend  →  HTML5, CSS3 (custom properties, grid, flexbox), Vanilla JS (ES6+)
API       →  Sofascore via RapidAPI (REST, async/await, fetch)
Charts    →  Chart.js
Storage   →  localStorage
```

---

## What I Learned

- Working with third-party REST APIs — handling auth headers, rate limits, and malformed responses
- Building a prediction model from raw statistical data
- Managing state in a framework-less environment
- Debugging CORS issues and understanding browser security policies
- Iterative problem solving — the live incidents feature alone required 15+ debugging cycles to get right

---

## How to Run

```bash
git clone https://github.com/d3xsz/scoutai
cd scoutai
python -m http.server 8080
# Open: http://localhost:8080/scoutai.html
```

**Windows:** Double-click `BASLAT.bat` to start the server and open the browser automatically.

---

## API Endpoints Used

```
GET /search                      Team and player search
GET /teams/get-last-matches      Last 10 matches per team
GET /teams/get-next-matches      Upcoming fixtures
GET /tournaments/get-live-events Live match feed by sport
GET /tournaments/get-standings   League standings (season-specific IDs)
GET /matches/get-incidents       Goals, cards, substitutions per match
GET /categories/list-live        Active live sport categories
```

---

## Prediction Formula

```
teamScore = (wins x 3) + draws + (avgGoals x 2) - (avgConceded x 1.5)
winProbability = teamScore / (homeScore + awayScore)
```

Probabilities are then mapped to: Match Result, Over/Under 2.5, BTTS, HT/FT, and Handicap.

---

*MIT License*
