# API Reference

The API reference is a technical document that describes how to use the API.
The API documentation is a user guide that
explains how to use the API.
The API reference is a subset of the API documentation.

## API Documentation

Discover all possibilities of the API.
The API documentation is a user guide that explains how to use the API.

All features of the API are documented in the subtopics of this topic.

lest go to the [Creation user](Create-user.md) topic.

## API authentication

This api uses [Laravel Sanctum](https://laravel.com/docs/10.x/sanctum) for authentication.
Read the next section for more information about authentication in javascript and axios.

Debug the api with [Postman](https://www.postman.com/) read the tutorial [use Postman with Sanctum](TutorialPostman.md)
for more information about authentication in Postman and explains to set up the tool for work with Sanctum.

## Request with axios for auth with Sanctum 3 & fortify

It Is a simple example of using axios with Sanctum 3 & fortify for authentication.
For more information about Sanctum 3 & fortify read the [Laravel Sanctum](https://laravel.com/docs/10.x/sanctum)

### Use axios with default config for request main api

<warning>
    Use axios version 1.3.3 for work with this example of code.
</warning>

install axios

```shell
npm i axios@1.3.3
```

Instance of axios with default config for request main api

```javascript
import axios from 'axios';

// instace of axios with default config for request main api
const RequestApi = axios.create({
  baseURL: 'http://localhost/',
  headers: {
    'Content-Type': 'application/json',
    'Accept': 'application/json',
    'Access-Control-Allow-Origin': 'localhost:5173', // value of dotenv variable SANCTUM_STATEFUL_DOMAINS
  },
  withCredentials: true, // for work with cross domain exemple : localhost
});
```

#### Example function for register user

```javascript
/**
 * Register User
 * @param object {name, email, password, password_confirmation} user info
 * @return {Promise<void>} user info
 */
async function register({name, email, password, password_confirmation}) {
  try {
    // Set CSRF cookie
    await RequestApi.get('sanctum/csrf-cookie');

    // register user
    await RequestApi.post('api/register', {
      name: name,
      email: email,
      password: password,
      password_confirmation: password_confirmation
    })

    const response = await RequestApi.post('api/user')

    return response.data

  } catch (error) {
    console.error(error);
  }
}
```

#### Example function for login user

```javascript
/**
 * login user with email and password
 * @param email
 * @param password
 * @return {Promise<any>} user info
 */
async function login(email, password) {
  try {
    // Set CSRF cookie
    await RequestApi.get('sanctum/csrf-cookie');

    // login user with email and password
    await RequestApi.post('api/login', {
      email: email,
      password: password
    })

    // get user info
    const response = await RequestApi.get('api/user');
    return response.data
  } catch (error) {
    console.error(error);
  }
}
```

#### Example function for logout user

```javascript
/**
 * logout user
 */
async function logout() {
  try {
    // logout user
    await RequestApi.post('api/logout');
  } catch (error) {
    console.error(error);
  }
}
```