# matlab-docker-wrapper
Wrapper to enable running MATLAB within a Docker container.

Installs a `matlab-docker-wrapper` script and desktop file which use the [MathWorks Docker containers](https://hub.docker.com/r/mathworks/matlab) to launch an instance of MATLAB. Settings and licence information are shared from the host's `~/.matlab`, with version-specific folders suffixed with `-docker` (e.g. `~/.matlab/R2023a-docker`).

## Licencing
Only supports LNU (Login Named User) authentication. You will need to execute `matlab-docker-wrapper` from an interactive shell on first run in order to provide credentials which will be saved.
