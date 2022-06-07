# test-before
The behavior below illustrates the edge case of using a `before` without an `init` in the same same Gitpod task.

**NOTE**: This is not the recommended way to use `before` because it is run twice, and results in unnecessary prebuilds when nothing in the `before` commands needs to be persisted.

- Use `init` instead of `before` when the main intent is to trigger a prebuild.
- Use `before` to extract common steps like selecting a kubernetes context or changing directories when **both** `init` and `command` tasks are present.

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
2. The `before` task is run again in the workspace (before any `command` task if there is one)
3. The workspace URL returned by `gp url` is different for the prebuild workspace.

### How to test

- Open this repo in a gitpod workspace
- `before.txt` contains 2 lines - one with the URL of the prebuild workspace, one with the URL of the main workspace
- `command.txt` contains the url of the main workspace
