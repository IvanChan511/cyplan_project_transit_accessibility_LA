# GTFS Schedule Data Dictionary
This dictionary provides the meaning of the following 11 `.txt` files, depending on the year of the data:
1. `agency.txt`: Transit agencies with service represented in this dataset.
2. `calendar_dates.txt`: Exceptions for the services defined in the `calendar.txt`.
3. `calendar.txt`: Service dates specified using a weekly schedule with start and end dates.
4. `feed_info.txt`: Dataset metadata, including publisher, version, and expiration information.  
5. `routes.txt`: Transit routes. A route is a group of trips that are displayed to riders as a single service.
6. `shapes.txt`: Rules for mapping vehicle travel paths, sometimes referred to as route alignments.  
7. `stop_times.txt`: Times that a vehicle arrives at and departs from stops for each trip.  
8. `stops.txt`: Stops where vehicles pick up or drop off riders. Also defines stations and station entrances.
9. `trips.txt`: Trips for each route. A trip is a sequence of two or more stops within a specific time period.    
10. `fare_attributes.txt`: Fare information for a transit agency's routes.
11. `fare_rules.txt`: Rules to apply fares for itineraries.

The information is adopted from the [General Transit Feed Specification Reference](https://gtfs.org/documentation/schedule/reference/).

## 1. `agency.txt`   
1. `agency_id`: Identifies a transit brand, which is often synonymous with a transit agency. A dataset may contain data from multiple agencies.
2. `agency_name`: Full name of the transit agency.
3. `agency_url`: URL of the transit agency.
4. `agency_timezone`: Timezone where the transit agency is located. 
5. `agency_lang`: Primary language used by this transit agency. 
6. `agency_phone`: A voice telephone number for the specified agency. This field is a string value that presents the telephone number as typical for the agency service area. It may contain punctuation marks to group the digits of the number. Dialable text (for example, TriMet `"503-238-RIDE"`) is permitted, but the field must not contain any other descriptive text.  
  
## 2. `calendar_dates.txt` 
1. `service_id`: Identifies a set of dates when a service exception occurs for one or more routes. Each (`service_id, date`) pair may only appear once in `calendar_dates.txt` if using `calendar.txt` and `calendar_dates.txt` in conjunction. If a `service_id` value appears in both `calendar.txt` and `calendar_dates.txt`, the information in `calendar_dates.txt` modifies the service information specified in `calendar.txt`.  
2. `date`: Date when the service exception occurs.
3. `exception_type`: Indicates whether service is available on the date specified in the date field. Valid options are:  
`1` - Service has been added for the specified date.  
`2` - Service has been removed for the specified date.
  
## 3. `calendar.txt` 
1. `service_id`: Identifies a set of dates when service is available for one or more routes.
2. `monday`: Indicates whether the service operates on all Mondays in the date range specified by the `start_date` and `end_date` fields. Note that exceptions for particular dates may be listed in `calendar_dates.txt`.  
Valid options are:  
`1` - Service is available for all Mondays in the date range.  
`0` - Service is not available for Mondays in the date range.  
3. `tuesday`: Functions in the same way as `monday` except applies to Tuesdays.
4. `wednesday`: Functions in the same way as `monday` except applies to Wednesdays.
5. `thursday`: Functions in the same way as `monday` except applies to Thursdays.
6. `friday`: Functions in the same way as `monday` except applies to Fridays.
7. `saturday`: Functions in the same way as `monday` except applies to Saturdays.
8. `sunday`: Functions in the same way as `monday` except applies to Sundays.
9. `start_date`: Start service day for the service interval.
10. `end_date`: End service day for the service interval. This service day is included in the interval.  
  
## 4. `fare_attributes.txt` 
1. `fare_id`: Identifies a fare class.
2. `price`: Fare price, in the unit specified by `currency_type`.
3. `currency_type`: Currency used to pay the fare.
4. `payment_method`: Indicates when the fare must be paid. Valid options are:  
`0` - Fare is paid on board.  
`1` - Fare must be paid before boarding.  
5. `transfers`: Indicates the number of transfers permitted on this fare. Valid options are:  
`0` - No transfers permitted on this fare.  
`1` - Riders may transfer once.  
`2` - Riders may transfer twice.  
`empty` - Unlimited transfers are permitted.  
6. `transfer_duration`: Length of time in seconds before a transfer expires. When `transfers=0`, this field may be used to indicate how long a ticket is valid for, or it may be left empty.
7. `fare_note`: Additional Note for the fare class.
  
## 5. `fare_rules.txt` 
1. `route_id`: Identifies a route associated with the fare class. If several routes with the same fare attributes exist, create a record in `fare_rules.txt` for each route.
2. `fare_id`: Identifies a fare class.
3. `route_id_base`: Base `route_id`, within 2 - 3 digits.

## 6. `feed_info.txt` 
1. `feed_id`: ID of the dataset.
2. `feed_publisher_name`: Full name of the organization that publishes the dataset. This may be the same as one of the `agency.agency_name` values.  
3. `feed_publisher_url`: URL of the dataset publishing organization's website. This may be the same as one of the `agency.agency_url` values.  
4. `feed_lang`: Default language used for the text in this dataset. 
5. `feed_version`: String that indicates the current version of their GTFS dataset.  
6. `feed_license`: The license of their GTFS dataset.
7. `feed_contact_email`: Email address for communication regarding the GTFS dataset and data publishing practices. 
8. `feed_contact_url`: URL for contact information, a web-form, support desk, or other tools for communication regarding the GTFS dataset and data publishing practices.  
9. `feed_start_date`: The dataset provides complete and reliable schedule information for service in the period from the beginning of the `feed_start_date` day to the end of the `feed_end_date day`. Both days may be left empty if unavailable. 
10. `feed_end_date`: (see above)

## 7. `routes.txt` 
1. `route_id`: Identifies a route.
2. `route_short_name`: Short name of a route. Often a short, abstract identifier (e.g., `"32", "100X", "Green"`) that riders use to identify a route. 
3. `route_long_name`: Full name of a route. 
4. `route_desc`: Description of a route that provides useful, quality information. Should not be a duplicate of `route_short_name` or `route_long_name`.  
5. `route_type`: Indicates the type of transportation used on a route. Valid options are:  
`0` - Tram, Streetcar, Light rail. Any light rail or street-level system within a metropolitan area.  
`1` - Subway, Metro. Any underground rail system within a metropolitan area.  
`2` - Rail. Used for intercity or long-distance travel.  
`3` - Bus. Used for short- and long-distance bus routes.  
6. `route_color`: Route color designation that matches public-facing material. Defaults to white (`FFFFFF`) when omitted or left empty.
7. `route_text_color`: Legible color to use for text drawn against a background of route_color. 
8. `route_url`: URL of a web page about the particular route. Should be different from the `agency.agency_url` value.
  
## 8. `shapes.txt` 
1. `shape_id`: Identifies a shape.
2. `shape_pt_lat`: Latitude of a shape point. Each record in `shapes.txt` represents a shape point used to define the shape.
3. `shape_pt_lon`: Longitude of a shape point.
4. `shape_pt_sequence`: Sequence in which the shape points connect to form the shape. Values must increase along the trip but do not need to be consecutive.

## 9. `stop_times.txt` 
1. `trip_id`: Identifies a trip.
2. `arrival_time`: Arrival time at the stop (defined by `stop_times.stop_id`) for a specific trip (defined by `stop_times.trip_id`) in the time zone specified by `agency.agency_timezone`, not `stops.stop_timezone`.  
If there are not separate times for arrival and departure at a stop, `arrival_time` and `departure_time` should be the same.  
For times occurring after midnight on the service day, enter the time as a value greater than `24:00:00` in `HH:MM:SS`.  
If exact arrival and departure times (`timepoint=1`) are not available, estimated or interpolated arrival and departure times (`timepoint=0`) should be provided.  
3. `departure_time`:  Required	Departure time from the stop (defined by `stop_times.stop_id`) for a specific trip (defined by `stop_times.trip_id`) in the time zone specified by `agency.agency_timezone`, not `stops.stop_timezone`.  
If there are not separate times for arrival and departure at a stop, `arrival_time` and `departure_time` should be the same.  
For times occurring after midnight on the service day, enter the time as a value greater than `24:00:00` in `HH:MM:SS`.  
If exact arrival and departure times (`timepoint=1`) are not available, estimated or interpolated arrival and departure times (`timepoint=0`) should be provided.  
4. `stop_id`: Identifies the serviced stop. All stops serviced during a trip must have a record in `stop_times.txt`. Referenced locations must be `stops/platforms`, i.e., their `stops.location_type` value must be `0` or `empty`. A stop may be serviced multiple times in the same trip, and multiple trips and routes may service the same stop.
5. `stop_sequence`: Order of stops, location groups, or GeoJSON locations for a particular trip. The values must increase along the trip but do not need to be consecutive.
6. `stop_headsign`: Text that appears on signage identifying the trip's destination to riders. This field overrides the default `trips.trip_headsign` when the headsign changes between stops. If the headsign is displayed for an entire trip, `trips.trip_headsign` should be used instead.  
A `stop_headsign` value specified for one `stop_time` does not apply to subsequent `stop_times` in the same trip. If you want to override the `trip_headsign` for multiple `stop_times` in the same trip, the `stop_headsign` value must be repeated in each `stop_time` row.
7. `pickup_type`: Indicates pickup method. Valid options are:  
`0` or `empty` - Regularly scheduled pickup.  
`1` - No pickup available.  
`2` - Must phone the agency to arrange pickup.  
`3` - Must coordinate with driver to arrange pickup.  
8. `drop_off_type`: Indicates drop-off method. Valid options are:  
`0` or `empty` - Regularly scheduled drop-off.  
`1` - No drop-off available.  
`2` - Must phone the agency to arrange drop-off.  
`3` - Must coordinate with driver to arrange drop-off.  
9. `trip_id_event`: The event ID corresponds to the trip ID. 
10. `route_code`: Route CODE.
11. `destination_code`: Destination CODE.
12. `timepoint`: Indicates if arrival and departure times for a stop are strictly adhered to by the vehicle or if they are instead approximate and/or interpolated times. This field allows a GTFS producer to provide interpolated stop times, while indicating that the times are approximate. Valid options are:  
`0` - Times are considered approximate.  
`1` - Times are considered exact.   
13. `bay_num`: The Bay number the route stops by, if the stop contains multiple Bays.

## 10. `stops.txt` 
1. `stop_id`: Identifies a location: stop/platform, station, entrance/exit, generic node, or boarding area (see `location_type`). Multiple routes may use the same `stop_id`.
2. `stop_code`: Short text or a number that identifies the location for riders.
3. `stop_name`: Name of the location. The `stop_name` should match the agency's rider-facing name for the location as printed on a timetable, published online, or represented on signage. 
4. `stop_desc`: Description of the location that provides useful, quality information. Should not be a duplicate of `stop_name`.
5. `stop_lat`: Latitude of the location.
6. `stop_lon`: Longitude of the location.
7. `stop_url`: URL of a web page about the location. 
8. `location_type`: Location type. Valid options are:  
`0` (or empty) - **Stop** (or **Platform**). A location where passengers board or disembark from a transit vehicle. Is called a platform when defined within a parent_station.  
`1` - **Station**. A physical structure or area that contains one or more platforms.  
`2` - **Entrance/Exit**. A location where passengers can enter or exit a station from the street. If an entrance/exit belongs to multiple stations, it may be linked by pathways to both, but the data provider must pick one of them as parent.  
`3` - **Generic Node**. A location within a station, not matching any other `location_type`, that may be used to link together pathways defined in `pathways.txt`.  
`4` - **Boarding Area**. A specific location on a platform, where passengers can board and/or alight vehicles.  
9. `parent_station`: Defines hierarchy between the different locations defined in `stops.txt`. 
10. `tpis_name`:  Transit Passenger Information System Name.

## 11. `trips.txt` 
1. `route_id`: Identifies a route.  
2. `service_id`: Identifies a set of dates when service is available for one or more routes.  
3. `trip_id`: Identifies a trip.
4. `trip_headsign`: Text that appears on signage identifying the trip's destination to riders. 
5. `direction_id`: 	Indicates the direction of travel for a trip. This field should not be used in routing; it provides a way to separate trips by direction when publishing timetables. Valid options are:  
`0` - Travel in one direction (e.g. outbound travel).  
`1` - Travel in the opposite direction (e.g. inbound travel).  
6. `block_id`: 	Identifies the block to which the trip belongs. A block consists of a single trip or many sequential trips made using the same vehicle, defined by shared service days and `block_id`. A `block_id` may have trips with different service days, making distinct blocks. 
7. `shape_id`: Identifies a geospatial shape describing the vehicle travel path for a trip.
8. `trip_id_event`: Full Trip ID including Event (TBD).