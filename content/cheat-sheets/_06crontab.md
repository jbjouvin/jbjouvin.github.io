+++ 
date = "1979-01-01"
title = "crontab"
description = "crontab"
+++


<h2 id=Crontab>Crontab</h2>

<img src=https://i.stack.imgur.com/R4e9r.png height=400 width=600>

```sh
# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

