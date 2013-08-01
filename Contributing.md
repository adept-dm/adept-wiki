Adept is currently in the proposal and discussion stage and needs your involvement!

If you want to learn how to develop in Scala, SBT, Gradle or Ant, then Adept should be a perfect place for you to start.


Discuss existing and propose new ideas on the development [mailing list] [mailinglist]

## Bugs
Found a bug? That is great!

Make sure the bug has simplest reproduction steps you could think of and submit it on the [Github issue tracker](/adept-dm/adept/issues)

## Docs
All great open source projects has great documentation. 

Found a typo or do you feel the urge to fix an explanation somewhere? 

Create an issue and add what you want you to fix. Github does not support pull requests for the wiki yet, therefore there is a separate repository here: ```https://github.com/adept-dm/adept-wiki``` where pull requests are welcomed. 

You need to make sure the the adept-wiki repository is up-to-date. 
Follow these steps to pull and merge the latest from the wiki:
```git remote add original git@github.com:adept-dm/adept.wiki.git # only needed first time```
```git pull original master```


Then follow the PR procedure as described below.

## Submitting PRs
Submitting pull requests are done using the normal [Github procedure](https://help.github.com/articles/using-pull-requests).

The preferred code styles are the following:
* **scala** [http://docs.scala-lang.org/style/]

Be sure to read the [[Design]] documentation to understand how Adept is built.

Also, try to follow the [boy scout rule of programming](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule) each time you do a pull request.


## Building
[![Build Status](https://travis-ci.org/adept-dm/adept.png?branch=master)](https://travis-ci.org/adept-dm/adept)

To build you need to install sbt: [http://www.scala-sbt.org/release/docs/Getting-Started/Setup.html#installing-sbt]. 

Then you simply start up sbt on your command line inside the adept directory:
`sbt`

To compile, run `compile` in the sbt prompt. To test, execute `test`.

If you are working on a specific project, use the `project` keyword to move to that project like this:
```project adept-core```


## Trying it out
### SBT

Read up on using SBT with Adept [here](/adept-dm/adept/wiki/SBT-TryingOut).

Be sure to have a look at the **converted projects** [here](/adept-dm/adept/wiki/SBT-Examples) and read up on the [migration guide from Ivy](SBTIvyMigration)



[mailinglist]: http://groups.google.com/group/adept-dev/