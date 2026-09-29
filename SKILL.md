---
name: dc-seasonal-produce
description: Know what produce is growing locally around Washington, DC right now (or in any month) and use it to plan, choose, and adjust recipes. Use this skill whenever the user asks what's in season, what's growing near them, what's at the farmers market, what to cook with local or seasonal produce, or wants a recipe rebuilt around seasonal ingredients. Also use it alongside healthify-recipe-vegetarian: when healthifying or making a recipe vegetarian, check its produce against the DC season and suggest local swaps for out-of-season ingredients, even if the user doesn't say "seasonal" or "local".
---

# DC Seasonal Produce

Help the user cook with what's actually growing near Washington, DC. The data comes from the DC Farm to School seasonality chart and lives in `references/dc-seasonality.md`: a month-by-month table, each month's "Farm-Fresh Feature" (the crop at its peak), a storage-crop list for Dec-Feb, and swap families for finding a local stand-in.

The user cares about eating well and cooking vegetarian, so seasonality is a nudge toward fresher, better-tasting produce, not a rule. A tomato salad in January is the user's call. Suggest, explain briefly, and let them decide.

## First: pin down the month

Use today's date from context. If the user names a month or says they're planning ahead, use that instead. Read the row for that month plus the adjacent months in `references/dc-seasonality.md`; crops right at the edge of their range are usually still fine at a farmers market. Also read the cross-check and supplemental sections there: they widen a few windows (early corn, summer potatoes, fall spinach) and add crops the DC chart omits, like onions, garlic, collards, Brussels sprouts and edamame.

## Modes

### A. "What's in season?" / meal ideas

Give the month's feature first, then a short grouped list (vegetables, fruit, greens/roots) of what else is growing. Keep it to what's useful: a handful of standout items, not a dump of the whole row. If asked what to cook, offer 3-5 vegetarian ideas built around those ingredients, and offer to search their Deglaze library (`search_recipes`) for matching saved recipes. In Dec-Feb say plainly that nothing is growing and give the storage crops instead.

### B. Checking a recipe (alongside healthify-recipe-vegetarian)

When healthify-recipe-vegetarian is running, do this after it has picked its healthy/vegetarian substitutions (its "Choose substitutions" step) so your seasonal swaps are folded into the same swaps table and the same saved recipe, rather than presented as a second, separate rewrite.

1. Go through the recipe's produce, including any produce you're adding as a meat replacement (mushrooms and lentils aren't on the chart, so don't flag them; jackfruit and other imports aren't local either, and that's fine when the dish needs them).
2. Sort each item as **in season**, **stored** (Dec-Feb crops, or fall crops in early winter), or **out of season**. Skip citrus, canned goods and other non-local staples rather than calling them out-of-season. Onions, garlic and herbs are local for much of the year (see the supplemental table), so only mention them in the rare case that one is clearly out of window.
3. For each out-of-season item, find a stand-in from the swap families that matches the *role* in the dish (texture, cooking method, flavor weight) and is in season. If nothing fits well, say so and leave it alone. A forced swap that changes the dish isn't worth it.
4. Sort the swaps the same way healthify does: **apply directly** when it's a close match in a supporting role (zucchini for yellow squash, kale for chard, one root for another), and **ask first** when it changes the dish's character (eggplant for the star of a zucchini boat, or swapping the main vegetable). Offer 2-3 options with a one-line tradeoff for the "ask first" ones.
5. Adjust the method for the new ingredient. Different produce has different water content and cook times: eggplant and zucchini release water, winter squash needs longer roasting, tender greens wilt in a minute. Update quantities, temperatures and steps the same way healthify does.
6. Don't let a seasonal swap undo a health or vegetarian goal (don't replace a bean with a starchy vegetable and lose the protein, for instance). Healthify's goals win ties.

Present the result as extra rows in healthify's swaps table (original, replacement, why: "in season in DC this month"), plus a line on what to look for at the market. When healthify saves the recipe, add a short seasonal note to `notes`, e.g. "Best Jun-Sep, when DC zucchini and tomatoes are in season. Swap for winter squash in fall." That keeps the recipe self-explanatory later and tells the user when to cook it.

If the user only asked "is this recipe seasonal?" without wanting changes, report the sort from step 2 and offer swaps instead of applying them.

### C. Planning around a specific ingredient or occasion

If the user has a produce item in hand ("I got a bag of okra") or wants a dish for a season, tell them where it falls in its season (early, peak, late) and what it pairs well with from the same months, since crops that grow together tend to cook well together.

## Honesty about the data

- The main chart is from 2013 and shows about 35 crops; the supplemental list comes from Virginia, Maryland and FRESHFARM guides, so say "regional guides show..." for those. Weather, farm practices and what a given market stocks vary, so phrase things as "the chart shows..." or "typically in season", not as guarantees.
- Say when an item isn't on the chart rather than guessing it's out of season.
- Don't invent availability, prices or specific farms. If the user wants to know what's at a particular market this week, tell them to check the market's vendor list or site, or offer to look it up.
