# Login

This endpoint is used to authenticate a user with email and password.

<note>
    You need a CSRF token to make this request to the server use Get CSRF cookie request to get it.
</note>

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/login" method="post">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "email": "john.doe@exemple.com",
            "password": "password2023",
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            email: "john.doe@exemple.com",
            password: "password2023",
        };
        </sample>
    </request>
</api-endpoint>

Authentication with email and password