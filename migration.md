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

Now that is working we will move to Angular 12

## Migrate Angular 11 to 12

`Ctrl+C` to stop Scully if it is running and then remove the `dist/` folder

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
✔ starting static server
✔ Scully static server started on "http://localhost:1668/"
✔ Angular distribution server started on "http://localhost:1864/"
```

After following the above links and check everything is working then we can save and commit.

## Migrate Angular 12 to 13

`Ctrl+C` to stop Scully if it is running and then remove the `dist/` folder

```bash
> ng update @angular/cli@13
> npm install
> npm run build
> npm run scully
> npm run scully:serve
```

And then you should see something like:

```bash
  ✔ Starting servers for project "DonutStore"
  ✔ Started Scully static server on "http://localhost:1668/"
  ✔ Started Angular distribution server on "http://localhost:1864/"
```

After following the above links and check everything is working then we can save and commit.

## Migrate Angular 13 to 14

`Ctrl+C` to stop Scully if it is running and then remove the `dist/` folder

```bash
> ng update @angular/cli@14
> npm install
> npm run build
```

Update `angular.json` file to add the `defaultProject` entry if not present already:

```json
{
    "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
    "version": 1,
    "newProjectRoot": "projects",
    "projects": {
        "DonutStore": {
            ... // REMOVED FOR BREVITY
        }
    },
    /** ADD THE LINE BELOW  **/
    "defaultProject": "DonutStore",
    "cli": {
        "analytics": "f630798a-e215-409c-8819-cde30d5df125"
    }
}
```

Update `scully.DotnutStore.config.ts` to satisfy Typescript:

```ts
function myDonutsIdPlugin(unhandledRoute) {
    return httpGetJson('http://localhost:3000/donuts').then((donuts: any[]) => {
        return donuts.map(donut => ({ route: `/donuts/${donut.id}` }));
    });
}
```

Now let's run scully to check everything is working

```bash
> npm run scully
> npm run scully:serve
```

And then you should see something like:

```bash
  ✔ Starting servers for project "DonutStore"
  ✔ Started Scully static server on "http://localhost:1668/"
  ✔ Started Angular distribution server on "http://localhost:1864/"
```

After following the above links and check everything is working then we can save and commit.
