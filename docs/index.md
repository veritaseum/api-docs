# Veritaseum Price API


## Describe Token

Returns information about a Ve tokenized asset

* **URL**

  /token/:symbol

* **Method:**

  `GET`

*  **URL query string params**

   None

* **Data Params**

  None

* **Success Response:**


  * **Code:** 200 <br />
    **Content:** `{"symbol":"VeSTBL","address":"0xb2c452b733a15253431dad3c878530b0385eed97"}`

* **Error Response:**


  * **Code:** 404 NOT FOUND <br />
    **Content:** `{"errorMessage":"[404] Symbol not found: :symbol"}`

* **Sample Call:**

 ```
 curl  'https://api.veritaseum.com/v1/token/VESTBL'
 ```

## Get Token Price

Returns current token price(s)

* **URL**

  /token/:symbol/price

* **Method:**

  `GET`

*  **URL query string params**

   None

* **Data Params**

  None

* **Success Response:**


  * **Code:** 200 <br />
    **Content:** `{ "symbol": "VESTBL", "price": { "USD" : "128637.567" }, "timestamp": "2018-07-05T10:25:42.666Z" }`

* **Error Response:**


  * **Code:** 404 NOT FOUND <br />
    **Content:** `{"errorMessage":"[404] Symbol not found: :symbol"}`

* **Sample Call:**

 ```
 curl  'https://api.veritaseum.com/v1/token/VESTBL/price'
 ```

## Get Token Price History

Returns historical token prices

* **URL**

  /token/:symbol/price/history

* **Method:**

  `GET`

*  **URL query string params**

   **Required:**

   * `start_date [string]` — return prices on and after the specified start date (ISO 8601)
   * `end_date [string]` —- return prices up including the specified end date (ISO 8601)

   **Optional:**

   * `collapse [string]` — Change the frequency of data
      * `daily` (default)
      * `weekly`
       * `monthly`

* **Data Params**

  None

* **Success Response:**


  * **Code:** 200 <br />
    **Content:**
    ```
    {
        "prices": [
          {
            "USD": "129037.7296",
            "date": "2014-12-10"
          },
          {
            "USD": "129362.6192",
            "date": "2014-12-09"
          },
          {
            "USD": "125467.6016",
            "date": "2014-12-08"
          },
          {
            "USD": "124994.6128",
            "date": "2014-12-07"
          }
        ],
        "range": {
          "from": "2014-12-07",
          "to": "2014-12-10",
          "complete": true
        },
        "collapse": "daily"
    }
    ```

* **Error Response:**


  * **Code:** 404 NOT FOUND <br />
    **Content:** `{"errorMessage":"[404] Symbol not found: :symbol"}`

* **Sample Call:**

 ```
 curl  'https://api.veritaseum.com/v1/token/VeSTBL/price/history?start_date=2014-12-07&end_date=2014-12-10'
 ```

* **Notes:**

In order to obtain data spanning more than a year, use `collapse=weekly` or `collapse=monthly` to get weekly or monthly prices (first day of the month/week)
 
