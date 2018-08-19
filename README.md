# `rtx`
A command line chat program for http://waksmemes.x10host.com/

Based on the original chat program `cli-chat` developed by @ehrenjn.

Only verified to work with python3 on linux, with uxterm. Requires that
the terminal support vt220 escape sequences.

the name is short for recieve/trasnmit.

# Improvements and features
- Refactored code base. The code base is slightly less of a mess. Linewraps at 80 as god inteneded.
- multithreaded UI. Drops the need to run two individual processes.
- completely backwards compatible with cli-chat
- can emulate cli-chat (to an extent)
- much more user configurability

# Usage
`rtx` has three modes
1. `rx`
	- recieve only, identical to `chat.py -r`
2. `tx`
	- transmit only, similar to `chat.py`
3. `rtx` (default)
	- simultaneously transmit and recieve, similar to `ui.sh`, but without
	the tmux dependance

## Configuration
`rtx` is extensively configurable. There are three places that configuration 
information comes from:
1. `configure_from_default`. The minimal default configuration stored internally.
2. `~/.config/rtx/config.py`. The user configuration file.
3. the command line.

Settings have the following precedance:

command line > `config.py` > defaults

Configuration information is handled as python dictionaries and functions. The
user config file is simply a python module that is imported during setup.

### Default Configuration
Out of the box `rtx` is configured to connect to `main` on waksmemes, with
no key and a fetch depth of 24 messages. Messages are formatted in a similar
style to `chat.py`. If `rtx` is launched without a config file or command line
options it behaves similarly to `ui.sh` except that it does not require tmux.

### Config File
The config file is a small python module that is loaded during setup. The
following directory structure must be present for the config file to be used:
`~/.config/rtx/`
	`__init__.py # blank`
	`config.py`

### Command Line
The following command line options are currently supported:
`--url=`
`--room=`
`--key=`
`--depth=`
`--pack_settings=`
`--unpack_settings=`
`--mode=`
