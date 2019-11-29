---
title: Remind me API docs

language_tabs: # must be one of https://git.io/vQNgJ
  - Ruby

toc_footers:
  - <a href='http://nugeninfo.com'>Remind me API Docs</a>

search: true
---

# Introduction

Remind me Api Docs

# Login-Signup

## Signup - Create User


> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Email already taken"
}

```

This endpoint will save a new user.
Send below params for different account types

For Personal => `address,city,province,postal_code,country,dob,first_name,last_name`

For Business => `address,city,province,postal_code,country,dob,business_name,business_speciality, contact_person_name,business_website_url`


### HTTP Request

`POST https://remindmee.herokuapp.com/v1/users`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
mobile | String | Mobile number of user
account_type | String | 'personal' or 'business'
email | String | User email
address | String | address of user
city | String | city of user
province | String | province of user
postal_code | String | postal code of user
country | String | country of user
dob | String | Date of birth
first_name | String | First name
last_name | String | Last name
business_name | String | Bussiness name
business_speciality | String | Business Speciality
business_website_url | String | Website url
contact_person_name | String | Contact person name

<aside class="success">
 Send Data in the below formar
</aside>

`{
  "email": "shilpasyal55@gmail.com",
  "mobile": "98787888",
  "account_type": "personal",
  "userdetail_attributes":{
    "first_name": "shilpaa",
    "last_name": "syal",
    "address": "jalandhar",
    "city":"jal",
    "province": "jij",
    "postal_code": "27",
    "country": "india",
    "dob": "12"
  } 
}`


## Login - Authentication

> Success-Response:

```json

HTTP 200 OK
{
  "token": "7dhf8hfjhdjf8rrhjdjfhdf844",
  "msg": 1,
  "account_type": "personal"
}

```

> Error-Response

```json
HTTP 401 Unprocessable entity
{
     "msg": 0,
     "error": "Email/Password doesnot match"
}

```

Login/Authenticate User.

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/login`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Email of user
password | String | Password of user


## Fetch Single User

> Success-Response:

```json

HTTP 200 OK
{
    "id": 1,
    "mobile": "98787888",
    "email": "shilpasyal55@gmail.com",
    "account_type": "personal",
    "is_active": true,
    "created_at": "2019-11-29T13:41:34.581Z",
    "updated_at": "2019-11-29T13:41:34.581Z"
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Unable to find detail"
}

```

Fetch single user detail

### HTTP Request

`GET https://remindmee.herokuapp.com/v1/getUser`

### Query Parameters

No Parameter

<aside class="success">
 User must be authorized to fetch data.Send user token in the header.
</aside>

## Update Password

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Your password was incorrect"
}

```

Update user Password when user is logged in

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/changePassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
old_password | String | Old Password of the user
new_password | String | New Password of the user

<aside class="success">
 User must be authorized to change password.Send user token in the header.
</aside>

## Send Code for Forgot Password

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Email not present in our database"
}

```

To reset password, Api will send code for resetting the password.

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/forgotPassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
mobile | String | Registered Mobile number of user


## Change Password (Forgot Password)

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Email not present in our database"
}

```

Change Password

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/updatePassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
code | String | Code sent to the registered mobile number
password | String | New Password

