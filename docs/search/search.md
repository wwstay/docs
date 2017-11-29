# Search APIs

#### /v1/hotels

The search APIs provides an endpoint to search
for hotels and apartments within a vicinity and also
filter the results based on various parameters.

## Basic Search

**Request** - A simple search to find hotels in San Jose, US

URL:
```
https://stage.wwstay.com/app/api/v1/hotels?lat=37.2970155&lng=-121.8174109&check_in=2015-08-01&check_out=2015-08-06
```

**Response**

```json
{
    "check-in": "2015-08-01",
    "check-out": "2015-08-06",
    "hotels": [
        {
            "address": "1727 Technology Dr, San Jose, CA 95110, United States",
            "currency": "USD",
            "description": "The stylishly-appointed Courtyard San Jose Airport Hotel is a departure from the same old business travel. Offering complimentary San Jose Airport shuttle service and located near Saratoga, Santa Clara and the Winchester Mystery House, our San Jose, California hotel puts you at the center of the Silicon Valley's best attractions. The state-of-the-art Courtyard signature lobby offers guests choices with free Wi-Fi throughout, flexible spaces to work or relax in and the GoBoard\u00ae, which provides access to the latest news, weather and airport conditions. From our San Jose Airport hotel, guests can savor healthy meals and snacks at the Bistro \u2013 Eat. Drink. Connect.\u00ae, which serves specialty drinks made with Starbucks\u00ae coffee. Our San Jose, California hotel also offers a spacious fitness center, outdoor pool and spacious lodging choices meant to help guests stay productive while on the road. The Courtyard San Jose Airport Hotel near Saratoga, California, winner of TripAdvisor's Certificate of Excellence.",
            "id": "4416ixnjso",
            "name": "Courtyard by Marriott San Jose Airport",
            "room_from": 120.87
        },
        {
            "address": "1727 Technology Dr, San Jose, CA 95110, United States",
            "currency": "USD",
            "description": "The stylishly-appointed Courtyard San Jose Airport Hotel is a departure from the same old business travel. Offering complimentary San Jose Airport shuttle service and located near Saratoga, Santa Clara and the Winchester Mystery House, our San Jose, California hotel puts you at the center of the Silicon Valley's best attractions. The state-of-the-art Courtyard signature lobby offers guests choices with free Wi-Fi throughout, flexible spaces to work or relax in and the GoBoard\u00ae, which provides access to the latest news, weather and airport conditions. From our San Jose Airport hotel, guests can savor healthy meals and snacks at the Bistro \u2013 Eat. Drink. Connect.\u00ae, which serves specialty drinks made with Starbucks\u00ae coffee. Our San Jose, California hotel also offers a spacious fitness center, outdoor pool and spacious lodging choices meant to help guests stay productive while on the road. The Courtyard San Jose Airport Hotel near Saratoga, California, winner of TripAdvisor's Certificate of Excellence.",
            "id": "4416ixnjso",
            "name": "Courtyard by Marriott San Jose Airport",
            "room_from": 120.87
        }
    ],
    "latitude": 37.2970155,
    "longitude": -121.8174109,
    "num_hotels": 20,
    "more_results":true,
    "next_page": 2,
    "query": "San Jose,US",
    "status": "ok"
}
```

&nbsp;

## Search Hotel Request Fields

The search query accepts various filters

|Query Param  | Significance                                                                                                                                                |OPTIONAL/MANDATORY    |
-----------   | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |----------------------|
|currency     | Room rates are returned in this currency.  A conversion charge of 3.5% is included in the rates if the local currency is different from requested currency. |Optional(default USD) |
|star_rating  | Show only hotels that have specified star rating. star_rating=3,5                                                                                           |Optional              |
|Check_in     | Date (YYYY-MM-DD) - The requested check-in date of the hotel reservation.                                                                                   |Mandatory             |
|Check_out    | Date (YYYY-MM-DD) - The requested check-Out date of the hotel reservation.                                                                                  |Mandatory             |
|lat          |Latitude coordinate for the search origin point                                                                                                              |Mandatory             |
|lng          |Longitude coordinate for the search origin point                                                                                                             |Mandatory             |
|room_count   |Defines required number of rooms.                                                                                                                            |Optional (default 1)  |
|next_page    |If the response contains 'more_results' as 'true' then you can get more search results by applying this filter.                                              |Optional              |


&nbsp;

## Examples

* Search only 3 and 5 star hotels in London,UK

```
/v1/hotels?lat=37.2970155&lng=-121.8174109&check_in=2015-08-01&check_out=2015-08-06&star_rating=3,4
```

* Search hotels in London,UK but see room rates in INR

```
/v1/hotels?lat=37.2970155&lng=-121.8174109&check_in=2015-08-01&check_out=2015-08-06&currency=INR
```

* Search for more results

```
/v1/hotels?lat=37.2970155&lng=-121.8174109&check_in=2015-08-01&check_out=2015-08-06&next_page=2
```
