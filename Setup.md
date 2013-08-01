Currently CLI and other build tool plugins are under construction, so only SBT is supported.

If you want to help out and add support for more, be sure to read the [[Contributing]] section!

## Setup SBT

### Adding the plugin
Add or open up the existing `project/plugins.sbt` file and add the following lines:

```scala

resolvers += Resolver.url("bintray", new URL("http://dl.bintray.com/freekh/adept-ivy"))(Resolver.ivyStylePatterns)

addSbtPlugin("org.adept" % "adept-sbt" % "0.8.0-PRE-ALPHA-20130727185333")
```

Then you have to add the adept settings, either in a `*.scala` file or in a `*.sbt` file.

If you have ***.sbt** (e.g. `build.sbt`) file do the following:
- add settings:
```scala
import adept.sbt.AdeptKeys._

adeptSettings
```
- add repositories and dependencies:
```scala
adeptRepositories += "central" -> "git@github.com:freekh/adept-central.git"

adeptDependencies ++= Seq(
  "play" % "play_2.10" % "2.1.2" % "test"
)
```

If you have a ***.scala** (e.g. `project/Build.scala`) file do the following:
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
  adeptRepositories += "central" -> "git@github.com:freekh/adept-central.git" //just an example
  adeptDependencies ++= Seq(
     "com.github.scala-incubator.io"     %%   "scala-io-file"            %   "0.4.1" exclude("javax.transaction", "jta")
  )
```



### Migrating 



### Examples
- Play20 with Adept (a normal project): https://github.com/freekh/Play20/tree/adept
- sbteclipse with Adept (a SBT plugin): https://github.com/freekh/sbteclipse/tree/v2.1.1-adept
