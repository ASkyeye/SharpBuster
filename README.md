# SharpBuster
This is a C# implementation of a directory brute forcing tool. I hacked this together in a night over a 6 pack of IPAs so it is in early stages. Usability and reliability updates will come in the next week.

## Why another directory brute forcing tool?
I couldn't find one written in C# for use with tools such as Cobalt Strike's execute-assembly, where it's not feasible to perform directory fuzzing over a SOCKS proxy.

There's also an option to download a wordlist from a remote host to avoid dropping files to disk.

## Usage
Using a wordlist on disk:

SharpBuster.exe -u http://google.com -w C:\Windows\Users\Public\wordlist.txt

Downloading a wordlist from a remote host:

SharpBuster.exe -u http://google.com --wordlisturl http://example.com/wordlist.txt

Run with extensions appended to the wordlist:

SharpBuster.exe -u http://google.com --wordlisturl http://example.com/wordlist.txt -e php,aspx

Run with extensions and recurse through directories: (Note: recursion is in the works)

SharpBuster.exe -u http://google.com --wordlisturl http://example.com/wordlist.txt -e php,aspx --recursion true

## Help
```shell
Options:
  -u | --url        The URL to brute force
  -w | --wordlist   The full path to the wordlist to use
  --wordlisturl     URL of wordlist to use to avoid writing to disk
  -e | --ext        A comma separated list of extensions to append, ex: php,asp,aspx
  -r | --recursive  Perform a recurisve search
  --username        Username for basic authentication
  --password        Password for authentication
  --proxy           Address of proxy to use, ex: http://127.0.0.1:8080
  --proxy-creds     Credentials to use to authenticate to proxy, ex: username:password
  --cookie          Cookie to use, ex: myCookie=value | If multiple cookies are being used, separate them with a comma
  -h | --help       Show help information
```
