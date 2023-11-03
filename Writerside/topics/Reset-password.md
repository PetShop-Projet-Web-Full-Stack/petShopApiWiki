# Reset password

This endpoint is used to reset the user password authenticated.

If the user is not authenticated use the [Forgot password](Forgot-password.md) endpoint.

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/reset-password" method="POST">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "email": "john.doe@exempl.com",
            "password": "password2023",
            "password_confirmation: "password2023",
            "token": "Token from the email link",
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            email: "john.doe@exempl.com",
            password: "password2023",
            password_confirmation: "password2023",
            token: "Token from the email link",
        };
        </sample>
    </request>
</api-endpoint>