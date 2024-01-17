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

Variable values for following examples
```javascript
const STD_WINE_PREF = 0.35;
const STD_BEER_PREF = 0.2;
const STD_SPIRIT_PREF = 0.35;
const STD_ALCFREE_PREF = 0.1;

const SPIRIT_SERVING_PER_BOTTLE = 16.0;
const WINE_SERVING_PER_BOTTLE = 5.0;
const ALCFREE_SERVING_PER_BOTTLE = 8.0;

let totalDrinks = 100;
```

```javascript
numTotalDrinks = Math.ceil(AVG_DRINKS_PER_HOUR * eventDuration) * guestCount;
```

```javascript
wineCount = Math.ceil(parseFloat(totalDrinks * STD_WINE_PREF) / WINE_SERVING_PER_BOTTLE);

// ex.
// wineCount = (100 * 0.35) / 5
// wineCount = 7
```

```javascript
beerCount = Math.ceil(parseFloat(totalDrinks * STD_BEER_PREF));

// ex.
// beerCount = 100 * 0.2
// beerCount = 20
```

```javascript
spiritCount = Math.ceil(parseFloat(totalDrinks * STD_SPIRIT_PREF) / SPIRIT_SERVING_PER_BOTTLE);

// ex.
// spiritCount = (100 * 0.35) / 16
// spiritCount = 2.1875
// spiritCount = 3 --Rounded up
```

```javascript
bottlesOfSpirit = Math.ceil(parseFloat(totalDrinks * STD_SPIRIT_PREF) / SPIRIT_SERVING_PER_BOTTLE);

// Calculate # of bottles to be used as mixers, assuming 1:3 (spirit:mixer) ratio for cocktails
// ** 750 mL per spirit bottle; 2000 mL per mixer bottle **
mixerBottles = Math.ceil(((bottlesOfSpirit * 750.0) * 3.0) / 2000.0);

alcFreeCount = Math.ceil((parseFloat(totalDrinks * STD_ALCFREE_PREF) / ALCFREE_SERVING_PER_BOTTLE)) + mixerBottles;

// ex.
// bottlesOfSpirit = (100 * 0.35) / 16
// bottlesOfSpirit = 2.1875
// bottlesOfSpirit = 3 --Rounded up

// mixerBottles = ((3 * 750) * 3) / 2000
// mixerBottles = (2250 * 3) / 2000
// mixerBottles = 3.375
// mixerBottles = 4 --Rounded up

// alcFreeCount = ((100 * 0.1) / 8) + 4
// alcFreeCount = (10 / 8) + 4
// alcFreeCount = 1.25 + 4
// alcFreeCount = 2 + 4 --Rounded up
// alcFreeCount = 6
```
> Alcohol-free drinks have to be used for both cocktails and for guests who will only drink alcohol-free beverages. Hence the above calculations.

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
