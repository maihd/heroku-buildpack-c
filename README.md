Heroku buildpack: C
===================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for C apps.
It uses [Make](http://www.gnu.org/software/make/).

Usage
-----

Example usage:

    $ ls
    autogen.sh configure  Makefile  myapp.c

    $ heroku create --stack cedar --buildpack http://github.com/maihd/heroku-buildpack-c.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> C app detected
    -----> Running autogen.sh
           ...
    -----> Configuring
           Looking for somelibrary… ok
    -----> Compiling with Make
           gcc -o myapp myapp.c

The buildpack will detect your app as C if it has the file `Makefile` in the root.  It will run a `autogen.sh` script, then `configure` script if it exists in the root of the repository. It will then run `make` to compile the app.