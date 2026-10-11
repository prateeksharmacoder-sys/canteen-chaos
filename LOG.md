# Debug log

Your notes. One entry per bug you fixed, using the template below.

This file is read as carefully as your code. A correct fix you cannot
explain counts for little; a bug you could not fix but investigated
honestly still counts for something.


### CC-01 : "The search suggestions are behind everything"

**Reproduced:** Started typing a dish name("bread") in the search bar. The list of suggestions appeared, but some suggestions are hidden behind the menu category navigation bar. first suggestion and second partially part was not clickable.
![alt text](<cc-1-bug.png>)

**Cause:** The search suggestions dropdown (.cat-tabs) had an incorrect stacking order (z-index =40 ), causing other page elements to appear in front of it.this prevented clicks from reaching the suggestions.

**Fix:** Corrected stacking order (z-index = 0) so that it appears above the page content. Checked the parent containers for overflow restrictions and ensured that no overlapping elements block clicks on the suggestions.

**Checked:** All search suggestions are visible and clickable. Selecting a dish works correctly, and the dropdown displays above other page elements without being cut off.

**Time:** About 10 minutes, most of it spent identifying which element (css class- name from inspect) was covering the dropdown and why clicks were not reaching the suggestions.

### CC-02 : "Can't read anything in dark mode"

**Reproduced:** Switched the website to dark mode. Dish names and prices became almost invisible against the dark background, while the grey line underneath the dish name remained visible. 
![alt text](cc-2-bug.png)

**Cause:** The dark mode styles were not applying the correct text colors to dish names and prices. Some elements may have been using hardcoded dark text colors that blended into the dark background.

**Fix:** Removed conflicting hardcoded colors (.dish-body { color:#2b2118;}) and ensured all dish details follow the active theme.

**Checked:** Dish names, prices and descriptions are clearly readable in both light and dark modes. and the text colors are applied correctly when switching themes and opening the website.

**Time:** About 20 minutes, most of it spent tracking down conflicting text colors and checking which styles were overriding the dark mode theme.







Delete the example before you submit.



## Example — delete this

### CC-99 — "The cart total is wrong"

**Reproduced:** Added 2 dosas at Rs. 60 each. The cart showed
Rs. 119.99999 instead of Rs. 130. Happened every time, on any dish with
a price ending in .50.

**Cause:** The total was being added up with plain floating point and
never rounded, so 0.1 + 0.2 style errors showed up on screen. The
rounding helper existed but this one place was not using it.

**Fix:** Ran the total through the existing rounding helper instead of
adding a new one, so every price on screen goes through the same path.

**Checked:** Cart, checkout and the order screen all show Rs. 130 now.
Prices without decimals still show without a trailing .00.

**Time:** about 40 minutes, most of it working out that the cart and the
order screen round in different places.



## CC-0X — "<the complaint, in short>"

**Reproduced:**

**Cause:**

**Fix:**

**Checked:**

**Time:**



## Could not fix

For anything you investigated but did not solve. Say what you tried and
where you got to. This is worth marks — leaving it blank when you got
stuck is not.

### CC-0X — "<the complaint>"

**What I tried:**

**Where I got to:**

**What I would try next:**



## Extra credit

Anything not on the bug log: a problem you found yourself, a test you
wrote, or a fix you are unsure about. Same format, plus one line on how
you noticed it.
