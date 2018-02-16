# heroku-exploreation

## Deploying
To get going with Heroku download and install the [cli](https://devcenter.heroku.com/articles/heroku-cli) for your platform.
Login with your credentials    
    
    heroku login
    
Next go to your application directory. If it is not a git repository go ahead and create one
    
    git init
    git add .
    git commit
    
Now the application is ready to be deployed on Heroku:

    heroku create
    git config --list | grep heroku
    git push heroku master

The _heroku create_ command adds a remote repository reference and when we push to that repository the application gets deployed.
Heroku auto detects which technology is being used and uses the relevant _buildpack_ to handle your application. Custom buildpacks
can be specified, but usually not needed.

Once the application have been pushed to Heroku check the logs to verify:

    heroku apps
    heroku logs -a thawing-river-91434 --tail
    
First inspect the output of the _heroku apps_ command to get your application name and then issue the _logs_ command to inspect logs from the application.

## Procfile
In some situations you must tell Heroku how to startup the application. The _Procfile_ can be used to specify this

    web: java -Dspring.profiles.active=heroku -jar target/myapp.jar
    
In the example above we would like to activate the heroku Spring profile during startup.

## Addons
There are lots of different addons, e.g. a PostgreSQL addon. If you add the PostgreSQL addon a _DATABASE_URL_ variable is exposed to your application and can be used to connect to the database.
