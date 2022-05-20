# test-before


#### .gitpod.yml
```yaml
tasks:
  - before: |
      echo `gp url` >> before.txt
    command: |
      echo `gp url` >> command.txt
```

This repo demonstrates the following

1. A gitpod `before` task is run as part of a prebuild even if there is no `init` task
2. The `before` task is run again in front of the `command` task in the workspace
3. The workspace URL returned by `gp url` is different for the prebuild workspace.

### How to test

- Open this repo in a gitpod workspace
- `before.txt` contains 2 lines - one with the URL of the prebuild workspace, one with the URL of the main workspace
- `command.txt` contains the url of the main workspace
