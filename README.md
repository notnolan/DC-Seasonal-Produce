# DC Seasonal Produce

A [Claude](https://claude.com) skill that knows what produce is growing locally around Washington, DC, and uses it to plan meals and adjust recipes.

- Answers "what's in season?" for any month, with each month's peak crop.
- Pairs with a recipe-healthifying skill: checks a recipe's produce against the local season and suggests in-season swaps that match the ingredient's role in the dish.
- Falls back to storage crops in Dec-Feb, when nothing is growing.

## Install

```bash
git clone https://github.com/notnolan/DC-Seasonal-Produce ~/.claude/skills/dc-seasonal-produce
```

## Data

The month-by-month table was read from the DC Farm to School / DC Greens / OSSE "What's Growing Around Here?" seasonality chart (2013), which is image-only. It is cross-checked against the Virginia Grown availability calendar, the Maryland's Best seasonality chart and FRESHFARM's Mid-Atlantic guide, with a supplemental list of crops the DC chart omits. See [`references/dc-seasonality.md`](references/dc-seasonality.md). Growing seasons vary with weather, so treat results as typical, not guaranteed.
