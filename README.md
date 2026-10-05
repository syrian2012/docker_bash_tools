# docker_bash_tools

A small set of bash helpers that make Docker and Docker Compose easier to use from your terminal.

This version adds an interactive container picker, fuzzy selection with fzf when available, colorized output, and improved helper commands for inspecting, logging, and managing containers.

## Requirements

- Bash 4+
- GNU date
- Docker installed and configured
- Optional: fzf for interactive fuzzy selection
- Optional: bat for nicer syntax-highlighted output when inspecting JSON or shell output

## Installation

From this repository directory:

```bash
install -m 644 code_in_bashrc ~/.docker_tools
grep -qxF 'source ~/.docker_tools' ~/.bashrc || echo 'source ~/.docker_tools' >> ~/.bashrc
source ~/.bashrc
```

Then log out and log back in, or open a new shell.

If Docker access is restricted, make sure your user is added to the docker group:

```bash
sudo usermod -aG docker $USER
```

## How it works

Every container-based command supports three styles:

- `dstop` -> opens an interactive picker
- `dstop web` -> filters by name and shows a matching menu
- `dstop web-1` -> uses the exact container name directly

If `fzf` is installed, the picker becomes a fuzzy, searchable menu. If not, it falls back to a numbered list.

Colors are enabled automatically in a terminal. You can disable them with:

```bash
NO_COLOR=1
# or
DTOOLS_COLOR=0
```

You can also disable the preview pane in the fzf picker:

```bash
DTOOLS_PREVIEW=0
```

## Main commands

### Docker container listing

- `dps` - list running containers in a compact table
- `dps -a` - include stopped containers
- `dps --full` - show Docker's native output
- `dcps` - list Docker Compose services in a compact table
- `dcps --full` - show Compose's native output
- `dhelp` - interactive help menu for all available commands
- `dstats` - live CPU/memory/network stats for containers

### Container details and searches

- `dinfo [name]` - show a detailed, human-readable container dashboard
- `dgrep [pattern]` - show matching containers with their info
- `dgrep -t [pattern]` - compact table view
- `dinspect [name]` - show raw `docker inspect` output with syntax highlighting

### Shell access

- `dbash [name]` - open an interactive bash shell inside a running container, falling back to sh
- `dsh [name]` - open `/bin/sh` inside a running container
- `dex [name] [command]` - run a command inside a container

### Lifecycle management

- `dstart [name]` - start a container
- `drestart [name]` - restart a container
- `dstop [name]` - stop a running container
- `drm [name]` - remove a container (asks for confirmation)
- `dsrm [name]` - stop and remove a container (asks for confirmation)

### Logs

- `dlog [name]` - view logs, defaulting to the last 200 lines
- `dlog web -f` - follow logs
- `dlog web --tail 500` - show custom tail length
- `dlogc [name]` - clear a container's log file

### Docker and Compose shortcuts

- `dimgs` - `docker images`
- `drmi` - `docker rmi`
- `db` - `docker build .`
- `dcup` - `docker compose up -d`
- `dcdown` - `docker compose down`
- `dcstart` - `docker compose start`
- `dcstop` - `docker compose stop`
- `dcrestart` - `docker compose restart`
- `dcpull` - `docker compose pull`
- `dcbuild` - `docker compose build`

## Examples

```bash
dps

dps -a

dinfo web

dinfo web-1

dgrep web

dbash web

dex web ls -la /etc

dlog web --tail 100

# live stats, all containers
dstats

# live stats for containers matching 'api'
dstats api
```

## Notes

- `dhelp` is the easiest way to discover the toolset.
- `dps` and `dcps` automatically page output with `less` for easier reading.
- The scripts are intentionally designed to work well with both regular Docker containers and Compose services.

## Contact

For professional DevOps services, optimization, and consultation, contact me at mhd4.hz@gmail.com.

### Enjoy with love, Mohammad Haidar.
