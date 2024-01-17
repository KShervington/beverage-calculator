# Beverage Calculator

**Created by**: Kyle Shervington

|  |  |
|---|---|
| **Description** | A tool that allows users to calculate how many drinks will be needed for their event, based on event duration and number of guests. |
| **Client** | Twyst Cocktail |
| **Business Contact** | Najee Wooten |

| Constants | Description |
|---|---|
| `AVG_DRINKS_PER_HOUR` | Average amount of drinks a single guest will have each hour |
| `STD_WINE_PREF` | `simple` Decimal representation of the percentage of guests who prefer wine |
| `STD_BEER_PREF` | `simple` Decimal representation of the percentage of guests who prefer beer |
| `STD_SPIRIT_PREF` | `simple` Decimal representation of the percentage of guests who prefer cocktails |
| `STD_ALCFREE_PREF` | `simple` Decimal representation of the percentage of guests who prefer non-alcoholic drinks |
| `SPIRIT_SERVING_PER_BOTTLE` | # of servings from a single 750 mL spirit/liquor bottle |
| `WINE_SERVING_PER_BOTTLE` | # of servings from a single 750 mL wine bottle |
| `ALCFREE_SERVING_PER_BOTTLE` | # of servings from a single 2 L mixer bottle |

## Simple View

| Inputs | Description |
|---|---|
| `eventDurantion` | Length of event (in hours) |
| `guestCount` | # of guests that will attend the event |

| Outputs | Description |
|---|---|
| `numTotalDrinks` | Total # of drinks to be served at the event |
| `wineCount` | # of 750 mL bottles of wine needed |
| `beerCount` | # of 12 oz. cans of beer needed |
| `spiritCount` | # of 750 mL bottles of spirit/liquor needed |
| `alcFreeCount` | # of 2 L bottles of mixer (likely soda) needed |

### Output Calculations
```javascript
numTotalDrinks = Math.ceil(AVG_DRINKS_PER_HOUR * eventDuration) * guestCount;
```
```javascript
wineCount = Math.ceil(parseFloat(totalDrinks * STD_WINE_PREF) / WINE_SERVING_PER_BOTTLE);
```


## Advanced View

| Inputs | Description |
|---|---|
| `eventDurantion` | Length of event (in hours) |
| `guestCount` | # of guests that will attend the event |
| `advWineGuests` | # of guests that will drink wine |
| `advBeerGuests` | # of guests that will drink beer |
| `advSpiritGuests` | # of guests that will drink cocktails</br> _Assuming these guests will only drink cocktails instead of unmixed spirits/liquor_ |
| `advAlcFreeGuests` | # of guests that will drink alcohol-free beverages |

> Inputs prefixed with `adv` are calculated as a percentage of total `guestCount`. That is, the user will enter the percentage of guests who prefer each drink, and the "# of guests" for that drink type will be derived. ex. `guestCount = 20`, user enters 25% for "% of guests who prefere wine"; Therefore, `advWineGuests === 5`.

| Outputs | Description |
|---|---|
| `numTotalDrinks` | Total # of drinks to be served at the event |
| `wineCount` | # of 750 mL bottles of wine needed |
| `beerCount` | # of 12 oz. cans of beer needed |
| `spiritCount` | # of 750 mL bottles of spirit/liquor needed |
| `alcFreeCount` | # of 2 L bottles of mixer (likely soda) needed |

| Value | Formula |
|---|---|
| Total Drinks | 1.5 * total_drinks |
| Business Contact | Najee Wooten |

> ## Creator's Note:
> 
> This tool was integrated into the client's Squarespace website as a code block.
> That is reason all the styling, HTML, and Javascript are in one file.
> That being said, this drink calculator will still be fully functional when launched
> independently, though it will look different than it does on the client's website.
