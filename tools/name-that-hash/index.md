## name-that-hash

### Installation

```bash
pip3 install name-that-hash
```

### Usage

```bash
nth [OPTIONS]
```

### Flags

```bash
Options:
  -t, --text TEXT      Check one hash, use single quotes ' as inverted commas
                       " messes up on Linux.

  -f, --file FILENAME  Checks every hash in a newline separated file.
  -g, --greppable      Are you going to grep this output? Prints in JSON
                       format.

  -b64, --base64       Decodes hashes in Base64 before identification. For
                       files with mixed Base64 & non-encoded it attempts
                       base64 first and then falls back to normal hash
                       identification per hash.

  -a, --accessible     Turn on accessible mode, does not print ASCII art. Also
                       does not print very large blocks of text, as this can
                       cause some pains with screenreaders. This reduces the
                       information you get. If you want the least likely
                       feature but no banner, use --no-banner.

  -e, --extreme        Searches for hashes within a string. This mode will get
                       5d41402abc4b2a76b9719d911017c592 from
                       ####5d41402abc4b2a76b9719d911017c592###

  --no-banner          Removes banner from startup.
  --no-john            Don't print John The Ripper Information.
  --no-hashcat         Don't print Hashcat Information.
  -v, --verbose        Turn on debugging logs. -vvv for maximum logs.
  --help               Show this message and exit.
```

### Examples

#### Text as input

```bash
nth --text 5f4dcc3b5aa765d61d8327deb882cf99
```

#### File as input

```bash
nth --file unknownhash.txt
```

#### Decode hashes in Base64 before identification

```bash
nth --text 5f4dcc3b5aa765d61d8327deb882cf99 -b64
```

#### Output as JSON

```bash
nth --text 5f4dcc3b5aa765d61d8327deb882cf99 -g 
```

#### Hide the banner

```bash
nth --text 5f4dcc3b5aa765d61d8327deb882cf99 --no-banner 
```

#### Hide the banner and only show Most likely

```bash
nth --text 5f4dcc3b5aa765d61d8327deb882cf99 --accessible 
```

### Related pages

{{< related_pages_table tag="password-cracking" >}}

### Also see

[Github Project](https://github.com/HashPals/Name-That-Hash)