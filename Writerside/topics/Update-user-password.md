# Update user password

Use the Login endpoint to get the authentication token
or use forgot password endpoint to get the reset password without being authenticated.

<note>
    This endpoint requires authentication.
</note>

> the password must be at least 8 characters long.

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user/password" method="PUT">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "current_password": "password2023",
            "password": "password2024",
            "password_confirmation": "password2024"
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            current_password: "password2023",
            password: "password2024",
            password_confirmation: "password2024"
        };
        </sample>
    </request>
</api-endpoint>
