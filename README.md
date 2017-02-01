Welcome friends to the Github Repo based on the wonderful project:

https://github.com/sahat/hackathon-starter

<img src="signin.png">

LinkedIn OAuth:

<img src="linkedin-auth.png">

Google OAuth:

<img src="google.png">

FB User Page (once logged in):

<img src="fbpage.png">

LinkedIn User Page (once logged in):

<img src="linkedinpage.png">

**Live Demo**: http://ampingit.herokuapp.com/login


- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Obtaining API Keys](#obtaining-api-keys)

- [FAQ](#faq)
- [How It Works](#how-it-works-mini-guides)
- [Cheatsheets](#cheatsheets)
    - [ES6](#-es6-cheatsheet)
    - [JavaScript Date](#-javascript-date-cheatsheet)
    - [Mongoose Cheatsheet](#mongoose-cheatsheet)
- [Deployment](#deployment)
- [Changelog](#changelog)
- [Contributing](#contributing)
- [License](#license)

Features
--------

- **Local Authentication** using Email and Password
- **OAuth 1.0a Authentication** via Twitter
- **OAuth 2.0 Authentication** via Facebook, Google, GitHub, LinkedIn, Instagram
- Flash notifications
- MVC Project Structure
- Node.js clusters support
- Sass stylesheets (auto-compiled via middleware)
- Bootstrap 3 + Extra Themes
- Contact Form (powered by Mailgun, Sendgrid or Mandrill)
- **Account Management**
 - Gravatar
 - Profile Details
 - Change Password
 - Forgot Password
 - Reset Password
 - Link multiple OAuth strategies to one account
 - Delete Account
- CSRF protection
- **API Examples**: Facebook, Foursquare, Last.fm, Tumblr, Twitter, Stripe, LinkedIn and more.

Getting Started
---------------

The easiest way to get started is to clone the repository:

```bash
# Get the latest snapshot
git clone --depth=1 https://github.com/sahat/hackathon-starter.git myproject

# Change directory
cd myproject

# Install NPM dependencies
npm install

# Or, if you prefer to use `yarn` instead of `npm`
yarn install

# Then simply start your app
node app.js
```

**Note:** I highly recommend installing [Nodemon](https://github.com/remy/nodemon).
It watches for any changes in your  node.js app and automatically restarts the
server. Once installed, instead of `node app.js` use `nodemon app.js`. It will
save you a lot of time in the long run, because you won't need to manually
restart the server each time you make a small change in code. To install, run
`sudo npm install -g nodemon`.


Obtaining API Keys
------------------

To use any of the included APIs or OAuth authentication methods, you will need
to obtain appropriate credentials: Client ID, Client Secret, API Key, or
Username & Password. You will need to go through each provider to generate new
credentials.

**Hackathon Starter 2.0 Update:** I have included dummy keys and passwords for
all API examples to get you up and running even faster. But don't forget to update
them with *your credentials* when you are ready to deploy an app.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/1000px-Google_2015_logo.svg.png" width="200">
- Visit <a href="https://cloud.google.com/console/project" target="_blank">Google Cloud Console</a>
- Click on the **Create Project** button
- Enter *Project Name*, then click on **Create** button
- Then click on *APIs & auth* in the sidebar and select *API* tab
- Click on **Google+ API** under *Social APIs*, then click **Enable API**
- Next, under *APIs & auth* in the sidebar click on *Credentials* tab
- Click on **Create new Client ID** button
- Select *Web Application* and click on **Configure Consent Screen**
- Fill out the required fields then click on **Save**
- In the *Create Client ID* modal dialog:
 - **Application Type**: Web Application
 - **Authorized Javascript origins**: http://localhost:3000
 - **Authorized redirect URI**: http://localhost:3000/auth/google/callback
- Click on **Create Client ID** button
- Copy and paste *Client ID* and *Client secret* keys into `.env`

**Note:** When you ready to deploy to production don't forget to
add your new url to *Authorized Javascript origins* and *Authorized redirect URI*,
e.g. `http://my-awesome-app.herokuapp.com` and
`http://my-awesome-app.herokuapp.com/auth/google/callback` respectively.
The same goes for other providers.

<hr>

<img src="http://www.doit.ba/img/facebook.jpg" width="200">
- Visit <a href="https://developers.facebook.com/" target="_blank">Facebook Developers</a>
- Click **My Apps**, then select **Add a New App* from the dropdown menu
- Select **Website** platform and enter a new name for your app
- Click on the **Create New Facebook App ID** button
- Choose a **Category** that best describes your app
- Click on **Create App ID** button
- In the upper right corner click on **Skip Quick Star**
- Copy and paste *App ID* and *App Secret* keys into `.env`
 - **Note:** *App ID* is **clientID**, *App Secret* is **clientSecret**
- Click on the *Settings* tab in the left nav, then click on **+ Add Platform**
- Select **Website**
- Enter `http://localhost:3000` under *Site URL*

**Note:** After a successful sign in with Facebook, a user will be redirected back to home page with appended hash `#_=_` in the URL. It is *not* a bug. See this [Stack Overflow](https://stackoverflow.com/questions/7131909/facebook-callback-appends-to-return-url) discussion for ways to handle it.

<hr>

<img src="https://github.global.ssl.fastly.net/images/modules/logos_page/GitHub-Logo.png" width="200">
- Go to <a href="https://github.com/settings/profile" target="_blank">Account Settings</a>
- Select **Applications** from the sidebar
- Then inside **Developer applications** click on **Register new application**
- Enter *Application Name* and *Homepage URL*
- For *Authorization Callback URL*: http://localhost:3000/auth/github/callback
- Click **Register application**
- Now copy and paste *Client ID* and *Client Secret* keys into `.env` file

<hr>

<img src="https://g.twimg.com/ios_homescreen_icon.png" width="90">
- Sign in at <a href="https://apps.twitter.com/" target="_blank">https://apps.twitter.com</a>
- Click **Create a new application**
- Enter your application name, website and description
- For **Callback URL**: http://127.0.0.1:3000/auth/twitter/callback
- Go to **Settings** tab
- Under *Application Type* select **Read and Write** access
- Check the box **Allow this application to be used to Sign in with Twitter**
- Click **Update this Twitter's applications settings**
- Copy and paste *Consumer Key* and *Consumer Secret* keys into `.env` file

<hr>

<img src="http://www.danpontefract.com/wp-content/uploads/2014/02/logo-linkedin.png" width="200">
- Sign in at <a href="https://developer.linkedin.com/" target="_blank">LinkedIn Developer Network</a>
- From the account name dropdown menu select **API Keys**
 - *It may ask you to sign in once again*
- Click **+ Add New Application** button
- Fill out all the *required* fields
 - **OAuth 2.0 Redirect URLs**: http://localhost:3000/auth/linkedin/callback
 - **JavaScript API Domains**: http://localhost:3000
- For **Default Application Permissions** make sure at least the following is checked:
 - `r_basicprofile`
- Finish by clicking **Add Application** button
- Copy and paste *API Key* and *Secret Key* keys into `.env` file
 - *API Key* is your **clientID**
 - *Secret Key* is your **clientSecret**

<hr>

Project Structure
-----------------

| Name                               | Description                                                  |
| ---------------------------------- | ------------------------------------------------------------ |
| **config**/passport.js             | Passport Local and OAuth strategies, plus login middleware.  |
| **controllers**/api.js             | Controller for /api route and all api examples.              |
| **controllers**/contact.js         | Controller for contact form.                                 |
| **controllers**/home.js            | Controller for home page (index).                            |
| **controllers**/user.js            | Controller for user account management.                      |
| **models**/User.js                 | Mongoose schema and model for User.                          |
| **public**/                        | Static assets (fonts, css, js, img).                         |
| **public**/**js**/application.js   | Specify client-side JavaScript dependencies.                 |
| **public**/**js**/main.js          | Place your client-side JavaScript here.                      |
| **public**/**css**/main.scss       | Main stylesheet for your app.                                |
| **public/css/themes**/default.scss | Some Bootstrap overrides to make it look prettier.           |
| **views/account**/                 | Templates for *login, password reset, signup, profile*.      |
| **views/api**/                     | Templates for API Examples.                                  |
| **views/partials**/flash.pug       | Error, info and success flash notifications.                 |
| **views/partials**/header.pug      | Navbar partial template.                                     |
| **views/partials**/footer.pug      | Footer partial template.                                     |
| **views**/layout.pug               | Base template.                                               |
| **views**/home.pug                 | Home page template.                                          |
| .env.example                       | Your API keys, tokens, passwords and database URI.           |
| app.js                             | The main application file.                                   |
| package.json                       | NPM dependencies.                                            |
| yarn.lock                          | Contains exact versions of NPM dependencies in package.json. |

**Note:** There is no preference how you name or structure your views.
You could place all your templates in a top-level `views` directory without
having a nested folder structure, if that makes things easier for you.
Just don't forget to update `extends ../layout`  and corresponding
`res.render()` paths in controllers.



FAQ
---

### How do I switch SendGrid for another email delivery service, like Mailgun or SparkPost?
Inside the `nodemailer.createTransport` method arguments, simply change the service from `'Sendgrid'` to some other email service. Also, be sure to update both username and password below that. See the [list of all supported services](https://github.com/nodemailer/nodemailer-wellknown#supported-services) by Nodemailer.

<hr>

`partials/flash.pug` is a partial template that contains how flash messages
are formatted. Previously, flash
messages were scattered throughout each view that used flash messages
(contact, login, signup, profile), but now, thankfully it is uses a *DRY* approach.

The flash messages partial template is *included* in the `layout.pug`, along with footer and navigation.
```jade
body
    include partials/header

    .container
      include partials/flash
      block content

    include partials/footer
```

<hr>

### How do I create a new page?
A more correct way to be to say "How do I create a new route". The main file `app.js` contains all the routes.
Each route has a callback function associated with it. Sometimes you will see 3 or more arguments
to routes. In cases like that, the first argument is still a URL string, while middle arguments
are what's called middleware. Think of middleware as a door. If this door prevents you from
continuing forward, you won't get to your callback function. One such example is a route that requires authentication.

```js
app.get('/account', passportConfig.isAuthenticated, userController.getAccount);
```

It always goes from left to right. A user visits `/account` page. Then `isAuthenticated` middleware
checks if you are authenticated:

```js
exports.isAuthenticated = (req, res, next) => {
  if (req.isAuthenticated()) {
    return next();
  }
  res.redirect('/login');
};
```

If you are authenticated, you let this visitor pass through your "door" by calling `return next();`. It then proceeds to the
next middleware until it reaches the last argument, which is a callback function that typically renders a template on `GET` requests or redirects on `POST` requests. In this case, if you are authenticated, you will be redirected to *Account Management* page, otherwise you will be redirected to *Login* page.

```js
exports.getAccount = (req, res) => {
  res.render('account/profile', {
    title: 'Account Management'
  });
};
```

<hr>

###Mongoose Cheatsheet

#### Find all users:
```js
User.find((err, users) => {
  console.log(users);
});
```

#### Find a user by email:
```js
let userEmail = 'example@gmail.com';
User.findOne({ email: userEmail }, (err, user) => {
  console.log(user);
});
```

#### Find 5 most recent user accounts:
```js
User
  .find()
  .sort({ _id: -1 })
  .limit(5)
  .exec((err, users) => {
    console.log(users);
  });
```

#### Get total count of a field from all documents:
Let's suppose that each user has a `votes` field and you would like to count
the total number of votes in your database across all users. One very
inefficient way would be to loop through each document and manually accumulate
the count. Or you could use [MongoDB Aggregation Framework](https://docs.mongodb.org/manual/core/aggregation-introduction/) instead:

```js
User.aggregate({ $group: { _id: null, total: { $sum: '$votes' } } }, (err, votesCount)  => {
  console.log(votesCount.total);
});
```
:top: <sub>[**back to top**](#table-of-contents)</sub>

Deployment
----------

Once you are ready to deploy your app, you will need to create an account with
a cloud platform to host it. These are not the only choices, but they are my top
picks. From my experience, **Heroku** is the easiest to get started with, it will
automatically restart your Node.js process when it crashes, zero-downtime
deployments and custom domain support on free accounts. Additionally, you can
create an account with **mLab** and then pick one of the *4* providers below.
Again, there are plenty of other choices and you are not limited to just the ones
listed below.

### 1-Step Deployment with Heroku

<img src="http://blog.exadel.com/wp-content/uploads/2013/10/heroku-Logo-1.jpg" width="200">
- Download and install [Heroku Toolbelt](https://toolbelt.heroku.com/)
- In terminal, run `heroku login` and enter your Heroku credentials
- From *your app* directory run `heroku create`
- Run `heroku addons:create mongolab`.  This will set up the mLab add-on and configure the `MONGOLAB_URI` environment variable in your Heroku app for you.
- Lastly, do `git push heroku master`.  Done!

**Note:** To install Heroku add-ons your account must be verified.

---

<img src="http://i.imgur.com/7KnCa5a.png" width="200">
- Open [mlab.com](https://mlab.com) website
- Click the yellow **Sign up** button
- Fill in your user information then hit **Create account**
- From the dashboard, click on **:zap:Create new** button
- Select **any** cloud provider (I usually go with AWS)
- Under *Plan* click on **Single-node (development)** tab and select **Sandbox** (it's free)
 - *Leave MongoDB version as is - `2.4.x`*
- Enter *Database name** for your web app
- Then click on **:zap:Create new MongoDB deployment** button
- Now, to access your database you need to create a DB user
- Click to the recently created database
- You should see the following message:
 - *A database user is required to connect to this database.* **Click here** *to create a new one.*
- Click the link and fill in **DB Username** and **DB Password** fields
- Finally, in `.env` instead of `mongodb://localhost:27017/test`, use the following URI with your credentials:
 - `db: 'mongodb://USERNAME:PASSWORD@ds027479.mongolab.com:27479/DATABASE_NAME'`

**Note:** As an alternative to mLab, there is also [Compose](https://www.compose.io/).


<img src="http://www.opencloudconf.com/images/openshift_logo.png" width="200">
- First, install this Ruby gem: `sudo gem install rhc` :gem:
- Run `rhc login` and enter your OpenShift credentials
- From your app directory run `rhc app create MyApp nodejs-0.10`
 - **Note:** *MyApp* is the name of your app (no spaces)
- Once that is done, you will be provided with **URL**, **SSH** and **Git Remote** links
- Visit provided **URL** and you should see the *Welcome to your Node.js application on OpenShift* page
- Copy and and paste **Git Remote** into `git remote add openshift YOUR_GIT_REMOTE`
- Before you push your app, you need to do a few modifications to your code

Add these two lines to `app.js`, just place them anywhere before `app.listen()`:
```js
var IP_ADDRESS = process.env.OPENSHIFT_NODEJS_IP || '127.0.0.1';
var PORT = process.env.OPENSHIFT_NODEJS_PORT || 8080;
```

Then change `app.listen()` to:
```js
app.listen(PORT, IP_ADDRESS,() => {
  console.log(`Express server listening on port ${PORT} in ${app.settings.env} mode`);
});
```
Add this to `package.json`, after *name* and *version*. This is necessary because, by default, OpenShift looks for `server.js` file. And by specifying `supervisor app.js` it will automatically restart the server when node.js process crashes.

```js
"main": "app.js",
"scripts": {
  "start": "supervisor app.js"
},
```

- Finally, you can now push your code to OpenShift by running `git push -f openshift master`
 - **Note:** The first time you run this command, you have to pass `-f` (force) flag because OpenShift creates a dummy server with the welcome page when you create a new Node.js app. Passing `-f` flag will override everything with your *Hackathon Starter* project repository. **Do not** run `git pull` as it will create unnecessary merge conflicts.
- And you are done!

<img src="https://upload.wikimedia.org/wikipedia/commons/f/ff/Windows_Azure_logo.png" width="200">

- Login to [Windows Azure Management Portal](https://manage.windowsazure.com/)
- Click the **+ NEW** button on the bottom left of the portal
- Click **COMPUTE**, then **WEB APP**, then **QUICK CREATE**
- Enter a name for **URL** and select the datacenter **REGION** for your web site
- Click on **CREATE WEB APP** button
- Once the web site status changes to *Running*, click on the name of the web site to access the Dashboard
- At the bottom right of the Quickstart page, select **Set up a deployment from source control**
- Select **Local Git repository** from the list, and then click the arrow
- To enable Git publishing, Azure will ask you to create a user name and password
- Once the Git repository is ready, you will be presented with a **GIT URL**
- Inside your *Hackathon Starter* directory, run `git remote add azure [Azure Git URL]`
- To push your changes simply run `git push azure master`
 - **Note:** *You will be prompted for the password you created earlier*
- On **Deployments** tab of your Windows Azure Web App, you will see the deployment history

<img src="http://www.comparethecloud.net/wp-content/uploads/2014/06/ibm-bluemix_pr-030514.jpg" width="200">

- Go to [Codename: Bluemix](http://bluemix.net) to signup for the free trial, or login with your *IBM id*
- Install [Cloud Foundry CLI](https://github.com/cloudfoundry/cli)
- Navigate to your **hackathon-starter** directory and then run `cf push [your-app-name] -m 512m` command to deploy the application
 - **Note:** You must specify a unique application name in place of `[your-app-name]`
- Run `cf create-service mongodb 100 [your-service-name]` to create a [MongoDB service](https://www.ng.bluemix.net/docs/#services/MongoDB/index.html#MongoDB)
- Run `cf bind-service [your-app-name] [your-service-name]` to associate your application with a service created above
- Run `cf files [your-app-name] logs/env.log` to see the *environment variables created for MongoDB.
- Copy the **MongoDB URI** that should look something like the following: `mongodb://68638358-a3c6-42a1-bae9-645b607d55e8:46fb97e6-5ce7-4146-9a5d-d623c64ff1fe@192.155.243.23:10123/db`
- Then set it as an environment variable for your application by running `cf set-env [your-app-name] MONGODB_URI [your-mongodb-uri]`
- Run `cf restart [your-app-name]` for the changes to take effect.
- Visit your starter app at **http://[your-app-name].ng.bluemix.net**
- Done!

**Note:** Alternative directions, including how to setup the project with a DevOps pipeline are available at [http://ibm.biz/hackstart](http://ibm.biz/hackstart).
A longer version of these instructions with screenshots is available at [http://ibm.biz/hackstart2](http://ibm.biz/hackstart2).
Also, be sure to check out the [Jump-start your hackathon efforts with DevOps Services and Bluemix](https://www.youtube.com/watch?v=twvyqRnutss) video.

---

<img src="https://avatars2.githubusercontent.com/u/2810941?v=3&s=64" width="64" align="left">

# Google Cloud Platform

- [Download and install Node.js](https://nodejs.org/)
- [Select or create](https://console.cloud.google.com/project) a Google Cloud Platform Console project
- [Enable billing](https://support.google.com/cloud/answer/6293499#enable-billing) for your project (there's a $300 free trial)
- Install and initialize the [Google Cloud SDK](https://cloud.google.com/sdk/docs/quickstarts)
- Create an `app.yaml` file at the root of your `hackathon-starter` folder with the following contents:

    ```yaml
    runtime: nodejs
    vm: true
    manual_scaling:
      instances: 1
    ```
- Make sure you've set `MONGODB_URI` or `MONGOLAB_URI` in `.env.example`
- Run the following command to deploy the `hackathon-starter` app:

    ```bash
    gcloud app deploy
    ```
- [Monitor your deployed app](https://console.cloud.google.com/appengine) in the Cloud Console
- [View the logs](https://console.cloud.google.com/logs/viewer) for your app in the Cloud Console

Changelog
---------

### 4.3.0 (November 6, 2016)
- [Added new theme](http://demos.creative-tim.com/get-shit-done/index.html) by Creative Tim (Thanks @conacelelena)
- Added ESLint configuration to *package.json*
- Added *yarn.lock* (Thanks @niallobrien)
- Added **express-status-monitor** (to see it in action: `/status`)
- Added missing error handling checks (Thanks @dskrepps)
- Server address during the app startup is now clickable (⌘ + LMB) (Thanks @niallobrien)
- Fixed redirect issue in the account page (Thanks @YasharF)
- Fixed `Mongoose.promise` issue (Thanks @starcharles)
- Removed "My Friends" from Facebook API example due to Graph API changes
- Removed iOS7 theme
- `User` model unit tests improvements (Thanks @andela-rekemezie)
- Switched from **github-api** to the more popular **github** NPM module
- Updated Yarn and NPM dependencies

### 4.2.1 (September 6, 2016)
- User model minor code refactoring
- Fixed gravatar display issue on the profile page
- Pretty terminal logs for database connection and app server
- Added compiled *main.css* to *.gitignore*

### 4.2.0 (August 21, 2016)
- Converted templates from jade to pug (See [Rename from "Jade"](https://github.com/pugjs/pug#rename-from-jade))

### 4.1.1 (August 20, 2016)
- Updated dependencies

### 4.1.0 (July 23, 2016)
- Improved redirect logic after login [#435](https://github.com/sahat/hackathon-starter/pull/435)
- Removed Venmo API (see [Venmo Halts New Developer Access To Its API](https://techcrunch.com/2016/02/26/how-not-to-run-a-platform/))
- Removed BitGo API due to issues with `secp256k1` dependency on Windows

### 4.0.1 (May 17, 2016)
- Renamed `MONGODB` to `MONGODB_URI` environment variable
- Set engine `"node": "6.1.0"` in *package.json*

### 4.0.0 (May 13, 2016)
- **ECMAScript 2015 support!** (Make sure you are using Node.js 6.0+)
 - Thanks  @vanshady and @prashcr
- Added `<meta theme-color>` support for *Chrome for Android*
- Added Yahoo Finance API example
- Updated Aviary API example
- Flash an error message when updating email to that which is already taken
- Removing an email address during profile update is no longer possible
- PayPal API example now uses *return_url* and *cancel_url* from `.env`
- Added client-side `required=true` attributes to input fields 
- Fixed broken `show()` function in the GitHub API example
- Fixed YQL query in the Yahoo Weather API example
- Fixed *Can't set headers after they are sent* error in Stripe API example
- Code refactoring and cleanup
- Updated Travis-CI Node.js version
- Updated NPM dependencies
- Removed Mandrill references

### 3.5.0 (March 4, 2016)
- Added file upload example
- Added Pinterest API example
- Added timestamp support to the User schema
- Fixed `next` parameter being *undefined* inside `getReset` handler
- Refactored querysting param usage in *api.js* controller
- Removed *setup.js* (generator) due to its limited functionality and a lack of updates

### 3.4.1 (February 6, 2016)
- Added "Obtaining Twilio API Keys" instructions.
- Updated Bootstrap v3.3.6.
- Updated jQuery v2.2.0.
- Updated Font Awesome v4.5.0.
- Removed `debug` and `outputStyle` from the Sass middleware options.
- Removed `connect-assets` (no longer used) from *package.json*`.
- Fixed Font Awesome icon syntax error in *profile.jade*.
- Fixed Cheerio broken link.

### 3.4.0 (January 5, 2016)
- Use `dontenv` package for managing API keys and secrets.
- Removed *secrets.js* (replaced by *.env.example*).
- Added .env to .gitignore.
- Fixed broken Aviary API image.

### 3.3.1 (December 25, 2015)
- Use `connect-mongo` ES5 fallback for backward-compatibility with Node.js version `< 4.0`.

### 3.3.0 (December 19, 2015)
- Steam authorization via OpenID.
- Code style update. (No longer use "one-liners" without braces)
- Updated LinkedIn scope from `r_fullprofile` to `r_basicprofile` due to API changes.
- Added LICENSE file.
- Removed [Bitcore](https://bitcore.io/) example due to installation issues on Windows 10.


### 3.2.0 (October 19, 2015)
- Added Google Analytics script.
- Split *api.js* `require` intro declaration and initialization for better performance. (See <a href="https://github.com/sahat/hackathon-starter/issues/247">#247</a>)
- Removed [ionicons](http://ionicons.com).
- Removed [connect-assets](https://github.com/adunkman/connect-assets). (Replaced by [node-sass-middleware](https://github.com/sass/node-sass-middleware))
- Fixed alignment styling on /login, /profile and /account
- Fixed Stripe API `POST` request.
- Converted LESS to Sass stylesheets.
- Set `node_js` version to "stable" in *.travis.yml*.
- Removed `mocha.opts` file, pass options directly to package.json
- README cleanup and fixes.
- Updated Font Awesome to 4.4.0

### 3.1.0 (August 25, 2015)
- Added Bitcore example.
- Added Bitgo example.
- Lots of README fixes.
- Fixed Google OAuth profile image url.
- Fixed a bug where `connect-assets` served all JS assets twice.
- Fixed missing `csrf` token in the Twilio API example form.
- Removed `multer` middleware.
- Removed Ordrx API. (Shutdown)

### 3.0.3 (May 14, 2015)
- Added favicon.
- Fixed an email issue with Google login.

### 3.0.2 (March 31, 2015)
- Renamed `navbar.jade` to `header.jade`.
- Fixed typos in README. Thanks @josephahn and @rstormsf.
- Fix radio button alignment on small screens in Profile page.
- Increased `bcrypt.genSalt()` from **5** to **10**.
- Updated package dependencies.
- Updated Font Awesome `4.3.0`.
- Updated Bootstrap `3.3.4`.
- Removed Ionicons.
- Removed unused `User` variable in *controllers/api.js*.
- Removed Nodejitsu instructions from README.

### 3.0.1 (February 23, 2015)
- Reverted Sass to LESS stylesheets. See <a href="https://github.com/sahat/hackathon-starter/issues/233">#233</a>.
- Convert email to lower case in Passport's LocalStrategy during login.
- New Lob API.
- Updated Font Awesome to 4.3.0
- Updated Bootstrap and Flatly theme to 3.3.2.

### 3.0.0 (January 11, 2015)
- New Ordr.in API example.
- Brought back PayPal API example.
- Added `xframe` and xssProtection` protection via **lusca** module.
- No more CSRF route whitelisting, either enable or dsiable it globally.
- Simplified "remember original destination" middleware.
 - Instead of excluding certain routes, you now have to "opt-in" for the routes you wish to remember for a redirect after successful authentication.
- Converted LESS to Sass.
- Updated Bootstrap to 3.3.1 and Font Awesome to 4.2.0.
- Updated jQuery to 2.1.3 and Bootstrap to 3.3.1 JS files.
- Updated Ionicons to 2.0.
- Faster travis-ci builds using `sudo: false`.
- Fixed YUI url on Yahoo API example.
- Fixed `mongo-connect` deprecation warning.
- Code cleanup throughout the project.
- Updated `secrets.js` notice.
- Simplified the generator (`setup.js`), no longer removes auth providers.
- Added `git remote rm origin` to Getting Started instructions in README.

### 2.4.0 (November 8, 2014)
- Bootstrap 3.3.0.
- Flatly 3.3.0 theme.
- User model cleanup.
- Removed `helperContext` from connect-assets middleware.

### 2.3.4 (October 27, 2014)
- Font Awesome 4.2.0 [01e7bd5c09926911ca856fe4990e6067d9148694](https://github.com/sahat/hackathon-starter/commit/01e7bd5c09926911ca856fe4990e6067d9148694)
- Code cleanup in `app.js` and `controllers/api.js`. [8ce48f767c0146062296685cc101acf3d5d224d9](https://github.com/sahat/hackathon-starter/commit/8ce48f767c0146062296685cc101acf3d5d224d9) [cdbb9d1888a96bbba92d4d14deec99a8acba2618](https://github.com/sahat/hackathon-starter/commit/cdbb9d1888a96bbba92d4d14deec99a8acba2618)
- Updated Stripe API example. [afef373cd57b6a44bf856eb093e8f2801fc2dbe2](https://github.com/sahat/hackathon-starter/commit/afef373cd57b6a44bf856eb093e8f2801fc2dbe2)
- Added 1-step deployment process with Heroku and mLab add-on. [c5def7b7b3b98462e9a2e7896dc11aaec1a48b3f](https://github.com/sahat/hackathon-starter/commit/c5def7b7b3b98462e9a2e7896dc11aaec1a48b3f)
- Updated Twitter apps dashboard url. [e378fbbc24e269de69494d326bc20fcb641c0697](https://github.com/sahat/hackathon-starter/commit/e378fbbc24e269de69494d326bc20fcb641c0697)
- Fixed dead links in the README. [78fac5489c596e8bcef0ab11a96e654335573bb4](https://github.com/sahat/hackathon-starter/commit/78fac5489c596e8bcef0ab11a96e654335573bb4)

### 2.3.3 (September 1, 2014)
- Use *https* (instead of http) profile image URL with Twitter authentication

### 2.3.2 (July 28, 2014)
- Fixed an issue with connect-assets when running `app.js` from an outside folder
- Temporarily disabled `setup.js` on Windows platform until [blessed](https://github.com/chjj/blessed) fixes its problems

### 2.3.1 (July 15, 2014)
- Migrated to Nodemailer 1.0

### 2.3 (July 2, 2014)
- Bootstrap 3.2
- New default theme
- Ionicons fonts
- Fixed bodyParser deprecation warning
- Minor visual updates
- CSS cleanup via RECESS
- Replaced `navbar-brand` image with a font icon

### 2.2.1 (June 17, 2014)
- Added IBM Codename: BlueMix deployment instructions

### 2.2 (June 6, 2014)
- Use Lodash instead of Underscore.js
- Replaced all occurrences of `_.findWhere` with `_.find`
- Added a flash message when user deletes an account
- Updated and clarified some comments
- Updated the Remove Auth message in `setup.js`
- Cleaned up `styles.less`
- Redesigned API Examples page
- Updated Last.fm API example
- Updated Steam API example
- Updated Instagram API example
- Updated Facebook API example
- Updated jQuery to 2.1.1
- Fixed a bug that didn't remove Instagram Auth properly
- Fixed Foursquare secret token

### 2.1.4 (June 5, 2014)
- Fixed a bug related to `returnTo` url (#155)

### 2.1.3 (June 3, 2014)
- Font Awesome 4.1
- Updated icons on some API examples
- Use LESS files for *bootstrap-social* and *font-awesome*

### 2.1.2 (June 2, 2014)
- Improved Twilio API example
- Updated dependencies

### 2.1.1 (May 29, 2014)
- Added **Compose new Tweet** to Twitter API example
- Fixed email service indentation
- Fixed Mailgun and Mandrill secret.js properties
- Renamed `navigation.jade` to `navbar.jade`

### 2.1 (May 13, 2014)
- New and improved generator - **setup.js**
- Added Yahoo API
- CSS and templates cleanup
- Minor improvement to the default theme
- `cluster_app.js` has been moved into **setup.js**

### 2.0.4 (April 26, 2014)
- Added Mandrill e-mail service (via generator)

### 2.0.3 (April 25, 2014)
- LinkedIn API: Fixed an error if a user did not specify education on LinkedIn
- Removed email constraint when linking OAuth accounts in order to be able to merge accounts that use the same email address
- Check if email address is already taken when creating a new local account
 - Previously relied on Validation Error 11000, which doesn't always work
- When creating a local account, checks if e-mail address is already taken
- Flash notifications can now be dismissed by clicking on �?

### 2.0.2 (April 22, 2014)
- Added Instagram Authentication
- Added Instagram API example
- Updated Instagram Strategy to use a "fake" email address similar to Twitter Startegy

### 2.0.1 (April 18, 2014)
- Conditional CSRF support using [lusca](https://github.com/krakenjs/lusca)
- Fixed EOL problem in `generator.js` for Windows users
- Fixed outdated csrf token string on profile.jade
- Code cleanup

### 2.0.0 (April 15, 2014)
There are have been over **500+** commits since the initial announcement in
January 2014 and over a **120** issues and pull requests from **28** contributors.

- Documentation grew **8x** in size since the announcement on Hacker News
- Upgraded to Express 4.0
- Generator for adding/removing authentication providers
- New Instagram authentication that can be added via generator
- Forgot password and password reset for Local authentication
- Added LinkedIn authentication and API example
- Added Stripe API example
- Added Venmo API example
- Added Clockwork SMS example
- Nicer Facebook API example
- Pre-populated secrets.js with API keys (not linked to my personal accounts)
- Grid layout with company logos on API Examples page
- Added tests (Mocha, Chai, Supertest)
- Gravatar pictures in Navbar and Profile page
- Tracks last visited URL before signing in to redirect back to original destination
- CSRF protection
- Gzip compression and static assets caching
- Client-side JavaScript is automatically minified+concatenated in production
- Navbar, flash messages, footer refactored into partial templates
- Support for Node.js clusters
- Support for Mailgun email service
- Support for environment variables in secrets.js
- Switched from less-middleware to connect-assets
- Bug fixes related to multi-authentication login and account linking
- Other small fixes and changes that are too many to list

Contributing
------------

If something is unclear, confusing, or needs to be refactored, please let me know.
Pull requests are always welcome, but due to the opinionated nature of this
project, I cannot accept every pull request. Please open an issue before
submitting a pull request. This project uses
[Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) with a
few minor exceptions. If you are submitting a pull request that involves
Pug templates, please make sure you are using *spaces*, not tabs.

License
-------

The MIT License (MIT)

Copyright (c) 2014-2016 Sahat Yalkabov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
