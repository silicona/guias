# Cron

Sacar el crontab del ordenador - Ejecutar `sudo crontab -e`

minute hour    mday    month   wday    who     command

`*/5    *       *       *       *       root    /usr/libexec/atrun`

`* 		* * * * tar -czcf /var/backups/copia-.tgz.gz /home/linux`
