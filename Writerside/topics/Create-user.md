# Create user

This endpoint is used to create a new user.

<note>
    You need a CSRF token to make this request to the server use Get CSRF cookie request to get it.
</note>
> the password must be at least 8 characters long.
<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/register" method="POST">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "name": "John Doe",
            "email": "john.doe@exemple.com",
            "password": "password2023", 
            "password_confirmation": "password2023"
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            name: "John Doe",
            email: "john.doe@exempl.com",
            password: "password2023",
            password_confirmation: "password2023"
        };
        </sample>
    </request>
</api-endpoint>