# packagecloud-poll
`packagecloud-poll` repeatedly polls the [packagecloud.io](https://packagecloud.io) API, looking for a specific package 
filename to appear. It is intended to be used in continuous integration/continuous deployment pipelines, where we want 
to block something until we are sure a package has been uploaded and is available before continuing onwards.

## Installation
```shell
pip install packagecloud-poll
```

## Setup
You must set a `PACKAGECLOUD_TOKEN` environment variable before you can run packagecloud-poll. See the [packagecloud API
documentation](https://packagecloud.io/docs/api) for instrcutions on how to generate a token.

```shell
export PACKAGECLOUD_TOKEN=deadbeefdeadbeefdeadbeefdeadbeefdeadbeefdeadbeef
```

## Example invocation
```shell
packagecloud-poll --user my_user --repo my_repo_name --type deb --distro ubuntu --distro_version precise --arch amd64 --pkg_name myorg-stuff --filename myorg-stuff_v5.3_precise_amd64.deb
```

## Running
```
packagecloud-poll

Packagecloud-poll repeatedly polls the packagecloud API, looking for a specific package filename to appear. It is
intended to be used in continuous integration/continuous deployment scenarios where we want to block until we are sure
a package has been indexed and is avaiable before continuing.

All arguments are mandatory except for --timeout, --poll_interval and --log-level.

Increased productivity gains high favour from the machine god.

Usage:
    packagecloud-poll --user user --repo repo_name --type type --distro distro --distro_version distro_version --arch arch --pkg_name pkg_name --filename filename [--timeout timeout] [--poll_interval poll_interval] [--log-level log_level]
    packagecloud-poll --help
    packagecloud-poll --version

Options:
    --user <user>                      Packagecloud user.
    --repo <repo_name>                 Packagecloud repository.
    --type <type>                      Package type. (i.e. rpm or deb)
    --distro <distro>                  Package distro. (i.e. ubuntu)
    --distro_version <distro_version>  Package distro version. (i.e. precise)
    --arch <arch>                      Package arch. (i.e. amd64 or x86_64)
    --pkg_name <pkg_name>              Name of the package to poll for.
    --filename <filename>              File name of the package to poll for. (i.e mystuff_v5.3_precise_amd64.deb)
    --timeout <timeout>                Time in seconds to poll for [default: 600].
    --poll_interval <timeout>          Polling interval in seconds [default: 30].
    --log-level <log_level>            Set output log level. One of DEBUG, INFO, WARN, ERROR or CRITICAL [default: INFO].
    --help                             Show this screen.
    --version                          Show version.
```
