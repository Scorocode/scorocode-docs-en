## Sending push notifications to devices.

**https://api.scorocode.ru/api/v1/sendpush**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "",     // application identifier, mandatory
    "cli"         : "",     // client key, mandatory
    "acc"         : "",     // access key, mandatory, messageKey or masterKey for full access
    "sess"        : "",     // session ID, mandatory, if acc != masterKey
    "coll"        : "",     // collection name, mandatory, "users", "roles" or "devices"
    "query"       : {},     // devices collection query for sampling addressees with field_name/operator:value pairs, optional
    "msg"         : {
        "data"    : {
            "gcm": {        // data for Android devices, optional
                "protocol": "http",   // protocol to be used: 'http' || 'xmpp', optional
                "notification": {
                    "body" : "great match!",
                    "title" : "Portugal vs. Denmark",
                    "icon" : "myicon"
                },
                "data": {
                    "key": "value"
                }
            },
            "apns": {       // data for iOs devices, optional
                "id": "123e4567-e89b-12d3-a456-42665544000", // apns-id, optional
                "topic": "com.sideshow.Apns2",               // apns-topic, optional
                "collapseId": "my_collapse",                 // apns-collapse-id, optional
                "expiration": "2006-01-02T15:04:05Z07:00",   // apns-expiration, optional
                "priority":5,                                // apns-priority, optional
                "aps" : {
                    "alert" : {
                        "title" : "Portugal vs. Denmark",
                        "body" : "great match!",
                        "action-loc-key" : "Watch"
                    },
                    "badge" : 5
                },
                "acme1" : "bar",
                "acme2" : [ "bang",  "whiz" ]
            }
        }
    }
}
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "fb33e473e08515ff6b57ef6f59392e5d",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "devices",
        "query": {
            "userId": {
                "$exists": true
            }
        },
        "msg": {
             "data": {
              "gcm": {
                    "protocol": "http",
                    "notification": {
                        "body" : "great match!",
                        "title" : "Portugal vs. Denmark",
                        "icon" : "myicon"
                    },
                    "data": {
                        "key": "value"
                    }
                },
                "apns": {
                    "aps" : {
                        "alert" : {
                            "title" : "Portugal vs. Denmark",
                            "body" : "great match!",
                            "action-loc-key" : "Watch"
                        },
                        "badge" : 5
                    },
                    "acme1" : "bar",
                    "acme2" : [ "bang",  "whiz" ]
                }
            }
        }
    }' "https://api.scorocode.ru/api/v1/sendpush"


**Responses:**

!!! success "Success"
    ```JSON
    {
        "count"       : int,       
        "error"       : false
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------

## Sending SMS to users.

**https://api.scorocode.ru/api/v1/sendsms**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "",     // application identifier, mandatory
    "cli"         : "",     // client key, mandatory
    "acc"         : "",     // access key, mandatory, messageKey or masterKey for full access
    "sess"        : "",     // session ID, mandatory, if acc != masterKey
    "coll"        : "",     // collection name, mandatory, "users" or "roles"
    "query"       : {},     // users collection query for sampling the addressees with field_name/operator:value pairs, optional
    "msg"         : {
        "text"        : "" // sms text
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "fb33e473e08515ff6b57ef6f59392e5d",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "users",
        "query": {
            "phone": {
                "$exists": true
            }
        },
        "msg": {
            "text": "SMS text"
        }
    }' "https://api.scorocode.ru/api/v1/sendsms"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "count"       : int      
        "error"       : false
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

