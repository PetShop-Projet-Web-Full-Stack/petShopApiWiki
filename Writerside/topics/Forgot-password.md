# Forgot password

This endpoint is used to send a reset password link to the user email.
if the user is authenticated, use the endpoint [Update user password](Update-user-password.md) to update the password

<note>
    This endpoint does not require authentication.
</note>

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/forgot-password" method="POST">
<request>
<sample lang="JSON" title="Payload">
{
    "email": "john.doe@exempl.com"
}
</sample>
<sample lang="javascript" title="JavaScript">
cosnt data = {
    email: "john.doe@exempl.com"
};
</sample>
</request>
</api-endpoint>