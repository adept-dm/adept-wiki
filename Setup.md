Currently CLI and other build tool plugins are under construction, so only SBT is supported.

If you want to help out and add support for more, be sure to read the [[Contributing]] section!

For **examples**, see projects using Adept here: [[Example-Projects]]

## Setup SBT
Add or open up the existing `project/plugins.sbt` file and add the following lines:

```scala

resolvers += Resolver.url("bintray", new URL("http://dl.bintray.com/freekh/adept-ivy"))(Resolver.ivyStylePatterns)

addSbtPlugin("org.adept" % "adept-sbt" % "0.8.0-PRE-ALPHA-20130727185333")
```

Then you have to add the adept settings, **either** in a `*.scala` file or in a `*.sbt` file.

Check out bintray to find more recent releases: https://bintray.com/freekh/adept-ivy/adept-sbt

### .sbt files
If you have **.sbt** (e.g. `build.sbt`) file do the following:
- add settings:
```scala
import adept.sbt.AdeptKeys._

adeptSettings
```
- add repositories and dependencies:
```scala
adeptRepositories += "central" -> "git@github.com:freekh/adept-central.git" //<- JUST AN EXAMPLE

adeptDependencies ++= Seq(
  "play" % "play_2.10" % "2.1.2" % "test" //<- JUST AN EXAMPLE
)
```

### .scala files
If you have a **.scala** (e.g. `project/Build.scala`) file do the following:
- add imports:
```scala
import adept.sbt.AdeptKeys._
import adept.sbt.AdeptPlugin._
```
- add the `adeptSettings` to your build settings:
```scala
Defaults.defaultSettings ++ adeptSettings
```
- add a repository and the adeptDependencies:
```scala
  adeptRepositories += "central" -> "git@github.com:freekh/adept-central.git" //<- JUST AN EXAMPLE
  adeptDependencies ++= Seq(
     "com.github.scala-incubator.io"     %%   "scala-io-file"            %   "0.4.1" exclude("javax.transaction", "jta") //<- JUST AN EXAMPLE
  )
```

### Compiling and inspecting the tree
After having setup the adept plugin you should be able to execute in sbt: 
```scala
compile
```

Another interesting thing you can do is to inspect the dependency tree from sbt:
```scala
adept-tree
```
This will give you information not only about which dependencies you have, but also information about the dependencies that was evicted.

### Migrating from Ivy
If the dependencies you are requiring are not available in an adept repository yet (check out [[Repositories]] for more information), you can **import dependencies using Ivy**.

After setting up your project and entered your `adeptDependencies` simply enter the following command in the sbt prompt:
```scala
adept-ivy-add
```

This will add your dependencies to the `local` repositories under (`~/.adept/repos/local`).
