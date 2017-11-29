# Book API

The book API provides an endpoint to book a particular
room type.  Points to note about the book API -

 * It only works over POST.
 * Error codes follow the
   [HTTP 1.1 spec](http://www.w3.org/Protocols/rfc2616/rfc2616.html).
   So for example,
    - Missing arguments will give a 400 (Bad request)
    - HTTP GET will give 405 (Method not allowed), etc.
 * All error responses should be handled in the client application.
 * The access token should be sent in the POST header.  The header should -

    ```
    "Authorization: Bearer <TOKEN>"
    ```

## Successful request &amp; response

URL:
```
https://stage.wwstay.com/api/v1/book/:room_id
```

**Example**

```
$ curl -X POST -v -H "Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ" -d "check_in=2018-08-01&check_out=2018-08-06&guest_name=Pradip+Caulagi&guest_email=pradip@wwstay.com&guest_contact=+919876543210" "https://stage.wwstay.com/g/api/v1/book/yf24muyn92"

* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8000 (#0)
> POST /api/v1/book/yf24muyn92 HTTP/1.1
> User-Agent: curl/7.35.0
> Host: localhost:8000
> Accept: */*
> Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ
> Content-Length: 124
> Content-Type: application/x-www-form-urlencoded
> 
* upload completely sent off: 124 out of 124 bytes
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Wed, 15 Apr 2018 12:02:17 GMT
< Server: WSGIServer/0.1 Python/2.7.6
< Vary: Accept-Language, Cookie
< X-Frame-Options: SAMEORIGIN
< Content-Type: application/json
< Content-Language: en
< 
* Closing connection 0

{
    "cancellation_policy": "Free cancellation 2 days before 2018-08-01",
    "check_in": "2018-08-01",
    "check_out": "2018-08-06",
    "confirmation_number": "q8f8fmw0fc",
    "status": "ok"
}
```

## More examples

**GET request**

```
$ curl -X GET -v "https://stage.wwstay.com/api/v1/book/yf24muyn92?access_token=fEmpyz2cGde6PppfslzkHCRfP13PgQ"

* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8000 (#0)
> GET /api/v1/book/yf24muyn92?access_token=fEmpyz2cGde6PppfslzkHCRfP13PgQ HTTP/1.1
> User-Agent: curl/7.35.0
> Host: localhost:8000
> Accept: */*
> 
* HTTP 1.0, assume close after body
< HTTP/1.0 405 METHOD NOT ALLOWED
< Date: Wed, 15 Apr 2018 11:36:17 GMT
< Server: WSGIServer/0.1 Python/2.7.6
< Vary: Accept-Language, Cookie
< X-Frame-Options: SAMEORIGIN
< Content-Type: text/html; charset=utf-8
< Content-Language: en
< Allow: POST
< 
* Closing connection 0
```

**Request without Authorization token in headers**

```
$ curl -X POST -v "https://stage.wwstay.com/api/v1/book/yf24muyn92"

* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8000 (#0)
> POST /api/v1/book/yf24muyn92 HTTP/1.1
> User-Agent: curl/7.35.0
> Host: localhost:8000
> Accept: */*
> 
* HTTP 1.0, assume close after body
< HTTP/1.0 403 FORBIDDEN
< Date: Wed, 15 Apr 2018 11:38:32 GMT
< Server: WSGIServer/0.1 Python/2.7.6
< Vary: Accept-Language, Cookie
< X-Frame-Options: SAMEORIGIN
< Content-Type: text/html; charset=utf-8
< Content-Language: en
< 
* Closing connection 0
```

**Request with missing parameters**

```
$ curl -X POST -v -H "Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ" "https://stage.wwstay.com/api/v1/book/yf24muyn92"

* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8000 (#0)
> POST /api/v1/book/yf24muyn92 HTTP/1.1
> User-Agent: curl/7.35.0
> Host: localhost:8000
> Accept: */*
> Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ
> 
* HTTP 1.0, assume close after body
< HTTP/1.0 400 BAD REQUEST
< Date: Wed, 15 Apr 2018 11:40:14 GMT
< Server: WSGIServer/0.1 Python/2.7.6
< Vary: Accept-Language, Cookie
< X-Frame-Options: SAMEORIGIN
< Content-Type: text/html; charset=utf-8
< Content-Language: en
< 
* Closing connection 0

Required parameters are missing
```

**Wrong dates (see message at the end)**

```
$ curl -X POST -v -H "Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ" -d "check_in=2018-09-01&check_out=2018-08-06&guest_name=Pradip+Caulagi&guest_email=pradip@wwstay.com&guest_contact=+919876543210" "https://stage.wwstay.com/api/v1/book/yf24muyn92"

* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8000 (#0)
> POST /api/v1/book/yf24muyn92 HTTP/1.1
> User-Agent: curl/7.35.0
> Host: localhost:8000
> Accept: */*
> Authorization: Bearer fEmpyz2cGde6PppfslzkHCRfP13PgQ
> Content-Length: 124
> Content-Type: application/x-www-form-urlencoded
> 
* upload completely sent off: 124 out of 124 bytes
* HTTP 1.0, assume close after body
< HTTP/1.0 400 BAD REQUEST
< Date: Wed, 15 Apr 2018 11:53:55 GMT
< Server: WSGIServer/0.1 Python/2.7.6
< Vary: Accept-Language, Cookie
< X-Frame-Options: SAMEORIGIN
< Content-Type: text/html; charset=utf-8
< Content-Language: en
< 
* Closing connection 0

Invalid check-in/check-out dates
```


## Contact

Have questions that are not answered here?  Send us an email to dev@wwstay.com
