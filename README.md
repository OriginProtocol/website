# originprotocol.com

Official website for Origin Protocol

This is a Flask app with the source code for [www.originprotocol.com](https://www.originprotocol.com). The code is all `Python 2.7` with `Postgres` for the database (basically just for the mailing list). The database is not required to be configured if you're just working on the website.

## Installing
_Note: This site is set up differently from typical virtualenv/flask applications._

Setup a virtualenv
```
virtualenv --python=/usr/local/bin/python2 company-website && cd company-website
```

Clone
```
git clone https://github.com/OriginProtocol/company-website.git && cd company-website
```

Enter virtual environment
```
source env.sh
```

Install requirements
```
pip install -r requirements.txt
```

Rename the file `sample.env` to `.env`, and update env variables as desired.
```
mv sample.env .env
```

Run it!
```
python main.py
```

Open browser to view
```
open http://127.0.0.1:5000/
```

**Problems?** Hit us up in the `engineering` channel on [Discord](https://www.originprotocol.com/discord) if you need help.

## Localization
See README in `translations` directory

## Database changes

We use [Flask Migrate](https://flask-migrate.readthedocs.io/en/latest/) to handle database revisions. If you make changes to the database, use `flask db migrate` to generate the required migration file and then `flask db upgrade` to implement and test your changes on your local database before committing.

## Recaptcha

To enable recaptcha, add the following environment variables to `.env`

    RECAPTCHA_SITE_KEY = "<YOUR SITE KEY>"
    RECAPTCHA_SECRET_KEY = "<YOUR SECRET KEY>"

You can get Recaptcha keys here: https://www.google.com/recaptcha/admin

## Development

To deploy a development copy of the site on Heroku, just choose which branch you would like to use and follow the instructions: 

`Master` branch (stable):

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/originprotocol/company-website/tree/master)

`Develop` branch (active development):

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/originprotocol/company-website/tree/develop)

We use both the python and the nginx buildpacks:

	heroku buildpacks:set heroku/python
	heroku buildpacks:add https://github.com/heroku/heroku-buildpack-nginx

As a minium, you must set these 3 config variables:

|Config          |Value|
|----------------|------|
|FLASK_SECRET_KEY|(make something up)|
|PROJECTPATH     |/app|
|HOST            |(domain name of your dev heroku app)|

There are more optional config variables you can set. See [sample.env](sample.env) for a full list.

## Contributing

We'd love to have you join us and contribute to this project. Please join our [#engineering channel on Discord](http://www.originprotocol.com/discord) and read our [guidelines on contributing](http://docs.originprotocol.com/#contributing) to get started.


