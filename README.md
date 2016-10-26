# secured-static-land
Have a static documentation website but may have sensitive information that you only want to expose to a certain group of people? This tool is for you!

Secured your static website with different oauth provider with ease, deploy to anywhere that support Docker.

[Live url](https://secured-static-land.herokuapp.com/)

## What is this?
[oauth2_proxy](https://github.com/bitly/oauth2_proxy) is a reverse proxy and static file server that provides authentication using Providers (Google, Github, and others) to validate accounts by email, domain or group.

This project provides a `Dockerfile` and a `oauth2_proxy.cfg` to make it easier for you deploy to any platform that support Docker deployment.

## How to use it?
* Clone the repo to your local

```sh
$ git clone git@github.com:fraserxu/secured-static-land.git
```

* Put your documentation or static file inside `/static` folder, this can be any static website or files generated by React.js, Vue.js or markdown files.

*  Update `oauth2_proxy.cfg` to config `provider`, `email domains`. For more details please check [oauth2_proxy.sample.cfg](https://github.com/bitly/oauth2_proxy/blob/master/contrib/oauth2_proxy.cfg.example
).

**Import notes:** Please do not put `client_id`, `client_secret` or any sensitive information in your source code,
you can pass it through environment variables instead.

The following environment variables can be used in place of the corresponding command-line arguments:

- `OAUTH2_PROXY_CLIENT_ID`
- `OAUTH2_PROXY_CLIENT_SECRET`
- `OAUTH2_PROXY_COOKIE_NAME`
- `OAUTH2_PROXY_COOKIE_SECRET`
- `OAUTH2_PROXY_COOKIE_DOMAIN`
- `OAUTH2_PROXY_COOKIE_EXPIRE`
- `OAUTH2_PROXY_COOKIE_REFRESH`
- `OAUTH2_PROXY_SIGNATURE_KEY`

### Example to deploy to Heroku.
Make sure you have a working Docker installation (eg. `docker ps`) and that you’re logged in to Heroku (`heroku login`).

Install the container-registry plugin by running:

```sh
$ heroku plugins:install heroku-container-registry
```

Log in to the Heroku container registry:

```sh
$ heroku container:login
```

Create a heroku app from command line:

```sh
$ heroku create
```

Build the image and push to the Heroku container registry:

```sh
$ heroku container:push web
```

Now open the app in your browser:

```sh
$ heroku open
```

Last but not least, go to the `settings` page of you app and put the required environment variables to the `Config Vars` section.

:tada:

## License
MIT