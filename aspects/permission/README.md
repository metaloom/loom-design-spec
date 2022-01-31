# ACL

## Permission Models

### RBAC

* Requires a role to be created for each new user since individual user permissions can only be mapped via a user specific role.

### RBAC + User Permissions

* Does not require a user specific role since the needed permissions can be assigned to the user instead.
* Harder caching invalidation since two areas need to be checked


### Posix Permissions

TBD


## Permission Levels

### Entity Class Level Permissions

* Coarse Permission Level
* Easier to setup
* Less permissions to check / store

### Object Level Permissions

* Fine Permission Level
* Potentially many permissions need to be stored
* Perm invalidation / caching more complex

## Requirements

* A User has only write access to its own contents.
* For object level permissions it is a must that permissions get automatically inherited.
