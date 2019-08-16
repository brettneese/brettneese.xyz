Category: Quick Tips
Date: 2019/08/16
Tags: lambda, aws, nodejs



# Using custom data sources in `node-convict`  via the `convict.load()` function to simplify application configuration

[node-convict](https://github.com/mozilla/node-convict) is a wonderful NPM module that lets you declaratively define configuration settings via JSON (or Javascript objects) and where the values for those configuration options should come from (environmental variables, command line arguments, etc), as well as add validation and even add documentation for them. 

It's incredibly flexible and I use it in virtually every `node` project - it's miles better than parsing `process.env` manually or even setting hardcoded constants in the app itself.

One of the more interesting uses of `convict` is to load values from an outside source -- for instance, from the AWS Parameter Store. Previously, I've used my own custom fork of `convict` for this, but I was recently made aware that I can make stock `convict ` do this as well, via a call to the `load()` function. I'm currently rewriting my AWS Parameter Store provider to use native `convict` functions and will write up a more detailed description of this when its done, but [here's a simple example](https://runkit.com/brettneese/simple-convict-load-example).

The downside of this method is that it is static and potentially synchronous. That's fine for all my use cases, though, as I load all my values on application/function start anyway.

