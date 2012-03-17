# Common Lisp on Heroku -- Example Project

This project is an example of how to use [my fork](https://github.com/jsmpereira/heroku-buildpack-cl) of the [Heroku Common Lisp Buildpack](https://github.com/mtravers/heroku-buildpack-cl).  See the buildpack repository for more information and credits.

### This is the Hunchentoot branch.

## Instructions:
First, get yourself set up with a [Heroku account and tools](http://devcenter.heroku.com/articles/quickstart).

Then [fork this project](/jsmpereira/heroku-cl-example/fork_select) (and optionally modify it with your own content).

Change directory into the heroku-cl-example.

Next, create your own Heroku application using CL Buildpack:

    heroku create -s cedar --buildpack http://github.com/jsmpereira/heroku-buildpack-cl.git

Install http://devcenter.heroku.com/articles/labs-user-env-compile to have config vars available at build time.

You can choose implementation via:
```heroku config:add CL_IMPL=sbcl```
or
```heroku config:add CL_IMPL=ccl```

Choose webserver via:
```heroku config:add CL_WEBSERVER=hunchentoot```
or
```heroku config:add CL_WEBSERVER=aserve```

To avoid trouble with SBCL source encoding use: ```heroku config:add LANG=en_US.UTF-8```

And deploy:

    git push heroku branch

Where you should replace *branch* with the branch of your choice. There are currently 2 branches. *Master* has Huchentoot specific code and *aserve* has AllegroServe specific code.

That's it! Use `heroku open` to view your app in your browser!

## More details:

Currently https://github.com/jsmpereira/heroku-buildpack-cl let's you run Hunchentoot with SBCL and CCL and AllegroServe(portableaserve) with CCL.

There is a pending issue with [acl-compat](https://github.com/mtravers/portableaserve/tree/master/acl-compat) bundled with portableaserve preventing use with SBCL. Look [here](https://github.com/mtravers/wuwei/issues/10) for more information.

The file heroku-setup.lisp gets loaded at compile time, and needs to load any Lisp files or packages required.

Thanks to [Mike Travers](https://github.com/mtravers) for getting Common Lisp on Heroku.
