# Job and CronJob Worksheet

__Task 6, step 2: How many jobs run? How many run at the same time?__


```
There were 8 total job runs since the completions was set at 8.  At a time only 2 jobs ran, since the parallelism is set at 2.
```

__Task 6, step 5: What you observe when running the CronJob?__

```
It ran for 8 times and 2 execution at each invocation per the schedule defined in the cron
that is every minute.  
[hregupathy@WFILv2-031 manifests]$ kubectl get cronjobs
NAME       SCHEDULE    SUSPEND   ACTIVE   LAST SCHEDULE   AGE
cron-app   * * * * *   False     1        14s             4m42s
[hregupathy@WFILv2-031 manifests]$ kubectl get pods
NAME                      READY   STATUS      RESTARTS   AGE
cron-app-28509027-clw45   0/1     Completed   0          92s
cron-app-28509027-km5vb   0/1     Completed   0          96s
cron-app-28509027-l7nfr   0/1     Completed   0          84s
cron-app-28509027-lt2jw   0/1     Completed   0          96s
cron-app-28509027-nlp74   0/1     Completed   0          88s
cron-app-28509027-p8f96   0/1     Completed   0          88s
cron-app-28509027-rzcz2   0/1     Completed   0          85s
cron-app-28509027-sgvmf   0/1     Completed   0          92s
cron-app-28509028-7gp4d   0/1     Completed   0          36s
cron-app-28509028-8d9g6   0/1     Completed   0          32s
cron-app-28509028-9vhtq   0/1     Completed   0          32s
cron-app-28509028-d48nr   0/1     Completed   0          28s
cron-app-28509028-fbb7j   0/1     Completed   0          36s
cron-app-28509028-wqzg7   0/1     Completed   0          28s
cron-app-28509028-zdjm8   0/1     Completed   0          24s
cron-app-28509028-ztfps   0/1     Completed   0          24s


```