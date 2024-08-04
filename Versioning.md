## Semantic Versioning 
- [semver.org](semver.org)
- MAJOR.MINOR.PATCH
- Given a version number MAJOR.MINOR.PATCH, increment the:
    1. MAJOR version when you make incompatible API changes (i.e. "breaking" change)
    2. MINOR version when you add functionality in a backward compatible manner
    3. PATCH version when you make backward compatible bug fixes
- *Signature*: [general information about a function like the name, scope and parameters](https://en.wikipedia.org/wiki/Type_signature#Signature) 
  - When you change the signature of a function, it will result in a MAJOR increment. 
- Try to make your changes MINOR version changes when possible, to minimize the impact on users' code.
- When MAJOR = 0, the project is still experimental (i.e. "alpha" phase/unstable)
- DeprecationWarning: `from warning import warn`
- Avoid 3rd party dependecies whenever possible.
  - Only use dependecies from groups that maintain, update, and secure their packages