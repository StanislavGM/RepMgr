# RepMgr

#ommands:
$repmgr -f $repconf primary register
$repmgr -f $repconf primmary unregister -F
$repmgr -f $repconf standby register
$repmgr -U repmgr -d repdb -h <primary_host> -f $repconf standby clone
$repmgr -f $repconf node service --action=restart --checkpoint
$repmgr standby switchover -f $repconf --siblings-follow -R postgres
$repmgr node rejoin -f $repconf -d 'host=<primary_host>  user=repmgr dbname=repdb password=abc' --force-rewind --config-files=postgresql.local.conf,postgresql.conf -v
