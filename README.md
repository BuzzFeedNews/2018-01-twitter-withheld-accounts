# Analysis of Country-"Withheld" Twitter Accounts

This repository contains data and analysis supporting the BuzzFeed News article, "[An Inside Look At The Accounts Twitter Has Censored In Countries Around The World](https://www.buzzfeed.com/craigsilverman/country-withheld-twitter-accounts)," published January 24, 2018. That article contains important contextual and methodological details. Please read it before continuing below.

# Data

This repository contains the following three datasets:

- [`data/withheld-accounts.csv`](data/withheld-accounts.csv): This file contains metadata on all of the Twitter accounts BuzzFeed News observed being withheld in at least one country. You can find a more detailed description of the columns below. Unless noted otherwise, all data came directly from Twitter's API. Countries in which an account is withheld are [explicitly indicated in Twitter's API](https://blog.twitter.com/developer/en_us/a/2012/new-withheld-content-fields-api-responses.html).

- [`data/first-observations.csv`](data/first-observations.csv): This file indicates the first date on which BuzzFeed News noticed that a particular account was being withheld in a particular country. To be clear: These dates do __not__ not correspond to the dates on which Twitter began withholding that account in that country. All this file affirmatively says is that the account was first withheld *on this date or earlier*.

- [`data/twitter-transparency-reports/*.csv`](data/twitter-transparency-reports): These tables come directly from [Twitter's semiannual transparency reports](https://transparency.twitter.com/), specifically their [reports on "removal requests"](https://transparency.twitter.com/en/removal-requests.html).

## Fields in the `withheld-accounts.csv` file

| Field name              | Description    |
|-------------------------|----------------|
| `user_id_numfix`        | This is a copy of the `user_id` field, but prefixed with an `'` so that it is not converted into scientific notation by spreadsheet programs. |
| `user_id`               | This is the account's Twitter-assigned identification number. |
| `screen_name`           | This is the account's screen name, e.g., `@screenname`. |
| `bio`                   | This is the most recent profile bio that BuzzFeed News observed for this account. |
| `withheld_category`     | This the account's most recent status, with regards to withholding, as categorized by BuzzFeed News in its most recent data collection. See below for possible values. |
| `withheld_in_countries` | This is a ` + `-separated list of two-letter abbreviations corresponding to the countries in which BuzzFeed News observed this account being withheld in its most recent data collection. |
| `withheld_ever`         | This is a list similar to `withheld_in_countries`, except for *every country* in which BuzzFeed News has observed this account being withheld at any point. |
| `followers_count`       | This is the number of followers that this account had at the time of the most recent data collection. |
| `following_count`       | This is the number of accounts this account followed at the time of the most recent data collection. |
| `signup_date`           | This is the date on which the account was created. |
| `first_observed`        | This is the date on which BuzzFeed News first observed this account being withheld. See above for important caveats about this date. |

### `withheld_category` values in `withheld-accounts.csv`

The `withheld_category` field in the `withheld-accounts.csv` file can be one of the following four values:

- `withheld`: As of the most recent data collection, this account was still withheld in at least one country.
- `not_withheld`: As of the most recent data collection, this account was no longer being withheld in any country.
- `media_violation`: This account was previously withheld in one or more countries but, as of the most recent data collection, was "temporarily unavailable" globally for violating Twitter's Media Policy.
- `inactive`: This account was previously withheld in one or more countries but, as of the most recent data collection, was no longer accessible on Twitter — because, for example, the account has been suspended or the account's creator has deleted it.

# Analysis

This repository contains two analysis notebooks, both written in Python:

- [`notebooks/analyze-withheld-accounts.ipynb`](notebooks/analyze-withheld-accounts.ipynb), which focuses on the data collected from Twitter's API.
- [`notebooks/analyze-twitter-transparency-reports.ipynb`](notebooks/analyze-twitter-transparency-reports.ipynb), which focuses on the data collected from Twitter's transparency reports.

# Reproducibility

To reproduce the calculations, you'll need to do the following:

- Ensure that you have installed [Python](https://www.python.org/) and the Python libraries listed in [`requirements.txt`](requirements.txt).
- Re-run each of the Jupyter notebooks in the [`notebooks/`](notebooks/) directory. (Shortcut: run `make reproduce`; requires Python 3.)

# Feedback / Questions?

Contact Jeremy Singer-Vine at [jeremy.singer-vine@buzzfeed.com](jeremy.singer-vine@buzzfeed.com).

Looking for more from BuzzFeed News? [Click here for a list of our open-sourced projects, data, and code](https://github.com/BuzzFeedNews/everything).
