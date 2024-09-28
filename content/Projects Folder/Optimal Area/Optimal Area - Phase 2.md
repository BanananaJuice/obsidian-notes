## Objective
The objective of this section is to obtain the necessary data to determine the quality of life and duration travelling to work from each postal code

## Summary of Work

### Duration Travelling
The duration travelling was calculated from the central point of each postal code to the work destination, in this case being EY. Using the Google Maps distance matrix API in python, I managed to pull the average number of seconds it would take to travel from each location to work at 7:30am during a weekday.

### Quality of Life Index
The quality of life index was an interesting problem to tackle. 
Unlike the UK, South Africa does not make available any extremely granular quality of life index per postal code. 
This prompted me to find out a way to calculate the quality of life by myself.

Quality of Life Index is calculated using literacy rates, infant mortality, and life expectancy.
This was a good starting point for my calculations, however I felt that none of these measures truly expressed the quality of life I was looking calculate. 

I then went over to Statsa to look at the data I could obtain on the most granular level possible. This ended up being the ward level census that took place in 2011. This turned out to be a treasure trove of data which is publicly available at the following link [https://superweb.statssa.gov.za/webapi/jsf/dataCatalogueExplorer.xhtml]

Ultimately, I chose to use access to water, access to plumbed ablution, and median income as the factors contributing to my quality of life index calculations.

After web scraping the mapping of postal codes to wards data from the municipal website I had finally finished assigning each data point to it's postal code. Finally, a quality of life index was calculated.

