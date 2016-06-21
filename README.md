A minimal, React.js based SPA(read-only blog) prototype written in less than 200 lines of code with support two types of routing - Hash-based and pushState-based.

## Prerequisite

All configuration is done by `state` variable, which is hardcoded in index.html. Before we start to customize, it's recommended to understand properly what state this blogging tool has as of now.

```
var state = {
  blogs:           // array of Blog entry hash
  location:        // hash string for the page
  isHashBasedAjax: // boolean to decide which ajax mode is used, hash-based or pushState-based
};
```

## Usage

The only thing we need to implement before deploy this tool is about data source(`state.blogs`). With the current code in `index.html`, blog entries are hardcoded in index.html but in reality, you will need to code one of following choise.

- Fetch blog data dynamically
  * Fetch json data file(blog data) from the internet asynchronously at window.onload timing
- Pre-compile index.html file
  * Make your own template file based on `index.html` file with your favorite programming language
  * Just inject $blogs variable to construct `state` variable in Javascript world

## Supporting Hash-based and pushState-based routing

When `state.isHashBasedAjax` is set to `true`, Hash-based routing such as `example.com/#about` is enabled. Generally speaking pushState-based routing is better from the SEO point of view, however Hash-based routing sometimes win because it works anywhere you want. For Hash-based routing, http-server level configuration(e.g. rewrite rules with .htaccess) or CDN-level configuration(e.g. S3 Routing Rules or CloudFront Path Pattern) is not required.

If you would like to use pushState-based routing on the other hand, just use `state.isHashBasedAjax = true` whenever `example.com/about`-ish style, pushSate-based routing is needed.

Following documentation will give you great introduction to start configuration.

- Apache(.htaccess)
  * TBD
- NGINX(.conf)
  * TBD
- S3(Routing Rules)
  * [Cloudfront rewrite url to S3](http://stackoverflow.com/a/29176968)
- CloudFront(Path Pattern)
  * TBD

## Acknowledgement 

Without @jamesknelson's following series of great posts, this idea would not have been realized. Thanks @jamesknelson!

- (Learn React By Itself -- no JSX, no Flux, no ES6, no Webpack)[http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/]
- (Learn Raw React: Ridiculously Simple Forms)[http://jamesknelson.com/learn-raw-react-ridiculously-simple-forms/]
- (React and pushState: You’re doing it wrong)[http://jamesknelson.com/push-state-vs-hash-based-routing-with-react-js/]
- (Building a Router with Raw React)[http://jamesknelson.com/routing-with-raw-react/]

## LICENSE

MIT
