

**Ubuntu**
`/etc/systemd/resolv.conf | system.conf | user.conf | timesyncd.conf | networkd.conf | journald.conf`



`/usr/bin/journalctl -r (reverse) | -n 20 (20 most recent) | -f (what in realtime) | --utc
            -k (kernel =  dmesg) | -u ssh (services)
            --since=yesterday --until=now
            --since "2022-08-09 00:01:18" --until="2022-08-10 00:00:01"
            --output=verbose|json|json-pretty
            -e (jump to end of the journal log)
            -x (show extra info)`
            
 
