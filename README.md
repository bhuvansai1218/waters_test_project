# waters-corporation-provider-artifactory


## Provider

```
provider "artifactory" {
  username = "${var.artifactory_username}"
  password = "${var.artifactory_password}"
  url      = "${var.artifactory_url}"
}
```

* `username` - (Required) Your username used to connect to Artifactory. You can
  also set this via the environment variable. `ARTIFACTORY_USER`

* `password` - (Required) Your password or an API key used to connect to Artifactory. You can
  also set this via the environment variable. `ARTIFACTORY_PASSWORD`

* `url` - (Required) The url to your Artifactory instance. This will typically be
  everything in front of the /webapp of your web console login. For instance, Artifactory
  cloud users will have a url similar to `https://youraccountname.jfrog.io/youraccountname`. You can
  also set this via the environment variable. `ARTIFACTORY_URL`
  
## Resources

### artifactory\_group

Provides support for creating groups in Artifactory. 



### artifactory\_user

Provides support for creating users in Artifactory. 

**This resource does not allow setting of the user's password**. 

Instead, a random password is generated for each user. The user should do a 
_forgot my password_ to reset their password. On updates, the password is set, 
then immediately expired. This should trigger an email to the user if Artifactory is configured to.

#### Example Usage

```
resource "artifactory_user" "Bhuvan" {
    name     = "Bhuvan.Sai"
    email    = "bhuvan.sai@outlook.com"
    is_admin = true
    groups   = [ "readers", "publishers" ]
}
```

#### Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the user.
* `email` - (Required) The user's email address.
* `is_admin` - (Optional) Does this user have admin privileges. Default `false`.
* `is_updatable` - (Optional) Can this user update their profile?. Cannot be `false` 
when is_admin is set to `true`. Default `true`.
* `groups` - (Optional) An array of groups this user belongs to.
* `realm` - (Computed) The realm the user belongs to.

---
