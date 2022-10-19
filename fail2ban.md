# fail2ban

> Il est vivement déconseillé de modifier
> les fichiers de configuration `/etc/fail2ban/fail2ban.conf`
> et `/etc/fail2ban/jail.conf`
> (notamment car ils peuvent être écrasés par une mise à jour).
> Ces fichiers contiennent les configurations de base
> qu'on peut surcharger au moyen d'un ou plusieurs fichiers enregistrés dans `/etc/fail2ban/jail.d`
> Le fichier `/etc/fail2ban/jail.conf` doit servir uniquement de référence et de documentation.
[Source](https://doc.ubuntu-fr.org/fail2ban#configuration)

So /etc/fail2ban/jail.d/custom.conf will be used

`bantime` so the ban time
`findtime` the duration to look for fail

See list of jails
`fail2ban-client status`
Control a specific jail (sshd)
`fail2ban-client [start|stop|status] sshd`
`Currently failed` is the number of failed login but not yet ban
See also `[recidive]` section

Ban manually an ip
`fail2ban-client set [nom du jail] banip [IP à bannir]`

List of possible jails
`/etc/fail2ban/filter.d`

How to check config?
