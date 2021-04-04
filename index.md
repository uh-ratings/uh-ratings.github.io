
<img src="doc/landing.png">

Digits is an application that allows users to:

  * Register an account.
  * Create and manage a set of contacts.
  * Add a set of timestamped notes regarding their interactions with each contact.


### Installation

First, [install Meteor](https://www.meteor.com/install).

Second, [download a copy of Digits](https://github.com/hangbozhang/digits). Note that Digits is a private repo and so you will need to request permission from the author to gain access to the repo.

Third, cd into the app/ directory of your local copy of the repo, and install third party libraries with:

```
$ meteor npm install
```

Once the libraries are installed, you can run the application by invoking:

```
$ meteor npm run start
```

The first time you run the app, it will create some default users and data. Here is the output:

```
meteor npm run start

> meteor-application-template-react@ start C:\Users\Public\github\hangbozhang\app
> meteor --no-release-check --exclude-archs web.browser.legacy,web.cordova --settings ../config/settings.development.json

[[[[[ C:\Users\Public\github\hangbozhang\digits\app ]]]]]

=> Started proxy.
=> Started MongoDB.
W20210402-22:26:10.714(-10)? (STDERR) Note: you are using a pure-JavaScript implementation of bcrypt.
W20210402-22:26:10.811(-10)? (STDERR) While this implementation will work correctly, it is known to be
W20210402-22:26:10.812(-10)? (STDERR) approximately three times slower than the native implementation.
W20210402-22:26:10.813(-10)? (STDERR) In order to use the native implementation instead, run
W20210402-22:26:10.813(-10)? (STDERR) 
W20210402-22:26:10.814(-10)? (STDERR)   meteor npm install --save bcrypt
W20210402-22:26:10.814(-10)? (STDERR) 
W20210402-22:26:10.815(-10)? (STDERR) in the root directory of your application.
I20210402-22:26:12.166(-10)? Creating the default user(s)
I20210402-22:26:12.167(-10)?   Creating user admin@foo.com.
I20210402-22:26:12.395(-10)?   Creating user john@foo.com.
I20210402-22:26:12.641(-10)? Creating default Contacts.
I20210402-22:26:12.642(-10)?   Adding: Johnson (john@foo.com)
I20210402-22:26:12.678(-10)?   Adding: Casanova (john@foo.com)
I20210402-22:26:12.681(-10)?   Adding: Binsted (admin@foo.com)
I20210402-22:26:12.768(-10)? Monti APM: completed instrumenting the app
=> Started your app.

=> App running at: http://localhost:3000/
   Type Control-C twice to stop.
```
**Note regarding "bcrypt warning"**. You will also get the following message when you run this application:

```
Note: you are using a pure-JavaScript implementation of bcrypt.
While this implementation will work correctly, it is known to be
approximately three times slower than the native implementation.
In order to use the native implementation instead, run

  meteor npm install --save bcrypt

in the root directory of your application.
```

On some operating systems (particularly Windows), installing bcrypt is much more difficult than implied by the above message. Bcrypt is only used in Meteor for password checking, so the performance implications are negligible until your site has very high traffic. You can safely ignore this warning without any problems during initial stages of development.

If all goes well, the template application will appear at [http://localhost:3000](http://localhost:3000).  You can login using the credentials in [settings.development.json](https://github.com/hangbozhang/digits/blob/master/config/settings.development.json), or else register a new account.

Lastly, you can run ESLint over the code in the imports/ directory with:

```
meteor npm run lint
```

## User Interface Walkthrough

#### Landing page

When you first bring up the application, you will see the landing page that provides a brief introduction to the capabilities of Digits:

<img src="doc/landing.png">

The next step is to use the Login menu to either Login to an existing account or register a new account.

#### Register

If you do not yet have an account on the system, you can register by clicking on "Login", then "Sign up":

<img src="doc/register.png">

#### Sign in

Click on the Login link, then click on the Signin link to bring up the Sign In page which allows you to login:

<img src="doc/signin.png">

#### User home page

After successfully logging in, the system takes you to your home page. It is just like the landing page, but the NavBar contains links to list contact and add new contacts:After successfully logging in, the system takes you to your home page. It is just like the landing page, but the NavBar contains links to list contact and add new contacts:

<img src="doc/home.png">

#### List Contacts

Clicking on the List Contacts link brings up a page that lists all of the contacts associated with the logged in user:

<img src="doc/list-contacts.png">

This page also allows the user to add timestamped “notes” detailing interactions they’ve had with the Contact. For example:

<img src="doc/list-contacts-note.png">

#### Edit Contacts

From the List Contacts page, the user can click the “Edit” link associated with any Contact to bring up a page that allows that Contact information to be edited:

<img src="doc/edit-contact.png">

#### Admin mode

It is possible to designate one or more users as “Admins” through the settings file. When a user has the Admin role, they get access to a special NavBar link that retrieves a page listing all Contacts associated with all users:

<img src="doc/admin-page.png">
