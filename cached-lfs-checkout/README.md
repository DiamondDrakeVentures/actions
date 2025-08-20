# Cached LFS Checkout action

This action checks out a repository with LFS contents and caches such LFS contents.

LFS objects are first restored from cache.
Then, LFS objects are pulled from the remote; up-to-date objects are automatically skipped over.
Once the checked out repository is up-to-date, stale LFS objects are pruned.
Lastly, the objects are stored in cache.

## Usage

``` yaml
- uses: diamonddrakeventures/actions/cached-lfs-checkout@main
  with:
    # Personal Access Token (PAT) used to fetch the repository.
    # The PAT is configured with the local git config, which enables your scripts to run
    # authenticated git commands.
    # The post-job step removes the PAT.
    #
    # We recommend using a service account with the least permissions necessary.
    # Also when generating a new PAT, select the least scopes necessary.
    #
    # Default: ${{ github.token }}
    token: ''

    # Repository name with owner.
    # For example, actions/checkout.
    #
    # Default: ${{ github.repository }}
    repository: ''

    # The branch, tag, or SHA to checkout.
    # When checking out the repository that triggered a workflow, this defaults to the reference or
    # SHA for that event.
    # Otherwise, uses the default branch.
    ref: ''

    # Number of commits to fetch.
    # 0 indicates all history for all tags and branches.
    #
    # Default: 1
    fetch-depth: ''

    # Whether to checkout submodules: `true` to checkout submodules or `recursive` to recursively
    # checkout submodules.
    #
    # Default: false
    submodules: ''

    # Whether the cache is cross-platform.
    # This is useful to cache dependencies which are runner platform independent.
    #
    # Default: false
    crossPlatform: ''
```
