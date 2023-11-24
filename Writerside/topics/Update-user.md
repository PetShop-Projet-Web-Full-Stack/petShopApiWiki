# Update user

<note>
    This endpoint is required authentication
</note>

## Description

This endpoint allows you to update a user data.

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user/profile-information" method="PUT">
<request>
    <sample lang="javascript" title="payload">
    {
        "name": "John Doe",
        "email": "john.doe@mail.com",
    }
    </sample>
    <sample lang="javascript" title="JavaScript">
        const data = {
            name: "John Doe",
            email: "john.doe@mail.com",
        };
    </sample>
</request>
</api-endpoint>