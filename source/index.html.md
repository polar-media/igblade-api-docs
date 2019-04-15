---
title: IGBlade API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript
  - php

toc_footers:
  - <a href='https://app.igblade.pro/settings'>Get your API key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the IGBlade API! You can use our API to access IGBlade API endpoints, which can get information on Instagram accounts in our database.


# Authentication

The IGBlade API uses API keys to allow access to the API. You can find your API key at your [settings page](https://app.igblade.pro/settings).

The API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer YOUR_API_TOKEN`

<aside class="notice">
You must replace <code>YOUR_API_TOKEN</code> with your personal API key.
</aside>

# Instagram Accounts

## Get profile


```shell
curl "https://igblade.com/api/v2/accounts/9gag" \
     -H 'Authorization: Bearer YOUR_API_KEY_HERE'
```

```javascript
jQuery.ajax({
    url: "https://igblade.com/api/v2/accounts/9gag",
    type: "GET",
    headers: {
        "Authorization": "Bearer YOUR_API_KEY_HERE",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// get cURL resource
$ch = curl_init();

// set url
curl_setopt($ch, CURLOPT_URL, 'https://igblade.com/api/v2/accounts/9gag');

// set method
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'GET');

// return the transfer as a string
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

// set headers
curl_setopt($ch, CURLOPT_HTTPHEADER, [
  'Authorization: Bearer YOUR_API_KEY_HERE',
]);

// send the request and save response to $response
$response = curl_exec($ch);

// stop if fails
if (!$response) {
  die('Error: "' . curl_error($ch) . '" - Code: ' . curl_errno($ch));
}

echo 'HTTP Status Code: ' . curl_getinfo($ch, CURLINFO_HTTP_CODE) . PHP_EOL;
echo 'Response Body: ' . $response . PHP_EOL;

// close curl resource to free up system resources 
curl_close($ch);
```

> The above command returns JSON structured like this:

```json
{
  "profile": {
    "id": 1,
    "ig_id": "259220806",
    "name": "9GAG: Go Fun The World",
    "username": "9gag",
    "profile_picture": "https:\/\/scontent-sea1-1.cdninstagram.com\/vp\/510fefdff719465defd2bcb01bb9d8a9\/5D38690E\/t51.2885-19\/s320x320\/18645376_238828349933616_4925847981183205376_a.jpg?_nc_ht=scontent-sea1-1.cdninstagram.com",
    "created_at": ...,
    "updated_at": ...,
    "last_stat_at": ...,
    "is_private": 0,
    "is_verified": 1,
    "is_business": 1,
    "biography": "Get our app for the latest \n\ud83c\udf1f MEMES\n\ud83d\udc7e GIFS\n\ud83d\udcf9 VIDEOS\n\ud83d\udc47\ud83c\udffb",
    "business_address": null,
    "business_email": null,
    "business_phone": null,
    "external_url": "http:\/\/9gag.com\/app",
  },
  "last_stat": {
    "account_id": 1,
    "follower_count": 50306840,
    "following_count": 28,
    "media_count": 19209,
    "engagement_rate": 0.0062,
    "created_at": ...
  },
  "summary": {
    "daily_growth": -1623,
    "daily_growth_previous": -7563,
    "monthly_growth": 220487,
    "monthly_growth_previous": 384055,
    "followers_last_month": 49906,
    "followers_last_month_previous": 409721,
    "followers_last_week": -17417,
    "followers_last_week_previous": -55269,
    "average_likes": 176239,
    "average_comments": 2528,
    "average_likes_previous": 440534,
    "average_comments_previous": 3641
  }
}
```

This endpoint retrieves basic information about an Instagram account. 

The data includes, `profile`, `last_stat` and `summary`.

### HTTP Request

`GET https://igblade.com/api/v2/accounts/<USERNAME>`

### URL Parameters

Parameter | Description
--------- | -----------
USERNAME | The Instagram username of the account you want to fetch

<aside class="success">
Remember — you must use your API key.
</aside>

## Get charts

```shell
curl "https://igblade.com/api/v2/accounts/9gag/charts?start=2019-03-16T00:00:00.000Z&end=2019-04-15T23:59:59.999Z" \
     -H 'Authorization: Bearer YOUR_API_KEY_HERE'
```

```javascript
jQuery.ajax({
    url: "https://igblade.com/api/v2/accounts/9gag/charts",
    type: "GET",
    data: {
        "start": "2019-03-16T00:00:00.000Z",
        "end": "2019-04-15T23:59:59.999Z",
    },
    headers: {
        "Authorization": "Bearer YOUR_API_KEY_HERE",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// get cURL resource
$ch = curl_init();

// set url
curl_setopt($ch, CURLOPT_URL, 'https://igblade.com/api/v2/accounts/9gag/charts?start=2019-03-16T00:00:00.000Z&end=2019-04-15T23:59:59.999Z');

// set method
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'GET');

// return the transfer as a string
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

// set headers
curl_setopt($ch, CURLOPT_HTTPHEADER, [
  'Authorization: Bearer YOUR_API_KEY_HERE',
]);

// send the request and save response to $response
$response = curl_exec($ch);

// stop if fails
if (!$response) {
  die('Error: "' . curl_error($ch) . '" - Code: ' . curl_errno($ch));
}

echo 'HTTP Status Code: ' . curl_getinfo($ch, CURLINFO_HTTP_CODE) . PHP_EOL;
echo 'Response Body: ' . $response . PHP_EOL;

// close curl resource to free up system resources 
curl_close($ch);



```

> The above command returns JSON structured like this:

```json
{
  "followers": {
    "data": {
      "labels": [
        "2019-04-14",
        "2019-04-15"
      ],
      "data": [
        50311630,
        50306840
      ]
    },
    "name": "Followers"
  },
  "followings": {
    "data": {
      "labels": [
        "2019-04-14",
        "2019-04-15"
      ],
      "data": [
        28,
        28
      ]
    },
    "name": "Followings"
  },
  "engagement": {
    "data": {
      "labels": [
        "2019-04-14",
        "2019-04-15"
      ],
      "data": [
        0.8500000000000001,
        0.62
      ]
    },
    "name": "Engagement Rate"
  },
  "followers-growth": {
    "data": {
      "labels": [
        "2019-04-14",
        "2019-04-15"
      ],
      "data": [
        0,
        -4790
      ]
    },
    "name": "Followers",
    "type": "bar"
  },
  "average_likes": {
    "data": {
      "labels": [
        "2019-04-14",
        "2019-04-15"
      ],
      "data": [
        427648.85500000004,
        311902.408
      ]
    },
    "name": "Average likes"
  }
}
```

This endpoint retrieves chart data for the requested account

### HTTP Request

`GET https://igblade.com/api/v2/accounts/<USERNAME>/charts`

### URL Parameters

Parameter | Description
--------- | -----------
USERNAME | The Instagram username of the account you want to fetch

### Query Parameters

Parameter | Description
--------- | -----------
start | The starting date for the time-range you want to fetch in ISO 8601 format
end | The ending date for the time-range you want to fetch in ISO 8601 format