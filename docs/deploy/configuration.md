# Configuration

### Configuration Variables

These config vars are used to define the behaviour of Gavel. There are descriptions tagged to these fields that provide some context. 

#### IGNORE_CONFIG_FILE

This field **must** be set to true in order for any of these config items to work as environment variables.

#### ADMIN_PASSWORD

This item controls the password to the administrator account for gavel. Make sure that this is a secure password, and kept secret. An easy way to get a secure password is this [Random Key Generator](https://randomkeygen.com/). More details about the admin panel can be found [here](/administration).

#### BASE_URL

This defines the base URL of the Gavel application. The app uses this primarily to fill information in correspondence. The base url of apps on heroku is `https://<app-name>.herokuapp.com/`. However, you can customize this to something like `https://judge.hackdfw.com` through heroku by using the steps provided [on the heroku custom domains page](https://devcenter.heroku.com/articles/custom-domains).

#### DISABLE_EMAIL

Setting this to false will disallow the app from sending emails to judges. This **must** be set to true in order to send emails of any kind. Please read more about email configuration below. Notably in the [EMAIL_PROVIDER](#emailprovider) section.

#### EMAIL_PROVIDER

This field defines the service that gavel will use to send emails. Currently, the only services that are available are [smtp](), [mailgun](), and [sendgrid](). Each service requires certain other fields to be populated as detailed below:

| SMTP                                    | MAILGUN                                 | SENDGRID                                |
| :-------------------------------------- | :-------------------------------------- | :-------------------------------------- |
| [DISABLE_EMAIL](#disable-email) = false | [DISABLE_EMAIL](#disable-email) = false | [DISABLE_EMAIL](#disable-email) = false |
| [BASE_URL](#base-url)                   | [BASE_URL](#base-url)                   | [BASE_URL](#base-url)                   |
| [EMAIL_FROM](#email-from)               | [EMAIL_FROM](#email-from)               | [EMAIL_FROM](#email-from)               |
| [EMAIL_HOST](#email-host)               | [MAILGUN_API_KEY](#mailgun-api-key)     | [SENDGRID_API_KEY](#sendgrid-api-key)   |
| [EMAIL_PORT](#email-port)               | [MAILGUN_DOMAIN](#mailgun-domain)       |                                         |
| [EMAIL_USER](#email-user)               |
| [EMAIL_PASSWORD](#email-password)       |

**Please ensure that the `EMAIL_PROVIDER` field is populated with either `smtp`, `mailgun`, or `sendgrid`.**

#### EMAIL_FROM

Email addresses sent from the [email provider](#emailprovider) will be sent from this address. This email address must be valid and an address that the **email provider can successfully send from**. All valid email providers are dependent on this variable.

#### EMAIL_HOST

This should be populated with the SMTP host that you want gavel to use. This is giong to vary depending on the email provider you use. By defualt, it is `smtp.gmail.com` which is the SMTP host for gmail. To authenticate SMTP, please see [EMAIL_USER](#emailuser), and [EMAIL_PASSWORD](#emailpassword). 

#### EMAIL_USER

This is the username that is used to authenticate [EMAIL_HOST](#email-host), alongside [EMAIL_PASSWORD](#email-password).

#### EMAIL_PASSWORD

This is the password to authenticate SMTP using [EMAIL_HOST](#email-host), and [EMAIL_PASSWORD](#email-password).

#### EMAIL_PORT

This is the SMTP port that will be appended to [EMAIL_HOST](#email-host) to authenticate SMTP.

#### MAILGUN_API_KEY

This is the API Key that mailgun uses to authenticate the [MAILGUN_DOMAIN](#mailgun-domain).

#### MAILGUN_DOMAIN

This is the mailgun domain that is authenticated using [MAILGUN_API_KEY](#mailgun-api-key).

#### SENDGRID_API_KEY

This is the API key that Gavel uses to authenticate the sendgrid service.

#### SECRET_KEY

The secret key is used to hash requests and CSRF tokens. This must be a long, randomly generated alphanumeric string to be effective.

#### VIRTUAL_EVENT

This defines whether your gavel instance is set up for judging a virtual event. Setting this to true produces embedded demo videos and long project description in gavel. Optimized for judging on a computer rather than mobile phone.
