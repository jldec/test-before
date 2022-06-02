# test-before
⚠️ The behavior described below was always GitHub-specific, and as of [#21d3f0](https://github.com/gitpod-io/gitpod/commit/21d3f00d47f7b073fa517dd186963bcb87abc652) will no longer work.  
Use `init` instead of `before` when the main intent is to trigger a prebuild and you previously relied on a single `before` without any `init`. Use `before` to extract common steps when both `init` and `command` are also present.

#### .gitpod.yml (this will no longer behave as described below)
```yaml
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

touch  
touch  
touch  
touch  
touch 31  
touch 32  
touch 33  
