# coin-miners-block
A simple bash script to bans sites in /etc/hosts, from an anti-coin-miner "Anti-WebMiner" blacklist at https://github.com/greatis/Anti-WebMiner
Must be run as root in the crontab, with -y
Changes are logged in /var/log/coin-miners-block.log

Options:
-   -n       (default): do nothing, just prints what would be done
-   -y       modify the /etc/hosts file, silent mode
-   -e file  after a modification, execute the file. Can be repeated

Example of crontab entry:
`00 06 * * * coin-miners-block -y -e /etc/hosts.triggers`

Example of trigger file contents (/etc/hosts.triggers above):
`/etc/init.d/dnsmasq restart >/tmp/dnsmask.restart.log 2>&1`

(C) 2017 Colas Nahaboo http://colas.nahaboo.net, MIT license
