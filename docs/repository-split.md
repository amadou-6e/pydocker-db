# Repository split

The database package moved from `amadou-6e/py-docker` to
`amadou-6e/pydocker-db`, preserving history through a1479be. The original
repository becomes a general container library. This extraction preserves the
database API and default drivers; adopting the new runtime is a later change.

`py-dockerdb` remains the canonical distribution containing `docker_db`.
`distributions/pydocker-db` builds the requested metadata-only install alias.
Build and validate each distribution independently. Never rename the canonical
distribution while both could own the same installed files.

Before release, configure the canonical project's PyPI trusted publisher for
this repository and retire its old repository publisher. The new alias needs
its own publisher or appropriately scoped upload credential. Name registration
is not guaranteed by a missing PyPI page. Do not publish before review, fresh
installation, upgrade/uninstall checks and the real database CI suite pass.

Automatic publication is disabled during this transition. CI builds and validates
both distributions, including the alias extras for graph, rag and test. No release
of the new runtime should trigger database publication. Existing default driver
dependencies and database source remain unchanged in this extraction.
