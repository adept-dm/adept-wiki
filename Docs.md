Adept is split in separate sub-projects which are listed below.

If you want to build Adept or want to contributing, read about it [here](/adept-dm/adept/wiki/Contribute).

### Adept Core (adept-core)
Adept-core contains the core [models](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.package), the [main entry point] (http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.Adept) for the API and the core operations. The operations are private, to make it possible to change the logic without breaking the API.

Currently it also contains a modules that [imports from Ivy](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.ivy.IvyImport$)

Read more about the core design [here](/adept-dm/adept/wiki/Design). 

Scaladoc is available [here](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html)


### Adept CLI (adept-cli)
This project contains command line interface (CLI).

Read about how to get started with the CLI [here](/adept-dm/adept/wiki/Design)

Scaladoc is available [here](http://adept-dm.github.io/adept/scaladoc/adept-cli/index.html)


### Adept sbt (adept-sbt)
Unsurprisingly this project contains the plugin so that you can use Adept with sbt.

Read more about using Adept together with SBT [here] [/adept-dm/adept/wiki/SBT]

Scaladoc is available [here](http://adept-dm.github.io/adept/scaladoc/adept-sbt/index.html)