# compile-time-env

A Heroku [Buildpack][buildpacks] to make [Config Vars][config-vars] available during Slug compilation.

## How to use it

Create a `.compile-time-env` file in the root of your App/repository.
Add Config Var names you want to export (one per line):

```console
$ cat .compile-time-env
SOME_ENV_VAR
# lines starting with # are considered comments, and will be skipped
ANOTHER_VAR
```

Add this Buildpack as the first Buildpack in your App.
Or, at least before other Buildpacks that need the Config Vars.

```console
$ heroku buildpacks:add --index=1 stevenharman/compile-time-env --app=<YOUR-APP-NAME>
```

On the next deploy the Config Vars specified in the `.compile-time-env` file will be available in the Slug compilation phase. 

## License

This work is licensed under [MIT License](./LICENSE).

Copyright (c) 2022 Steven Harman

[buildpacks]: https://devcenter.heroku.com/articles/buildpacks "Heroku Buildpacks"
[config-vars]: https://devcenter.heroku.com/articles/config-vars "Configuration and Config Vars"
