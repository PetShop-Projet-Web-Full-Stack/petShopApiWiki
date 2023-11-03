# Confirm password

This endpoint is used to confirm the user password before sensitive information is displayed or updated.

After the user has confirmed the password, the status is stored in the session and can be checked with the endpoint [Confirm password status](Confirm-password-status.md).

<note>
    This endpoint requires authentication.
</note>

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user/confirm-password" method="POST">
    <request>
        <sample lang="JSON" title="Payload">
        {
            "password": "password"
        }
        </sample>
        <sample lang="javascript" title="JavaScript">
        const data = {
            password: "password"
        };
        </sample>
    </request>
</api-endpoint>