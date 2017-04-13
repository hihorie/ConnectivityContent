# Reference

## Authentication

The top points of sale and regions API requires HTTP basic auth credentials to be supplied with every request.

Credentials must match a valid hotelier username/password.  If data for a specific hotel or list of hotels is being requested, the credentials must be authorized to access data for those hotels.

## Top Points of Sale and Regions Endpoint

```
GET /lodging-sort/v1/hops/HopsTopTpidsAndRegions
```

The top points of sale and regions endpoint will return a sorted list of top regions for each of the top points of sale by bookings for a specified hotel.

## Request Parameters

| Name                | Parameter Type | Data Type | Example              | Description
|---------------------|----------------|-----------|----------------------|-----------------|
| `Authorization`     | Header         | String    | `Basic dGVzdDp0ZXN0` | Unique identifier for a property/hotel. |
| `hotelId`           | Query          | Integer   | `123`                | Hotel identifier |

##### Sample Request with all parameters specified
```
https://services.expediapartnercentral.com/lodging-sort/v1/hops/HopsTopTpidsAndRegions?hotelId=1
```

## Response Format
|Name | Type | Description|
|-----|------|-------------|
|hotelId | Integer | Unique identifier for a property/hotel. |
|tpid |    Integer | Point of Sale ID |
| regionId |   Long    | GAIA region ID |

##### Sample Response

```
{
    "hopsTpidsList": [
        {
            "sortedRegionList": [
                2114,
                800053,
                6144914
            ],
            "tpid": 3101
        },
        {
            "sortedRegionList": [
                2114
            ],
            "tpid": 3109
        },
        {
            "sortedRegionList": [
                2114
            ],
            "tpid": 3107
        }
    ],
    "hotelId": 1
}

```

## TPID to Point of Sale Mapping

The point of sale is encoded into an ID called a tpid.  All possible values for point of sale are listed below:

| Point of Sale | TPID |
|---|---|
|expedia.com            |       1|
|expedia.com.br         |       69|
|expedia.ca             |   4|
|Expedia.com.ar         |       70|
|Expedia.com.mx         |       12|
|Expedia.com.au         |       25|
|Expedia.com.hk         |       18|
|Expedia.in             |   27|
|Expedia.co.jp          |       28|
|Expedia.co.kr          |       16|
|Expedia.com.my         |       15|
|Expedia.nz             |   29|
|Expedia.com.ph         |       68|
|Expedia.com.sg         |       14|
|Expedia.com.tw         |       62|
|Expedia.co.th          |       17|
|Expedia.com.vn         |       71|
|Expedia.co.id          |       61|
|expedia.co.uk          |       3|
|expedia.de             |   6|
|expedia.it             |   8|
|expedia.es             |   9|
|expedia.fr             |   20|
|Expedia.co.at          |       6|
|Expedia.be             |   64|
|Expedia.dk             |   67|
|Expedia.ie             |   63|
|Expedia.nl             |   11|
|Expedia.no             |   66|
|Expedia.se             |   65|
|hotels.com             |   251463|
|hoteis.com             |   86175|
|hoteles.com            |       97815|
|hoteles.com            |       208646|
|hoteles.com            |       208691|
|hoteles.com            |       133480|
|hoteles.com            |       97814|
|hoteles.com            |       125191|
|hoteles.com            |       208666|
|hoteles.com            |       208650|
|fr.hotels.com          |       208711|
|hoteles.com            |       140093|
|hoteles.com            |       208703|
|hoteles.com            |       208642|
|hotels.com             |   70583|
|de.hotels.com          |       71004|
|cn.hotels.com          |       86159|
|hotels.co.uk           |       207191|
|de.hotels.com          |       70994|
|it.hotels.com          |       70996|
|hoteles.com            |       70995|
|hotels.ca              |               70991|
|fr.hotels.com          |       70993|
|fr.hotels.com          |       71002|
|hr.hotels.com          |       213609|
|cs.hotels.com          |       213610|
|da.hotels.com          |       70998|
|et.hotels.com          |       213612|
|fi.hotels.com          |       83481|
|gr.hotels.com          |       213613|
|zh.hotels.com          |       83786|
|hu.hotels.com          |       213615|
|is.hotels.com          |       213616|
|hotels.com             |   252364|
|id.hotels.com          |       236979|
|hotels.com             |   207181|
|jp.hotels.com          |       84882|
|kr.hotels.com          |       91256|
|lv.hotels.com          |       213617|
|lt.hotels.com          |       213618|
|ms.hotels.com          |       248814|
|hoteles.com            |       91871|
|nl.hotels.com          |       71001|
|hotels.com             |   87703|
|hoteles.com            |       208654|
|no.hotels.com          |       71000|
|hoteles.com            |       140094|
|hoteles.com            |       208699|
|hoteles.com            |       140095|
|hotels.com             |   95327|
|pl.hotels.com          |       126760|
|hoteis.com             |   207189|
|ru.hotels.com          |       126796|
|hotels.com             |   84478|
|sk.hotels.com          |       213639|
|hotels.com             |   354116|
|nl.hotels.com          |       208707|
|sv.hotels.com          |       70999|
|Fr.hotels.com          |       71003|
|tw.hotels.com          |       91257|
|th.hotels.com          |       248811|
|tr.hotels.com          |       213635|
|uk.hotels.com          |       213636|
|hoteles.com            |       208695|
|hoteles.com            |       133479|
|vi.hotels.com          |       144555|
|hotels.com             |   373527|
|voyages-sncf.com      |           7|

## Error Messages

When there are errors, the top points of sale and regions API always returns a 200 response.  The error message is specified in an error field in the response.  The following are some sample error messages:

```JSON
{
    "error":"No hotelId specified"
}
```

```JSON
{
    "error":"No clientId specified or unknown clientId"
}
```

```JSON
{
    "error":"No data found",
    "hotelId":1234567890
}
```