# cryptocurrency_analysis
Pulls and visualizes cryptocurrency data from BraveNewCoin's Mashable API.

There are two versions of this notebook. One can interact with .ipynb version in Jupyter Notebook if they have the proper API key.

The other is a static .html version.

This notebook contains some functions for pulling data from BraveNewCoin's API on Mashable/Kong into a pandas. It uses the requests package to handle requests and visualizes the data with matplotlib.

I have omitted the API key due to Mashape's licensing. The user should please replace the string "MY_SUPER_SECRET_KEY" with thier own if they have access to this Mashape API. This will allow the user to see data and visualizations other than the ones I have included in the sample below.

The key functions are get_coins(), get_fiat(), get_twap() and plot_twap().

get_coins() and get_fiat() each return a dictionary of names and symbols so that the user can look up the symbols for coins (cryptocurrencies) and currencies (fiat) and determine if their data available in the API.

get_twap() returns a DataFrame with the Time Weighted Average Price (TWAP) for each coin in a list of coins and a currency. I've decided to focus on TWAP because I am interested in using the data in order to determine if coins have the properties that are expected in a currency according to economic and financial theory. (Visualizations suggest that they don't.) At a latter time, I plan to use changepoint analysis to see if there are periods of time where the coins are well behaved.

plot_twap() takes the data from get_twap() and generates some useful graphs given a currency pair and a date range. In order to avoid pulling the data more than once, plot_twap() uses the data already loaded by get_twap(). Data that hasn't been pulled by get_twap() won't be available to be visualized.

get_data() may also be of interest. It pulls and formats all of the data available from the API for a given coin and currency. get_twap() relies on get_data().
