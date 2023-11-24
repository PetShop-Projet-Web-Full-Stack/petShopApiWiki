# Delete user

<note>
    This endpoint is required authentication
</note>

## Description

This endpoint allows you to delete a user.

If you have an admin role, you can delete all users except the admin user.

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user" method="DELETE">
<request>
    <sample lang="javascript" title="payload">
    {
        "id": 1
    }
    </sample>
    <sample lang="javascript" title="JavaScript">
        const data = {
            id: 1
        };
    </sample>
</request>
</api-endpoint>