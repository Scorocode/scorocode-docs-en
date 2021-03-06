## Get application info

**https://api.scorocode.ru/api/v1/app**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : ""  // access key, mandatory, masterKey only
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb"
    }' "https://api.scorocode.ru/api/v1/app"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "app": {
        "_id": "584e64f8982fd55332741516",
        "appId": "48f172923acd719b42c73ac3a492cfc8",
        "name": "HTTPApp",
        "description": "",
        "userId": "5745b2123evlfh062612e3f",
        "serverId": "5745a5e63ef62fs0626ftgeb",
        "limits": {
          "rps": 20,
          "store": 10737418240,
          "pushValue": 0,
          "pushUsed": 0,
          "developers": 1,
          "ws": 200,
          "scriptTimeout": 3
        },
        "schemas": {
          "devices": {
            "id": "584e64f8982fd55332741515",
            "name": "devices",
            "useDocsACL": false,
            "ACL": {
              "create": [
                "*"
              ],
              "read": [
                "*"
              ],
              "remove": [
                "*"
              ],
              "update": [
                "*"
              ]
            },
            "triggers": {
              "afterFind": {
                "code": "",
                "isActive": false
              },
              "afterInsert": {
                "code": "",
                "isActive": false
              },
              "afterRemove": {
                "code": "",
                "isActive": false
              },
              "afterUpdate": {
                "code": "",
                "isActive": false
              },
              "beforeInsert": {
                "code": "",
                "isActive": false
              },
              "beforeRemove": {
                "code": "",
                "isActive": false
              },
              "beforeUpdate": {
                "code": "",
                "isActive": false
              }
            },
            "fields": [
              {
                "name": "readACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "updateACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "removeACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "createdAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "updatedAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "userId",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "deviceId",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": true,
                "required": true
              },
              {
                "name": "deviceType",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": true,
                "required": true
              }
            ],
            "system": true,
            "indexes": []
          },
          "roles": {
            "id": "584e64f8982fd55332741513",
            "name": "roles",
            "useDocsACL": false,
            "ACL": {
              "create": [
                "*"
              ],
              "read": [
                "*"
              ],
              "remove": [
                "*"
              ],
              "update": [
                "*"
              ]
            },
            "triggers": {
              "afterFind": {
                "code": "",
                "isActive": false
              },
              "afterInsert": {
                "code": "",
                "isActive": false
              },
              "afterRemove": {
                "code": "",
                "isActive": false
              },
              "afterUpdate": {
                "code": "",
                "isActive": false
              },
              "beforeInsert": {
                "code": "",
                "isActive": false
              },
              "beforeRemove": {
                "code": "",
                "isActive": false
              },
              "beforeUpdate": {
                "code": "",
                "isActive": false
              }
            },
            "fields": [
              {
                "name": "name",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": false,
                "required": true
              },
              {
                "name": "readACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "updateACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "removeACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "createdAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "updatedAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              }
            ],
            "system": true,
            "indexes": []
          },
          "users": {
            "id": "584e64f8982fd55332741514",
            "name": "users",
            "useDocsACL": false,
            "ACL": {
              "create": [
                "*"
              ],
              "read": [
                "*"
              ],
              "remove": [
                "*"
              ],
              "update": [
                "*"
              ]
            },
            "triggers": {
              "afterFind": {
                "code": "",
                "isActive": false
              },
              "afterInsert": {
                "code": "",
                "isActive": false
              },
              "afterRemove": {
                "code": "",
                "isActive": false
              },
              "afterUpdate": {
                "code": "",
                "isActive": false
              },
              "beforeInsert": {
                "code": "",
                "isActive": false
              },
              "beforeRemove": {
                "code": "",
                "isActive": false
              },
              "beforeUpdate": {
                "code": "",
                "isActive": false
              }
            },
            "fields": [
              {
                "name": "email",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": true,
                "required": true
              },
              {
                "name": "phone",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "readACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "updateACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "removeACL",
                "type": "ACL",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "createdAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "updatedAt",
                "type": "Date",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "username",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": false,
                "required": true
              },
              {
                "name": "password",
                "type": "Password",
                "target": "",
                "system": true,
                "readonly": false,
                "required": true
              },
              {
                "name": "emailVerified",
                "type": "Boolean",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              },
              {
                "name": "roles",
                "type": "Array",
                "target": "",
                "system": true,
                "readonly": false,
                "required": false
              },
              {
                "name": "token",
                "type": "String",
                "target": "",
                "system": true,
                "readonly": true,
                "required": false
              }
            ],
            "system": true,
            "indexes": []
          }
        },
        "accessKeys": {
          "fileKey": "31adc32bac245299cfad0d7b1912bc2a",
          "masterKey": "ffe86fefg25fbklacsdee8cd4c59644a",
          "messageKey": "605a1248a2d27424ec43f6bdf435b0a7",
          "scriptKey": "333efb738b82c3096a3fgdbabd27f702",
          "websocketKey": "9627612736b1129d2ea9d615fb482a41"
        },
        "clientKeys": {
          "android": "db993776551ed6267fbe256ef0296cb8",
          "ios": "840ff61458ec11bf411859dbbf46d46a",
          "javascript": "d6859f41223c9997ff78c6b4vb3a96bb",
          "winphone": "3fbce82fafba9dccc60036f92b971654"
        },
        "readonly": true,
        "ACLPublic": {
          "create": false,
          "read": false,
          "remove": false,
          "update": false
        },
        "settings": {
          "emailVerified": false,
          "sessionTimeout": 72,
          "androidApiKey": "",
          "gcmSenderId": "",
          "mailTemplates": {
            "forgot": {
              "subject": "",
              "body": ""
            },
            "reg": {
              "subject": "",
              "body": ""
            }
          },
          "smtp": null
        },
        "storage": {
          "user": "",
          "password": ""
        },
        "npm": "{\"dependencies\":{}}",
        "stringId": "584e64f8982fd55332741516"
      },
      "error": false
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
-------------------------------------------------------------------------------------

