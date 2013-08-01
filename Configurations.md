This section needs more information.

Configurations in Adept are inspired by configurations in Ivy, but currently only a subset is supported.

You use configurations in 2 ways:
1) Defining which configuration you want when you are executing something that requires dependencies. Typical examples are: compile, test, ...
2) Defining which configuration  a certain dependency should use and what it should map to. Example: `compile->runtime`. This means that when you want to compile, I want the dependency to use it's `runtime` configuration.

Read up on what Ivy says on it [here](http://ant.apache.org/ivy/history/2.1.0/ivyfile/dependency.html)

### Supported configuration syntax:
- 'A->B' means that configuration(s) matched by A in the left set of confs is mapped to B in the right set of confs
- '*' means all configurations (`compile->*`)
- ';' separates multiple expressions (`compile->compile;default->compile`)
- ',' separates multiple configurations (`compile->compile,master`)
- '()' fallback configuration used if the first one is not found (`compile->compile(*)`, e.g. map compile to compile, if compile is not found use all configurations) 

### Not currently supported:
- '%' 
- '!' 
- '[' and ']'
- '@
- '#'
