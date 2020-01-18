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
  "account_type": "personal",
  "first_login": true
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
    "id": 2,
    "mobile": "98787888",
    "email": "amanpreetbh@gmail.com",
    "account_type": "personal",
    "is_active": true,
    "first_login": true,
    "user_id": 2,
    "first_name": "aman",
    "last_name": "sharma",
    "business_name": null,
    "business_speciality": null,
    "contact_person_name": null,
    "address": "jalandhar",
    "city": "jal",
    "province": "jij",
    "postal_code": "27",
    "country": "india",
    "dob": "12",
    "image": null,
    "business_website_url": null
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

`Use the user_id column value to do any operation`

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



## Change Password First Time

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
     "error": "Error while changing password.Please try again later."
}

```

Update user Password when user is logged in for first time

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/changeTemporaryPassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
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


## Update/Save User Image

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
     "error": "Image can't be blank"
}

```

Update or save user image.

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/updateImage`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
image | String | photo of  user

<aside class="success">
 User must be authorized to change password.Send user token in the header.
</aside>


## Update User Info

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
     "msg": 0
}

```

Update user credentials

### HTTP Request

`POST https://remindmee.herokuapp.com/v1/updateUser`


For Personal => `address,city,province,postal_code,country,dob,first_name,last_name`

For Business => `address,city,province,postal_code,country,dob,business_name,business_speciality, contact_person_name,business_website_url`


### HTTP Request

`POST https://remindmee.herokuapp.com/v1/updateUser`

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


#  Reminder/Event

## Create Reminder/Event


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
     "error": "Title Can't be blank"
}

```

This endpoint will save a new event/reminder.


### HTTP Request

`POST https://remindmee.herokuapp.com/v1/events`

### Query Parameters

See the example Object

<aside class="success">
 Send Data in the below formar
</aside>

```json
  {
  "title": "new task",
  "description": "dummy",
  "event_start": "2020-01-17 10:31:08 +0530",
  "event_end": "2020-01-17 10:31:08 +0530",
  "event_type": "event",  // or 'reminder'
  "is_recurring": true,
  "street_name": "test",
  "unit_suite": "test",
  "city": "test",
  "state": "test",
  "postal_code": "test",
  "invitees": [
    "shilpa@gmail.com",
    "aman@gmail.com"
  ],
  "reminder_setting": "2",  // days count
  "schedule": {
    "frequency": "weekly",
    "interval": 2,
    "day_of_month": "null",
    "month_of_year": "null",
    "recurrence_until": "2020-01-28",
    "days_of_week": {
      "monday": true,
      "tuesday": true,
      "wednesday": false,
      "thursday": false,
      "friday": false,
      "saturday": false,
      "sunday": false
    }
  }
}
```
