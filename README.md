# test-before

This is a variant of the test-before main branch with the command task commented out. 

#### .gitpod.yml
```yaml
tasks:
  - before: |
      echo `gp url` >> before.txt
```

This repo demonstrates the following

1. A gitpod `before` task is run as part of a prebuild even if there is no `init` task

### How to test

- Open this repo in a gitpod workspace
- `before.txt` contains 1 line with the URL of the prebuild workspace

test
