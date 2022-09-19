# DonutStore

An Angular app that uses the [DonutAPI](git@github.com:aaronfrost/DonutAPI.git) to show and teach about
building Jamstack apps in with Angular.

## Step1

In this branch we will install Scully to this project.

Run the following to add Scully to this project:

```bash
ng add @scullyio/init
```

At this point, read the changelog in the terminal to see what was changed about your app.

Noteworthy changes:

-   `app.module` - Imported the `ScullyLibModule`.
-   `polyfils.ts` - Updated to add some zone.js functionality.
-   `sculy.DonutStore.config.js` - Your new scully config file has been created.

## How to Verify

Great! So we have installed Scully, but now what do we do? Well, we need to verify that it successfully
installed Scully and that our project is able to be pre-rendered with Scully. To do this, run the
following steps from your terminal:

-   `ng build` - You need to run a build. Scully requires it prior to pre-rendering.
-   `npm run scully` - Now run Scully!

When that runs, notice that it generates our `/about` and `/` routes. But it shows you a warning
about your route `/donuts/:donutId`. In the next step we will address that warning.

But you can now check the contents of your `/dist/static` directory and see that your `/index.html`
`/about/index.html` pages were both pre-rendered to HTML and CSS.

Also notice that the scully build created a `scully-routes.json` file with a list of all the routes in
your app. This file will come in handy later.

## Now what?

To move on, stash your changes and checkout the `step2` branch.

```bash
git stash //hides your changes you just made
git checkout step2
```

## Migration

### Prerequisite

-   Current version is Angular 11 and Scully 1.0.0
-   Make sure you start the api project and leave it runing.
-   Clone this repo to a `DonutStore` folder and execute the following steps:

```bash
> npm install
> npm run build
> npm run scully
> npm run scully:serve
```

Then you should see something similar to:

```bash
starting static server
Scully static server started on "http://localhost:1668/"
Angular distribution server started on "http://localhost:1864/"
```

`Ctrl+C` to stop it and then remove the `dist/` folder

Now that is working we will move to Angular 12

```bash
> ng update
```
