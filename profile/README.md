# API Documentation
Description of each API endpoint used in this app is listed here.
The type of resource is listed along with a short description.
Any params or config objects are shown too along with response schema.
Examples are also shown in JavaScript.

## Authorization
### POST `api/v1/users/sign_in`
The sign in is a POST request that takes in a params object.
When the user is signed in, a JWT is returned.

| Params        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| email      | string | User's email (Required) |
| password      | string      | User's password (Required) |

Example of sign in (JS) using axios:
```javascript
const params = {
      user: {
        email: "test1@test.com",
        password: "12345",
      },
    };
const response = await authApi.post('api/v1/users/sign_in', params);
```
| Successful Response        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| data      | JSON | "Successfully authenticated" |
| status      | integer      | 200 OK |
| authorization | string | The JWT |

| Unsuccessful Response        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| data      | JSON | "Wrong password or username" |
| status      | integer      | 401 Unauthorized |



### GET `api/v1/users/sign_out`
The sign out is a GET request that takes in a config object.
When the user is signed out, the JWT is removed from app state and async storage.

| Config        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| Authorization      | string | JWT (Required) |

Example of sign out (JS) using axios:
```javascript
const config = {
  headers: {
    Authorization: "JWT goes here",
  },
};
const response = await authApi.get('api/v1/users/sign_out', config);
```
| Successful Response        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| data      | JSON | "Successfully Signed Out" |
| status      | integer      | 200 OK |

## Casa Cases
### GET `api/v1/casa_cases`
This route fetches (gets) all current casa cases for the signed in user. No params required. The JWT is required for every request.

| Config        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| Authorization      | string | JWT (Required) |

Example of fetching casa cases (JS) using axios:
```javascript
const config = {
  headers: {
    Authorization: "JWT goes here",
    'Content-Type': 'application/json',
    Accept: 'application/json',
  },
};
const response = await authApi.get('api/v1/casa_cases', config);
```

| Successful Response        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| data      | JSON array of objects | [{...}, {...}, {...}...] |
| status      | integer      | 200 OK |


## Case Contacts
### GET `api/v1/casa_contacts`
This route fetches (gets) all current casa cases for the signed in user. No params required. The JWT is required for every request.

| Config        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| Authorization      | string | JWT (Required) |

Example of fetching casa cases (JS) using axios:
```javascript
const config = {
  headers: {
    Authorization: "JWT goes here",
    'Content-Type': 'application/json',
    Accept: 'application/json',
  },
};
const response = await authApi.get('api/v1/case_contacts', config);
```

| Successful Response        | Type           | Description |
| ------------- |:-------------:| :-------------: |
| data      | JSON array of objects | [{...}, {...}, {...}...] |
| status      | integer      | 200 OK |
<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
