# Confirm password status

This endpoint is used for rechecking the password confirmation status,
after the user has confirmed the password, the status is stored in the session with the endpoint [Confirm password](Confirm-password.md).

<note>
    This endpoint requires authentication.
</note>

<api-endpoint openapi-path="./../openapi.yaml" endpoint="/api/user/confirmed-password-status" method="GET">
</api-endpoint>