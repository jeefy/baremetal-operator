# Releasing

Baremetal Operator follows the [semantic versioning](https://semver.org) scheme for its releases.
For every minor version, we create a branch named release-0.MINOR to keep stable, tested and
backward compatible code. For example:

|       | Release version | Branch name |
|:-----:| --------------- | ----------- |
| Minor | v0.1.0          | release-0.1 |
| Patch | v0.1.1          | release-0.1 |
| Patch | v0.1.2          | release-0.1 |
| Minor | v0.2.0          | release-0.2 |
| Patch | v0.2.1          | release-0.2 |
| Patch | v0.2.2          | release-0.2 |

## Releasing process

For version v0.x.y:

1. Create an annotated tag `git tag -a v0.x.y -m v0.x.y`. To use your GPG
   signature when pushing the tag, use `git tag -s [...]` instead
1. Push the tag to the GitHub repository `git push origin v0.x.y`
   NB: `origin` should be the name of the remote pointing to
   `github.com/metal3-io/baremetal-operator`. This will start
   GitHub action, which will create a GitHub release on a temporary URL. Go to the
   running GitHub action and click on the autogenerated release URL. You can preview the
   release notes and make necessary corrections before officially releasing.
   After the tag is pushed, Quay starts building operator container image automatically based on the
   Dockerfile at the root directory.
1. If it is minor release, create a branch `release-0.x` for backports and
    bug fixes. This is not needed for patch releases.

## Permissions

Releasing requires a particular set of permissions.

- Tag push access to the GitHub repository
- GitHub Release creation access