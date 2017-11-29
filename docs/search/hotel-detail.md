# Hotel Detail API

#### /v1/hotels/:id

The hotel API provides an endpoint to find all the 
details about a particular hotel, including room rates
and cancellation policies, images, amenities, etc.

## Request &amp; response

**Request** - Show details for a particular hotel

URL:
```
https://stage.wwstay.com/app/api/v1/hotels/:id
```

Example
```
https://stage.wwstay.com/app/api/v1/hotels/0wgpigipmp?check_in=2015-08-01&check_out=2015-08-06
```

**Response**

```json
{
    "check_in": "2015-08-01",
    "check_out": "2015-08-06",
    "hotel": {
        "address": "16 E 32nd St\r\nNew York, NY 10016\r\nUnited States",
        "currency": "USD",
        "description": "<p><b>Property Location</b> <br />Avalon Hotel is in the heart of New York, walking distance from Empire State Building and The Morgan Library and Museum. This 4-star hotel is close to Chrysler Building and Times Square.</p><p><b>Rooms</b> <br />Make yourself at home in one of the 100 air-conditioned rooms featuring iPod docking stations and flat-screen televisions. Complimentary wireless Internet access keeps you connected, and cable programming is available for your entertainment. Bathrooms have makeup/shaving mirrors and hair dryers. Conveniences include safes and desks, as well as multi-line phones with voice mail.</p><p><b>Rec, Spa, Premium Amenities</b> <br />Make use of convenient amenities such as complimentary wireless Internet access, concierge services, and a fireplace in the lobby. Getting to nearby attractions is a breeze with the area shuttle (surcharge).</p><p><b>Dining</b> <br />Satisfy your appetite at a coffee shop/caf\u00e9 serving guests of Avalon Hotel.</p><p><b>Business, Other Amenities</b> <br />Featured amenities include a business center, a computer station, and audiovisual equipment. Event facilities at this hotel consist of banquet facilities and a meeting/conference room. Parking (subject to charges) is available onsite.</p>",
        "images": [
            {
                "caption": "Standard Double Room - Special Offer",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_93_s.jpg"
            },
            {
                "caption": "Family Room",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_104_s.jpg"
            },
            {
                "caption": "Junior Suite, Non Smoking - Special Offer",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_91_s.jpg"
            },
            {
                "caption": "Deluxe Suite (2 Queen Beds with Sofa Bed)",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_105_s.jpg"
            },
            {
                "caption": "Deluxe Suite, 1 King Bed with Sofabed - Special Offer",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_89_s.jpg"
            },
            {
                "caption": "Executive Suite, 1 King Bed with Sofabed - Special Offer",
                "url": "http://media.expedia.com/hotels/1000000/90000/84700/84617/84617_90_s.jpg"
            }
        ],
        "latitude": 40.74673,
        "longitude": -73.98448,
        "name": "Avalon Hotel",
        "rooms": [
            {
                "cancellation_policy": "We understand that sometimes your travel plans change. We do not charge a change or cancel fee. However, this property (Avalon Hotel) imposes the following penalty to its customers that we are required to pass on: cancellations or changes made before 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. Cancellations or changes made after 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. The property makes no refunds for no shows or early checkouts.",
                "free_cancellation": "NA",
                "inclusions": "Standard Double Room - Special Offer",
                "rate": "1329.37",
                "room_id": 84617,
                "type": "Standard Double Room - Special Offer"
            },
            {
                "cancellation_policy": "We understand that sometimes your travel plans change. We do not charge a change or cancel fee. However, this property (Avalon Hotel) imposes the following penalty to its customers that we are required to pass on: cancellations or changes made before 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. Cancellations or changes made after 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. The property makes no refunds for no shows or early checkouts.",
                "free_cancellation": "NA",
                "inclusions": "Junior Suite, Non Smoking - Special Offer",
                "rate": "1524.42",
                "room_id": 84617,
                "type": "Junior Suite, Non Smoking - Special Offer"
            },
            {
                "cancellation_policy": "We understand that sometimes your travel plans change. We do not charge a change or cancel fee. However, this property (Avalon Hotel) imposes the following penalty to its customers that we are required to pass on: cancellations or changes made before 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. Cancellations or changes made after 11:59 PM ((GMT-05:00) Eastern Time (US &amp; Canada)) on Jul 30, 2015 are subject to a 1 Night Room &amp; Tax penalty. The property makes no refunds for no shows or early checkouts.",
                "free_cancellation": "NA",
                "inclusions": "Executive Suite, 1 King Bed with Sofabed - Special Offer",
                "rate": "1865.86",
                "room_id": 84617,
                "type": "Executive Suite, 1 King Bed with Sofabed - Special Offer"
            }
        ]
    },
    "id": "0wgpigipmp",
    "status": "ok"
}

```
&nbsp;

## Hotel Detail Request Fields

The search query accepts various filters

|Query Param  | Significance                                                                                                                                                |OPTIONAL/MANDATORY    |
-----------   | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |----------------------|
|currency     | Room rates are returned in this currency.  A conversion charge of 3.5% is included in the rates if the local currency is different from requested currency. |Optional(default USD) |
|star_rating  | Show only hotels that have specified star rating. star_rating=3,5                                                                                           |Optional              |
|Check_in     | Date (YYYY-MM-DD) - The requested check-in date of the hotel reservation.                                                                                   |Mandatory             |
|Check_out    | Date (YYYY-MM-DD) - The requested check-Out date of the hotel reservation.                                                                                  |Mandatory             |
|id           |Retrieve details for a specific Hotel ID.                                                                                                                    |Mandatory             |
|room_count   |Defines required number of rooms.                                                                                                                            |Optional (default 1)  |


&nbsp;


## Contact

Have questions that are not answered here?  Send us an email to dev@wwstay.com

