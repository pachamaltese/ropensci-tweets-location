# How big is rOpenSci bubble?

### Terminology

    * followers: users that follow @ropensci on Twitter.
    
### What to find in this repository

Aggregated data:

    * summary of total followers and their countries + mentions (`summary-yyyy-mm-dd.csv`)
    * followers by country (`data/followers-country-yyyy-mm-dd.rda`)

    
Unaggregated data:

    * details of followers (`data/followers-info-yyyy-mm-dd.rda`)
    * geographic locations of followers (`data/coded-yyyy-mm-dd.rda`)
    
### Methodology

I followed Bob Rudis’s [21 recipes for Mining Twitter data with rtweet](https://rud.is/books/21-recipes/index.html)

    * number of followers on a given date is obtained after [`rtweet::get_followers()`](https://rud.is/books/21-recipes/harvesting-friends-and-followers.html)

    * geographic locations of followers was obtained after [rtweet & Google geocoding API function from the ggmaps package](https://rud.is/books/21-recipes/geocoding-locations-from-profiles-or-elsewhere.html)
    
    * the localization requiered me to create an application on [Google Maps Platform](https://cloud.google.com/maps-platform/), in order to generate a token associated to the app "rOpenSci tweets" (ask me on slack for the .Rprofile with the credentials)

### Downsides

    * Twitter's API does not allow obtaining followers on a date yyyy-mm-dd, it gives you a stock of followers at the time of running the API call
    
    * In order to compute the growth rate in the social network, you'll need to run the script `01-data-analysis.R` and use the files here to compare the number of followers on date T against followers on date T+t
    
    * The script `scripts/01-users-and-location-extraction.R` requires a `.Rprofile` file with the credentials to use a Google Maps app I had to create, ask me on Slack for the details.
