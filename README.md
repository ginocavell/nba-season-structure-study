# Can the NBA make regular-season games matter more?

A season-length and scheduling study. I used five seasons of real NBA games to test whether a shorter or restructured season makes late-season games more meaningful, and what each option would cost the owners.

**Short answer:** cutting the season to 72 games did not make late-season races tighter. Keeping 82 games and ending the season with four games against teams near each other in the standings did, and it costs about a twentieth as much.

## Links

- **Written study:** [read the study](https://ginocavell.github.io/nba-season-structure-study/study.html)
- **Interactive simulator:** [open the simulator](https://ginocavell.github.io/nba-season-structure-study/)
- **Spreadsheet (data cleaning and revenue model):** [open the spreadsheet](https://docs.google.com/spreadsheets/d/1uEqaG4EatwY6mdqnjOoze7Ijbbew5FxRzjO0ZsuPntY/edit?usp=sharing)
- **Simulation code:** `nba_season_study.ipynb` in this repository

## What I found

I measured "seed-race games": games in the last third of the season between two teams in the same conference who are within 1 game of each other in the standings. All results come from a simulation calibrated on the five real seasons.

| Schedule | Seed-race share, last third | Owners' net cost per team per year (low to high) |
| --- | --- | --- |
| A: current 82 games | 4.3% | $0 |
| B: 72 games | 2.8% to 5.0% (random cut) | $10.7M ($2.0M to $19.4M) |
| C: 78 games plus 4 standings-matched games at the end | 6.8% | $0.5M ($0.13M to $1.5M) |

1. **A shorter season does not help.** My pre-set prediction of a 5-point gain was wrong.
2. **Ending the season with a block of conference games helps only a little.** A block of 10 moved the share from 4.2% to 4.8%, because it picks the opponent's conference but not how close the teams are.
3. **Matching opponents by standings works.** Four matched games raised the share to 6.8%. Anything from 2 to 8 matched games lands within the simulation's noise of that.
4. **I could not test whether closer races earn more money.** That is the weak link in the whole case.

## How it works

- **Data:** every regular-season game from 2021-22 through 2025-26 (1,230 games per season), cleaned in Google Sheets and re-checked in Python.
- **Simulation:** each team's strength is its average point margin. The model adds a home edge of about 2 points and game-to-game randomness of about 13.5 points, then replays the real schedule with random results.
- **Calibration:** simulated win-total spread was 13.95 against 13.84 real. The simulation runs about 18% low on seed-race share, so I compare schedules to each other rather than treating any number as a forecast.
- **Revenue model:** a line-by-line bridge from the league's projected $14.3 billion in revenue, built on public estimates and clearly labeled assumptions.

## Reproduce it

1. Get the game results for each season from [Basketball Reference](https://www.basketball-reference.com/). I do not include the raw game data in this repository, so please get it from the source.
2. Clean each season as described in the written study, and save one CSV per season (`s2022.csv` through `s2026.csv`).
3. Open `nba_season_study.ipynb` in [Google Colab](https://colab.research.google.com/), upload the five CSV files, and run the cells from the top.

## Files

- `README.md`: this file
- `index.html`: the interactive simulator (a single self-contained page)
- `nba_season_study.ipynb`: the Python simulation

## Limits

- Closeness of races is a proxy for how much a game matters. Stars, rivalries and storylines are not measured.
- The NBA Cup's value to the league is not public, so I used placeholders of $25M, $50M and $100M.
- Revenue figures are estimates, because team revenue is not public.
- The simulation does not model rest, travel or injuries, and it uses the real schedule for each season.
- Matching by standings gives top seeds a harder finish than bottom seeds.

## Next steps

- Test whether star availability changes how tight races are.
- Add tanking, Cup stakes and repeat-matchup fatigue.
- Check my closeness measure against national viewership data.

Built by Gino, finance major at Ohio State University. [add your full name and a contact link]
