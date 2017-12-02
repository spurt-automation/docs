# Spurt Protocol


## Connecting
If the connection originates from the localhost, there is no explicit requirement to provide authentication.
If the connection does not originate from the localhost, it is required to provide authentication.

### Authentication
The connection is initialized by the client sending `open` to the server.
The server replies with either `welcome` if no authentication is required, or with `authenticate` if it requires authentication.
When the client is prompted to authenticate, it should provide a username and a password, indicated with the keywords `user` and `password` respectively.
If the username and password are correct, the server replies with `welcome`. If not, the server replies with `denied` and implicitly allows the client to try again.
If the server does not allow remote connections, it shall respond with `denied` after it recieves the `open` command.


The normal authentication flow is shown below and in [Authentication.png](Authentication.png).
```
< open
> authenticate
< user CerebralFart
< password ********
> welcome
```

## Commands
A command can be sent after the client has been authenticated. It might require specific levels of access to be granted.

A command only returns if it has been successfully run, giving `done` if no errors occured or `error` followed by a more descriptive text otherwise.
```
< spurt 456 name set Notify of new pull requests
> done
```
OR
```
< spurt 456 name set Notify of new pull requests
> error spurt not found
```

## Queries
A query can be sent after the client has been authenticated. It might require specific levels of access.

### Multi-line returns
Since the return of a command can span multiple lines, the return value is terminated with the keyword `done`. This should be on its own line, not followed by any other text. As such, a return might look like

```
> Line 1
> Line 2
> Line 3
> done
``` 
