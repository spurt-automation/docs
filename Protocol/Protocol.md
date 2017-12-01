# Spurt Protocol


## Connecting
If the connection originates from the localhost, there is no explicit requirement to provide authentication.
If the connection does not originate from the localhost, there is a requirement to provide authentication.

### Authentication
The connection is initialized by the client sending `open` to the server.
The server replies with either `welcome` if no authentication is required, or with `authenticate` if it requires authentication.
When the client is prompted to authenticate, it should provide a username and a password, indicated with the keywords `user` and `password` respectively.
If the username and password are correct, the server replies with `welcome`. If not, the server replies with `denied` and implicitly allows the client to try again.
If the server does not allow remote connections, it shall respond with `denied` after it recieves the `open` command.


The normal authentication flow is shown below and in [Authentication.png].
```
> open
< authenticate
> user CerebralFart
> password ********
< welcome
```
