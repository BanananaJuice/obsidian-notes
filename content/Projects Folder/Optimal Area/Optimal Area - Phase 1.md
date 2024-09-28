## Objective
The objective of this phase was to create a list of all the suburbs with a specific radius around the users inputted work co-ordinates.

## Summary of work
In order to classify suburbs, I used postal codes as a differentiating factor. Each postal code would indicate a specific suburb which would be used in [[Optimal Area - Phase 2]] to calculate the commute distance and quality of life

Using the geopy and geonames api's I managed to return a JSON of all postal codes within a radius of the inputted work address.

Once I obtained the postal codes, I then used the google maps API to obtain the co-ordinates from centre point of all postal codes. All this information is then stored in a dataframe for ease of working