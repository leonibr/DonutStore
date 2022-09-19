## Migration path

the purpose of this document is to help others to migrate Angular and Scully side-by-side.

### Prerequisite

-   Latest angular cli installed globally
-   Current version is Angular 11 and Scully 1.0.0
-   Make sure you start the api project and leave it running.
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

## Migrate Angular 11 to 12

```bash
> ng update @angular/cli@12
```

Once finished goto to `package.json`, then search and update the dependencies to:

```bash
    "@scullyio/init": "^2.1.36",
    "@scullyio/ng-lib": "^2.1.36",
    "@scullyio/scully": "^2.1.36",
    "@scullyio/scully-plugin-critical-css": "2.1.36",
    "@scullyio/scully-plugin-puppeteer": "^2.1.36", # NEW ENTRY!!
    "rxjs": "~7.5.6",
    "tslib": "2.4.0",
```

-   Remove the `node_modules/` and `package-lock.json`
-   Check if the Api is still running on `http://localhost:3000`
-   Check if you are at correct folder `../DonutStore` and then:

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

After follow the above links and check everything is working then we can save and commit.
