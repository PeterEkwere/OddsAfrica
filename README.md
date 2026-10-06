# OddsAfrica

OddsAfrica collects live odds from the major African bookmakers and looks for arbitrage across them.

The idea is simple. Different books price the same match differently. When the gap is big enough you can back every outcome across a few books and come out ahead no matter who wins. That is an arbitrage, or a sure bet. OddsAfrica pulls odds from many books at once, lines them up by game and market, and points out those spots.

Written in Python.

## What it does

- Pulls odds from the major African books into one consistent format.
- Covers football, basketball, volleyball, darts and ice hockey.
- Finds arbitrage across books for the same game, and works out the stake split and the profit in `utils/calculate_arb`.
- Has a small API (`api/views`) with signup and login so a client can read the odds and the arbs.
- Logs each book on its own, so one book failing does not stop the rest of the run.

## Books it reads

Each book has its own scraper under `engine/bookie_models/`:

Bet9ja, BetKing, LiveScoreBet, MerryBet, NairaBet, Paripesa, SportyBet, 1xBet, bet22, Betpawa, Betwinner.

You can turn books and sports on or off per run in `run.py`.

## How it is laid out

| Part | Where |
|------|-------|
| Bookmaker scrapers | `engine/bookie_models/` |
| Arbitrage maths | `utils/calculate_arb.py` |
| API and auth | `api/views/` (signup, login, arbs) |
| Runner | `run.py` |
| Config | `config/config.py` |

## Running it

```bash
git clone https://github.com/PeterEkwere/OddsAfrica.git
cd OddsAfrica
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp config/config.example.py config/config.py   # set your own values
python run.py
```

Built and tested on Python 3.11.

## Where it is going

This is the first version. The plan is to cover more markets in each game and more books, and to put a cleaner public API over the engine.

## A note on use

OddsAfrica reads odds that the books already show in public, for research and comparison. Scraping and automated access can be against a book's terms, and betting rules change from place to place, so check both before pointing it at live sites or betting real money. This is for learning and research, not betting or financial advice.

## Author

Peter Udeme Ekwere. [GitHub](https://github.com/PeterEkwere), [LinkedIn](https://www.linkedin.com/in/peter-ekwere-9929ba257).

## License

See [`LICENSE`](LICENSE).