## Retrieve list of collections and their settings

**https://api.scorocode.ru/api/v1/app/collections**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : ""  // access key, mandatory, masterKey only
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb"
    }' "https://api.scorocode.ru/api/v1/app/collections"
    ```


!!! success "Success"
    ```JSON
    {
      "collections": {
        "devices": {
          "id": "584e64f8982fd55332741515",
          "name": "devices",
          "useDocsACL": false,
          "ACL": {
            "create": [
              "*"
            ],
            "read": [
              "*"
            ],
            "remove": [
              "*"
            ],
            "update": [
              "*"
            ]
          },
          "triggers": {
            "afterFind": {
              "code": "",
              "isActive": false
            },
            "afterInsert": {
              "code": "",
              "isActive": false
            },
            "afterRemove": {
              "code": "",
              "isActive": false
            },
            "afterUpdate": {
              "code": "",
              "isActive": false
            },
            "beforeInsert": {
              "code": "",
              "isActive": false
            },
            "beforeRemove": {
              "code": "",
              "isActive": false
            },
            "beforeUpdate": {
              "code": "",
              "isActive": false
            }
          },
          "fields": [
            {
              "name": "readACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "updateACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "removeACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "createdAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "updatedAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "userId",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "deviceId",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": true,
              "required": true
            },
            {
              "name": "deviceType",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": true,
              "required": true
            }
          ],
          "system": true,
          "indexes": []
        },
        "roles": {
          "id": "584e64f8982fd55332741513",
          "name": "roles",
          "useDocsACL": false,
          "ACL": {
            "create": [
              "*"
            ],
            "read": [
              "*"
            ],
            "remove": [
              "*"
            ],
            "update": [
              "*"
            ]
          },
          "triggers": {
            "afterFind": {
              "code": "",
              "isActive": false
            },
            "afterInsert": {
              "code": "",
              "isActive": false
            },
            "afterRemove": {
              "code": "",
              "isActive": false
            },
            "afterUpdate": {
              "code": "",
              "isActive": false
            },
            "beforeInsert": {
              "code": "",
              "isActive": false
            },
            "beforeRemove": {
              "code": "",
              "isActive": false
            },
            "beforeUpdate": {
              "code": "",
              "isActive": false
            }
          },
          "fields": [
            {
              "name": "name",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": false,
              "required": true
            },
            {
              "name": "readACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "updateACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "removeACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "createdAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "updatedAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            }
          ],
          "system": true,
          "indexes": []
        },
        "users": {
          "id": "584e64f8982fd55332741514",
          "name": "users",
          "useDocsACL": false,
          "ACL": {
            "create": [
              "*"
            ],
            "read": [
              "*"
            ],
            "remove": [
              "*"
            ],
            "update": [
              "*"
            ]
          },
          "triggers": {
            "afterFind": {
              "code": "",
              "isActive": false
            },
            "afterInsert": {
              "code": "",
              "isActive": false
            },
            "afterRemove": {
              "code": "",
              "isActive": false
            },
            "afterUpdate": {
              "code": "",
              "isActive": false
            },
            "beforeInsert": {
              "code": "",
              "isActive": false
            },
            "beforeRemove": {
              "code": "",
              "isActive": false
            },
            "beforeUpdate": {
              "code": "",
              "isActive": false
            }
          },
          "fields": [
            {
              "name": "email",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": true,
              "required": true
            },
            {
              "name": "phone",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "readACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "updateACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "removeACL",
              "type": "ACL",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "createdAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "updatedAt",
              "type": "Date",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "username",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": false,
              "required": true
            },
            {
              "name": "password",
              "type": "Password",
              "target": "",
              "system": true,
              "readonly": false,
              "required": true
            },
            {
              "name": "emailVerified",
              "type": "Boolean",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            },
            {
              "name": "roles",
              "type": "Array",
              "target": "",
              "system": true,
              "readonly": false,
              "required": false
            },
            {
              "name": "token",
              "type": "String",
              "target": "",
              "system": true,
              "readonly": true,
              "required": false
            }
          ],
          "system": true,
          "indexes": []
        }
      },
      "error": false
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

-------------------------------------------------------------------------------------

## Retrieve collection info.

**https://api.scorocode.ru/api/v1/app/collections/get**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory, masterKey only
    "coll"        : ""  // collection name, mandatory
}
```


!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "coll": "devices"
    }' "https://api.scorocode.ru/api/v1/app/collections/get"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "collection": {
        "id": "584e64f8982fd55332741515",
        "name": "devices",
        "useDocsACL": false,
        "ACL": {
          "create": [
            "*"
          ],
          "read": [
            "*"
          ],
          "remove": [
            "*"
          ],
          "update": [
            "*"
          ]
        },
        "triggers": {
          "afterFind": {
            "code": "",
            "isActive": false
          },
          "afterInsert": {
            "code": "",
            "isActive": false
          },
          "afterRemove": {
            "code": "",
            "isActive": false
          },
          "afterUpdate": {
            "code": "",
            "isActive": false
          },
          "beforeInsert": {
            "code": "",
            "isActive": false
          },
          "beforeRemove": {
            "code": "",
            "isActive": false
          },
          "beforeUpdate": {
            "code": "",
            "isActive": false
          }
        },
        "fields": [
          {
            "name": "readACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "updateACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "removeACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "createdAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "updatedAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "userId",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "deviceId",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": true,
            "required": true
          },
          {
            "name": "deviceType",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": true,
            "required": true
          }
        ],
        "system": true,
        "indexes": []
      },
      "error": false
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

-------------------------------------------------------------------------------------

## Create new collection

**https://api.scorocode.ru/api/v1/app/collections/create**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "collection": {          
        "name": "",          // collection name, mandatory  
        "useDocsACL": bool,  // "use documents ACL" flag, optional
        "ACL": {}            // ACL settings, optional
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "collection": {
                "name": "apicoll",
                "useDocsACL": false,
                "ACL": {
                    "create": [
                        "R5VGMes94p"
                    ],
                    "read": [
                        "*",
                        "R5VGMes94p"
                    ],
                    "remove": [
                        "R5VGMes94p"
                    ],
                    "update": [
                        "R5VGMes94p"
                    ]
                }
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/create"
    ```

**Responses:**

!!! success "Success"
    ```
    {
      "collection": {
        "id": "584e849e7e0b4e222480a282",
        "name": "apicoll",
        "useDocsACL": false,
        "ACL": {
            "create": [
                "R5VGMes94p"
            ],
            "read": [
                "*",
                "R5VGMes94p"
            ],
            "remove": [
                "R5VGMes94p"
            ],
            "update": [
                "R5VGMes94p"
            ]
        },
        "triggers": {
          "afterInsert": {
            "code": "",
            "isActive": false
          },
          "afterRemove": {
            "code": "",
            "isActive": false
          },
          "afterUpdate": {
            "code": "",
            "isActive": false
          },
          "beforeInsert": {
            "code": "",
            "isActive": false
          },
          "beforeRemove": {
            "code": "",
            "isActive": false
          },
          "beforeUpdate": {
            "code": "",
            "isActive": false
          }
        },
        "fields": [
          {
            "name": "readACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "updateACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "removeACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "createdAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "updatedAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          }
        ],
        "system": false,
        "indexes": []
      },
      "error": false
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



-------------------------------------------------------------------------------------

## Update collection settings

**https://api.scorocode.ru/api/v1/app/collections/update**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "collection": {
        "id": "",            // collection identifier, mandatory           
        "name": "",          // collection name, optional  
        "useDocsACL": bool,  // "use documents ACL" flag, optional
        "ACL": {}            // ACL settings, optional
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "collection": {
              "id": "584e852276e5e715e6ec2e8c",
              "useDocsACL": true,
              "ACL": {}
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/update"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "collection": {
        "id": "584e849e7e0b4e222480a282",
        "name": "apicoll",
        "useDocsACL": true,
        "ACL": {
            "create": [
                "R5VGMes94p"
            ],
            "read": [
                "*",
                "R5VGMes94p"
            ],
            "remove": [
                "R5VGMes94p"
            ],
            "update": [
                "R5VGMes94p"
            ]
        },
        "triggers": {
          "afterInsert": {
            "code": "",
            "isActive": false
          },
          "afterRemove": {
            "code": "",
            "isActive": false
          },
          "afterUpdate": {
            "code": "",
            "isActive": false
          },
          "beforeInsert": {
            "code": "",
            "isActive": false
          },
          "beforeRemove": {
            "code": "",
            "isActive": false
          },
          "beforeUpdate": {
            "code": "",
            "isActive": false
          }
        },
        "fields": [
          {
            "name": "readACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "updateACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "removeACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "createdAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "updatedAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          }
        ],
        "system": false,
        "indexes": []
      },
      "error": false
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

-------------------------------------------------------------------------------------

## Delete collection

**https://api.scorocode.ru/api/v1/app/collections/delete**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "collection": {
        "id": ""             // collection identifier, mandatory           
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "collection": {
                "id": "584e849e7e0b4e222480a282",
    }' "https://api.scorocode.ru/api/v1/app/collections/delete"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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


-------------------------------------------------------------------------------------

## Clone collection

**https://api.scorocode.ru/api/v1/app/collections/clone**

Method: `POST`

Headers: `Content-Type: application/json`


```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "collection": {
        "id": ""             // collection identifier, mandatory           
        "name": ""           // new collection name, mandatory
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "collection": {
                "id": "584e91b77e0b4e222480a316",
                "name": "clonedcoll"           
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/clone"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "collection": {
        "id": "584e91e70c62722cf9fe2191",
        "name": "clonedcoll",
        "useDocsACL": false,
        "ACL": {},
        "triggers": {
          "afterInsert": {
            "code": "",
            "isActive": false
          },
          "afterRemove": {
            "code": "",
            "isActive": false
          },
          "afterUpdate": {
            "code": "",
            "isActive": false
          },
          "beforeInsert": {
            "code": "",
            "isActive": false
          },
          "beforeRemove": {
            "code": "",
            "isActive": false
          },
          "beforeUpdate": {
            "code": "",
            "isActive": false
          }
        },
        "fields": [
          {
            "name": "readACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "updateACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "removeACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "createdAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "updatedAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          }
        ],
        "system": false,
        "indexes": []
      },
      "error": false
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


-------------------------------------------------------------------------------------

## Create new collection's index

**https://api.scorocode.ru/api/v1/app/collections/index/create**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "coll": "",              // collection name, mandatory
    "index": {
        "name": "",                    // index name, mandatory
        "fields": [
            {
                "name": "",            // field name, mandatory
                "order": 1 || -1       // sorting order, mandatory
            }
        ]
    }
}
```


!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "coll": "users",
            "index": {
                "name": "emailIndex",                    
                "fields": [
                    {
                        "name": "email",            
                        "order": 1       
                    }
                ]
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/index/create"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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


-------------------------------------------------------------------------------------

## Delete collection's index

**https://api.scorocode.ru/api/v1/app/collections/index/delete**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "coll": "",              // collection name, mandatory
    "index": {
        "name": ""           // index name, mandatory
    }
}
```


!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "coll": "users",
            "index": {
                "name": "emailIndex"                    
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/index/delete"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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

-------------------------------------------------------------------------------------

## Create new collection's field

**https://api.scorocode.ru/api/v1/app/collections/fields/create**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "coll": "",              // collection name, mandatory
    "collField": {     
        "name": "",          // field name, mandatory
        "type": "",          // field data type, mandatory
        "target": ""         // target collection name, mandatory for Pointer || Relation data type fields
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "coll": "users",                       
        "collField": {
            "name": "pointer",         
            "type": "Pointer",         
            "target": "devices"          
        }
    }' "https://api.scorocode.ru/api/v1/app/collections/fields/create"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "field": {
        "name": "pointer",
        "type": "Pointer",
        "target": "devices",
        "system": false,
        "readonly": false,
        "required": false
      }
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


-------------------------------------------------------------------------------------

## Delete collection's field

**https://api.scorocode.ru/api/v1/app/collections/fields/delete**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "coll": "",              // collection name, mandatory
    "collField": {   
        "name": ""           // field name, mandatory
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "coll": "users",                       
        "collField": {
            "name": "pointer"
        }
    }' "https://api.scorocode.ru/api/v1/app/collections/fields/delete"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
      "collection": {
        "id": "584e64f8982fd55332741514",
        "name": "users",
        "useDocsACL": false,
        "ACL": {
          "create": [
            "*"
          ],
          "read": [
            "*"
          ],
          "remove": [
            "*"
          ],
          "update": [
            "*"
          ]
        },
        "triggers": {
          "afterFind": {
            "code": "",
            "isActive": false
          },
          "afterInsert": {
            "code": "",
            "isActive": false
          },
          "afterRemove": {
            "code": "",
            "isActive": false
          },
          "afterUpdate": {
            "code": "",
            "isActive": false
          },
          "beforeInsert": {
            "code": "",
            "isActive": false
          },
          "beforeRemove": {
            "code": "",
            "isActive": false
          },
          "beforeUpdate": {
            "code": "",
            "isActive": false
          }
        },
        "fields": [
          {
            "name": "email",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": true,
            "required": true
          },
          {
            "name": "phone",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "readACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "updateACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "removeACL",
            "type": "ACL",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "createdAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "updatedAt",
            "type": "Date",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "username",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": false,
            "required": true
          },
          {
            "name": "password",
            "type": "Password",
            "target": "",
            "system": true,
            "readonly": false,
            "required": true
          },
          {
            "name": "emailVerified",
            "type": "Boolean",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          },
          {
            "name": "roles",
            "type": "Array",
            "target": "",
            "system": true,
            "readonly": false,
            "required": false
          },
          {
            "name": "token",
            "type": "String",
            "target": "",
            "system": true,
            "readonly": true,
            "required": false
          }
        ],
        "system": true,
        "indexes": []
      },
      "error": false
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


-------------------------------------------------------------------------------------

## Update collection's triggers

**https://api.scorocode.ru/api/v1/app/collections/triggers**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "coll": "",              // collection name, mandatory
    "triggers": {
        "beforeInsert": {      
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        },
        "afterInsert": {
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        },
        "beforeUpdate": {
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        },
        "afterUpdate": {
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        },
        "beforeRemove": {
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        },
        "afterRemove": {
            "code": "",       // trigger code, optional
            "isActive": bool  // trigger activation flag, optional
        }
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "coll": "users",                       
        "triggers": {
             "afterInsert": {
                "code": "DataManager.Insert({\n  coll:'logs', \n  doc: {\n    'docId': pool.newDoc._id,\n    'collection': 'users',\n    'operation': 'register',\n    'data': pool.newDoc\n    }\n  });",       
                "isActive": true
            }
        }
    }
    ' "https://api.scorocode.ru/api/v1/app/collections/triggers"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "triggers": {
        "afterFind": {
          "code": "",
          "isActive": false
        },
        "afterInsert": {
          "code": "DataManager.Insert({\n  coll:'logs', \n  doc: {\n    'docId': pool.newDoc._id,\n    'collection': 'users',\n    'operation': 'register',\n    'data': pool.newDoc\n    }\n  });",
          "isActive": true
        },
        "afterRemove": {
          "code": "",
          "isActive": false
        },
        "afterUpdate": {
          "code": "",
          "isActive": false
        },
        "beforeInsert": {
          "code": "",
          "isActive": false
        },
        "beforeRemove": {
          "code": "",
          "isActive": false
        },
        "beforeUpdate": {
          "code": "",
          "isActive": false
        }
      }
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


-------------------------------------------------------------------------------------

## Retreive folders and scripts list

**https://api.scorocode.ru/api/v1/app/scripts/folders**

Method: `POST`

Headers:

`Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "path": ""               // full path to directory, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "path": "/"
    }' "https://api.scorocode.ru/api/v1/app/scripts/folders"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "items": [
        {
          "_id": "",
          "name": "folder1",
          "path": "/folder1",
          "isScript": false
        },
        {
          "_id": "",
          "name": "folder2",
          "path": "/folder2",
          "isScript": false
        },
        {
          "_id": "584eb26a42d52f1ba275fdb2",
          "name": "somescript.js",
          "path": "/somescript.js",
          "isScript": true
        }
      ]
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



-------------------------------------------------------------------------------------

## Create new folder

**https://api.scorocode.ru/api/v1/app/scripts/folders/create**

Method: `POST`

Headers:

`Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "path": ""               // full path to directory, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "path": "/folder1/newfolder"
    }' "https://api.scorocode.ru/api/v1/app/scripts/folders/create"
    ```
**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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



-------------------------------------------------------------------------------------

## Delete folder

**https://api.scorocode.ru/api/v1/app/scripts/folders/delete**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "path": ""               // full path to directory, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
            "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
            "app": "48f172923acd719b42c73ac3a492cfc8",
            "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
            "coll": "users",
            "index": {
                "name": "emailIndex"                    
            }
    }' "https://api.scorocode.ru/api/v1/app/collections/index/delete"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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

-------------------------------------------------------------------------------------

## Retreive server-side script

**https://api.scorocode.ru/api/v1/app/scripts/get**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "script": ""             // server-side script identifier, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "script": "584eb54142d52f1ba275fdb3"
    }' "https://api.scorocode.ru/api/v1/app/scripts/get"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "script": {
        "_id": "584eb54142d52f1ba275fdb3",
        "appId": "584e64f8982fd55332741516",
        "name": "AYBABTU.js",
        "path": "/AYBABTU.js",
        "description": "",
        "code": "console.log(\"QWxsIHlvdXIgYmFzZSBhcmUgYmVsb25nIHRvIHVz\");",
        "jobStartAt": "2016-12-12T17:33:00+03:00",
        "isActiveJob": false,
        "jobType": "once",
        "repeat": {
          "custom": {
            "days": 0,
            "hours": 0,
            "minutes": 0
          },
          "daily": {
            "on": [],
            "hours": 0,
            "minutes": 0
          },
          "monthly": {
            "on": [],
            "days": [],
            "lastDate": false,
            "hours": 0,
            "minutes": 0
          }
        },
        "nextRun": "2016-12-12T17:33:00+03:00",
        "ACL": [
          "*"
        ]
      }
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



-------------------------------------------------------------------------------------

## Create new server-side script

**https://api.scorocode.ru/api/v1/app/scripts/create**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "cloudCode": {
        "path": ""                // full path and script name, mandatory
        "description": "",        // description, optional
        "code": "",               // server-side script code, optional
        "jobStartAt": "datetime", // timer start datetime, optional
        "isActiveJob": bool,      // timer activation flag, optional
        "jobType": "",            // timer type, optional, custom || daily || monthly
        "repeat": {               // timer repeat settings, optional
            "custom": {
                "days": int,
                "hours": int,
                "minutes": int
            },
            "daily": {
                "on": [int],
                "hours": int,
                "minutes": int
            }
            "monthly": {
                "on": [int],
                "days": [int],
                "lastDate": bool,
                "hours": int,
                "minutes": int
            }
        }
        "ACL": []                 // server-side script ACL settings, optional, array of user ids and/or "*" for anonymous access
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "cloudCode": {
            "path": "/AYBABTU.js",
            "description": "All your base",      
            "code": "console.log(\"QWxsIHlvdXIgYmFzZSBhcmUgYmVsb25nIHRvIHVz\");",             
            "jobStartAt": "2016-12-13T17:33:00+03:00", 
            "isActiveJob": false,    
            "jobType": "custom",           
            "repeat": {             
                "custom": {
                    "days": 0,
                    "hours": 0,
                    "minutes": 5
                }
            },
            "ACL": ["*"]
        }
    }' "https://api.scorocode.ru/api/v1/app/scripts/create"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "script": {
        "_id": "584fad1422a5482feb5b31ab",
        "appId": "584e64f8982fd55332741516",
        "name": "AYBABTU.js",
        "path": "/AYBABTU.js",
        "description": "All your base",
        "code": "console.log(\"QWxsIHlvdXIgYmFzZSBhcmUgYmVsb25nIHRvIHVz\");",
        "jobStartAt": "2016-12-13T17:33:00+03:00",
        "isActiveJob": false,
        "jobType": "custom",
        "repeat": {
          "custom": {
            "days": 0,
            "hours": 0,
            "minutes": 5
          },
          "daily": null,
          "monthly": null
        },
        "nextRun": "0001-01-01T00:00:00Z",
        "ACL": [
          "*"
        ]
      }
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



-------------------------------------------------------------------------------------

## Update server-side script

**https://api.scorocode.ru/api/v1/app/scripts/update**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{

    {
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "script": ""             // server-side script identifier, mandatory
    "cloudCode": {
        "path": ""                // full path and script name, mandatory
        "description": "",        // description, optional
        "code": "",               // server-side script code, optional
        "jobStartAt": "datetime", // timer start datetime, optional
        "isActiveJob": bool,      // timer activation flag, optional
        "jobType": "",            // timer type, optional, custom || daily || monthly
        "repeat": {               // timer repeat settings, optional
            "custom": {
                "days": int,
                "hours": int,
                "minutes": int
            },
            "daily": {
                "on": [int],
                "hours": int,
                "minutes": int
            }
            "monthly": {
                "on": [int],
                "days": [int],
                "lastDate": bool,
                "hours": int,
                "minutes": int
            }
        },
        "ACL": []                 // server-side script ACL settings, optional, array of user ids and/or "*" for anonymous access
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "script": "584fad1422a5482feb5b31ab",
        "cloudCode": {
            "isActiveJob": true    
        }
    }' "https://api.scorocode.ru/api/v1/app/scripts/update"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "script": {
        "_id": "584fad1422a5482feb5b31ab",
        "appId": "584e64f8982fd55332741516",
        "name": "AYBABTU.js",
        "path": "/AYBABTU.js",
        "description": "All your base",
        "code": "console.log(\"QWxsIHlvdXIgYmFzZSBhcmUgYmVsb25nIHRvIHVz\");",
        "jobStartAt": "2016-12-13T17:33:00+03:00",
        "isActiveJob": true,
        "jobType": "custom",
        "repeat": {
          "custom": {
            "days": 0,
            "hours": 0,
            "minutes": 5
          },
          "daily": null,
          "monthly": null
        },
        "nextRun": "0001-01-01T00:00:00Z",
        "ACL": [
          "*"
        ]
      }
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



-------------------------------------------------------------------------------------

## Delete server-side script

**https://api.scorocode.ru/api/v1/app/scripts/delete**

Method: `POST`

Headers:

`Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "script": ""             // server-side script identifier, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "script": "584fad1422a5482feb5b31ab"
    }' "https://api.scorocode.ru/api/v1/app/scripts/delete"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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



