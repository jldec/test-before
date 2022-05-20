# test-before

This repo demonstrates the following

1. a gitpod `before` task is run as part of a prebuild even if there is no `init` task
2. the `before` task is run again in front of the `command` task in the workspace
3. the workspace URL returned by `gp url` is different for the prebuild and does not match the workspace URL.

### How to test

- open this repo in a gitpod workspace
- before.txt contains 2 lines - one with the URL of the prebuild workspace, one with the URL of the main workspace
- command.txt contains the url of the main workspace

### .gitpod.yml
```yaml
tasks:
  - before: |
      echo `gp url` >> before.txt
    command: |
      echo `gp url` >> command.txt
```

