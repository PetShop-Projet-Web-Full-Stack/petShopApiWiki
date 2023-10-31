# Tutorial to use Postman with Laravel Sanctum

## Introduction

Discovery how to use Postman with Laravel Sanctum

in this tutorial we will use the [PetShopApi](Default-topic.md) as an example

> Install Postman or use the web
>
version [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/1a0b3b2b9b8b2b2b2b2b)

## Create a new environment in Postman
1. Click on the gear icon in the left sidebar
   ![Create a new environment in Postman](go-to-env-postman.png)
2. Click on the Add button '+'
3. Name your environment
4. Add a new variable named 'xsrf-token' don't insert any value
5. And select the environment you just created in the dropdown menu in the top right corner
   ![Select the environment you just created in the dropdown menu in the top right corner](select-new-postman.png)

## Create a new collection in Postman
1. Click on the left sidebar select the 'Collections' tab and click on the Add button '+'
2. Choose a blank collection and name it (ex : PetShopApi)
3. In the variables tab add a new variable named 'base_url' and set the value to 'http://localhost:8000/api' or the
   url of your api
4. Go to the 'Pre-request-Script' tab and add the following code
    ```javascript
    pm.sendRequest({
        url: pm.variables.get('base_url') + '/sanctum/csrf-cookie',
        method: 'GET',
        header: {
            'Accept': 'application/json',
            'Content-Type': 'application/json',
        },
    }, function (err, res) {
        pm.variables.set('xsrf-token', res.cookies[0].value);
    });
    ```
   <note>
     This code will get the csrf token and set it in the environment variable 'xsrf-token' after each request
   </note>

## Create a new request in Postman
1. On the left sidebar select the 'Collections' tab and click on the collection you just created
2. Click on the more options button '...' and select 'Add Request'
3. Name your request (ex : get user)
4. Select the request method (ex : get)
5. Set the url to http://localhost:8000/ or the url of your api and add the endpoint (ex : /api/user)
    <warning> Don't forget to add the base_url variable because the server
   will not be able to set cookies </warning>
6. Go to the 'Headers' tab and add the following headers
    ```text
    Accept: application/json
    Content-Type: application/json
    Referer: {{base_url}} 
    X-XSRF-TOKEN: {{xsrf-token}}
    ```
    - Referer is used to set the referer header set into environment
      variable [SANCTUM_STATEFUL_DOMAINS](QuickStarter.md#configure-your-sanctum-domain)

   <note>
     The X-XSRF-TOKEN header is used to send the csrf token to the server
   </note>
   <warning> If referer is not set in the header you will get a 403 error</warning>

You can now send your request and get the response