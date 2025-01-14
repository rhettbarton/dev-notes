- Design priniciples from Heroku
- [12factor.net](12factor.net)
  1. Code: One codebase tracked in revision control, many deploys
    - Use a code repo and version control (i.e. git)
    - Don't duplicate code - use libraries instead
  2. Dependencies: Explicitly declare and isolate dependencies
    - i.e. Docker to bundle all dependencies
  3. Configuration: Store config in the environment
    - Separate config from code
    - config is everything that is likely to vary between deploys (develop, stage, prod)
  4. Backing services: Treat backing services as attached resources
    - make no distinction between local and 3rd party services
    - "loose coupling" - changing resources requires no code changes, just environment config changes