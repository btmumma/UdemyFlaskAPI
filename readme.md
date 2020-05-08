# Mumma Flask Rest API
Created using Python, Flask-RESTful, and SQLAlchemy 

## Base URL:
https://mumma-stores-rest-api.herokuapp.com/

# Endpoints:
JWT Tokens are required through use of the /auth endpoint.
## GET items (url/items)
No Required Body/Header

Description: Returns a JSON response body of every item in the API, regardless of store.

Example Return Body: 
{
    "items": [
        {
            "name": "dog",
            "price": 59.99
        },
        {
            "name": "game",
            "price": 59.99
        }
    ]
}

## GET stores (url/stores)
No Required Body/Header

Description: Returns a JSON response body of a list of stores, and the items within them.

{
    "stores": [
        {
            "name": "test",
            "items": [
                {
                    "name": "dog",
                    "price": 59.99
                }
            ]
        },
        {
            "name": "MummaStore",
            "items": [
                {
                    "name": "game",
                    "price": 59.99
                }
            ]
        }
    ]
}

## GET stores (url/stores)
No Required Body/Header

Description: Returns a JSON response body of a list of stores, and the items within them.

{
    "stores": [
        {
            "name": "test",
            "items": [
                {
                    "name": "dog",
                    "price": 59.99
                }
            ]
        },
        {
            "name": "MummaStore",
            "items": [
                {
                    "name": "game",
                    "price": 59.99
                }
            ]
        }
    ]
}

## GET item/<name> (url/item/<name>)
Requires Authorization.
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint

Description: Returns a JSON response body with the details of a single item.

{
    "name": "dog",
    "price": 59.99
}

## GET store/<name> (url/store/<name>)
Requires Authorization.
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint

Description: Returns a JSON response body with the details of a single store, as well as the items within the store.

{
    "name": "test",
    "items": [
        {
            "name": "dog",
            "price": 59.99
        }
    ]
}


## POST store/<name> (url/store/<name>)
Requires Authorization.
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint

Description: Returns a JSON response body with the details of a newly posted store (name of the store and the items within it)

{
    "name": "mystore",
    "items": []
}

## DELETE store/<name> (url/store/<name>)
Requires Authorization.
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint

Description: Returns a JSON response body with a message, indicating the store is deleted. 

{
    "message": "Store deleted"
}

## POST items/<name> (url/items/<name>)
Headers:

Content-Type:application/json

Requires Body:



{
	"price": <Float>,
	"store_id": <(Existing Store ID Int)>
}


Description: Returns a JSON response body 201 CREATED with the body of what the user just posted. 

{
    "name": "jordan",
    "price": 120.99
}

## PUT items/<name> (url/items/<name>)
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint

Content-Type:application/json

Requires Body:



{
	"price": <Float>,
}


Description: Returns a JSON response body 200 with the body of what the user just updated. 

{
    "name": "jordan",
    "price": 110.99
}

## DELETE items/<name> (url/items/<name>)
Headers:

Authorization: JWT {token} -> This is received after POST to /auth endpoint


Description: Returns a JSON response body 200 with a message that the item was deleted. 

{
    "message": Item deleted.
}

## POST /auth (url/auth)
Headers:

Content-Type:application/json

Body -> Enter Same Credentials used in /register endpoint

{
"username": "test",
"password": "123"
}


Description: Returns a JSON response body 200 with a acess_token (this is your JWT for as long as you use that user.

{
    "access_token": <outputted here>
}

## POST /register (url/register)
Headers:

Content-Type:application/json

Body -> Enter Desired Credentials 

{
"username": "test",
"password": "123"
}


Description: Returns a JSON response body 201 with a message.

{
    "message": "User created successfully."
}
