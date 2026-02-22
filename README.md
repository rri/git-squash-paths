# git-squash-paths

## MOTIVATION

Suppose you have changes to a particular file(s) in your Git repository
over the course of several non-contiguous commits. You realize what you
really want is to collapse the changes into a single commit. Doing this
requires the changes to be split out of commits they are currently part
of, and merged into the target commit. This, of course, is non-trivial,
but that's where git-squash-paths comes in.

## EXAMPLE

Suppose your `/etc` folder has been initialized as a Git repostiory and
you have updates to `/etc/group` strewn across many commits.

What you want is to collapse them all into _one_ commit declaring group
configuration, instead of many updates to the `/etc/group` file.

### BEFORE

```
» git --no-pager log --oneline -- group
5cc4fc4 Group updates: render
fc67bf1 Group addition: vms
ab04207 Group updates: kvm
965d604 Group addition: git for source control
fb4eac6 Add polkit rule for giving users control of power
9584c15 Add greetd login manager service and permissions
332442b Set group configuration and user mapping
2f57270 Baseline
```

### RUN

```
» git-squash-paths 332442b group
```

### AFTER

```
» git --no-pager log --oneline -- group
f36688d Set group configuration and user mapping
2f57270 Baseline
```

Notice that all changes to the `group` file have been squashed into
`332442b`, replacing it with a new commit `f36688d`.

Multiple paths may be specified in one `git-squash-paths` command.

## INSTALLATION

Copy the `git-squash-paths` script into a folder in your `PATH` and
open a new shell to use the script.
