# GTFS Schedule Data Dictionary
This dictionary provides the meaning of the following 11 `.txt` files, depending on the year of the data:
1. `agency.txt` - Transit agencies with service represented in this dataset.
2. `calendar_dates.txt` - Exceptions for the services defined in the `calendar.txt`.
3. `calendar.txt` - Service dates specified using a weekly schedule with start and end dates.
4. `feed_info.txt` - Dataset metadata, including publisher, version, and expiration information.
5. `routes.txt` - Transit routes. A route is a group of trips that are displayed to riders as a single service.
6. `shapes.txt` - Rules for mapping vehicle travel paths, sometimes referred to as route alignments.  
7. `stop_times.txt` - Times that a vehicle arrives at and departs from stops for each trip.  
8. `stops.txt` - Stops where vehicles pick up or drop off riders. Also defines stations and station entrances.
9. `trips.txt` - Trips for each route. A trip is a sequence of two or more stops within a specific time period.    
10. `fare_attributes.txt` - Fare information for a transit agency's routes.
11. `fare_rules.txt` - Rules to apply fares for itineraries.

## `agency.txt`