# Landing Page for the Imperial Quantum Society

A simple landing page built with 11ty and Tailwind CSS, based on the [example page](https://github.com/ttntm/11ty-landing-page) by [ttntm](https://github.com/ttntm).

## How to run the site locally

**Requirements:**

1. Eleventy (developed and tested with version 0.12.1)
2. Tailwind CSS

All other dependencies are either linked from a CDN or included in this repository.

**Setup:**

1. Fork, clone or download
2. `cd` into the root folder
3. run `npm install`
4. run `npm run serve`
5. open a browser and go to `http://localhost:8080`

**Basic configuration:**

1. Eleventy -> `./.eleventy.js`
2. Tailwind -> `./tailwind.config.js`
3. Netlify -> `./netlify.toml`

CSS is built via PostCSS and based on `./src/_includes/css/_page.css`. Building CSS gets triggered by `./src/css/page.11ty.js` and Tailwind's config is set to JIT (see: [Tailwind docs](https://tailwindcss.com/docs/just-in-time-mode))

Please note that this CSS build _does not_ include the `normalize.css` file used for the 2 regular pages (imprint, privacy) - a minified production version is stored in `./src/static/css` and gets included in the build by default.

**Change Content:**

Page content is stored in

- `./src/`
- `./src/sections/`
- `./src/_data/`

**Change Templates/Layout:**

Page structure and templates are stored in `./src/_layouts/` and can be edited there.

Best have a look at `./layouts/base.njk` first to understand how it all comes together - the page itself is constructed from partial templates stored in `./src/includes/` and each section has a corresponding template file (`section.**.njk`) stored there.

`index.njk` in `./src/` arranges everything, meaning that sections can be added/re-ordered/removed/... there.

**Change images:**

Images are stored in `./static/img/`; everything in there can be considered a placeholder that should eventually be replaced with your actual production images.

## How to run the CMS locally

The netlify CMS is accessed by adding `/admin` to the base url, at which point you will need to authenticate. Authentication is handled by netlify identity (which limits us to 5 admin accounts), currently registration is closed and invite only, so reach out to Dan to be added. Information on the CMS can be found [here](https://www.netlifycms.org).

First create a `.env` in the root folder, this file should contain the port for the CMS backend, it is recommended to use 8082:
```
PORT=8082
```

To run the CMS locally you will need then need to edit `/admin/config.yml` and add your IP address to `local_backend/allowed_hosts`.

The in a separate process run the command:

```
npx netlify-cms-proxy-server
```

Once the CMS backend is running you can run the local site and navigate to the admin page, for example if you are using port 8080 this will mean going to the address `http://localhost:8080/admin`.
