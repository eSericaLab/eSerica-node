## Getting started

This is a basic API REST skeleton written on JavaScript using async/await. Great for building a starter web API for your front-end (Android, iOS, Vue, react, angular, or anything that can consume an API)

This project is created to help other developers create a **basic REST API in an easy way with Node.js**. This basic example shows how powerful and simple JavaScript can be. Do you want to contribute? Pull requests are always welcome to show more features.

## Features

*   Multiple environment ready (development, production)
*   Custom email/password user system with basic security and blocking for preventing brute force attacks.
*   Compressed responses.
*   Secured HTTP headers.
*   CORS ready.
*   Cache ready (Redis).
*   HTTP request logger in development mode.
*   i18n ready (for sending emails in multiple languages).
*   User roles.
*   Pagination ready.
*   User profile.
*   Users list for admin area.
*   Cities model and controller example.
*   Login access log with IP, browser and country location (for country it looks for the header `cf-ipcountry` that CloudFlare creates when protecting your website).
*   API autogenerated documentation by Postman.
*   API collection example for Postman.
*   Testing with mocha/chai for API endpoints.
*   NPM scripts for cleaning and seeding the MongoDB database.
*   NPM script for keeping good source code formatting using prettier and ESLint.
*   Use of ESLint for good coding practices.
*   Mailer example with Nodemailer and Mailgun.
*   Ability to refresh token
*   JWT Tokens, make requests with a token after login with `Authorization` header with value `Bearer yourToken` where `yourToken` is the **signed and encrypted token** given in the response from the login process.

## Requirements

*   Node.js **10+**
*   MongoDB **3.6+**
*   Redis **5.0+**

## How to install

### Install npm dependencies after installing (Git or manual download)

```bash
cd myproject
npm install
npm update
```

### Setting up environments (development or production)

1.  In the root this repository you will find a file named `.env.example`
2.  Create a new file by copying and pasting the file and then renaming it to just `.env`
3.  The file `.env` is already ignored, so you never commit your credentials.
4.  Change the values of the file to your environment (development or production)
5.  Upload the `.env` to your environment server(development or production)
6.  If you use the postman collection to try the endpoints, change value of the variable `server` on your environment to the url of your server, for development mode use <http://localhost:3000>

**IMPORTANT:** By default token expires in 3 days (4320 minutes set in .env.example). You can refresh token at endpoint GET /token. If everything it´s ok you will get a new token.

### Mailer

To ensure the deliverability of emails sent by this API, `Mailgun` is used for mailing users when they sign up, so if you want to use that feature go sign up at their website <https://www.mailgun.com>

If you want to try a different method it´s ok, I used <https://nodemailer.com> for this API and they have different transport methods like: smtp.

### i18n

Language is automatically detected from `Accept-Language` header on the request. So either you send locale manually on the request or your browser will send its default, if `Accept-Language` header is not sent then it will use `en` locale as default.

## How to run

### Database cleaning and seeding samples

There are 3 available commands for this: `fresh`, `clean` and `seed`.

```bash
npm run command
```

*   `fresh` cleans and then seeds the database with dynamic data.
*   `clean` cleans the database.
*   `seed` seeds the database with dynamic data.

### Running in development mode (lifting API server)

```bash
npm run dev
```

You will know server is running by checking the output of the command `npm run dev`

```bash
****************************
*    Starting Server
*    Port: 3000
*    NODE_ENV: development
*    Database: MongoDB
*    DB Connection: OK
****************************
```

### Running tests

It´s a good practice to do tests at your code, so a sample of how to do that in `mocha/chai` is also included in the `/test` directory

```bash
npm run test
```

### Formatting code

Format your code with prettier by typing:

```bash
npm run format
```

### Formatting markdown files

Format all your markdown files with remark by typing:

```bash
npm run remark
```

### Linting code

Lint your code with ESLint by typing:

```bash
npm run lint
```

## Usage

Once everything is set up to test API routes either use Postman or any other api testing application. Default username/password combination for login is `admin@admin.com/12345`.

### API documentation

<https://documenter.getpostman.com/view/487539/RWaHwoLV>

### Postman API example collection

You can import the example collection to Postman. To import, click the import button located and select `postman-example.json` located within the root directory.

Go to `manage environments` to create environments for development, production, etc. On each of the environments you create you will need to:

1.  Create a new key `authToken` and within the `/login` request this value is automatically updated after a successfull login through a script located in the `tests` tab. Each time you make a request to the API it will send `Authorization` header with the `token` value in the request, you can check this on the headers of users or cities endpoints in the Postman example.

2.  Create a second key `server` with the url of your server, for development mode use <http://localhost:3000>

This is a REST API, so it works using the following HTTP methods:

*   GET (Read): Gets a list of items, or a single item
*   POST (Create): Creates an item
*   PATCH (Update): Updates an item
*   DELETE: Deletes an item

### Creating new models

If you need to add more models to the project just create a new file in `/app/models/` and it will be loaded dynamically.

### Creating new routes

If you need to add more routes to the project just create a new file in `/app/routes/` and it will be loaded dynamically.

### Creating new controllers

When you create a new controller, try to also create another folder with validations and helpers. Ex. `/countries`, `/countries/validators` and `/countries/helpers`. An example of this is included in the repository.

## Demo

A demo of this API is located at: <https://api-demo.daniel-avellaneda.com>

### Login credentials

email: `admin@admin.com`\
password: `12345`

**IMPORTANT:** Database resets every 30 mins like "12:00am, 12:30am, 1:00am" and so on. So anything you do with the API will be lost after a short time.

[API documentation](###api-documentation)\
[Postman API example collection](###postman-api-example-collection)\
If you want to test it don´t forget to change the server variable to:\
`https://api-demo.daniel-avellaneda.com`

Demo is also linked to a VueJS project that shows how this API can be integrated to a frontend that is able to consume an API.\
Repo is here: <https://github.com/davellanedam/vue-skeleton-mvp>\
Running demo is here: <https://vue-demo.daniel-avellaneda.com>