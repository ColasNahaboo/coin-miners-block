# coin-miners-block
A simple bash script to bans sites in /etc/hosts, from an anti-coin-miner "Anti-WebMiner" blacklist at https://github.com/greatis/Anti-WebMiner

Very useful to run on a Linux server that serves as gateway to Windows machines.

Install by copying it in your PATH, e.g. `/usr/local/bin`, and set it up to be run as root in the crontab, with `-y`

Changes performed to `/etc/hosts` are logged in `/var/log/coin-miners-block.log`

Options:
-   `-n`       (default): do nothing, just prints what would be done
-   `-y`       modify the /etc/hosts file, silent mode
    -   `-e file`  after a modification, execute the file. Can be repeated

## Examples of use

Example of crontab entry:
`00 06 * * * coin-miners-block -y -e /etc/hosts.triggers`

Example of trigger file contents (/etc/hosts.triggers above):
`/etc/init.d/dnsmasq restart >/tmp/dnsmask.restart.log 2>&1`

Example of what is added to `/etc/hosts`

```
###################### BEGIN Anti-WebMiner blacklist
# Anti-WebMiner Start 1.86 43431
0.0.0.0 0x1f4b0.com
0.0.0.0 1q2w3.fun
0.0.0.0 1q2w3.life
...
0.0.0.0 zzqhsrg.ru
# Anti-WebMiner End
###################### END Anti-WebMiner blacklist
```



## License

(C) 2017 Colas Nahaboo http://colas.nahaboo.net, MIT license
