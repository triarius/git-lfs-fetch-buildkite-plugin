Git LFS Pull Buildkite Plugin
===

Git clone for repos with files larger than the memory of a system the buildkite-agent is running on can lead to the system running out of memory and the buildkite-agent becoming unresponsive. Such large files are ordinarily version controlled with git-lfs. However, `git clone` or `git checkout` will read the entire file into memory even if it is handled by git-lfs. A workaround is to checkout in two phases. First ignoring the LFS files and then using `git lfs pull` to pull the lfs files. See https://github.com/git-lfs/git-lfs/issues/3524.

This plugin automates the workaround described in that Issue. It needs to be added to every step in a pipeline YAML AND the initial pipeline upload step in the pipeline web page.

# Example

```yaml
steps:
  - command: "buildkite-agent pipeline upload"
    label: ":pipeline:"
    plugins:
      - triarius/git-lfs-pull#v0.1.0: {}
```
