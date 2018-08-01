---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation by Jacob Nouwatin</a>

search: true
---

# Welcome to the Book A Meal API

Welcome to the Book A Meal API Documentation! You can use our API to access Book A Meal API endpoints, which can get information on various Meals on Menu in our database. Users(Caterer) can perform various actions like Sign Up, Sign In, Add Meal, Edit Meal, Delete Meal, and other features.

# Authentication

Book A Meal platform needs users to be authenticated to be able to perform the actions specified above. On a successful sign up or sign in, a token is generated which gives users access to this privileges.

## Sign up

###Request

* Sign up end point: POST ```/api/v1/auth/signup```
* Body (```application/json```)

###Response
* Status: 201 Created
* Message: Registration successful
* Body (```application/json```)

###This end point is used to register/create a new user

###HTTP Request
POST ```https://book-a-meal-v1.herokuapp.com/api/v1/auth/signup```

###Response codes when error occurs on sign up
 HTTP Status Code | Message 
-------------- | -------------- 
400 | User credentials required / validation errors 
409 | email or password already exists 

> Customer Request:

```javascript
{
  "firstName": "Kareem",
  "lastName": "Aderibigbe",
  "email": "customer2@gmail.com",
  "password": "password",
  "confirmPassword": "password"
  "userType": "customer"
}
```
> Customer Response:

```javascript
{
    "message": "Registration Successful",
    "user": {
        "id": 5,
        "email": "customer2@gmail.com",
        "userType": "customer",
        "lastName": "Aderibigbe"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiZW1haWwiOiJjdXN0b21lcjJAZ21haWwuY29tIiwidXNlclR5cGUiOiJjdXN0b21lciIsImxhc3ROYW1lIjoiQWRlcm9iaWdiZSIsImlhdCI6MTUzMDQzMjE5NiwiZXhwIjoxNTMwNTE4NTk2fQ.clrZAIbJiZOGFVCI8fQf_8EUSqh3OobfZwVHUlFw_jE"
}
```

> Caterer Request:

