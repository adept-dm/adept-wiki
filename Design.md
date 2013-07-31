<img src="https://raw.github.com/wiki/adept-dm/adept/images/adept_diagram.png"
 alt="Adept diagram" title="Adept diagram" align="center" />

* **Git** is used to stored versioned meta-data
* **Repository** contains the meta-data in individual modules
* **Module** contains information needed to create the classpath such as: dependencies to other modules and the locations of artifacts
* **Build tools**, such as SBT, Gradle (not currently supported), Ant (not currently supported) uses Adept to create their classpath based on a set of modules

### In depth
Adept stores **meta-data** and **artifacts** separately: **meta-data** is versioned and stored in **git**. The versioned data enables adept to know exactly which version of the meta-data it was using at any given time.

An example of a repository is [here](https://github.com/freekh/adept-central).

The meta-data is composed [modules](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Module). The modules currently are stored in **json** files ([example](https://github.com/freekh/adept-central/blob/master/play/play/2.1.1/modules.json)).

The modules are identified by [coordinates](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Coordinates) and a [unique id](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.UniqueId). The coordinates determine where in a repository a module is stored.

The unique id is a string that makes it possible to **uniquely identify** the module in the current repository. The unique ids makes it possible for adept to know exactly which module was used.

A module has [artifacts](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Artifact), [dependencies](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Dependency), [configurations](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Configuration) and [overrides](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Override).

**Artifacts** includes a **hash** and a **location**. The hash is unique for the actual file represented by the artifact. This enables adept to efficiently cache artifacts.

**Dependencies** points to **other** modules. 

**Overrides** overrides dependencies in other modules. It commonly makes it possible to overwrite a version in other dependencies, with depending on the dependency.

Based on **configurations** and [exclusion rules](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.DependencyExclusionRule) a [tree](http://adept-dm.github.io/adept/scaladoc/adept-core/index.html#adept.core.models.Tree) will be built.



Configurations makes it possible to determine which artifacts and dependencies should be included in the tree. Read more about how configurations work in adept [here](/adept-dm/adept/wiki/Configurations).

**Exclusion rules** makes it possible to **exclude transitive dependencies**. Transitive dependencies are the dependencies introduced from a given dependency.

After the tree has been built, all overrides will be applied. If there are more overrides or forced dependencies, **consensus** (agreement) comes from picking the most common version, then the highest version.

Then, versions for the modules considered to be the **same** will be **evicted**. Again, only the modules with the highest version will be chosen. Read more about conflict resolution in adept [here](/adept-dm/adept/wiki/ConflictResolution).

It is possible to print the tree which is generated for debugabilty. The tree will indicate **every** dependency and artifact for all modules and whether they are **evicted** or not found/missing and the **reason** it was not included.