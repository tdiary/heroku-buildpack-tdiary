# Heroku Buildpack: tDiary

This is a [Heroku buildpack](https://devcenter.heroku.com/articles/buildpacks) for [tDiary](http://www.tdiary.org/) application. It designed to use with the [heroku official ruby buildpack](https://github.com/heroku/heroku-buildpack-ruby).

## Usage

### Automatically build and deploy

'Deploy to Heroku' Button is enabled.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/tdiary/tdiary-core/tree/heroku_to_master)

### Manually build and deploy

Clone [tDiary repository](https://github.com/tdiary/tdiary-core).

```
$ git clone https://github.com/tdiary/tdiary-core
```

Create your tDiary instance on heroku.

```
$ cd tdiary-core
$ heroku create
$ heroku addons:create sendgrid
$ heroku addons:create memcachier
$ heroku addons:create mongolab
$ heroku config:set TWITTER_KEY=YOUR_TWITTER_KEY
$ heroku config:set TWITTER_SECRET=YOUR_TWITTER_SECRET
$ heroku config:set TWITTER_NAME=YOUR_TWITTER_NAME
```

Set buildpacks.

```
$ heroku buildpacks:set https://github.com/tdiary/heroku-buildpack-tdiary
$ heroku buildpacks:add heroku/ruby
```

Build and deploy.

```
$ git push heroku master
$ heroku run
```

Open your tDiary site in a web browser.

```
$ heroku open
```

## How it works

This buildpack sets up some files (e.g. `Gemfile.lock`, `tdiary.conf`) to build tDiary on heroku.

 1. Delete original `Gemfile.lock` file
 2. Copy files in `misc/paas/heroku` directory to root directory

It does only preparation. Official heroku ruby buildpack is also needed.

## See also

Please read [offical tdiary document](http://www.tdiary.org/20150208.html) (in Japanese).