```javascript
{
  "businessName": "Yakoyo Restaurant",
  "ownerName": "Ben Olowonla",
  "businessAddress": "12, Adigbe str. Kosoko, Lagos"
  "email": "caterer2@gmail.com",
  "password": "password",
  "confirmPassword": "password"
  "userType": "caterer"
}
````
> Caterer Response:

```javascript
{
    "message": "Registration Successful",
    "user": {
        "id": 6,
        "email": "caterer2@gmail.com",
        "userType": "caterer",
        "businessName": "Yakoyo Restaurant",
        "businessAddress": "12, Adigbe str. Kosoko, Lagos",
        "ownerName": "Ben Olowonla"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NiwiZW1haWwiOiJjYXRlcmVyMkBnbWFpbC5jb20iLCJ1c2VyVHlwZSI6ImNhdGVyZXIiLCJidXNpbmVzc05hbWUiOiJZYWtveW8gUmVzdGF1cmFudCIsImJ1c2luZXNzQWRkcmVzcyI6IjEyLCBBZGlnYmUgc3RyLiBLb3Nva28sIExhZ29zIiwib3duZXJOYW1lIjoiQmVuIE9sb3dvbmxhIiwiaWF0IjoxNTMwNDMyODkwLCJleHAiOjE1MzA1MTkyOTB9.qcjTfbix48pTCgznph2EsgjurDS9KH31k6Pn66GOEaY"
}
```

##Sign in

###Request
* Sign in end point: POST ```/api/v1/auth/login ```
* Body (```application/json```)

###HTTP Request
POST ```https://book-a-meal-v1.herokuapp.com/api/v1/auth/login```

###Response
* Status: 200 Successful
* Message: Log in successful
* Body (```application/json```)

###This end point is used to sign in a user

###Response codes when error occurs on sign in
HTTP Status Code | Message 
-------------- | -------------- 
400 | Invalid login credentials / validation errors 
404 | Invalid credentials 


> Request:

```javascript
{
  "email": "caterer2@gmail.com",
  "password": "password"
}
````
> Response:

```javascript
{
    "message": "Log in successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NiwiZW1haWwiOiJjYXRlcmVyMkBnbWFpbC5jb20iLCJ1c2VyVHlwZSI6ImNhdGVyZXIiLCJpYXQiOjE1MzA0MzQ3ODd9.5LpQS7LCGTGF0-MaGM6wWNa37YwHKr-pSr65KBw0Uq0",
    "user": {
        "id": 6,
        "email": "caterer2@gmail.com",
        "userType": "caterer"
    }
}
```

# Meals

## Add Meal

###Request
* Add Meal end point: POST ```/api/v1/meals ```
* Body (```application/json```)

###HTTP Request
POST ```https://book-a-meal-v1.herokuapp.com/api/v1/meals```

###Response
* Status: 201 Created
* Message: Meal Created Successfully
* Body (```application/json```)

###This end point is used to add meal by the caterer

###Response codes when error occurs on adding meal
HTTP Status Code | Message 
-------------- | -------------- 
400 | Meal exist / validation errors

> Request:

```javascript
{
  "name": "Yam and Egg",
  "price": "2000",
  "image": "yamegg.png"
}
````
> Response:

```javascript
{
    "message": "Meal Created Successfully",
    "newMeal": 
    {
      "name": "Yam and Egg",
      "price": "2000",
      "image": "yamegg.png"
    }
}
```

## Modify Meal

###Request
* Modify Meal end point: PUT ```/api/v1/meals ```
* Body (```application/json```)

###HTTP Request
PUT ```https://book-a-meal-v1.herokuapp.com/api/v1/meals```

###Response
* Status: 200 Successful
* Message: Meal successfully updated
* Body (```application/json```)

###This end point is used to modify an existing meal

###Response codes when error occurs on modify meal
HTTP Status Code | Message 
-------------- | -------------- 
400 | Meal Not Found / validation errors / Error processing request

> Request:

```javascript
{
  "name": "Yam and Egg",
  "price": "2000",
  "image": "yamegg.png"
}
````
> Response:

```javascript
{
    "message": "Meal successfully updated",
    "meal": 
    {
      "name": "Yam and Egg",
      "price": "2000",
      "image": "yamegg.png"
    }
}
```

## Get A Meal

###Request
* Get Meal end point: GET ```/api/v1/meals/:id ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/meals/:id```

###Response
* Status: 200 Successful
* Message: Meal Details
* Body (```application/json```)

###This end point is used to get a meal

###Response codes when error occurs on get a meal
HTTP Status Code | Message 
-------------- | -------------- 
400 | Provide valid meal id / Error processing request

> Response:

```javascript
{
    "message": "Meal Details",
    "meal": 
    {
      "name": "Yam and Egg",
      "price": "2000",
      "image": "yamegg.png"
    }
}
```

## Delete A Meal

###Request
* Delete A Meal end point: DELETE ```/api/v1/meals/:id ```
* Body (```application/json```)

###HTTP Request
DELETE ```https://book-a-meal-v1.herokuapp.com/api/v1/meals:id```

###Response
* Status: 200 Successful
* Message: Meal successfully deleted
* Body (```application/json```)

###This end point is used to delete a meal

###Response codes when error occurs on delete a meal
HTTP Status Code | Message 
-------------- | -------------- 
400 | Provide valid meal id / You have no access to edit this meal / Error processing request

> Response:

```javascript
{
    "message": "Meal successfully deleted",
}
````

## Get a Caterer Meals

###Request
* Get Meals end point: GET ```/api/v1/meals ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/meals```

###Response
* Status: 200 Successful
* Message: All meals displayed
* Body (```application/json```)

###This end point is used to get a caterer meals

###Response codes when error occurs on get a get a caterer meals
HTTP Status Code | Message 
-------------- | -------------- 
400 | No meal found / Error processing request

> Response:

```javascript
{
    "message": "All meals displayed",
    "meals": [
      "meal": 
      {
        "name": "Yam and Egg",
        "price": "2000",
        "image": "yamegg.png"
      }
    ]
}
````

# Menu

## Set Menu

###Request
* Set MENU end point: POST ```/api/v1/menu ```
* Body (```application/json```)

###HTTP Request
POST ```https://book-a-meal-v1.herokuapp.com/api/v1/menu```

###Response
* Status: 200 Successful
* Message: Meals added to Menu
* Body (```application/json```)

###This end point is used to set menu

###Response codes when error occurs on set menu
HTTP Status Code | Message 
-------------- | -------------- 
400 | No meal found / Error processing request

> Request:

```javascript
{
  "menuDate": "2018-06-15",
  "mealId": [5]
}
````

> Response:

```javascript
{
    "message": "Meals added to Menu",
    "menu": {
        "id": 2,
        "menuDate": "2018-06-20T00:00:00.000Z",
        "userId": 2,
        "updatedAt": "2018-07-03T05:11:06.697Z",
        "createdAt": "2018-07-03T05:11:06.697Z"
    },
    "meals": [
        {
            "id": 5,
            "name": "Akamu and Akara",
            "price": 2500,
            "image": "https://res.cloudinary.com/sansaristic/image/upload/v1530594643/BookMeal/1530594641558pexels-photo-247685.png.png",
            "userId": 2,
            "createdAt": "2018-07-03T05:10:44.356Z",
            "updatedAt": "2018-07-03T05:10:44.356Z"
        }
    ]
}
````

## Get Menu

###Request
* Set MENU end point: GET ```/api/v1/menu ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/menu```

###This end point is used to get menu

###Response codes when error occurs on get menu
HTTP Status Code | Message 
-------------- | -------------- 
400 | The Date must be of format YYYY-MM-DD / Error processing request

> Request:

```javascript
{
  "menuDate": "2018-07-15"
}
````

> Response:

```javascript
{
  "message": "Menu for this Date",
    "dateMenu": [
        {
            "id": 1,
            "menuDate": "2018-07-15T00:00:00.000Z",
            "userId": 2,
            "createdAt": "2018-07-15T21:41:35.608Z",
            "updatedAt": "2018-07-15T21:41:35.608Z",
            "Meals": [
                {
                    "id": 1,
                    "name": "Fried Rice and chicken",
                    "price": 3500,
                    "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690817/BookMeal/1531690792726pexels-photo-247685.png.png",
                    "userId": 2,
                    "createdAt": "2018-07-15T21:40:20.014Z",
                    "updatedAt": "2018-07-15T21:40:20.014Z"
                },
                {
                    "id": 2,
                    "name": "Beans and Garri",
                    "price": 1500,
                    "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
                    "userId": 2,
                    "createdAt": "2018-07-15T21:40:55.256Z",
                    "updatedAt": "2018-07-15T21:40:55.256Z"
                }
            ]
        }
    ]
}
````

# Order

## Make Order

###Request
* Make ORDER end point: POST ```/api/v1/orders ```
* Body (```application/json```)

###HTTP Request
POST ```https://book-a-meal-v1.herokuapp.com/api/v1/orders```

###This end point is used to make an order

###Response codes when error occurs on make order
HTTP Status Code | Message 
-------------- | -------------- 
400 | This meal is not on this menu / Error processing request / validation errors

> Request:

```javascript
{
  "quantity": 2,
  "mealId": 2,
  "menuId": 1
}
````

> Response:

```javascript
{
  "message": "Order placed successfully",
    "order": {
        "id": 3,
        "mealId": 2,
        "userId": 1,
        "menuId": 1,
        "quantity": 2,
        "updatedAt": "2018-07-23T10:23:59.495Z",
        "createdAt": "2018-07-23T10:23:59.495Z",
        "meal": {
            "id": 2,
            "name": "Beans and Garri",
            "price": 1500,
            "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
            "userId": 2,
            "createdAt": "2018-07-15T21:40:55.256Z",
            "updatedAt": "2018-07-15T21:40:55.256Z"
        }
    }
}
````

## Modify an Order

###Request
* Modify an ORDER end point: PUT ```/api/v1/orders/:id ```
* Body (```application/json```)

###HTTP Request
PUT ```https://book-a-meal-v1.herokuapp.com/api/v1/orders/:id```

###This end point is used to modify an order

###Response codes when error occurs on modify an order
HTTP Status Code | Message 
-------------- | -------------- 
400 | This Order does not belong to this user / Error processing request / This meal is not on this menu / validation errors

> Request:

```javascript
{
  "quantity": 3,
}
````

> Response:

```javascript
{
  "message": "Order modified successfully",
    "modifiedOrder": {
        "id": 3,
        "mealId": "2",
        "menuId": "1",
        "userId": 1,
        "quantity": "3",
        "createdAt": "2018-07-23T10:23:59.495Z",
        "updatedAt": "2018-07-23T10:56:09.337Z",
        "meal": {
            "id": 2,
            "name": "Beans and Garri",
            "price": 1500,
            "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
            "userId": 2,
            "createdAt": "2018-07-15T21:40:55.256Z",
            "updatedAt": "2018-07-15T21:40:55.256Z"
        }
    }
}
````

## Get an Order

###Request
* Get an ORDER end point: GET ```/api/v1/order/:id ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/orders/:id```

###This end point is used to get an order

###Response codes when error occurs on get an order
HTTP Status Code | Message 
-------------- | -------------- 
400 | Order does not exist / Error processing request 

> Response:

```javascript
{
  
    "message": "Order details",
    "order": {
        "id": 3,
        "mealId": 2,
        "menuId": 1,
        "userId": 1,
        "quantity": 3,
        "createdAt": "2018-07-23T10:23:59.495Z",
        "updatedAt": "2018-07-23T10:56:09.337Z",
        "Meal": {
            "id": 2,
            "name": "Beans and Garri",
            "price": 1500,
            "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
            "userId": 2,
            "createdAt": "2018-07-15T21:40:55.256Z",
            "updatedAt": "2018-07-15T21:40:55.256Z"
        },
        "User": {
            "id": 1,
            "email": "kareem@gmail.com",
            "password": "$2a$10$VnVPQvRwb0OTj4PlLEK9xer44ozFLj0PeuYNBkSJieGcl0wfrIlty",
            "firstName": "Kareem",
            "lastName": "Aderobigbe",
            "businessName": null,
            "ownerName": null,
            "businessAddress": null,
            "userType": "customer",
            "createdAt": "2018-07-15T21:31:52.862Z",
            "updatedAt": "2018-07-15T21:31:52.862Z"
        }
    }
}
````

## Get Customer Orders

###Request
* Get a Customer ORDER end point: GET ```/api/v1/user-orders ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/user-orders```

###This end point is used to Get Customer Orders

###Response codes when error occurs on Get Customer Orders
HTTP Status Code | Message 
-------------- | -------------- 
400 | Error processing request 

> Response:

```javascript
{
    "message": "Orders gotten successfully",
    "orders": [
        {
            "id": 2,
            "mealId": 1,
            "menuId": 1,
            "userId": 1,
            "quantity": 2,
            "createdAt": "2018-07-15T21:43:33.393Z",
            "updatedAt": "2018-07-15T21:43:33.393Z",
            "Meal": {
                "id": 1,
                "name": "Fried Rice and chicken",
                "price": 3500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690817/BookMeal/1531690792726pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:20.014Z",
                "updatedAt": "2018-07-15T21:40:20.014Z"
            }
        },
        {
            "id": 3,
            "mealId": 2,
            "menuId": 1,
            "userId": 1,
            "quantity": 3,
            "createdAt": "2018-07-23T10:23:59.495Z",
            "updatedAt": "2018-07-23T10:56:09.337Z",
            "Meal": {
                "id": 2,
                "name": "Beans and Garri",
                "price": 1500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:55.256Z",
                "updatedAt": "2018-07-15T21:40:55.256Z"
            }
        },
        {
            "id": 1,
            "mealId": 2,
            "menuId": 1,
            "userId": 1,
            "quantity": 4,
            "createdAt": "2018-07-15T21:43:09.120Z",
            "updatedAt": "2018-07-15T21:43:09.120Z",
            "Meal": {
                "id": 2,
                "name": "Beans and Garri",
                "price": 1500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:55.256Z",
                "updatedAt": "2018-07-15T21:40:55.256Z"
            }
        }
    ]
}
````

## Get a Caterer Orders

###Request
* Get a Caterer ORDER end point: GET ```/api/v1/orders ```
* Body (```application/json```)

###HTTP Request
GET ```https://book-a-meal-v1.herokuapp.com/api/v1/orders```

###This end point is used to Get a Caterer Orders

###Response codes when error occurs on Get a Caterer Orders
HTTP Status Code | Message 
-------------- | -------------- 
400 | Error processing request 

> Response:

```javascript
{
    "message": "All Orders",
    "orders": [
        {
            "id": 2,
            "mealId": 1,
            "menuId": 1,
            "userId": 1,
            "quantity": 2,
            "createdAt": "2018-07-15T21:43:33.393Z",
            "updatedAt": "2018-07-15T21:43:33.393Z",
            "Meal": {
                "id": 1,
                "name": "Fried Rice and chicken",
                "price": 3500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690817/BookMeal/1531690792726pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:20.014Z",
                "updatedAt": "2018-07-15T21:40:20.014Z"
            },
            "User": {
                "id": 1,
                "email": "kareem@gmail.com",
                "password": "$2a$10$VnVPQvRwb0OTj4PlLEK9xer44ozFLj0PeuYNBkSJieGcl0wfrIlty",
                "firstName": "Kareem",
                "lastName": "Aderobigbe",
                "businessName": null,
                "ownerName": null,
                "businessAddress": null,
                "userType": "customer",
                "createdAt": "2018-07-15T21:31:52.862Z",
                "updatedAt": "2018-07-15T21:31:52.862Z"
            }
        },
        {
            "id": 1,
            "mealId": 2,
            "menuId": 1,
            "userId": 1,
            "quantity": 4,
            "createdAt": "2018-07-15T21:43:09.120Z",
            "updatedAt": "2018-07-15T21:43:09.120Z",
            "Meal": {
                "id": 2,
                "name": "Beans and Garri",
                "price": 1500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:55.256Z",
                "updatedAt": "2018-07-15T21:40:55.256Z"
            },
            "User": {
                "id": 1,
                "email": "kareem@gmail.com",
                "password": "$2a$10$VnVPQvRwb0OTj4PlLEK9xer44ozFLj0PeuYNBkSJieGcl0wfrIlty",
                "firstName": "Kareem",
                "lastName": "Aderobigbe",
                "businessName": null,
                "ownerName": null,
                "businessAddress": null,
                "userType": "customer",
                "createdAt": "2018-07-15T21:31:52.862Z",
                "updatedAt": "2018-07-15T21:31:52.862Z"
            }
        },
        {
            "id": 3,
            "mealId": 2,
            "menuId": 1,
            "userId": 1,
            "quantity": 3,
            "createdAt": "2018-07-23T10:23:59.495Z",
            "updatedAt": "2018-07-23T10:56:09.337Z",
            "Meal": {
                "id": 2,
                "name": "Beans and Garri",
                "price": 1500,
                "image": "https://res.cloudinary.com/sansaristic/image/upload/v1531690854/BookMeal/1531690851816pexels-photo-247685.png.png",
                "userId": 2,
                "createdAt": "2018-07-15T21:40:55.256Z",
                "updatedAt": "2018-07-15T21:40:55.256Z"
            },
            "User": {
                "id": 1,
                "email": "kareem@gmail.com",
                "password": "$2a$10$VnVPQvRwb0OTj4PlLEK9xer44ozFLj0PeuYNBkSJieGcl0wfrIlty",
                "firstName": "Kareem",
                "lastName": "Aderobigbe",
                "businessName": null,
                "ownerName": null,
                "businessAddress": null,
                "userType": "customer",
                "createdAt": "2018-07-15T21:31:52.862Z",
                "updatedAt": "2018-07-15T21:31:52.862Z"
            }
        }
    ]
}
````
