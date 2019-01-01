# lightning-navigator

Welcome to Lightning Navigator, the tool that helps you organaize, explore and navigate your Salesforce Metadata. Build Data Dictionary directly from any org with secure OAuth connection. This tool was built by Developers & Admins to enable you to focus on better support your business instead of searching for details and making documentation.

The app can deploy to Heroku or run locally.

To deploy your own copy of this app use this handy Heroku button.

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

## Running Locally

Make sure you have Java and Maven installed.  Also, install the [Heroku CLI](https://cli.heroku.com/).

```
$ git clone https://github.com/iandrosov/force-navigator
$ cd sf-oauth-java-example
$ mvn install or mvn clean install
$ heroku local:start
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

## Environment Configuration

This applcation will use OAuth to authorize user access to Salesforce ORG. The app will need environment configuration for Connected APP to set consumer key and secret values.

### Connected APP

Create your connected app that will represent your web app in Salesforce org. Once app is set up copy consumer key and secret generated for this new connected app.

### Set Enviroment Variables Local

For local runtime create `.env` file in your application root directory and set tehse variables

```
SF_CLIENT_ID=<Consumer Key from Connected App>
SF_CLIENT_SECRET=<Consumer secret from Connected App>
SF_REDIRECT_URI=https://localhost:5000/oauth/_callback
```

The callback URL need to be set on connected app, it can be any valid url choice taht your app will respond to, we selected this example `https://localhost:5000/oauth/_callback`. 

This is the url Salesforce will call HTTP GET method on to send tokens to. Your app needs to code this endpoint to get access tokens. Note callback must be HTTPS, the HTTP will not work.

### Set Environment on Heroku

To reun on Heroku app, need to configure Heroku Variables

```
SF_CLIENT_ID=<Consumer Key from Connected App>
SF_CLIENT_SECRET=<Consumer secret from Connected App>
SF_REDIRECT_URI=<Heroku app URL>/oauth/_callback
```