-------------------------------------------------------------------------------------

## Retreive bots list 

**https://api.scorocode.ru/api/v1/bots**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": ""                // access key, mandatory, masterKey only
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb"
    }' "https://api.scorocode.ru/api/v1/bots"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false,
      "items": [
        {
          "_id": "584fb8710c62722cf9fe2617",
          "name": "botobot",
          "botId": "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11",
          "appId": "584e64f8982fd55332741516",
          "scriptId": "584fb52f0c62722cf9fe2604",
          "isActive": false
        }
      ]
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



-------------------------------------------------------------------------------------

## Create new bot

**https://api.scorocode.ru/api/v1/bots/create**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "bot": {
        "name": "",          // bot name, mandatory
        "botId": "",         // telegram token you received from @BotFather, mandatory 
        "scriptId": "",      // server-side script identifier, mandatory
        "isActive": bool     // bot activation flag, optional
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "bot":{
            "name":"botobot",
            "isActive":false,
            "botId":"123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11",
            "scriptId":"584fb52f0c62722cf9fe2604"
        }
    }' "https://api.scorocode.ru/api/v1/bots/create"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
      "bot": {
        "_id": "584fb8710c62722cf9fe2617",
        "name": "botobot",
        "botId": "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11",
        "appId": "584e64f8982fd55332741516",
        "scriptId": "584fb52f0c62722cf9fe2604",
        "isActive": false
      },
      "error": false
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


