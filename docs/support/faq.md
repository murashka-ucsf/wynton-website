# Frequently Asked Questions (FAQs)

## Jobs

**Q**. _My submitted job is still in the queue - why is it not running?_

**A**. There could be several reason why your job is not running:
  1. If you have access to the members.q queue, it could be that you and other users in your lab are currently using all your slots, which in case your jobs are being queued in the communal long.q queue instead.
  2. The queue where your job is sitting may be full. If so, your job will eventually run.
  3. You might have asked for compute resources that cannot be met, e.g. more memory or more cores than available on any compute node, e.g. `-l mem=4048gb` or `-pe smp 256`.  If so, your job will never run.  Either lower the job's resource needs using `qdel`, or, alternatively,  remove the job (`qdel`) and submit (`qsub`) a new one with adjusted resources.
  4. You might have asked for compute resources that you do not have access to.  For instance, graphical processing units (GPUs) are currently only available to groups who have contributed with their own GPU hardware.  If so, please remove your job from the queue (`qdel`).
  5. `qstat -j <job_id>` will provide details on why a particular job is not running.  `qstat -u '*'` will show all jobs and their priority scores in the queue.


## Errors

**Q**. _I just started to get SSL-related errors when using `qsub` and `qstat` that I have never seen before;_
```
error: commlib error: ssl connect error (SSL handshake error)
ssl error (the used certificate is expired)
unable to contact qmaster using port 6444 on host "q"
```

**A**. Your Wynton account has expired.  If so, you should already have received an email from us with instructions on how to request the renewal.  If you have responded to that email, then it's a mistake on our end (sorry) - please drop us another email.