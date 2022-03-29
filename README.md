# Prerender.io Worker

A Worker for integrating an origin(s) with [Prerender.io](https://prerender.io).
The contents of the Worker is taken from Prerender.io's [integration documentation](https://docs.prerender.io/docs/24-cloudflare).

## Get Started

Install dependencies:

```
npm i
```

Edit `index.js` and add your prerendered domains to the `PRERENDERED_DOMAINS` variable:

```
const PRERENDERED_DOMAINS = ['prerender.jwdn.cc']
```

Add the same domain list to the `routes` configuration in `wrangler.toml` ensuring to append `/*` if you intend the Worker to apply to all paths of the route(s):

```
routes = ["prerender.jwdn.cc/*"]
```

### Deploy

```
wrangler publish
wrangler secret put PRERENDER_API_KEY
<enter the prerender api key when prompted - the api key is available in your Prerender.io account settings>

wrangler publish
```

⚠️ you'll see above that we had to `publish` twice as a **secret** can only be created once a Worker has already been published.