-------------------------------------------------------------------------------------

## Update bot

**https://api.scorocode.ru/api/v1/bots/update**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "bot": {
        "_id": "",           // bot identifier, mandatory
        "name": "",          // bot name, optional
        "botId": "",         // telegram token you received from @BotFather, optional 
        "scriptId": "",      // server-side script identifier, optional
        "isActive": bool     // bot activation flag, optional
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "bot": {
            "_id": "584fbd067e0b4e222480a7e4",
            "name": "botobot",
            "botId": "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew12",
            "appId": "584e64f8982fd55332741516",
            "scriptId": "584fb52f0c62722cf9fe2604",
            "isActive": false
        }
    }' "https://api.scorocode.ru/api/v1/bots/update"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
      "bot": {
        "_id": "584fbd067e0b4e222480a7e4",
        "name": "botobot",
        "botId": "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew12",
        "appId": "584e64f8982fd55332741516",
        "scriptId": "584fb52f0c62722cf9fe2604",
        "isActive": false
      },
      "error": false
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


-------------------------------------------------------------------------------------

## Delete bot

**https://api.scorocode.ru/api/v1/bots/delete**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app": "",               // application identifier, mandatory
    "cli": "",               // client key, mandatory
    "acc": "",               // access key, mandatory, masterKey only
    "bot": {
        "_id": ""            // bot identifier, mandatory
    }
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "acc": "ffe86fefg25fbklacsdee8cd4c59644a",
        "app": "48f172923acd719b42c73ac3a492cfc8",
        "cli": "d6859f41223c9997ff78c6b4vb3a96bb",
        "bot": {
            "_id": "584fbd067e0b4e222480a7e4"
        }
    }' "https://api.scorocode.ru/api/v1/bots/delete"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
      "error": false
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

