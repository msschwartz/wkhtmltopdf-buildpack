# wkhtmltopdf Buildpack

This is a [Heroku buildpack][0] for bundling a compatible [wkhtmltopdf][1]
binary with your environment.

## Versions

* Buildpack:   `0.2`
* wkhtmltopdf: `0.12.5` by default

*NOTE:* This fork of the buildpack only supports `0.12.5` and higher.  It inatalls
the deb package for Heroku-18 stack

## Usage

[Add this buildpack][2] to your Heroku application to install the `wkhtmltopdf`
and `wkhtmltoimage` binaries, and the corresponding library `libwkhtmltox`,
into the dynos:

```bash
$ heroku buildpacks:add https://github.com/srbartlett/wkhtmltopdf-buildpack.git
```

If you want to use a `wkhtmltopdf` version other than 0.12.3, set
`WKHTMLTOPDF_VERSION`:

```bash
heroku config:set WKHTMLTOPDF_VERSION="0.12/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb"
```

### Clearing Repo Cache

Remember to clean your repository cache if you are updating the version of
buildpack. To do that, run:

```bash
$ heroku plugins:install https://github.com/heroku/heroku-repo.git
$ heroku repo:purge_cache -a appname
```

## Troubleshooting

If you run into issues when trying to deploy with this buildpack, make sure your
app is running on `cedar-18`

```bash
$ heroku stack
```

[0]: http://devcenter.heroku.com/articles/buildpacks
[1]: http://wkhtmltopdf.org/
[2]: https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app
