This section is missing information.

Conflict resolution in Adept is done similarly as in Ivy.

First `overrides` (see [[Design]] document) are found and inserted. Then the highest version of conflicting modules are found. Conflicting modules are those who have the same organization and name, but different versions. 

See `ConflictResolver.scala` for the code.