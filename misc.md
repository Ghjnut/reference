Jenkins
-------
### PR Builder
#### Setup
Source Code Management -> Git -> Repositories -> Advanced
- Name: `origin`
- Refspec: `+refs/pull/*:refs/remotes/origin/pr/*`
Source Code Management -> Git -> Branches to Build
- Branch Specifier: `${sha1}`

#### Comments
- Can one of the admins verify this patch?
- ok to test
- test this please
- add to whitelist
- retest this please


Nagios
------
`/usr/local/nagios/`
`/usr/local/nagios/etc/nrpd.cfg` - Plugin config (shell commands)
`/usr/local/nagios/libexec/` - Plugins (check scripts)

Network
-------
#### Connections
`sudo netstat -lnput`

#### curl only headers
`curl -s -D - 127.0.0.1 -o /dev/null`

#### TCP Traffic monitoring
`tcpdump -n dst port 25`

#### ngrep for full payload
`ngrep -q -d eth1 -W byline port 25`

RAILS
-----
#### Dump to db/structure.sql
`bundle exec rake RUBY_ENV=production db:structure:dump`
#### Start mini-server
`bundle exec rake RUBY_ENV=production -s`

Libvirt
-------
`while read line; do virsh vol-delete $line; done < volumes`
`virsh vol-list default |awk '{print $2}' |grep -v Path | grep -v '^$' > volumes`
