Adept stores **meta-data** and **artifacts** separately: **meta-data** is versioned and stored in **git**. The versioned data enables adept to know exactly which version of the meta-data it was using at any given time.

The meta-data is composed **modules** (scaladoc). The modules currently are stored in **json** files.

The modules are identified by **coordinates** (scaladoc) and a **unique id**. The coordinates determine where in a repository a module is stored.

The unique id is a string that makes it possible to **uniquely identify** the module in the current repository. The unique ids makes it possible for adept to know exactly which module was used.

A **module** (scaladoc) has **artifacts** (scaladoc), **dependencies** (scaladoc), **configurations** (scaladoc) and **overrides** (scaladoc).

**Artifacts** (scaladoc) includes a **hash** and a **location**. The hash is unique for the actual file represented by the artifact. This enables adept to efficiently cache artifacts.

**Dependencies** (scaladoc) points to **other** modules. 

**Overrides** (scaladoc) overrides dependencies in other modules. It commonly makes it possible to overwrite a version in other dependencies, with depending on the dependency.

Based on **configurations** (scaladoc) and **exclusion rules** (scaladoc) a **tree** (scaladoc) will be built.



Configurations makes it possible to determine which artifacts and dependencies should be included in the tree. Read more about how configurations work in adept here (todo do this and link).

**Exclusion rules** makes it possible to **exclude transitive dependencies**. Transitive dependencies are the dependencies introduced from a given dependency.

After the tree has been built, all overrides will be applied. If there are more overrides or forced dependencies, **consensus** (agreement) comes from picking the most common version, then the highest version.

Then, versions for the modules considered to be the **same** will be **evicted**. Again, only the modules with the highest version will be chosen. Read more about conflict resolution in adept here (todo do this and link).

It is possible to print the tree which is generated for debugabilty. The tree will indicate **every** dependency and artifact for all modules and whether they are **evicted** or not found/missing and the **reason** it was not included.