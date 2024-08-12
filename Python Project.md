## Project Template
- https://github.com/mlops-club/cloud-course-python-package-cookiecutter
- pyproject.toml
  - Contains package settings
- Install recommended VS code extensions from `extensions.json`: Extensions > @recommended > Install Workspace Recommended Extensions
- Makefile: `sudo apt-get update -y && sudo apt-get install cmake`
  - Makefile is a thin wrapper around bash functions, written in run.sh
  - "Targets" from Makefile
    - e.g. `make install` - installs all dependencies from file
    - e.g. `make test` - runs all unit tests
    - e.g. `make lint` - uses precommit to executing liniting hooks
      - needs pre-commit: `sudo apt-get update -y && sudo apt-get install pre-commit` and restart terminal


## Testing

### VS Code Test Explorer
- Run and Debug > create a launch.json file > Python file > add purpose and env parameters 
- (VS Code Testing Setup)[https://code.visualstudio.com/docs/python/testing]
- settings.json
  ```json
  "python.testing.pytestArgs": [
      "tests"
  ],
  "python.testing.unittestEnabled": false,
  "python.testing.pytestEnabled": true,
  "editor.formatOnSave": true,
  "testing.defaultGutterClickAction": "debug",
  ```
- launch.json
  ```json 
      "configurations": [
          {
              "name": "Python Debugger: Current File",
              "type": "debugpy",
              "request": "launch",
              "program": "${file}",
              "purpose": [
                  "debug-test",
              ],
              "console": "integratedTerminal",
              "env": {
                  "AWS_PROFILE": "cloud-course"
              }
          }
      ]
  ```

### moto
- `from moto import mock_aws`
- put `@mock_aws` decorator before test function
- doesn't handle IAM permissions - essentially assumes Admin-level permissions

### localstack
- localstack.cloud
- Better for complex use-cases (compared to moto)
- some features are paid