Git LFS Pull Buildkite Plugin
===

# Example
```
steps:
  - command: "buildkite-agent pipeline upload"
    label: ":pipeline:"
    plugins:
      - triarius/git-lfs-pull: ~
```
