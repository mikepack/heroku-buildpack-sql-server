Heroku buildpack: SQL Server
=======================

A Heroku Buildpack created to write a config/database.yml file suiteable for use with Rails, [TinyTDS](https://github.com/rails-sqlserver/tiny_tds) and the [ActiveRecord SQL Server Adapter](https://github.com/rails-sqlserver/activerecord-sqlserver-adapter).

The database.yml file written accommodates oddities in requirements of the ActiveRecord SQL Server Adapter, for instance, decoding the username part of the URL, since SQL Server sometimes requires a `username@server` as the username.

Usage
-----

Add the `DATABASE_URI` environment variable, not to be confused with the `DATABASE_URL` environment variable supported by Rails. Remove the `DATABASE_URL` environment variable. If your installation of SQL Server requires the server to be part of the username, eg `username@server`, encode the `@` symbol in the username portion of the URL, eg: `sqlserver://username%40server:password@server.database.windows.net:1433/database?encoding=uft-8&azure=true`

This buildpack should be used in conjunction with
[heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi).
This has only been tested alongside the Ruby [buildpack](https://github.com/heroku/heroku-buildpack-ruby).
