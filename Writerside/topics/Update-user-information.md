# Update user information

Change the user profile information.

For changing the password use [Update user password](Update-user-password.md) endpoint.

<note>
    This endpoint requires authentication.
</note>

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user/profile-information" method="PUT">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "name": "John Doe",
            "email": "john.doe@exempl.com",
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            name: "John Doe",
            email: "john.doe@exempl.com",
        };
        </sample>
    </request>
</api-endpoint>