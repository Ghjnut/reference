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

GPG Sharing
-----------
1. Import public key
```
-bash-4.4$ gpg --import someone.public
gpg: key ABCDEF12: public key "Their Name <their_email@example.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
2. encrypt
```
-bash-4.4$ gpg -e -r their_email@example.com -s password_file

You need a passphrase to unlock the secret key for
user: "My Name <my_email@example.com>"
4096-bit RSA key, ID 01234567, created 2016-07-06

gpg: XXXXXXXX: There is no assurance this key belongs to the named user

pub  2048R/XXXXXXXX 2017-09-28 Their Name <their_email@example.com>
 Primary key fingerprint: AAAA BBBB CCCC DDDD EEEE  FFFF 0000 1111 2222 3333
      Subkey fingerprint: AAAA BBBB CCCC DDDD EEEE  FFFF 0000 1111 2222 3333

It is NOT certain that the key belongs to the person named
in the user ID.  If you *really* know what you are doing,
you may answer the next question with yes.

Use this key anyway? (y/N) y
```
