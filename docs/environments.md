# Environments

We understand the need to differentiate between test
and live environments.  The focus of the test environment
is to make it easy for developers and build a product that
covers all edge cases.  The focus of the production environment
is performance and security.  And the fact that all card numbers
and transactions are real.

## Test/Stage/QA

```
https://stage.wwstay.com/app/api
```
* The test environment is a replica of production.  All the
hotel and static data is refreshed in the test environment
every week from production.

* The hotel rates are not real.  We fetch the rates from a cache
that is updated daily rates from production.  If for some hotel
and date combination, no rate exists in the cache,
a random rate is selected.

* All book request and responses are dummy.  None of the reservations
will reflect in any of the live systems of the suppliers.

* You can use dummy cards for places where the system expects
a credit card to be sent.

## Production

```
https://qa.wwstay.com/app/api
```

* All hotel rates are (mostly) real.

* All bookings happen instantly (expect for the ones marked as 'on request')

* All financial transactions are real.

* The bookings will reflect with the suppliers instantly.

As always, if you have questions that are not answered here, feel
free to send a mail to [dev@wwstay.com]("mailto:dev@wwstay.com")
